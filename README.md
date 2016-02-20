# Generatorics

### A combinatorics library for JavaScript utilizing ES2015 generators. Generate combinations, permutations, and power sets of arrays or strings.

- Node
```
npm install generatorics
```
```javascript
var G = require('generatorics');
```

- Browser
```
bower install generatorics
```
```html
<script src="file/path/to/generatorics.js"></script>
```


## Usage

### Power Set
```javascript
for (var subset of G.powerSet(['a', 'b', 'c'])) {
  console.log(subset);
}
// [ ]
// [ 'a' ]
// [ 'a', 'b' ]
// [ 'a', 'b', 'c' ]
// [ 'a', 'c' ]
// [ 'b' ]
// [ 'b', 'c' ]
// [ 'c' ]
```

### permutation
```javascript
for (var perm of G.permutation(['a', 'b', 'c'], 2)) {
  console.log(perm);
}
// [ 'a', 'b' ]
// [ 'a', 'c' ]
// [ 'b', 'a' ]
// [ 'b', 'c' ]
// [ 'c', 'a' ]
// [ 'c', 'b' ]

for (var perm of G.permutation(['a', 'b', 'c'])) { // assumes full length of array
  console.log(perm);
}
// [ 'a', 'b', 'c' ]
// [ 'a', 'c', 'b' ]
// [ 'b', 'a', 'c' ]
// [ 'b', 'c', 'a' ]
// [ 'c', 'b', 'a' ]
// [ 'c', 'a', 'b' ]
```

### combination
```javascript
for (var comb of G.combination(['a', 'b', 'c'], 2)) {
  console.log(comb);
}
// [ 'a', 'b' ]
// [ 'a', 'c' ]
// [ 'b', 'c' ]
```

For efficiency, each array being yielded is the same one being mutated on each iteration.
```javascript
var combs = [];
for (var comb of G.combination(['a', 'b', 'c'], 2)) {
  combs.push(comb);
}
console.log(combs);
// [ [ 'b', 'c' ], [ 'b', 'c' ], [ 'b', 'c' ] ]
```

You can clone if necessary.
```javascript
var combs = [];
for (var comb of G.combination(['a', 'b', 'c'], 2)) {
  combs.push(comb.slice()); // slice with no args is an idiomatic way to clone an array
}
console.log(combs);
// [ [ 'a', 'b' ], [ 'a', 'c' ], [ 'b', 'c' ] ]
```

### permutation of combination
```javascript
for (var perm of G.permutationCombination(['a', 'b', 'c'])) {
  console.log(perm);
}
// [ ]
// [ 'a' ]
// [ 'a', 'b' ]
// [ 'a', 'b', 'c' ]
// [ 'a', 'c' ]
// [ 'a', 'c', 'b' ]
// [ 'b' ]
// [ 'b', 'a' ]
// [ 'b', 'a', 'c' ]
// [ 'b', 'c' ]
// [ 'b', 'c', 'a' ]
// [ 'c' ]
// [ 'c', 'a' ]
// [ 'c', 'a', 'b' ]
// [ 'c', 'b' ]
// [ 'c', 'b', 'a' ]
```

### cartesian product
```javascript
for (var prod of G.cartesian([0, 1, 2], [0, 10, 20], [0, 100, 200])) {
  console.log(prod);
}
// [ 0, 0, 0 ],  [ 0, 0, 100 ],  [ 0, 0, 200 ]
// [ 0, 10, 0 ], [ 0, 10, 100 ], [ 0, 10, 200 ]
// [ 0, 20, 0 ], [ 0, 20, 100 ], [ 0, 20, 200 ]
// [ 1, 0, 0 ],  [ 1, 0, 100 ],  [ 1, 0, 200 ]
// [ 1, 10, 0 ], [ 1, 10, 100 ], [ 1, 10, 200 ]
// [ 1, 20, 0 ], [ 1, 20, 100 ], [ 1, 20, 200 ]
// [ 2, 0, 0 ],  [ 2, 0, 100 ],  [ 2, 0, 200 ]
// [ 2, 10, 0 ], [ 2, 10, 100 ], [ 2, 10, 200 ]
// [ 2, 20, 0 ], [ 2, 20, 100 ], [ 2, 20, 200 ]
```

### base N
```javascript
for (var num of G.baseN(['a', 'b', 'c'])) {
  console.log(num);
}
// [ 'a', 'a', 'a' ], [ 'a', 'a', 'b' ], [ 'a', 'a', 'c' ]
// [ 'a', 'b', 'a' ], [ 'a', 'b', 'b' ], [ 'a', 'b', 'c' ]
// [ 'a', 'c', 'a' ], [ 'a', 'c', 'b' ], [ 'a', 'c', 'c' ]
// [ 'b', 'a', 'a' ], [ 'b', 'a', 'b' ], [ 'b', 'a', 'c' ]
// [ 'b', 'b', 'a' ], [ 'b', 'b', 'b' ], [ 'b', 'b', 'c' ]
// [ 'b', 'c', 'a' ], [ 'b', 'c', 'b' ], [ 'b', 'c', 'c' ]
// [ 'c', 'a', 'a' ], [ 'c', 'a', 'b' ], [ 'c', 'a', 'c' ]
// [ 'c', 'b', 'a' ], [ 'c', 'b', 'b' ], [ 'c', 'b', 'c' ]
// [ 'c', 'c', 'a' ], [ 'c', 'c', 'b' ], [ 'c', 'c', 'c' ]
```

