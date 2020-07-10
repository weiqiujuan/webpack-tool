### 此环境主要用于小页面的使用
    `webpack打包：npm run start
    浏览运行：npm run dev
    运行端口：http://localhost:8081/
    入口文件：app/index
    出口文件：build/bundle.js`
[环境搭建参考地址](https://www.jianshu.com/p/e4ba73a5829b)

---------------------------2020.7.10更新------------------------------
### 项目搭建步骤
> 1. 以项目命名一个新的文件夹
> 2. `npm init` 项目初始化
> 3. `npm install --save-dev webpack webpack-cli -g` 安装webpack
> 4. webpack.config.js 的 [webpack](https://www.webpackjs.com/concepts/?spm=a2c6h.12873639.0.0.4c4c7b0bdFjVq6) 配置
> 5. 创建 src目录和index.js入口文件, 执行`webpack --config ./webpack.config.js` 生成 dist文件夹
> <br>-------------------------以上简单的webpack项目配置完成-------------------------
> 5. 使用webpack-dev-server提供的简单的web服务器，并且配置热更新 ：`npm install -D webpack-dev-server` 安装
> 6. 配置服务器查找的文件地址`devServer: { contentBase: './dist'}`
> 7. `npm install react react-dom react-router-dom -S` 安装react相关(如果是react项目)
> 8. `npm install babel-core babel-loader babel-preset-env babel-preset-react -D` 支持es5,jsx
> 9. 关于样式的配置： 安装 `less-loader/scss-loader、style-loader、css-loader、postcss-loader`
> <br>-------------- 注意上述安装命令执行完成，均需在webpack.config.js中配置rules规则 ------------------
#### 优化：
1. `npm install --save-dev extract-text-webpack-plugin` 单独打包样式文件
2. `npm install -D file-loader url-loader`页面图片较多时会发送很多http请求，降低页面性能。url-loader引入图片编码，生成dataURI，把图片翻译成一串字符串。再把字符串打包到文件中，最终只需要引入文件就可以访问图片了
3. `npm install -save-dev html-webpack-plugin` 将为你生成一个 HTML5 文件， 其中包括使用 script 标签的 body 中的所有 webpack 包
4. `npm i --save-dev copy-webpack-plugin` 将单个文件或整个目录复制到构建目录。
5. 使用webpack4的splitChunks来分割代码。
6. `npm i webpack-bundle-analyzer -D` 展示出打包后的各个bundle所依赖的模块。
#### tips：
* 简化命令： `npm run build，npm run start`可完成打包
```json
{
    "scripts": {
        "start": "webpack-dev-server --mode development --open",
        "build": "webpack --config ./webpack.config.js"
      }
}
```
* 如果需要添加各种规则需求，所以可以将webpack.config.js中的rules提取出来放在.babelrc。

#### 注意
* 一些插件只有webpack4中才可使用,有时候打包或者运行出错很大原因在于版本的不兼容，谷歌就行。
* [webpack文档](https://www.webpackjs.com/concepts/) 所有的配置书写参考webpack官方文档，某些博客会给人造成很大的误导。
* 如果只是玩玩，那么react就用create-react-app,vue就用vue-cli足够了
[webpack4传送门](https://juejin.im/post/5cfe4b13f265da1bb13f26a8)