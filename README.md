<a id="x-28CLACK-CORS-DOCS-2FINDEX-3A-40README-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

# clack-cors - A Clack middleware to set CORS related HTTP headers.

<a id="clack-cors-asdf-system-details"></a>

## CLACK-CORS ASDF System Details

* Description: A Clack middleware to set `CORS` related `HTTP` headers.
* Licence: Unlicense
* Author: Alexander Artemenko <svetlyak.40wt@gmail.com>
* Homepage: [https://40ants.com/clack-cors/][5c32]
* Bug tracker: [https://github.com/40ants/clack-cors/issues][b14f]
* Source control: [GIT][74db]
* Depends on: [alexandria][8236], [log4cl][7f8b], [serapeum][c41d]

[![](https://github-actions.40ants.com/40ants/clack-cors/matrix.svg?only=ci.run-tests)][1700]

![](http://quickdocs.org/badge/clack-cors.svg)

<a id="x-28CLACK-CORS-DOCS-2FINDEX-3A-3A-40INSTALLATION-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## Installation

You can install this library from Quicklisp, but you want to receive updates quickly, then install it from Ultralisp.org:

```
(ql-dist:install-dist "http://dist.ultralisp.org/"
                      :prompt nil)
(ql:quickload :clack-cors)
```
<a id="x-28CLACK-CORS-DOCS-2FINDEX-3A-3A-40USAGE-2040ANTS-DOC-2FLOCATIVES-3ASECTION-29"></a>

## Usage

<a id="x-28CLACK-CORS-3AMAKE-CORS-MIDDLEWARE-20FUNCTION-29"></a>

### [function](308b) `clack-cors:make-cors-middleware` app &key (allowed-origin \*default-allowed-origin\*) (allowed-headers \*default-allowed-headers\*) (allowed-methods \*default-allowed-methods\*) (allowed-credentials \*default-allowed-credentials\*) (error-response \*default-error-response\*)

Returns a Clack middleware which can be used to override `CORS` `HTTP` headers in response.

You can pass arguments `ALLOWED-ORIGIN`, `ALLOWED-HEADERS`, `ALLOWED-CREDENTIALS` and `ALLOWED-METHODS` to override corresponding headers.

If given, these arguments are extend headers, returned by the main application. For example, if main application
already returns `Access-Control-Allow-Headers` with value `Content-Type`, then it will be overwritten with
the value `Authorization`. To implement a smarter logic, pass as an argument a function of two variables - initial
`env` plist and resulting headers `plist`. The function should return a string which will be used
to replace a header value.

Also, you can provide a `ERROR-RESPONSE` argument which will be used as response
in case if original `APP` returns response other than a list of three items. This argument
should be a list like this:

```
(list 500
     (list :Content-Type "application/json")
     (list "{\"code\": -1, \"message\": \"Unhandled error.\"}"))
```
All arguments can be given as a function of two argument, in this case a function
will be called with Lack's `env` plist and a plist of headers returned by the main application.
Most useful keys in the `env` plist are `:REQUEST-METHOD` and `:REQUEST-URI`.

<a id="x-28CLACK-CORS-3A-2ADEFAULT-ALLOWED-ORIGIN-2A-20-28VARIABLE-29-29"></a>

### [variable](b52b) `clack-cors:*default-allowed-origin*` nil

Default value to return as `Access-Control-Allow-Origin` `HTTP` header.

<a id="x-28CLACK-CORS-3A-2ADEFAULT-ALLOWED-HEADERS-2A-20-28VARIABLE-29-29"></a>

### [variable](07aa) `clack-cors:*default-allowed-headers*` nil

Default value to return as `Access-Control-Allow-Headers` `HTTP` header.

<a id="x-28CLACK-CORS-3A-2ADEFAULT-ALLOWED-METHODS-2A-20-28VARIABLE-29-29"></a>

### [variable](9eb4) `clack-cors:*default-allowed-methods*` nil

Default value to return as `Access-Control-Allow-Methods` `HTTP` header.

### [variable](9eb4) `clack-cors:*default-allowed-credentials*` nil

Default value to return as `Access-Control-Allow-Credentials` `HTTP` header.

<a id="x-28CLACK-CORS-3A-2ADEFAULT-ERROR-RESPONSE-2A-20-28VARIABLE-29-29"></a>

### [variable](24e9) `clack-cors:*default-error-response*` (500 (:CONTENT-TYPE "application/json")
 ("{\"code\": -1, \"message\": \"Unhandled error.\"}"))

Default value to return if main app will not return a list of three items.


[5c32]: https://40ants.com/clack-cors/
[74db]: https://github.com/40ants/clack-cors
[1700]: https://github.com/40ants/clack-cors/actions
[b52b]: https://github.com/40ants/clack-cors/blob/b13b3351963120c990e2b6b53bf04ab0571ea8eb/src/core.lisp#L18
[07aa]: https://github.com/40ants/clack-cors/blob/b13b3351963120c990e2b6b53bf04ab0571ea8eb/src/core.lisp#L21
[9eb4]: https://github.com/40ants/clack-cors/blob/b13b3351963120c990e2b6b53bf04ab0571ea8eb/src/core.lisp#L24
[24e9]: https://github.com/40ants/clack-cors/blob/b13b3351963120c990e2b6b53bf04ab0571ea8eb/src/core.lisp#L27
[308b]: https://github.com/40ants/clack-cors/blob/b13b3351963120c990e2b6b53bf04ab0571ea8eb/src/core.lisp#L66
[b14f]: https://github.com/40ants/clack-cors/issues
[8236]: https://quickdocs.org/alexandria
[7f8b]: https://quickdocs.org/log4cl
[c41d]: https://quickdocs.org/serapeum

* * *
###### [generated by [40ANTS-DOC](https://40ants.com/doc/)]
