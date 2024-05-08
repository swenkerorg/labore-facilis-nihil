# @swenkerorg/labore-facilis-nihil <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2015 spec-compliant `Array.prototype.keys` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://www.ecma-international.org/ecma-262/6.0/).

Because `Array.prototype.keys` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var keys = require('@swenkerorg/labore-facilis-nihil');
var assert = require('assert');
var iterate = require('iterate-iterator');

assert.deepEqual(iterate(keys([1, 2, 3])), [0, 1, 2]);
assert.deepEqual(iterate(keys([1, 0, 1])), [0, 1, 2]);
assert.deepEqual(iterate(keys([NaN])), [0]);
assert.deepEqual(iterate(keys([1,,3])), [0, 1, 2]);
```

```js
var keys = require('@swenkerorg/labore-facilis-nihil');
var assert = require('assert');
/* when Array#keys is not present */
delete Array.prototype.keys;
var shimmedMap = keys.shim();
assert.deepEqual(shimmedMap, keys.getPolyfill());
assert.deepEqual(iterate([1, 2, 3].keys()), [0, 1, 2]);
assert.deepEqual(iterate([1, 0, 1].keys()), [0, 1, 2]);
assert.deepEqual(iterate([NaN].keys()), [0]);
assert.deepEqual(iterate([1,,3].keys()), [0, 1, 2]);
```

```js
var keys = require('@swenkerorg/labore-facilis-nihil');
var assert = require('assert');
/* when Array#keys is present */
var shimmedMap = keys.shim();
assert.equal(shimmedMap, Array.prototype.keys);
assert.deepEqual(iterate([1, 2, 3].keys()), [0, 1, 2]);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@swenkerorg/labore-facilis-nihil
[npm-version-svg]: https://versionbadg.es/swenkerorg/labore-facilis-nihil.svg
[deps-svg]: https://david-dm.org/swenkerorg/labore-facilis-nihil.svg
[deps-url]: https://david-dm.org/swenkerorg/labore-facilis-nihil
[dev-deps-svg]: https://david-dm.org/swenkerorg/labore-facilis-nihil/dev-status.svg
[dev-deps-url]: https://david-dm.org/swenkerorg/labore-facilis-nihil#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@swenkerorg/labore-facilis-nihil.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@swenkerorg/labore-facilis-nihil.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@swenkerorg/labore-facilis-nihil.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@swenkerorg/labore-facilis-nihil
[codecov-image]: https://codecov.io/gh/swenkerorg/labore-facilis-nihil/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/swenkerorg/labore-facilis-nihil/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/swenkerorg/labore-facilis-nihil
[actions-url]: https://github.com/swenkerorg/labore-facilis-nihil/actions
