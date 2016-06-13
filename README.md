# Atomised CSS [![Build Status](https://travis-ci.org/sndrs/atomised-css.svg?branch=master)](https://travis-ci.org/sndrs/atomised-css)

PoC that creates an atomised stylesheet from a standard one, and provides a json map from the original classes to the atomic ones.

So this:
```CSS
.thing {
    background-color: red;
}
.thing--flat {
    background-color: red;
    line-height: 0;
}
```
becomes this:
```CSS
.a { background-color: red; }
.b { line-height: 0; }
```
```JSON
{
    "thing": ["a"],
    "thing--flat": ["a", "b"]
}
```
The idea is that in production, you would inline the atomic CSS and then do the following:
```HTML
<div class="thing"></div>
<div class="thing--flat"></div>
```
with
```HTML
<div class="a"></div>
<div class="a b"></div>
```

This means you should get the benefits of atomic CSS classes, while being able to write CSS as normal.

Note that elements must have only one class for it to work, and only class selectors can be used.

Currently, there is only a test suite, which you can run with the standard `npm test`.

### Node.js 0.10
It uses PostCSS, so [their caveat](https://github.com/postcss/postcss#nodejs-010-and-the-promise-api) about v0.10 applies.

## To do
- [x] pseudo selectors
- [x] media queries
- [ ] scoping classes?
