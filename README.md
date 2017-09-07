# cachemanifest-webpack-plugin 
Webpack Plugin to generate CACHE MANIFEST 

Script Copied from https://github.com/sospirited/appcache-webpack-plugin. 
The change is only this:

Previously it was being generated like this:

```
    CACHE MANIFEST
        
    # 8a214e75b87d45313fa7
    
    app-8a214e75b87d45313fa7.bundle.js
    appReact-8a214e75b87d45313fa7.bundle.js
    vendors-8a214e75b87d45313fa7.js
    vendors-style-8a214e75b87d45313fa7.css
    index.html
    
    CACHE:
    other.js
    
    NETWORK:
    *
```

Is now being generated like this:

```
    CACHE MANIFEST

    # 8a214e75b87d45313fa7
    
    CACHE:
    other.js
    app-8a214e75b87d45313fa7.bundle.js
    appReact-8a214e75b87d45313fa7.bundle.js
    vendors-8a214e75b87d45313fa7.js
    vendors-style-8a214e75b87d45313fa7.css
    index.html
    
    NETWORK:
    *
```

## How to use

Run `npm i --save-dev cachemanifest-webpack-plugin`

```javascript

var CacheManifestPlugin = require('appcache-webpack-plugin');

module.exports = {
  plugins: [
    new CacheManifestPlugin({
      cache: ['someOtherAsset.jpg'],
      network: null,  // No network access allowed!
      fallback: ['failwhale.jpg'],
      settings: ['prefer-online'],
      exclude: ['file.txt', /.*\.js$/]  // Exclude file.txt and all .js files
      output: 'my-manifest.appcache'
    })
  ]
}
```

Arguments:

* `cache`: An array of additional assets to cache.
* `network`: An array of assets that may be accessed via the network.
  Defaults to `['*']`.
* `fallback`: An array of fallback assets.
* `settings`: An array of settings.
* `exclude`: An array of strings or regex patterns. Assets in the compilation
that match any of these patterns will be excluded from the manifest.
* `output`: The filename to write the appcache to

## License

[MIT](http://www.opensource.org/licenses/mit-license.php)

