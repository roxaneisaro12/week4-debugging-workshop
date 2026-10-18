# Week 4: Debugging Workshop

## Introduction

This document explains six JavaScript errors found in `errors.html`. For each snippet, I identify the error type, explain why it occurs, and show the corrected code.

## Exercise 1: ReferenceError

**Error type:** ReferenceError

**Problem:** The variable is declared as `studentName`, but the code uses `studentname`. JavaScript is case-sensitive, so these are treated as different variable names.

**Incorrect code:**

```javascript
const studentName = "Aline";
console.log("Welcome, " + studentname);
```

**Corrected code:**

```javascript
const studentName = "Aline";
console.log("Welcome, " + studentName);
```

**How I fixed it:** I checked the variable name and corrected the capitalization so the code uses the declared variable.

## Exercise 2: TypeError

**Error type:** TypeError

**Problem:** The method `toUppercase()` is written with incorrect capitalization. The correct JavaScript string method is `toUpperCase()`.

**Incorrect code:**

```javascript
const city = "Kigali";
console.log(city.toUppercase());
```

**Corrected code:**

```javascript
const city = "Kigali";
console.log(city.toUpperCase());
```

**How I fixed it:** I checked the method name and corrected its capitalization. The code now prints `KIGALI`.

## Exercise 3: TypeError caused by an incorrect selector

**Error type:** TypeError

**Problem:** The selector `#page-titel` contains a spelling mistake. If no element matches this selector, `document.querySelector()` returns `null`. Trying to set `textContent` on `null` causes a TypeError.

**Incorrect code:**

```javascript
const title = document.querySelector("#page-titel");
title.textContent = "My Tasks";
```

**Corrected code:**

```javascript
const title = document.querySelector("#page-title");
title.textContent = "My Tasks";
```

**How I fixed it:** I checked the selector and corrected `page-titel` to `page-title`. The HTML must contain an element with `id="page-title"` for the selector to find it.

## Exercise 4: TypeError caused by reassignment of a constant

**Error type:** TypeError

**Problem:** A variable declared with `const` cannot be reassigned. The code attempts to change `score` from `0` to `10`.

**Incorrect code:**

```javascript
const score = 0;
score = score + 10;
console.log(score);
```

**Corrected code:**

```javascript
let score = 0;
score = score + 10;
console.log(score);
```

**How I fixed it:** I replaced `const` with `let` because the value needs to change. The output is `10`.

## Exercise 5: SyntaxError

**Error type:** SyntaxError

**Problem:** A comma is missing between `"avocado"` and `"banana"` in the array. This makes the array declaration invalid JavaScript syntax.

**Incorrect code:**

```javascript
const fruits = ["mango", "avocado" "banana"];
console.log(fruits.length);
```

**Corrected code:**

```javascript
const fruits = ["mango", "avocado", "banana"];
console.log(fruits.length);
```

**How I fixed it:** I added the missing comma between the second and third array elements. The output is `3`.

## Exercise 6: RangeError caused by infinite recursion

**Error type:** RangeError

**Problem:** The function calls itself repeatedly without a stopping condition. Eventually, JavaScript exceeds the maximum call stack size.

**Incorrect code:**

```javascript
function countdown(n) {
  console.log(n);
  countdown(n - 1);
}

countdown(5);
```

**Corrected code:**

```javascript
function countdown(n) {
  if (n < 0) {
    return;
  }

  console.log(n);
  countdown(n - 1);
}

countdown(5);
```

**How I fixed it:** I added a base case, `if (n < 0) return;`, to stop the recursion when the countdown reaches the stopping condition. The output is `5`, `4`, `3`, `2`, `1`, and `0`.

## Conclusion

This exercise helped me understand how to identify and fix common JavaScript errors. I learned to check variable names, method names, DOM selectors, variable declarations, syntax, and recursion stopping conditions. These techniques make debugging easier and help me write more reliable JavaScript code.
