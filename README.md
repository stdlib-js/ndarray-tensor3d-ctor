<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# Tensor3D

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Create a three-dimensional [ndarray][@stdlib/ndarray/ctor].

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/ndarray-tensor3d-ctor
```

Alternatively,

-   To load the package in a website via a `script` tag without installation and bundlers, use the [ES Module][es-module] available on the [`esm`][esm-url] branch (see [README][esm-readme]).
-   If you are using Deno, visit the [`deno`][deno-url] branch (see [README][deno-readme] for usage intructions).
-   For use in Observable, or in browser/node environments, use the [Universal Module Definition (UMD)][umd] build available on the [`umd`][umd-url] branch (see [README][umd-readme]).

The [branches.md][branches-url] file summarizes the available branches and displays a diagram illustrating their relationships.

To view installation and usage instructions specific to each branch build, be sure to explicitly navigate to the respective README files on each branch, as linked to above.

</section>

<section class="usage">

## Usage

```javascript
var tensor3d = require( '@stdlib/ndarray-tensor3d-ctor' );
```

#### tensor3d( \[dtype]\[, options] )

Returns a three-dimensional [ndarray][@stdlib/ndarray/ctor] having a specified [data type][@stdlib/ndarray/dtypes].

```javascript
var getDType = require( '@stdlib/ndarray-dtype' );
var getShape = require( '@stdlib/ndarray-shape' );

var arr = tensor3d();
// returns <ndarray>

var sh = getShape( arr );
// returns [ 0, 0, 0 ]

var dt = String( getDType( arr ) );
// returns 'float64'
```

By default, the function returns an [ndarray][@stdlib/ndarray/ctor] having a [`float64`][@stdlib/ndarray/dtypes] data type. To specify an alternative [data type][@stdlib/ndarray/dtypes], provide a `dtype` argument.

```javascript
var getDType = require( '@stdlib/ndarray-dtype' );
var getShape = require( '@stdlib/ndarray-shape' );

var arr = tensor3d( 'int32' );
// returns <ndarray>

var sh = getShape( arr );
// returns [ 0, 0, 0 ]

var dt = String( getDType( arr ) );
// returns 'int32'
```

The function accepts the following arguments:

-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options.

The function accepts the following options:

-   **order**: specifies whether an [ndarray][@stdlib/ndarray/ctor] is `'row-major'` (C-style) or `'column-major'` (Fortran-style). Default: `'row-major'`.
-   **mode**: specifies how to handle indices which exceed array dimensions (see [`ndarray`][@stdlib/ndarray/ctor]). Default: `'throw'`.
-   **submode**: a mode array which specifies for each dimension how to handle subscripts which exceed array dimensions (see [`ndarray`][@stdlib/ndarray/ctor]). If provided fewer modes than dimensions, an [`ndarray`][@stdlib/ndarray/ctor] instance recycles modes using modulo arithmetic. Default: `[ options.mode ]`.
-   **readonly**: boolean indicating whether an array should be **read-only**. Default: `false`.

#### tensor3d( K, M, N\[, dtype]\[, options] )

Returns a three-dimensional [ndarray][@stdlib/ndarray/ctor] having a specified shape.

```javascript
var getShape = require( '@stdlib/ndarray-shape' );

var arr1 = tensor3d( 5, 5, 5 );
// returns <ndarray>

var sh1 = getShape( arr1 );
// returns [ 5, 5, 5 ]

var arr2 = tensor3d( 3, 3, 3, 'uint8' );
// returns <ndarray>

var sh2 = getShape( arr2 );
// returns [ 3, 3, 3 ]
```

The function accepts the following arguments:

-   **K**: number of elements in the first dimension.
-   **M**: number of elements in the second dimension.
-   **N**: number of elements in the last dimension.
-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options. See above.

#### tensor3d( shape\[, dtype]\[, options] )

Returns a three-dimensional [ndarray][@stdlib/ndarray/ctor] having a specified shape.

```javascript
var getShape = require( '@stdlib/ndarray-shape' );

var arr1 = tensor3d( [ 5, 5, 5 ] );
// returns <ndarray>

var sh1 = getShape( arr1 );
// returns [ 5, 5, 5 ]

var arr2 = tensor3d( [ 3, 3, 3 ], 'uint8' );
// returns <ndarray>

var sh2 = getShape( arr2 );
// returns [ 3, 3, 3 ]
```

The function accepts the following arguments:

-   **shape**: array shape. Must contain exactly three elements.
-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options. See above.

#### tensor3d( obj\[, dtype]\[, options] )

Creates a three-dimensional [ndarray][@stdlib/ndarray/ctor] from an array-like object or iterable.

```javascript
var getShape = require( '@stdlib/ndarray-shape' );

