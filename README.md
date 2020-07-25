# Enhanced reducer
[![NPM](https://nodei.co/npm/enhanced-reducer.png)](https://nodei.co/npm/enhanced-reducer/)

An enhanced version of react's `useReducer` which supports middleware and static `getState` callback.

# API

`export const useEnhancedReducer`

- Parameters `(reducer, initState, initializer, middlewares = [])`
- Return `[state, dispatch, getState]`

The `useEnhancedReducer` is fully compatible with `useReducer`.
The returned value is sample as of `useReducer`, except the additional last value `getState`.

The `getState` is guaranteed to unchanged (like `dispatch`).

`useEnhancedReducer` also accepts `middlewares` parameter.

Sample middleware:

```javascript
const logMiddleware = state => getState => next => action => {
  console.log('before action', action, getState())
  next(action)
  console.log('after action', action, getState()) // *NOTE*: because `dispatch(action)`` is not synchronous. it does not guarantee that this getState() call return the value after the action is applied.
}
```

# Usage samples and tests
Check [my blog post](https://transang.me/get-state-callback-with-usereducer/) or these two codepens: [1](https://codepen.io/tranvansang/pen/JjGYPNP), [2](https://codepen.io/tranvansang/pen/gOPapKx).
