# Create React App WordPress Configuration
This is an ejected and slightly modified create-react-app configuration to use within your local WordPress project (e.g. XAMPP). You could use this to create a react-based WordPress Plug-In or WordPress Theme.
<br>


## Install
Go to your plugin or theme root (e.g localdisk:/xampp/htdocs/wordpress/wp-content/plugins/myplugin) 
```sh
git clone git@github.com:owiekindisch/create-react-app-wordpress.git
npm install
npm start
```
A more complexer way to start would be to create a fresh react project with [create-react-app](https://github.com/facebookincubator/create-react-app#getting-started) and [eject](https://github.com/facebookincubator/create-react-app#converting-to-a-custom-setup) it. After that you are able to change/replace the files manually. I personally don't understand this use case, but it is possible.


## Known Issues
Related to this pull request [#1588](https://github.com/facebookincubator/create-react-app/pull/1588) there is an issue that the websocket tries to connect to `http://localhost:80`(default) instead of `http://localhost:3000`(default). There is no fix for it yet so you need to change these two lines by yourself in `node_modules/react-dev-utils/webpackHotDevClient.js`.   
<br>

## Custom folder structure
To use your custom folder structure, you can just edit `_config/paths.js` as follow. I recommend to specify relative paths with `resolveApp()`. It starts from the current working directory (project root).

Property | Description
------------ | -------------
appBuild | Directory for build files
appPublic | Directory where webpack-dev-server serves the bundle.js, assets to use in WordPress
appIndexJs | Path to index.js
appPackageJson | Path to package.json
appSrc | Directory where webpack modules should start to process
yarnLockFile | Path to yarn.lock
testsSetup | Path to setupTests.js
appNodeModules | Directory to node_modules
publicUrl | URL to the `appPublic` static files. Specified in your packages.json at "homepage". You should specify "homepage" if you import media files in your react code 


## Host & Port
By default the http-proxy-middleware listening to `http://localhost:80`. If you have other host or port settings to load your WordPress project you can change that inside the `package.json` file at `proxy`.

The webpack-dev-server itself listening to `http://localhost:3000` by default. To change this setting you need to change that in `_scripts/start.js`.
<br>
