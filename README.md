# RxJS Observable Example

This is an example of using RxJS `Observable` to demonstrate how values are emitted synchronously and asynchronously.

## Code Example

```javascript
import { Observable } from "rxjs";

const observable = new Observable((subscriber) => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  setTimeout(() => {
    subscriber.next(4);
    subscriber.complete();
  }, 1000);
});

console.log("just before subscribe");
observable.subscribe({
  next(x) {
    console.log("got value " + x);
  },
  error(err) {
    console.error("something wrong occurred: " + err);
  },
  complete() {
    console.log("done");
  },
});
console.log("just after subscribe");
```

## Explanation

1. **Observable Creation**:

   - The `Observable` is created using `new Observable()`, where the function passed to it is executed every time an observer subscribes.
   - It emits the values `1`, `2`, and `3` synchronously.
   - After 1 second, it emits the value `4` and completes the sequence.

2. **Subscription**:

   - The `subscribe()` method is used to observe the emitted values from the observable.
   - It takes three callbacks:
     - `next`: executed for each emitted value.
     - `error`: executed if an error occurs (not used in this example).
     - `complete`: executed once the observable finishes emitting values.

3. **Output**:
   - When you run this code, the following will be printed to the console:
     ```
     just before subscribe
     got value 1
     got value 2
     got value 3
     just after subscribe
     got value 4
     done
     ```

## How to Run

1. Make sure you have RxJS installed in your project:

   ```bash
   npm install rxjs
   ```

2. Save the code in a JavaScript file, for example `observable-example.js`.

3. Run the file using Node.js:
   ```bash
   node observable-example.js
   ```

## Resources

- This is simply the getting started documentation from below:

- [RxJS Documentation](https://rxjs.dev/guide/observable)
