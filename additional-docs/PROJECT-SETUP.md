# Create new Angular app

```shell
ng new
```

* Application name `msg-cart-gen`
* Strict bundle control
* Without routing
* Scss styling sheets

Add the production build command to the package.json scripts

```json
"build:prod": "ng build --aot --extract-css=true --build-optimizer=true --vendor-chunk=true --prod",
```

# Install Prettier

```shell
npm i -D prettier tslint-config-prettier
```

Once installed, we can create .prettierrc file which allows to customize copule of formatting options as specified here.
Sample configuration as shown below

```json
    "printWidth": 140,
    "singleQuote": true,
    "useTabs": false,
    "tabWidth": 4,
    "semi": true,
    "bracketSpacing": true
```

For Angular, we can make prettier play nicely with tslint which is provided by AngularCLI, to do that we can install
tslint-config-prettier and add it in last item in the extends array filed in tslint.json file.

```json
{
    "extends" : ["tslint:recommended", "tslint-config-prettier"],
    ...
}
```

We can add npm script to package.json just to run the command to format code before checking Define a script task in
your package.json

```json
"format:check": "prettier --config ./.prettierrc --list-different \"src/{app,environments,assets}/**/*{.ts,.js,.json,.css,.scss}\"",
"format:write": "prettier --config ./.prettierrc --write \"src/{app,environments,assets}/**/*{.ts,.js,.json,.css,.scss}\""
```

# Install webpack bundle analyzer

```shell
npm i -D webpack-bundle-analyzer
```

Define a script task in your package.json

```json
"analyze" : "ng build --prod --stats-json && webpack-bundle-analyzer ./dist/<app-name>/stats.json"
```

# Install Compodoc

```shell
npm i -D @compodoc/compodoc
```

Define a script task in your package.json

```json
"compodoc": "npx compodoc -p tsconfig.json src"
```

# Install PrimeNG and Angular CDK

```shell
npm i primeng primeicons primeflex @angular/cdk
```

set the required styles to the angular.json array

```json
"styles": [
"src/assets/scss/reset.scss",
"node_modules/primeicons/primeicons.css",
"node_modules/primeflex/primeflex.css",
"primeng/resources/themes/vela-blue/theme.css",
"node_modules/primeng/resources/primeng.min.css",
"src/styles.scss"
],
```

Create the default reset styles file under `src/assets/scss/reset.scss`

```scss
/* You can add global styles to this file, and also import other style files */
/* http://meyerweb.com/eric/tools/css/reset/
   v2.0 | 20110126
   License: none (public domain)
*/

html, body, div, span, applet, object, iframe, h1, h2, h3, h4, h5, h6, p, blockquote, pre, a, abbr, acronym, address, big, cite, code, del, dfn, em, img, ins, kbd, q, s, samp, small, strike, strong, sub, sup, tt, var, b, u, i, center, dl, dt, dd, ol, ul, li, fieldset, form, label, legend, table, caption, tbody, tfoot, thead, tr, th, td, article, aside, canvas, details, embed, figure, figcaption, footer, header, hgroup, menu, nav, output, ruby, section, summary, time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 14px;
  font: inherit;
  vertical-align: baseline;
}

/* HTML5 display-role reset for older browsers */

article, aside, details, figcaption, figure, footer, header, hgroup, main, menu, nav, section {
  display: block;
}

body {
  line-height: 1;
}

ol, ul, li {
  list-style: none;
}

blockquote, q {
  quotes: none;
}

blockquote {
  &:before, &:after {
    content: '';
    content: none;
  }
}

q {
  &:before, &:after {
    content: '';
    content: none;
  }
}

table {
  border-collapse: collapse;
  border-spacing: 0;
}

button, input, select, textarea {
  background-color: transparent;
  outline: none;
  border: 0;
}
```

## Install Akita for state management
```shell
npm i @datorama/akita
```

#Install Angular Google Sheets DB plugin
```shell
npm i ng-google-sheets-db
```

# Final steps
Format the project, install dependencies and start the server
```shell
npm run format:write
npm install
npm start
```
