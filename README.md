
# 1. Event Handling in React

In normal **HTML**, events are written like this:

```html
<button onclick="myFunction()">Click</button>
```

But in **React**, events work a little differently.

React uses **camelCase event names** and JavaScript functions.

Example:

```jsx
<button onClick={handleClick}>Click</button>
```

---

# 2. Adding Event Handler (Way 1)

The most common way is **creating a function and passing it to the button**.

```jsx
export default function Button() {

  function handleClick() {
    alert("You clicked me!");
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}
```

### Explanation

* `handleClick` is a function.
* It is passed to the `<button>` as a **prop**.
* React calls it when the button is clicked.

So:

* **handleClick → event handler**
* **onClick → event**

---

# 3. Inline Event Handler in JSX

Instead of defining a function separately, we can define it **directly inside JSX**.

```jsx
<button onClick={function handleClick() {
  alert("You clicked me!");
}}>
  Click
</button>
```

This works, but it’s usually **less clean** than defining a function separately.

---

# 4. Using Anonymous Function in JSX

Another common way is using **arrow functions**.

```jsx
<button onClick={() => {
  alert("You clicked me!");
}}>
  Click me
</button>
```

This method is often used when the logic is **small and simple**.

---

# 5. Event Handler Naming Convention

In React, event handlers usually follow this pattern:

```
handle + EventName
```

Examples:

```
handleClick
handleMouseEnter
handleSubmit
```

Example:

```jsx
<button onClick={handleClick}>
```

This naming convention makes code **clean and easy to understand**.

---

# 6. Important Rule: Pass Function, Don't Call It

A function should be **passed**, not **called**.

Correct ✅

```jsx
<button onClick={handleClick}>
```

Wrong ❌

```jsx
<button onClick={handleClick()}>
```

If you call it like this, the function will run **every time the component renders**, not when the user clicks.

---

# 7. Inline Function Warning

Correct:

```jsx
<button onClick={() => alert("Clicked")}>
```

Wrong:

```jsx
<button onClick={alert("Clicked")}>
```

The wrong one runs **immediately when the component loads**.

---

# 8. Event Propagation

Event propagation means **events move through the DOM tree**.

Example:

If a button is inside a div:

* Clicking the button
* May also trigger the div event.

React follows the same concept.

---

# 9. Preventing Default Behavior

Sometimes forms automatically **refresh the page** when submitted.

To prevent that, we use:

```jsx
event.preventDefault()
```

Example:

```jsx
function handleSubmit(event) {
  event.preventDefault();
  console.log("Form submitted");
}
```

---

# 10. Introduction to React Hooks

Today I also learned about **React Hooks**.

Hooks allow us to **use React features inside functional components**.

One of the most common hooks is:

```
useState()
```

---

# 11. useState Concept

`useState` is used to **store and update data inside a component**.

Example:

```jsx
const [count, setCount] = useState(0);
```

Here:

* `count` → state value
* `setCount` → function to update the state

---

# 12. Different Types of Initialization in useState()

We can initialize state with different data types.

### Number

```jsx
const [count, setCount] = useState(0);
```

### Boolean

```jsx
const [isLoggedIn, setIsLoggedIn] = useState(false);
```

### String

```jsx
const [name, setName] = useState("John");
```

### Array

```jsx
const [items, setItems] = useState([]);
```

### Object

```jsx
const [user, setUser] = useState({
  name: "Rahim",
  age: 20
});
```

### Null

```jsx
const [data, setData] = useState(null);
```

---

# 13. State Update Function

The second value from `useState` is the **update function**.

Example:

```jsx
setCount(count + 1);
```

React uses this function to **update the UI automatically**.

This happens **under the hood using React’s re-rendering system**.

---

# 14. Loading Dynamic Data

I also learned how React loads **dynamic data from APIs**.

There are several ways to do this.

---

### 1. Using async / await

```jsx
async function getData(){
  const response = await fetch(url);
}
```

---

### 2. Using React use() (Modern React)

React now provides a **use() hook** for handling promises in some cases.

---

### 3. Using useEffect (Traditional Way)

Previously, developers used:

```
useEffect()
```

to fetch data when the component loads.

Example:

```jsx
useEffect(()=>{
 fetchData()
},[])
```

But newer React patterns are evolving.

---


# 📌 Summary

Today I learned several important React concepts:

✅ Different ways to handle events
✅ Inline event handlers
✅ Arrow functions in event handlers
✅ Event propagation
✅ Preventing default form behavior
✅ Introduction to React hooks
✅ useState for managing state
✅ Initializing state with different data types
✅ Loading dynamic data using async/await and other methods


