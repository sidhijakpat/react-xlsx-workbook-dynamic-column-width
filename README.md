# React Excel Workbook

React Excel Workbook is a library for defining downloadable excel workbooks with react components.

## Example

```jsx
import React from 'react'
import {render} from 'react-dom'
import Workbook from 'react-xlsx-workbook-dynamic-column-width'

const data1 = [
  {
    foo: '123',
    bar: '456',
    baz: '789'
  },
  {
    foo: 'abc',
    bar: 'BCAC24VO11NAONA',
    baz: 'hij'
  },
  {
    foo: 'aaa',
    bar: 'bbb',
    baz: 'ccc'
  }
]

const data2 = [
  {
    aaa: 1,
    bbb: 2,
    ccc: 3
  },
  {
    aaa: 4,
    bbb: 5,
    ccc: 6
  }
]

const columnWidths = [
  { wch: 10 },
  { wch: 20 },
  { wch: 10 }
]

const example = (
  <div className="row" style={{marginTop: '100px'}}>
    <div className="col-xs-12 text-center">
      <Workbook filename="example.xlsx" element={<button className="btn btn-lg btn-primary">Try me!</button>}>
        <Workbook.Sheet data={() => data1} columsWidths={ columnWidths } name="Sheet A">
          <Workbook.Column label="Foo" value="foo"/>
          <Workbook.Column label="Bar" value="bar"/>
        </Workbook.Sheet>
        <Workbook.Sheet data={data2} name="Another sheet">
          <Workbook.Column label="Double aaa" value={row => row.aaa * 2}/>
          <Workbook.Column label="Cubed ccc " value={row => Math.pow(row.ccc, 3)}/>
        </Workbook.Sheet>
      </Workbook>
    </div>
  </div>
)

render(example, document.getElementById('app'))
```

![Example](http://i.imgur.com/dfhivAs.png)
![Excel](http://i.imgur.com/OnInSNv.png)

Workbooks can have multiple sheets. Sheets can use the same or different data sets(an array of objects).
Sheets have columns. Columns define a column label and value. Values can either be a string(the property name) or a function
that takes the current object and returns a value.

## Dependencies

This package uses [file-saver](https://www.npmjs.com/package/file-saver) and [xlsx](https://www.npmjs.com/package/xlsx) packages. I am only familiar with webpack and in order for everything to work with webpack you must use the [json-loader](https://www.npmjs.com/package/json-loader) and have this defined in your webpack config.

```js
node: {fs: 'empty'},
externals: [
  {'./cptable': 'var cptable'},
  {'./jszip': 'jszip'}
]
```

See the `example` directory for a working example.

## Testing

I have no idea how to test this.
