# Summary

The current fork of node-inspector allows users to debug electron main process. Follow the steps below in order to debug an electron app:

```bash
npm install -d
npm install node-gyp
npm install node-pre-gyp
node_modules/.bin/node-pre-gyp --target=<electron version> --runtime=electron --fallback-to-build --directory node_modules/v8-debug/ --dist-url=https://atom.io/download/atom-shell reinstall
```

I have tested the above steps against electron version 1.4.8.

Now, in order to debug your main process execute the following steps:

```bash
# in your app folder - lets assume it is $HOME/work/electron-app
npm install -d
./node_modules/.bin/electron --debug main.js

# in this repository root folder
ELECTRON_RUN_AS_NODE=true $HOME/work/electron-app/node_modules/.bin/electron bin/inspector.js
open http://127.0.0.1:8080/?port=5858
```

Wait for a couple of seconds until you see the source files displayed. It is possible to be forced to press F8 multiple times after each breakpoint.

Except this, it works as expected.