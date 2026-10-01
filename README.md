# Login & Signup Form

A simple Login and Signup form built with **React.js**.

I made this project mainly to understand how React state works and how the UI can change based on the current state. The form switches between Login and Signup without refreshing the page.

## Tech Used

* React.js
* JavaScript
* JSX
* CSS

## Project Structure

```text
src/
│
├── App.js
├── App.css
│
└── components/
    ├── Assets/
    │   ├── person.png
    │   ├── email.png
    │   └── password.png
    │
    └── LoginSignup/
        ├── LoginSignup.jsx
        └── LoginSignup.css
```

## What I Built

The form has two states:

* **Sign Up**
* **Login**

When the page loads, it starts with **Sign Up**.

If I click **Login**, the form changes to Login mode. If I click **Sign Up**, it switches back.

The main thing I wanted to understand here was how React can update the UI automatically when a state changes.

---

## 1. Using `useState`

I used React's `useState` hook for keeping track of whether the user is on Login or Signup.

```jsx
const [action, setAction] = useState("Sign Up");
```

Here:

* `action` stores the current value.
* `setAction` is used to change that value.
* `"Sign Up"` is the initial value.

So initially:

```text
action = "Sign Up"
```

When I click Login, I change it using:

```jsx
setAction("Login");
```

And when I click Sign Up:

```jsx
setAction("Sign Up");
```

---

## 2. Why I Used `action`

I used `action` to control different parts of the form.

For example:

```jsx
<div className="text">{action}</div>
```

Instead of hardcoding:

```jsx
<div className="text">Sign Up</div>
```

the heading now depends on the state.

If `action` is `"Sign Up"`:

```text
Sign Up
```

If `action` is `"Login"`:

```text
Login
```

This makes the UI dynamic.

---

## 3. Using `onClick`

The Login button has:

```jsx
onClick={() => setAction("Login")}
```

So whenever I click Login, React runs:

```jsx
setAction("Login")
```

The state changes and React updates the UI.

For Sign Up:

```jsx
onClick={() => setAction("Sign Up")}
```

This changes the state back to Signup mode.

---

## 4. Why I Used the Ternary Operator

I used the **ternary operator** because some parts of the form should only appear in one of the two states.

The basic syntax is:

```jsx
condition ? valueIfTrue : valueIfFalse
```

It is basically a shorter way of writing an `if-else` condition.

---

## 5. Showing the Name Field Only During Signup

A Name field is required when creating an account, but it isn't needed when logging in.

So I used:

```jsx
{action === "Login" ? <div></div> : <div className="input">
    <img src={user_icon} alt="" />
    <input type="text" placeholder="Name" />
</div>}
```

The condition is:

```jsx
action === "Login"
```

If the user is in Login mode, the Name field is hidden.

If the user is in Signup mode, the Name field is shown.

So:

```text
Login   → Name hidden
Sign Up → Name visible
```

---

## 6. Showing Forgot Password Only During Login

Forgot Password doesn't make much sense on the Signup screen, so I only show it when the user is logging in.

```jsx
{action === "Sign Up"
    ? <div></div>
    : <div className="forgot-password">
        Forgot Password?
        <span>Click Here!</span>
      </div>
}
```

This gives:

```text
Sign Up → Forgot Password hidden
Login   → Forgot Password visible
```

---

## 7. Changing the Button Style

I also used a ternary operator to change the class of the buttons.

For Login:

```jsx
className={action === "Login" ? "submit gray" : "submit"}
```

If Login is the current state, it gets:

```text
submit gray
```

Otherwise it gets:

```text
submit
```

I did the same thing for the Sign Up button:

```jsx
className={action === "Sign Up" ? "submit gray" : "submit"}
```

This helps show which mode is currently selected.

---

# How It Works

### When the page first loads

```text
action = "Sign Up"
```

So:

```text
Heading          → Sign Up
Name field       → Visible
Forgot Password  → Hidden
Sign Up button   → Selected
```

### When I click Login

```text
setAction("Login")
```

The state changes to:

```text
action = "Login"
```

React then updates the UI:

```text
Heading          → Login
Name field       → Hidden
Forgot Password  → Visible
Login button     → Selected
```

### When I click Sign Up again

```text
setAction("Sign Up")
```

The state changes back:

```text
action = "Sign Up"
```

and the UI changes back to Signup mode.

---

## What I Learned

While making this project, I mainly learned how:

* `useState` stores changing values.
* `setAction()` updates the state.
* `onClick` handles user interaction.
* React automatically re-renders when state changes.
* Ternary operators can be used for conditional rendering.
* The same state can control multiple parts of the UI.
* `className` can also be changed dynamically based on state.

## Current Limitations

This is currently a **frontend project**. The form doesn't create real accounts or authenticate users yet.

The next step would be connecting it to a backend and database so that Signup and Login actually work with stored user information.

## Future Improvements

Some things I can add later:

* Real Login and Signup functionality
* Backend API
* Database
* Password validation
* Show/Hide password
* Forgot password functionality
* Form validation
* Authentication using JWT
* Responsive design

---

## Final Note

This project was mainly built to get comfortable with **React state and conditional rendering**.

The important part for me wasn't just creating the form UI, but understanding how changing one state variable like:

```jsx
setAction("Login");
```

can automatically change different parts of the page.
