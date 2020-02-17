# vsm-json-pretty



## Specification

This is a function that converts VSM-JSON (as a JSON-String or JS-Object)
into a pretty, compact, readable JSON5-String.

It builds on the package
[`json-stringify-pretty-compact`](https://github.com/lydell/json-stringify-pretty-compact),
and in addition also:
- generates JSON5,
- adds specific compactifying optimizations for a VSM data structure,
- provides a build for the browser.

(Note: to convert the generated JSON5-String back to a JS-Object, use the
[json5](https://github.com/json5/json5) package).



## Installation
### Node.js
```sh
npm install vsm-json-pretty
```

```js
const VsmJsonPretty = require('vsm-json-pretty')
```


### Browsers
```html
<script src="https://unpkg.com/vsm-json-pretty@^1.0.0/dist/vsm-json-pretty.min.js"></script>
```

This will create a global variable `VsmJsonPretty`.



## Example
```js
var vsm = {
  terms: [
    {  str : 'subj', classID: null, instID: null },
    { "str": "rel" , classID: null, instID: null },
    {  str : 'obj' , classID: 'http://ont.ex/D/Obj', instID: null, dictID: 'http://ont.ex/D' }
  ],
  conns: [
    { type: 'T', pos: [ 0, 1, 2 ] }
  ]
};

var str  = VsmJsonPretty(vsm);
var str2 = VsmJsonPretty(JSON.stringify(vsm));
console.log(str);
console.log(str2);

/* Both output the same:
{ terms: [
    { str: 'subj', classID: null, instID: null },
    { str: 'rel', classID: null, instID: null },
    { str: 'obj',
      classID: 'http://ont.ex/D/Obj',
      instID: null,
      dictID: 'http://ont.ex/D'
    }
  ],
  conns: [ { type: 'T', pos: [ 0, 1, 2 ] } ]
}
*/
```


## License

[AGPL](LICENSE.md).
