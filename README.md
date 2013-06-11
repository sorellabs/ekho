Ekho
====

[![Build Status](https://travis-ci.org/killdream/ekho.png)](https://travis-ci.org/killdream/ekho)
[![Dependencies Status](https://david-dm.org/killdream/ekho.png)](https://david-dm.org/killdream/ekho)

A DOM-agnostic eventing library with bubbling.


## Example

```js
// Inherit from Eventful
var Thing = Eventful.derive({
  say:
  function _say(message) {
    this.trigger('say', message)
  }
})

// Instantiate
var foo = Thing.make()
var bar = Thing.make(foo) // bar events will bubble to foo

// Attach some listeners
foo.on('say', function(a) {
  console.log('foo:', a)
})

bar.on('say', function(a) {
  console.log('bar:', a)
})

// Then trigger the events
bar.say('Hello')
// => bar: Hello
// => foo: Hello

foo.say('Hello')
// => foo: Hello
```


## Installing

    $ npm install ekho
    

## Platform support

This library assumes an ES5 environment, but can be easily supported in ES3
platforms by the use of shims. Just include [es5-shim][] :3

[es5-shim]: https://github.com/kriskowal/es5-shim

[![browser support](https://ci.testling.com/killdream/polygamous.png)](http://ci.testling.com/killdream/polygamous)


## Licence

MIT/X11. i.e.: Do whatever you fucking want, bro.
