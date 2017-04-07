# api documentation for  [stringify (v5.1.0)](https://github.com/JohnPostlethwait/stringify#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-stringify.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-stringify) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-stringify.svg)](https://travis-ci.org/npmdoc/node-npmdoc-stringify)
#### Browserify middleware to be able to require() text files (including templates) inside of your client-side JavaScript files.

[![NPM](https://nodei.co/npm/stringify.png?downloads=true)](https://www.npmjs.com/package/stringify)

[![apidoc](https://npmdoc.github.io/node-npmdoc-stringify/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-stringify_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-stringify/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-stringify/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-stringify/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "John Postlethwait",
        "email": "john.postlethwait@gmail.com"
    },
    "bugs": {
        "url": "https://github.com/JohnPostlethwait/stringify/issues"
    },
    "contributors": [
        {
            "name": "James Newell",
            "email": "james@digitaledgeit.com.au"
        },
        {
            "name": "Kevin Ingersoll",
            "email": "kingersoll@gmail.com"
        },
        {
            "name": "Livoras",
            "email": "livoras@163.com"
        },
        {
            "name": "Sébastien David",
            "email": "sebastien.david.1983@gmail.com"
        },
        {
            "name": "Kenneth Skovhus",
            "email": "kenneth.skovhus@gmail.com"
        },
        {
            "name": "Michaelangelo Jong",
            "email": "mike96angelo@gmail.com"
        },
        {
            "name": "Matthew Dunsdon",
            "email": "matthewdunsdon@gmail.com"
        }
    ],
    "dependencies": {
        "browserify-transform-tools": "^1.5.3",
        "html-minifier": "1.1.1"
    },
    "description": "Browserify middleware to be able to require() text files (including templates) inside of your client-side JavaScript files.",
    "devDependencies": {
        "gulp": "3.9.0",
        "gulp-jshint": "2.0.0",
        "gulp-mocha": "2.2.0",
        "jshint": "2.9.1",
        "jshint-stylish": "2.1.0",
        "mocha": "2.4.5",
        "should": "8.2.1"
    },
    "directories": {},
    "dist": {
        "shasum": "2a57a7915a537a8ba884b566dabfdb96ac4973c2",
        "tarball": "https://registry.npmjs.org/stringify/-/stringify-5.1.0.tgz"
    },
    "engines": {
        "node": ">=4.0.0"
    },
    "gitHead": "ad5ffa7f8b7b08a68c8a6201a67fa3ce094b58c3",
    "homepage": "https://github.com/JohnPostlethwait/stringify#readme",
    "keywords": [
        "browserify",
        "browserify-transform",
        "require",
        "template",
        "text",
        "txt",
        "client-side"
    ],
    "license": "MIT",
    "main": "./index.js",
    "maintainers": [
        {
            "name": "johnpostlethwait",
            "email": "john.postlethwait@gmail.com"
        }
    ],
    "name": "stringify",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/JohnPostlethwait/stringify.git"
    },
    "scripts": {},
    "version": "5.1.0",
    "website": "http://johnpostlethwait.github.com/stringify/"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module stringify](#apidoc.module.stringify)
1.  [function <span class="apidocSignatureSpan"></span>stringify (content)](#apidoc.element.stringify.stringify)
1.  [function <span class="apidocSignatureSpan">stringify.</span>getExtensions (options)](#apidoc.element.stringify.getExtensions)
1.  [function <span class="apidocSignatureSpan">stringify.</span>getMinifyOptions (options)](#apidoc.element.stringify.getMinifyOptions)
1.  [function <span class="apidocSignatureSpan">stringify.</span>getTransformOptions (options)](#apidoc.element.stringify.getTransformOptions)
1.  [function <span class="apidocSignatureSpan">stringify.</span>minify (filename, contents, options)](#apidoc.element.stringify.minify)
1.  [function <span class="apidocSignatureSpan">stringify.</span>registerWithRequire (options)](#apidoc.element.stringify.registerWithRequire)
1.  [function <span class="apidocSignatureSpan">stringify.</span>requireStringify (module, filename)](#apidoc.element.stringify.requireStringify)
1.  object <span class="apidocSignatureSpan">stringify.</span>DEFAULT_MINIFY_OPTIONS
1.  object <span class="apidocSignatureSpan">stringify.</span>MINIFY_TRANSFORM_OPTIONS
1.  object <span class="apidocSignatureSpan">stringify.</span>NODE_REQUIRE_OPTIONS
1.  object <span class="apidocSignatureSpan">stringify.</span>TRANSFORM_OPTIONS



# <a name="apidoc.module.stringify"></a>[module stringify](#apidoc.module.stringify)

#### <a name="apidoc.element.stringify.stringify"></a>[function <span class="apidocSignatureSpan"></span>stringify (content)](#apidoc.element.stringify.stringify)
- description and source-code
```javascript
function stringify(content) {
  return 'module.exports = ' + JSON.stringify(content) + ';\n';
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.stringify.getExtensions"></a>[function <span class="apidocSignatureSpan">stringify.</span>getExtensions (options)](#apidoc.element.stringify.getExtensions)
- description and source-code
```javascript
function getExtensions(options) {
<span class="apidocCodeCommentSpan">  /**
   * The file extensions which are stringified by default.
   * @type    {string[]}
   */
</span>  var extensions = TRANSFORM_OPTIONS.includeExtensions;

  if (options) {
    if (Object.prototype.toString.call(options) === '[object Array]') {
      extensions = options;
    } else if (options.extensions && options.extensions._) {
      extensions = options.extensions._;
    } else if(options.extensions) {
      extensions = options.extensions;
    }
  }

  // Lowercase all file extensions for case-insensitive matching.
  extensions = extensions.map(function (ext) {
    return ext.toLowerCase();
  });

  return extensions;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.stringify.getMinifyOptions"></a>[function <span class="apidocSignatureSpan">stringify.</span>getMinifyOptions (options)](#apidoc.element.stringify.getMinifyOptions)
- description and source-code
```javascript
function getMinifyOptions(options) {
  if (!options || !options.minify) {
    return { requested: false };
  }

  var minifierOpts = options.minifier,
      minify = { requested: true, options: DEFAULT_MINIFY_OPTIONS };

  if (options.minifyAppliesTo) {
    minify.config = { appliesTo: options.minifyAppliesTo };
  } else if (minifierOpts && minifierOpts.extensions) {
    var extensions = minifierOpts.extensions._ || options.minifier.extensions;
    minify.config = { appliesTo: { includeExtensions: extensions } };
  }

  if (options.minifyOptions) {
    minify.options = options.minifyOptions;
  } else if (minifierOpts && minifierOpts.options) {
    minify.options = minifierOpts.options;
  }

  return minify;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.stringify.getTransformOptions"></a>[function <span class="apidocSignatureSpan">stringify.</span>getTransformOptions (options)](#apidoc.element.stringify.getTransformOptions)
- description and source-code
```javascript
function getTransformOptions(options) {
  if (!options) {
    return {};
  }

  if (Object.prototype.toString.call(options) === '[object Array]') {
    options = { appliesTo: { includeExtensions: options }  };
  }

  if (options.extensions && !options.appliesTo) {
    var extensions = options.extensions._ || options.extensions;
    options.appliesTo = { includeExtensions: extensions };
    delete options.extensions;
  }

  return options;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.stringify.minify"></a>[function <span class="apidocSignatureSpan">stringify.</span>minify (filename, contents, options)](#apidoc.element.stringify.minify)
- description and source-code
```javascript
function minify(filename, contents, options) {
  var minifier = getMinifyOptions(options);

  if (minifier.requested) {
    if (!tools.skipFile(filename, minifier.config, MINIFY_TRANSFORM_OPTIONS)) {
      return htmlMinifier.minify(contents, minifier.options);
    }
  }

  return contents;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.stringify.registerWithRequire"></a>[function <span class="apidocSignatureSpan">stringify.</span>registerWithRequire (options)](#apidoc.element.stringify.registerWithRequire)
- description and source-code
```javascript
function registerWithRequire(options) {
  NODE_REQUIRE_OPTIONS = options || {};

  var exts = getExtensions(NODE_REQUIRE_OPTIONS);

  for (var i = 0; i < exts.length; i++) {
    require.extensions[ exts[i] ] = requireStringify;
  }
}
```
- example usage
```shell
...

Allows you to "stringify" your non-JS files using the NodeJS module system.
Please only use Stringify this way in NodeJS (Read: Not the browser/Browserify!)

'''javascript
var stringify = require('stringify');

stringify.registerWithRequire({
extensions: ['.txt', '.html'],
minify: true,
minifyAppliesTo: {
  includeExtensions: ['.html']
},
minifyOptions: {
  // html-minifier options
...
```

#### <a name="apidoc.element.stringify.requireStringify"></a>[function <span class="apidocSignatureSpan">stringify.</span>requireStringify (module, filename)](#apidoc.element.stringify.requireStringify)
- description and source-code
```javascript
function requireStringify(module, filename) {
  var contents;

  try {
    contents = fs.readFileSync(path.resolve(filename), 'utf8');
  } catch (error) {
    throw new Error('Stringify could not find module \'' + path.resolve(filename) + '\'.');
  }

  module.exports = minify(filename, contents, NODE_REQUIRE_OPTIONS);
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