## Documentation

<a name="module_G"></a>
## G

* [G](#module_G)
    * [.factorial(n)](#module_G.factorial) ⇒ <code>Number</code>
    * [.factoradic(n)](#module_G.factoradic) ⇒ <code>Array</code>
    * [.P(n, r)](#module_G.P) ⇒ <code>Number</code>
    * [.C(n, r)](#module_G.C) ⇒ <code>Number</code>
    * [.combination(arr, [size])](#module_G.combination) ⇒ <code>Generator</code>
    * [.permutation(arr, [size])](#module_G.permutation) ⇒ <code>Generator</code>
    * [.powerSet(arr)](#module_G.powerSet) ⇒ <code>Generator</code>
    * [.permutationCombination(arr)](#module_G.permutationCombination) ⇒ <code>Generator</code>
    * [.baseN(arr, [size])](#module_G.baseN) ⇒ <code>Generator</code>
    * [.cartesian(...sets)](#module_G.cartesian) ⇒ <code>Generator</code>

<a name="module_G.factorial"></a>
### G.factorial(n) ⇒ <code>Number</code>
Calculates a factorial

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Number</code> - n!  

| Param | Type | Description |
| --- | --- | --- |
| n | <code>Number</code> | The number to operate the factorial on. |

<a name="module_G.factoradic"></a>
### G.factoradic(n) ⇒ <code>Array</code>
Converts a number to the factorial number system. Digits are in least significant order.

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Array</code> - digits of n in factoradic in least significant order  

| Param | Type | Description |
| --- | --- | --- |
| n | <code>Number</code> | Integer in base 10 |

<a name="module_G.P"></a>
### G.P(n, r) ⇒ <code>Number</code>
Calculates the number of possible permutations of "r" elements in a set of size "n".

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Number</code> - n P r  

| Param | Type | Description |
| --- | --- | --- |
| n | <code>Number</code> | Number of elements in the set. |
| r | <code>Number</code> | Number of elements to choose from the set. |

<a name="module_G.C"></a>
### G.C(n, r) ⇒ <code>Number</code>
Calculates the number of possible combinations of "r" elements in a set of size "n".

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Number</code> - n C r  

| Param | Type | Description |
| --- | --- | --- |
| n | <code>Number</code> | Number of elements in the set. |
| r | <code>Number</code> | Number of elements to choose from the set. |

<a name="module_G.combination"></a>
### G.combination(arr, [size]) ⇒ <code>Generator</code>
Generates all combinations of a set.

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Generator</code> - yields each combination as an array  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| arr | <code>Array</code> &#124; <code>String</code> |  | The set of elements. |
| [size] | <code>Number</code> | <code>arr.length</code> | Number of elements to choose from the set. |

<a name="module_G.permutation"></a>
### G.permutation(arr, [size]) ⇒ <code>Generator</code>
Generates all permutations of a set.

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Generator</code> - yields each permutation as an array  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| arr | <code>Array</code> &#124; <code>String</code> |  | The set of elements. |
| [size] | <code>Number</code> | <code>arr.length</code> | Number of elements to choose from the set. |

<a name="module_G.powerSet"></a>
### G.powerSet(arr) ⇒ <code>Generator</code>
Generates all possible subsets of a set (a.k.a. power set).

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Generator</code> - yields each subset as an array  

| Param | Type | Description |
| --- | --- | --- |
| arr | <code>Array</code> &#124; <code>String</code> | The set of elements. |

<a name="module_G.permutationCombination"></a>
### G.permutationCombination(arr) ⇒ <code>Generator</code>
Generates the permutation of the combinations of a set.

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Generator</code> - yields each permutation as an array  

| Param | Type | Description |
| --- | --- | --- |
| arr | <code>Array</code> &#124; <code>String</code> | The set of elements. |

<a name="module_G.baseN"></a>
### G.baseN(arr, [size]) ⇒ <code>Generator</code>
Generates all possible "numbers" from the digits of a set.

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Generator</code> - yields all digits as an array  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| arr | <code>Array</code> &#124; <code>String</code> |  | The set of digits. |
| [size] | <code>Number</code> | <code>arr.length</code> | How many digits will be in the numbers. |

<a name="module_G.cartesian"></a>
### G.cartesian(...sets) ⇒ <code>Generator</code>
Generates the cartesian product of the sets.

**Kind**: static method of <code>[G](#module_G)</code>  
**Returns**: <code>Generator</code> - yields each product as an array  

| Param | Type | Description |
| --- | --- | --- |
| ...sets | <code>Array</code> &#124; <code>String</code> | Variable number of sets of n elements. |