var data = [ [ [ 1.0, 2.0 ], [ 3.0, 4.0 ] ], [ [ 5.0, 6.0 ], [ 7.0, 8.0 ] ] ];

var arr1 = tensor3d( data );
// returns <ndarray>

var sh1 = getShape( arr1 );
// returns [ 2, 2, 2 ]

var arr2 = tensor3d( [ [ [ 1.0, 2.0 ], [ 3.0, 4.0 ] ] ], 'float32' );
// returns <ndarray>

var sh2 = getShape( arr2 );
// returns [ 1, 2, 2 ]
```

The function accepts the following arguments:

-   **obj**: array-like object or iterable from which to generate an [ndarray][@stdlib/ndarray/ctor]. If an array-like object, the value must be a doubly nested array (i.e., an array-like object of array-like objects of array-like objects), where the nested arrays at each depth must have the same number of elements. If an iterable, the iterable must return nested array-like objects, each of which must have the same number of elements.
-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options. See above.

#### tensor3d( buffer\[, byteOffset\[, K, M, N]]\[, dtype]\[, options] )

Returns a three-dimensional [ndarray][@stdlib/ndarray/ctor] view of an [`ArrayBuffer`][@stdlib/array/buffer].

```javascript
var ArrayBuffer = require( '@stdlib/array-buffer' );
var getDType = require( '@stdlib/ndarray-dtype' );
var getShape = require( '@stdlib/ndarray-shape' );

var buf = new ArrayBuffer( 32 );

var arr1 = tensor3d( buf );
// returns <ndarray>

var sh1 = getShape( arr1 );
// returns [ 1, 1, 4 ]

var dt1 = String( getDType( arr1 ) );
// returns 'float64'

var arr2 = tensor3d( buf, 'float32' );
// returns <ndarray>

var sh2 = getShape( arr2 );
// returns [ 1, 1, 8 ]

var dt2 = String( getDType( arr2 ) );
// returns 'float32'

var arr3 = tensor3d( buf, 16 );
// returns <ndarray>

var sh3 = getShape( arr3 );
// returns [ 1, 1, 2 ]

var dt3 = String( getDType( arr3 ) );
// returns 'float64'

var arr4 = tensor3d( buf, 16, 'float32' );
// returns <ndarray>

var sh4 = getShape( arr4 );
// returns [ 1, 1, 4 ]

var dt4 = String( getDType( arr4 ) );
// returns 'float32'

var arr5 = tensor3d( buf, 8, 1, 2, 1 );
// returns <ndarray>

var sh5 = getShape( arr5 );
// returns [ 1, 2, 1 ]

var dt5 = String( getDType( arr5 ) );
// returns 'float64'

var arr6 = tensor3d( buf, 10, 1, 2, 2, 'int16' );
// returns <ndarray>

var sh6 = getShape( arr6 );
// returns [ 1, 2, 2 ]

var dt6 = String( getDType( arr6 ) );
// returns 'int16'
```

The function accepts the following arguments:

-   **buffer**: underlying [`ArrayBuffer`][@stdlib/array/buffer].
-   **byteOffset**: integer byte offset specifying the location of the first indexed element. Default: `0`.
-   **K**: number of elements in the first dimension.
-   **M**: number of elements in the second dimension.
-   **N**: number of elements in the last dimension.
-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options. See above.

#### tensor3d( buffer\[, byteOffset\[, shape]]\[, dtype]\[, options] )

Returns a three-dimensional [ndarray][@stdlib/ndarray/ctor] view of an [`ArrayBuffer`][@stdlib/array/buffer].

```javascript
var ArrayBuffer = require( '@stdlib/array-buffer' );
var getDType = require( '@stdlib/ndarray-dtype' );
var getShape = require( '@stdlib/ndarray-shape' );

var buf = new ArrayBuffer( 32 );

var arr1 = tensor3d( buf, 8, [ 1, 2, 1 ] );
// returns <ndarray>

var sh1 = getShape( arr1 );
// returns [ 1, 2, 1 ]

var dt1 = String( getDType( arr1 ) );
// returns 'float64'

var arr2 = tensor3d( buf, 10, [ 1, 2, 2 ], 'int16' );
// returns <ndarray>

var sh2 = getShape( arr2 );
// returns [ 1, 2, 2 ]

var dt2 = String( getDType( arr2 ) );
// returns 'int16'
```

The function accepts the following arguments:

-   **buffer**: underlying [`ArrayBuffer`][@stdlib/array/buffer].
-   **byteOffset**: integer byte offset specifying the location of the first indexed element. Default: `0`.
-   **shape**: array shape. Must contain exactly three elements.
-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options. See above.

#### tensor3d.factory( dtype\[, options] )

Returns a function for creating a three-dimensional [ndarray][@stdlib/ndarray/ctor].

```javascript
var getDType = require( '@stdlib/ndarray-dtype' );
var getShape = require( '@stdlib/ndarray-shape' );

