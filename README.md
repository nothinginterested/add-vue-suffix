# add-vue-suffix

🔨Give some vue files ,find reference and add `.vue` suffix;(Useful for some project migrate to `vite` from `webpack`)

English | [中文](https://github.com/BryanAdamss/add-vue-suffix/blob/master/README.zh-CN.md)

## Install

```sh
npm i -D add-vue-suffix

or

yarn add add-vue-suffix -D
```

## Usage

### with cli

```bash
npx add-vue-suffix --resolveConifg ./path/to/resolve-config.js
```

or

```json
{
  "scripts": {
    "add-vue-suffix": "add-vue-suffix --resolveConifg ./path/to/resolve-config.js"
  }
}
```

- `resolveConifg` is a path to a `enhanced-resolve` config file;
- Because [`webpack` use `enhanced-resolve` underhood](https://webpack.js.org/concepts/module-resolution/),so you just point to a `webpack config` that contain `resolve` property.
- etc

```js
// webpack.config.js
module.exports={
  input:'./src/index.js',

  ...,

  resolve:{
    extensions: ['.js', '.vue', '.json'],
    alias: {
      '@': resolve('src'),
      Api: resolve('src/api'),
      Api2: resolve('src/api2'),
      Assets: resolve('src/assets'),
      Base: resolve('src/base'),
      Config: resolve('src/config'),
      Components: resolve('src/components'),
      Directives: resolve('src/directives'),
      Plugins: resolve('src/plugins'),
      Routes: resolve('src/routes'),
      Sass: resolve('src/sass'),
      Services: resolve('src/services'),
      Stores: resolve('src/stores'),
      Utils: resolve('src/utils'),
      Views: resolve('src/views')
  }
}
```

- If you use `vue-cli` or other not emit `webpack config` cli,you can just create a `js` file that export a object that contain `resolve` property like above.

### with function

```js
import addVueSuffix from 'add-vue-suffix'

addVueSuffix({
  withAST = false, // add-vue-suffix use regexp to replace import/export/import() by default;If you got some error,set this to true,it will use babel to replace import/export/import();
  patterns = ['src/**/*.vue', 'src/**/*.js'], // some file may be import vue file;search `vue` and `js` under `src` by default;
  globbyOptions = {}, // custom globby options, it will override default globby options;
  resolveConfig = {}, // https://www.npmjs.com/package/enhanced-resolve；https://webpack.js.org/configuration/resolve/#resolve
  debug = false,// set true will not rewrite file;
})
```

## NPM

- [vue-cli-plugin-auto-alias](https://www.npmjs.com/package/vue-cli-plugin-auto-alias)
- [@bryanadamss/drawing-board](https://www.npmjs.com/package/@bryanadamss/drawing-board)
- [@bryanadamss/num2chn](https://www.npmjs.com/package/@bryanadamss/num2chn)
- [ant-color-converter](https://www.npmjs.com/package/ant-color-converter)

## Show your support

Give a ⭐️ if this project helped you!

## 📝 License

Copyright © 2021 [BryanAdamss@foxmail.com](https://github.com/BryanAdamss).<br />
This project is [MIT](https://github.com/kefranabg/readme-md-generator/blob/master/LICENSE) licensed.

## Contributors ✨

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://bryanadamss.github.io/"><img src="https://avatars3.githubusercontent.com/u/7441504?v=4" width="64px;" alt=""/><br /><sub><b>GuangHui</b></sub></a><br /><a href="#projectManagement-BryanAdamss" title="Project Management">📆</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

This project follows the [all-contributors](https://github.com/all-contributors/all-contributors) specification. Contributions of any kind welcome!
