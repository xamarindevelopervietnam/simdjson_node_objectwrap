# simdjson, Node.js and Napi::ObjectWrap

## A Napi:ObjectWrap that allows to use C++ simdjson library with Node.js
...

## Performance results
...

## Requirements
...

## Getting started
```
git clone https://github.com/croteaucarine/simdjson_node_objectwrap
cd simdjson_node_objectwrap
npm install
node example.js
```

## Code usage and example
Example below is also available in repo under the file example.js
```javascript
'use strict';

const fs = require('fs');
const { simdjson } = require('bindings')('addon');

const github_events = 'jsonexamples/github_events.json';
const content = fs.readFileSync(github_events, 'utf-8');
const simdjsonOBJ = new simdjson(content);

// Display object content
console.log(simdjsonOBJ);

// Display Object Keys
console.log(simdjsonOBJ.keys());

// Display Object length
console.log(simdjsonOBJ.length);

// Display strignified Object
console.log(JSON.stringify(simdjsonOBJ));

// Display Own Property Names
console.log(Object.getOwnPropertyNames(simdjsonOBJ));

// Display Own Property Descriptors
console.log(Object.getOwnPropertyDescriptors(simdjsonOBJ));

// Loop through JSON Array 
// try-catch intercepts error if object is not an array
try {
    var i  = 1;
    for (let item of simdjsonOBJ) {
        console.log(item);
        i++;
    }
} catch(error) {
    console.error(error);
}

// Display nested elements
try {
    var i  = 1;
    for (let item of simdjsonOBJ) {
        console.log(item.actor.login);
        i++;
    }
} catch(error) {
    console.error(error);
}
```

## Benchmarks
...