var Float32Tensor3D = tensor3d.factory( 'float32' );

var arr = new Float32Tensor3D( [ [ [ 1.0, 2.0 ], [ 3.0, 4.0 ] ] ] );
// returns <ndarray>

var dt = String( getDType( arr ) );
// returns 'float32'

var sh = getShape( arr );
// returns [ 1, 2, 2 ]
```

The function accepts the following arguments:

-   **dtype**: [data type][@stdlib/ndarray/dtypes].
-   **options**: function options (_optional_).

The function accepts the following options:

-   **order**: specifies whether the default memory layout for a returned [ndarray][@stdlib/ndarray/ctor] should be `'row-major'` (C-style) or `'column-major'` (Fortran-style). Default: `'row-major'`.
-   **mode**: specifies the default behavior when handling indices which exceed array dimensions (see [`ndarray`][@stdlib/ndarray/ctor]). Default: `'throw'`.
-   **submode**: specifies the default behavior for each dimension when handling subscripts which exceed array dimensions (see [`ndarray`][@stdlib/ndarray/ctor]). If provided fewer modes than dimensions, an [`ndarray`][@stdlib/ndarray/ctor] instance recycles modes using modulo arithmetic. Default: `[ options.mode ]`.
-   **readonly**: boolean indicating whether to return a **read-only** [ndarray][@stdlib/ndarray/ctor] by default. Default: `false`.

The function returned by the `factory` method supports the same arguments and options as `tensor3d` above, except for the `dtype` argument, as the returned function always returns a three-dimensional [ndarray][@stdlib/ndarray/ctor] having the same [data type][@stdlib/ndarray/dtypes].

When providing options to the returned function, the provided option values override the defaults established during function creation.

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

## Notes

-   Nested arrays are flattened in lexicographic order, such that, for an input nested array `obj`, `obj[i][j][k]` corresponds to the element `tensor.get(i, j, k)` in the returned three-dimensional ndarray. In other words, an input nested array is assumed to be comprised of matrices (i.e., two-dimensional arrays). Similarly, if `obj` is an iterable, each nested array returned by the iterable is assumed to correspond to an element along the first dimension.
-   If provided an `ArrayBuffer` without corresponding shape arguments, the leading dimensions of the returned ndarray always have a size of one.

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
var discreteUniform = require( '@stdlib/random-discrete-uniform' );
var cartesianProduct = require( '@stdlib/array-cartesian-product' );
var unzip = require( '@stdlib/utils-unzip' );
var dtypes = require( '@stdlib/ndarray-dtypes' );
var ndarray2array = require( '@stdlib/ndarray-to-array' );
var sum = require( '@stdlib/blas-ext-sum' );
var logEachMap = require( '@stdlib/console-log-each-map' );
var tensor3d = require( '@stdlib/ndarray-tensor3d-ctor' );

// Create an array of random shapes:
var shapes = discreteUniform( [ 10, 3 ], 2, 8, {
    'dtype': 'int32'
});

// Resolve a list of supported ndarray integer-valued data types:
var dts = dtypes( 'integer_and_generic' );

// Create shape-dtype pairs:
var pairs = cartesianProduct( ndarray2array( shapes ), dts );

// Split the pairs into individual arguments:
var args = unzip( pairs );

// Define a callback to create a random three-dimensional ndarray and return the sum of all ndarray elements:
function clbk( shape, dtype ) {
    var buf = ndarray2array( discreteUniform( shape, 0, 100 ) );
    var x = tensor3d( buf, dtype );
    return sum( x ).get();
}

// Apply the callback and print the results:
logEachMap( 'shape: [%3s]. dtype: %7s. sum: %d.', args[ 0 ], args[ 1 ], clbk );
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-tensor3d-ctor.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-tensor3d-ctor

[test-image]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-tensor3d-ctor/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-tensor3d-ctor?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-tensor3d-ctor.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-tensor3d-ctor/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/tree/deno
[deno-readme]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/tree/umd
[umd-readme]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/tree/esm
[esm-readme]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ndarray-tensor3d-ctor/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-tensor3d-ctor/main/LICENSE

[@stdlib/array/buffer]: https://github.com/stdlib-js/array-buffer

[@stdlib/ndarray/ctor]: https://github.com/stdlib-js/ndarray-ctor

[@stdlib/ndarray/dtypes]: https://github.com/stdlib-js/ndarray-dtypes

</section>

<!-- /.links -->
