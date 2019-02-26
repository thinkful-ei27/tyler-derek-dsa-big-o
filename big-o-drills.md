# Even or odd
```
function isEven(value){
  if (value % 2 == 0){
    return true;
  }
  else
    return false;
}
```
*O(1)* because it's one operation that doesn't care what size the input is.

# Are you here?
```
function areYouHere(arr1, arr2) {
    for (let i=0; i<arr1.length; i++) {
        const el1 = arr1[i];
        for (let j=0; j<arr2.length; j++) {
            const el2 = arr2[j];
            if (el1 === el2) return true;
        }
    }
    return false;
}
```
*O(n^2)* because a `for` loop nested inside of another `for` loop.

# Doubler
```
function doubleArrayValues(array) {
    for (let i=0; i<array.length; i++) {
        array[i] *= 2;
    }
    return array;
}
```
*O(n)* because it has one `for` loop. It only has one operation, but it scales with the input size.

# Naive Search
```
function naiveSearch(array, item) {
    for (let i=0; i<array.length; i++) {
        if (array[i] === item) {
            return i;
        }
    }
}
```
Best case is *O(1)*, worst case is *O(n)* because it may need to go through every item in the array.

# Creating pairs:
```
function createPairs(arr) {
    for (let i = 0; i < arr.length; i++) {
        for(let j = i+1; j < arr.length; j++) {
            console.log(arr[i] + ", " +  arr[j] );
        }
    }
}
```
*O(n^2)* because of the nested `for` loops.

# Computing fibonaccis
```
function generateFib(num) {
  let result = [];
  for (let i = 1; i <= num; i++) {

    // we're adding the first item
    // to the result list, append the
    // number 0 to results
    if (i === 1) {
      result.push(0);
    }
    // ...and if it's the second item
    // append 1
    else if (i == 2) {
      result.push(1);
    }

    // otherwise, sum the two previous result items, and append that value to results.
    else {
      result.push(result[i - 2] + result[i - 3]);
    }
  }
  // once the for loop finishes
  // we return `result`.
  return result;
}
```
*O(n)* because it only loops through every number up to `num` once.

# An Efficient Search
```
function efficientSearch(array, item) {
    let minIndex = 0;
    let maxIndex = array.length - 1;
    let currentIndex;
    let currentElement;

    while (minIndex <= maxIndex) {
        currentIndex = Math.floor((minIndex + maxIndex) / 2);
        currentElement = array[currentIndex];

        if (currentElement < item) {
            minIndex = currentIndex + 1;
        }
        else if (currentElement > item) {
            maxIndex = currentIndex - 1;
        }
        else {
            return currentIndex;
        }
    }
    return -1;
}
```
*O(log(n))* because it halves the array each time it runs.

# Random element
```
function findRandomElement(arr) {
    return arr[Math.floor(Math.random() * arr.length)];
}
```
*O(1)* because it only does one operation regardless of input size.

# Is it prime?
```
function isPrime(n) {
    // if n is less than 2 or a decimal, it's not prime
    if (n < 2 || n % 1 != 0) {
        return false;
    }
    // otherwise, check if `n` is divisible by any integer
    // between 2 and n.
    for (let i = 2; i < n; ++i) {
        if (n % i == 0) return false;
    }
    return true;
}
```
Best case is *O(1)* because of the `if` statement. Worst case is *O(n)* because the number of times the loop runs scales with the input.

# Counting Sheep 
## Recursive
```
function countSheep(num){
    //stopping condition of base case
    if(num === 0){
        console.log(`All sheep jumped over the fence`);
    } 
    //this is the recursive case
    //this will be executed until it reaches base case
    else{
        console.log(`${num}: Another sheep jump over the fence`);
        countSheep(num-1);
    }
}
```
Best case is *O(1)* if input is 0. Otherwise, it's *O(n)* because it is essentially a loop counting down.

## Iterative
```
function countSheepLoop(num){
    for(let i=num; i>0; i--){
        console.log(`counting sheeps ${i}`);
    }
}
```
*O(n)* because the number of times the loop runs depends on the `num` given to it.

# Array Double
## Recursive
```
function double_all(arr) {
    if (!arr.length) {
        return [];
    }
    return [arr[0] * 2, ...double_all(arr.slice(1))];
}
```
*O(n)* because as the array gets longer, the number of calls increases proportionally to the length of the input.

## Iterative
```
function double_all(arr) {
    var ret = Array(arr.length);
    for (var i = 0; i < arr.length; ++i) {
        ret[i] = arr[i] * 2;
    }
    return ret;
}
```
*O(n)* because it's another `for` loop.

# Reverse String
## Recursive
```
function reverseString(str) {
    if (str.length < 2) {
        return str;
    }
    return reverseString(str.slice(1)) + str[0];
}
```
*O(n)* because it runs on every character in the string, so as the string lengthens, it runs more times.

## Iterative
```
function reverse_tail(str) {
    var accumulator = "";
    while (str !== "") {
    	accumulator = str[0] + accumulator;
    	str = str.slice(1);
    }
    return accumulator;
}
```
*O(n)* because it's a another loop over all the characters in the string. See above.

# Triangular Number
## Recursive
```
function triangle(n) {
    if (n < 2) 
        return n;
    return n + triangle(n - 1);
}
```
*O(n)* because it's essentially another countdown loop.

## Iterative