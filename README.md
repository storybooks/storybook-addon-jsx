# storybook-addon-jsx

This Storybook addon show you the JSX of the story.
It can be usefull to see what props you set for example.

![Storybook Addon JSX Démo](screenshot.png)

## Getting started

` yarn add --dev storybook-addon-jsx `

Create a file called `addons.js` in your storybook config (default: `.storybook`) :

```javascript
import '@kadira/storybook/addons'
import 'storybook-addon-jsx/register'
```

Then use it when you write stories :

```javascript

import React from 'react'
import { setAddon, storiesOf } from '@kadira/storybook'
import JSXAddon from 'storybook-addon-jsx'

setAddon(JSXAddon)

const Test = ({
  fontSize = '16px',
  fontFamily = 'Arial',
  align = 'left',
  color = 'red',
  children,
}) => (
  <div style={{ color, fontFamily, fontSize, textAlign: align }}>
    {children}
  </div>
)

storiesOf('test', module)
  .addWithJSX('Paris', () => (
    <Test fontSize={45} fontFamily="Roboto" align="center" color="#CAF200">
      Hello
    </Test>
  ))
  .addWithJSX('Orleans', () => <Test color="#236544">Hello</Test>)

storiesOf('test 2', module).addWithJSX('Paris', () => (
  <div color="#333">test</div>
))

```

## TODO

- add a button for copy/paste the JSX code