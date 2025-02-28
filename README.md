# Javascript Quick functions

Most of you probably already know them, lodash/underscore was built to provide utility functions for common tasks in Javascript. But some you don’t want to install a package for small use case. So I created this file to provide a quick access to the most used functions. I hope you will find it useful.

### [Demo & Reference](https://devsmitra.github.io/javascript-quick-functions)

---

# Table of contents

[Functions](#functions)

- [Regular function](#regular-function)
- [Function expression](#function-expression)
- [Arrow function](#arrow-function)
- [Generator function](#generator-function)
- [Time the execution of your code](#time-the-execution-of-your-code)
- [Evaluate a string](#evaluate-a-string)

[Array](#array)

- [Create an array of numbers from 1 to n](#create-an-array-of-numbers-from-1-to-n)
- [Create an array of numbers from 1 to n with a step](#create-an-array-of-numbers-from-1-to-n-with-a-step)
- [Create an array and fill it with a value](#create-an-array-and-fill-it-with-a-value)
- [Shuffling an array](#shuffling-an-array)
- [Convert an object into a list of `[key, value]` pairs](#convert-an-object-into-a-list-of-key-value-pairs)
- [Convert a list of `[key, value]` pairs into an object](#convert-a-list-of-key-value-pairs-into-an-object)
- [Remove an element from an array](#remove-an-element-from-an-array)
- [Remove Duplicated from Array](#remove-duplicated-from-array)
- [Swap variables or values](#swap-variables-or-values)

[Numbers](#numbers)

- [Generate random number](#generate-random-number)
- [Generate random number with a step](#generate-random-number-with-a-step)
- [Number is even or not](#number-is-even-or-not)
- [Number is odd or not](#number-is-odd-or-not)
- [Find the factorial of a number](#find-the-factorial-of-a-number)
- [Find the sum of an array](#find-the-sum-of-an-array)
- [Find median of an array](#find-median-of-an-array)
- [Find largest numbers](#find-largest-numbers)
- [Find average of Numbers](#find-average-of-numbers)
- [Find smallest numbers](#find-smallest-numbers)
- [Find mode of an array](#find-mode-of-an-array)
- [Find the range of an array](#find-the-range-of-an-array)
- [Pick a random element from an array](#pick-a-random-element-from-an-array)
- [Map an array without .map()](#map-an-array-without-map)
- [Empty an array without .splice()](#empty-an-array-without-splice)
- [Convert array to object](#convert-array-to-object)
- [Find intersection of two arrays](#find-intersection-of-two-arrays)
- [Remove falsy values from an array](#remove-falsy-values-from-an-array)
- [Rounding number to N decimal place](#rounding-number-to-n-decimal-place)

[String](#string)

- [Reverse String](#reverse-string)
- [Find Longest Word in a String](#find-longest-word-in-a-string)
- [Generate Title Case](#generate-title-case)
- [Is String Palindrome](#is-string-palindrome)
- [Copy to Clipboard](#copy-to-clipboard)
- [Find a vowel in a string](#find-a-vowel-in-a-string)
- [Email validator](#email-validator)
- [Validate only character and space](#validate-only-character-and-space)
- [Validate only number](#validate-only-number)
- [Casting values in arrays using map](#casting-values-in-arrays-using-map)

[Date & Object](#date--object)

- [Check object is empty or not](#check-object-is-empty-or-not)
- [Get the current date](#get-the-current-date)
- [Find the day of the week](#find-the-day-of-the-week)
- [Find the day of the year](#find-the-day-of-the-year)
- [Find the number of days in a month](#find-the-number-of-days-in-a-month)
- [Find the current month](#find-the-current-month)
- [Find the number of seconds until midnight](#find-the-number-of-seconds-until-midnight)
- [Log Time from Date](#log-time-from-date)
- [Format JSON output with spaces](#format-json-output-with-spaces)
- [Deep clone an object](#deep-clone-an-object)

[Promises](#promises)

- [Wait for a promise to resolve](#wait-for-a-promise-to-resolve)
- [Is function async](#is-function-async)
- [Callback to Promise](#callback-to-promise)
- [Promise retry](#promise-retry)

[Styling](#styling)

- [Generate a random color](#generate-a-random-color)
- [Convert to rem](#convert-to-rem)
- [Styled Components get color from theme](#styled-components-get-color-from-theme)

[Window & Dom](#window--dom)

- [Get selected text](#get-selected-text)

[Data Structures](#data-structures)

- [Create a stack](#create-a-stack)
- [Create a queue](#create-a-queue)
- [Recursion](#recursion)
- [Memoization (cache)](#memoization-cache)

# Functions

### Regular function

```javascript
function sum(a, b) {
  return a + b;
}
```

### Function expression

```javascript
const sum = function (a, b) {
  return a + b;
};
```

### Arrow function

```javascript
const sum = (a, b) => {
  return a + b;
};
// OR
const sum = (a, b) => a + b;
```

### Generator function

```javascript
function* indexGenerator() {
  let index = 0;
  while (true) {
    yield index++;
  }
}
const g = indexGenerator();
console.log(g.next().value); // => 0
console.log(g.next().value); // => 1
```

### Time the execution of your code

```javascript
console.time("time");
for (let i = 0; i < 1000000; i++) {
  // do something
}
console.timeEnd("time"); // time: 0.827ms
```

### Evaluate a string

```javascript
const toJavascript = (str) => eval(str);
toJavascript("alert('Hello World')");
```

# Array

### Create an array of numbers from 1 to n

```javascript
const range = (n) => Array.from({ length: n }, (_, i) => i + 1);
console.log(range(10)); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### Create an array of numbers from 1 to n with a step

```javascript
const range = (n, step = 1) => Array.from({ length: n }, (_, i) => i * step);
console.log(range(10, 2)); // [1, 3, 5, 7, 9]
```

### Create an array and fill it with a value

```javascript
const fill = (len, value) => Array(len).fill(value);
console.log(fill(3, 0)); // [0, 0, 0]
```

### Shuffling an array

```javascript
const shuffleArray = (arr) => arr.sort(() => 0.5 - Math.random());
console.log(shuffleArray([1, 2, 3, 4])); // [3, 2, 1, 4]
```

### Convert an object into a list of `[key, value]` pairs

```javascript
const toPairs = (obj) => Object.entries(obj);
console.log(toPairs({ a: 1, b: 2, c: 3 })); // [['a', 1], ['b', 2], ['c', 3]]
```

### Convert a list of `[key, value]` pairs into an object

```javascript
const fromPairs = (pairs) =>
  pairs.reduce((a, b) => ({ ...a, [b[0]]: b[1] }), {});
console.log(
  fromPairs([
    ["a", 1],
    ["b", 2],
    ["c", 3],
  ])
); // { a: 1, b: 2, c: 3 }
```

### Remove an element from an array

```javascript
const removeElement = (arr, element) => arr.filter((e) => e !== element);
console.log(removeElement([1, 2, 3, 4], 2)); // [1, 3, 4]
```

### Remove Duplicated from Array

```javascript
const removeDuplicated = (arr) => [...new Set(arr)];
console.log(removeDuplicated([1, 2, 3, 3, 4, 4, 5, 5, 6])); // Result: [ 1, 2, 3, 4, 5, 6 ]

const removeDuplicate = (arr) =>
  Object.values(arr.reduce((a, b) => (a[b] ? a : { ...a, [b]: b }), {}));
console.log(removeDuplicate([1, 2, 3, 3])); // Result: [ 1, 2, 3, ]
```

### Swap variables or values

```javascript
const swap = (a, b) => [b, a];
let a = 1,
  b = 2;
[b, a] = swap(a, b);
console.log(a, b); // 2, 1
```

# Numbers

### Generate random number

```javascript
const random = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;
console.log(random(1, 10)); // Result: 1 ~ 10
```

### Generate random number with a step

```javascript
const random = (min, max, step = 1) =>
  Math.floor(Math.random() * (max - min + 1)) * step + min;
console.log(random(1, 10, 2)); // Result: 1 ~ 10 with step 2
```

### Number is even or not

```javascript
const isEven = (num) => num % 2 === 0;
console.log(isEven(4)); // true
```

### Number is odd or not

```javascript
const isOdd = (num) => num % 2 !== 0;
console.log(isOdd(4)); // false
```

### Find the factorial of a number

```javascript
const factorial = (num) => (num === 0 ? 1 : num * factorial(num - 1));
console.log(factorial(5)); // 120
```

### Find the sum of an array

```javascript
const sum = (arr) => arr.reduce((a, b) => a + b, 0);
console.log(sum([1, 2, 3, 4])); // 10
```

### Find median of an array

```javascript
const median = (arr) => {
  const mid = Math.floor(arr.length / 2),
    nums = [...arr].sort((a, b) => a - b);
  return arr.length % 2 !== 0 ? nums[mid] : (nums[mid - 1] + nums[mid]) / 2;
};
console.log(median([1, 2, 3, 4])); // 2.5
```

### Find largest numbers

```javascript
const findLargest = (arr) => arr.map((subArr) => Math.max(...subArr));
console.log(
  findLargest([
    [4, 5, 1, 3],
    [13, 27, 18, 26],
    [32, 35, 37, 39],
    [1000, 1001, 857, 1],
  ])
); // [5, 27, 39, 1001]
```

### Find average of Numbers

```javascript
const findAverage = (arr) => arr.reduce((a, b) => a + b, 0) / arr.length;
console.log(findAverage([1, 2, 3, 4])); // 2.5
```

### Find smallest numbers

```javascript
const findSmallest = (arr) => arr.map((subArr) => Math.min(...subArr));
console.log(
  findSmallest([
    [4, 5, 1, 3],
    [13, 27, 18, 26],
    [32, 35, 37, 39],
    [1000, 1001, 857, 1],
  ])
); // [1, 18, 32, 857]
```

### Find mode of an array

```javascript
const mode = (arr) => {
  const counts = arr.reduce((a, b) => {
    a[b] = (a[b] || 0) + 1;
    return a;
  }, {});
  const maxCount = Math.max(...Object.values(counts));
  return Object.keys(counts).filter((key) => counts[key] === maxCount);
};
console.log(mode([3, "a", "a", "a", 2, 3, "a", 3, "a", 2, 4, 9, 3])); // ['a']
```

### Find the range of an array

```javascript
const range = (arr) => Math.max(...arr) - Math.min(...arr);
console.log(range([1, 2, 3, 4])); // 3
```

### Pick a random element from an array

```javascript
const pick = (arr) => arr[Math.floor(Math.random() * arr.length)];
console.log(pick([1, 2, 3, 4])); // 2
```

### Map an array without .map()

```javascript
const map = (arr, cb) => Array.from(arr, cb);
console.log(map([1, 2, 3, 4], (n) => n * 2)); // [2, 4, 6, 8]
```

### Empty an array without .splice()

```javascript
const empty = (arr) => {
  arr.length = 0;
  return arr;
};
console.log(empty([1, 2, 3, 4])); // []
```

### Convert array to object

```javascript
const toObject = (arr) => ({ ...arr });
console.log(toObject(["a", "b"])); // { 0: 'a', 1: 'b' }
```

### Find intersection of two arrays

```javascript
const intersection = (arr1, arr2) => {
  const set = new Set(arr1);
  return arr2.filter((x) => set.has(x));
};
console.log(intersection([1, 2, 3], [2, 3, 4])); // [2, 3]
```

### Remove falsy values from an array

```javascript
const compact = (arr) => arr.filter(Boolean);
console.log(compact([0, 1, false, 2, "", 3, "a", "e" * 23, NaN, "s", 34])); // [1, 2, 3, 'a', 's', 34]
```

### Rounding number to N decimal place

```javascript
const round = (num, decimals = 0) => num.toFixed(decimals);
console.log(round(1.005, 2)); // 1.00
```

# String

### Reverse String

```javascript
const reverseString = (str) => str.split("").reverse().join("");
console.log(reverseString("hello")); // olleh
```

### Find Longest Word in a String

```javascript
const findLongestWord = (str) =>
  str.split(" ").reduce((a, b) => (a.length > b.length ? a : b));
console.log(findLongestWord("The quick brown fox jumped over the lazy dog")); // jumped
```

### Generate Title Case

```javascript
const titleCase = (str) =>
  str
    .split(" ")
    .map((word) => word[0].toUpperCase() + word.slice(1).toLowerCase())
    .join(" ");
console.log(titleCase("the quick brown fox")); // The Quick Brown Fox
```

### Is String Palindrome

```javascript
const isPalindrome = (str) => str === str.split("").reverse().join("");
console.log(isPalindrome("madam")); // true
```

### Copy to Clipboard

```javascript
const copyToClipboard = (text) => navigator.clipboard.writeText(text);
copyToClipboard("Hello World");
```

### Find a vowel in a string

```javascript
const findVowel = (str) => str.match(/[aeiou]/gi);
console.log(findVowel("hello")); // ['e', 'o']
```

### Email validator

```javascript
const validateEmail = (email) => {
    const re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
    return re.test(String(email).toLowerCase());
};
console.log(validateEmail('abc@aaa.co'); // true
```

### Validate only character and space

```javascript
const validateName = (name) => /^[A-Za-z\s]+$/.test(name);
console.log(validateName("abc")); // true
console.log(validateName("123")); // false
```

### Validate only number

```javascript
const validateNumber = (number) => /^[0-9]+$/.test(number);
console.log(validateNumber("123")); // true
console.log(validateNumber("abc")); // false
```

### Casting values in arrays using map

```javascript
const castArray = (arr) => arr.map(Number);
console.log(castArray(["1", "2", [3]])); // [1, 2, 3]
```

# Date & Object

### Check object is empty or not

```javascript
const isEmpty = (obj) => Object.keys(obj).length === 0;
console.log(isEmpty({})); // true
```

### Get the current date

```javascript
const getDate = () => new Date();
console.log(getDate()); // 2020-05-25T09:57:37.869Z
```

### Find the day of the week

```javascript
const getDayName = (date) => {
  const days = [
    "Sunday",
    "Monday",
    "Tuesday",
    "Wednesday",
    "Thursday",
    "Friday",
    "Saturday",
  ];
  return days[date.getDay()];
};
console.log(getDayName(new Date())); // Friday
```

### Find the day of the year

```javascript
const getDayOfYear = (date) => {
  const firstDay = new Date(date.getFullYear(), 0, 1);
  return Math.ceil((date - firstDay) / 86400000);
};
console.log(getDayOfYear(new Date())); // 182
```

### Find the number of days in a month

```javascript
const getDaysInMonth = (date) =>
  new Date(date.getFullYear(), date.getMonth() + 1, 0).getDate();
console.log(getDaysInMonth(new Date())); // 31
```

### Find the current month

```javascript
const getMonthName = (date) => {
  const months = [
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December",
  ];
  return months[date.getMonth()];
};
console.log(getMonthName(new Date())); // March
```

### Find the number of seconds until midnight

```javascript
const getSecondsUntilMidnight = (date) =>
  (24 - date.getHours()) * 60 * 60 +
  (60 - date.getMinutes()) * 60 +
  (60 - date.getSeconds());
console.log(getSecondsUntilMidnight(new Date())); // 86400
```

### Log Time from Date

```javascript
const logTime = (date) => date.toTimeString().slice(0, 8);
logTime(new Date()); // 09:57:37

const logTime = (date) => date.toLocaleTimeString("en-GB");
logTime(new Date()); // 09:57:37
```

### Format JSON output with spaces

```javascript
const formatJSON = (json) => JSON.stringify(json, null, 2);
console.log(formatJSON({ a: 1, b: 2 }));
```

### Deep clone an object

```javascript
const clone = (obj) => JSON.parse(JSON.stringify(obj));
console.log(clone({ a: 1, b: 2 })); // { a: 1, b: 2 }

// OR

const deepCopy = (obj, copy = {}) => {
  if (!obj || typeof obj !== "object") return obj;
  for (const key in obj) {
    if (obj.hasOwnProperty(key)) copy[key] = deepCopy(obj[key]);
  }
  return copy;
};
```

# Promises

### Wait for a promise to resolve

```javascript
const wait = (ms) => new Promise((resolve) => setTimeout(resolve, ms));
wait(1000).then(() => console.log("You'll see this after 1 second"));
await wait(1000); // Next line will be executed after 1 second
```

### Is function async

```javascript
const isAsync = (fn) => fn.constructor.name === "AsyncFunction";
console.log(isAsync(async () => {})); // true
```

### Callback to Promise

```javascript
const promisify =
  (fn) =>
  (...args) => {
    return new Promise((res, reject) =>
      fn(...args, (err, data) => (err ? reject(err) : res(data)))
    );
  };
```

### Promise retry

```javascript
const retry = (fn, times = 3) => {
  return (...args) =>
    new Promise((resolve, reject) => {
      const attempt = (n) => {
        fn(...args)
          .then(resolve)
          .catch((err) => {
            if (n === times) return reject(err);
            attempt(n + 1);
          });
      };
      attempt(1);
    });
};
```

# Styling

### Generate a random color

```javascript
const getRandomColor = () =>
  `#${Math.floor(Math.random() * 16777215).toString(16)}`;
console.log(getRandomColor()); // #f0f0f0

const randomHex = () =>
  `#${Math.floor(Math.random() * 0xffffff)
    .toString(16)
    .padEnd(6, "0")}`;
console.log(randomHex()); // #f0f0f0
```

### Convert to rem

```javascript
const toRem = (px) => `${px / 16}rem`;
console.log(toRem(16)); // 1rem
```

### Styled Components get color from theme

```javascript
Off topic but very useful

const getPrimaryMain = props => props.theme.main

const Button = styled.button`
    color: ${getPrimaryMain};
    border: 2px solid ${getPrimaryMain};
`;
```

# Window & Dom

### Get selected text

```javascript
const getSelectedText = () => window.getSelection().toString();
console.log(getSelectedText()); // Hello World
```

# Data Structures

### Create a stack

```javascript
const Stack = () => {
  let data = [];
  return {
    push(item) {
      data.push(item);
    },
    pop() {
      return data.pop();
    },
    peek() {
      return data[data.length - 1];
    },
    get length() {
      return data.length;
    },
  };
};
```

### Create a queue

```javascript
const Queue = () => {
  let data = [];
  return {
    push(item) {
      data.push(item);
    },
    pop() {
      return data.shift();
    },
    peek() {
      return data[0];
    },
    get length() {
      return data.length;
    },
  };
};
```

### Recursion

```javascript
const range = (n) => {
  if (n === 0) return;
  console.log(n);
  range(n - 1);
};
console.log(range(5));
```

### Memoization (cache)

Try the following code without memo and with memo.

```javascript
const fib = (n) => {
  if (n < 2) return n;
  return fib(n - 1, memo) + fib(n - 2, memo);
};
console.log(fib(40)); // Browser crash or timeout

const fib = (n, memo = {}) => {
  if (n < 2) return n;
  if (memo[n]) return memo[n];
  memo[n] = fib(n - 1, memo) + fib(n - 2, memo);
  return memo[n];
};
console.log(fib(40)); // 102334155
```

# Tools used

[Table of contents Builder](https://luciopaiva.com/markdown-toc/)
