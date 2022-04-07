## Iterators

Lots of kinds

- for...
- for...in
- for...of
- map
- forEach
- reduce
- filter

The ones marked `Async friendly` will work with `promises` and `async/await` within the loop. The `Not Async friendly` will NOT work because the loop will not wait for the async functions to complete. The loop will resolve immediately. In the case of `map`, you'll just be left with an array of pending `promises`.

### for...

_\*Async friendly_

The classic for loop is the most versatile and works in async situations as well. Your go to when you are unsure of what to use:

```js
const heroes = ["batman", "spider-man", "bananaman"];
for (let i = 0; i < heroes.length; i++) {
  console.log(heroes[i]);
}
```

### for...in

_\* Not Async friendly_

A great way to get the keys of an object is to use the `for...in` iterator. You
can then use that key to grab the corresponding value in the object. I would use this for object iteration.

```js
const honda = {
  car: "honda",
  type: "automobile",
  fans: "many",
};

for (let key in honda) {
  console.log(`this is the key ${key}`);
  console.log(`this is the value ${honda[key]}`);
}
```

More involved example...

### for...of

_\*Async friendly_

Where `for...in` will give you the property names of the object, `for...of` will give you the values. This is great for iterating over array values.

```js
const superHeroes = ["spider-man", "batman", "superman"];

for (let hero of superHeroes) {
  console.log(`hero: ${hero}`);
}
```

### map

_\* Not Async friendly_

If you want to go through some values and slap it into an array, use `map`. It will take a custom callback where the first `arg` is each individual value and the second as the index. The following will upper case each hero name:

```js
const superHeroes = ["spider-man", "batman", "superman"];

const array = superHeroes.map((hero) => {
  return hero.toUpperCase();
});

console.log(array);
```

### forEach

_\* Not Async friendly_

If you want to just go through the values and not produce anything, use `forEach`. This will just log each value, similar to `for...of`. The callback is similar to `map`, 1st arg is the value, 2nd arg is the index:

```js
const superHeroes = ["spider-man", "batman", "superman"];

superHeroes.forEach((hero, index) => {
  console.log(hero, index);
});
```

### filter

_\* Not Async friendly_

Filter, as its name suggests, includes values that you want and stores them in an array. This function will only include values that have `spider` in the name. Filter will include values where the callback returns `true`:

```js
const superHeroes = ["spider-man", "spider-woman", "superman", "squirral"];

const spiders = superHeroes.filter((hero) => hero.includes("spider"));

console.log(spiders);
```

### reduce

_\* Not Async friendly_

Reduce will take for example a bunch of values and reduce those values into a given initial value. The callback supplied will have the `previousValue` and the `currentValue`. The 2nd arg to reduce is the `initialValue`. The following will reduce all the letters in the array in to a single word.

```js
const letters = ["h", "e", "l", "l", "o", " ", "w", "o", "r", "l", "d"];

const initialValue = "";
const fullWord = letters.reduce((prevValue, currentValue) => {
  console.log(prevValue);
  return prevValue + currentValue;
}, initialValue);

console.log(fullWord);
```
