# The new geoloqi.js library.

* CORS Support
* No Dependancies
* Clean Simple API
* Handles Authentication and Persisting Sessions
* IE 8 and 9 support

# Node Tests
If you want to run the node tests just `npm test`

# Browser Tests

Testing is done via [Grunt](http://gruntjs.com/) and [Phantom JS](http://phantomjs.org/). To install these just run...

If you want to run the tests in a browser with `grunt` or `grunt jasmine` you will need to install Phantom JS and grunt.

* `npm install grunt -g`
* `brew install phantomjs`

Once these are installed you can now run the tests with `grunt jasmine`.

If you do not want to run tests from the command line just open up `spec/SpecRunner.html` in your browser.

# Building

Make sure you have all the testing dependancies installed then run `grunt` from the command line. If the files lints and passes all the tests it will be concatinated and minified to the `dist` folder.

# Todos
* Session persistance
* HTML5 Geolocation Helpers
* Batching and deferred lists
* Socket helpers (socket.io and native websockets)

# geoloqi.get() and geoloqi.post()

`geoloqi.get(method, data, callback, context);`
`geoloqi.get(method, callback);`
`geoloqi.get(method, callback, context);`

`data` and `callback` are optional, if you define a `callback` you can optionally declare a `context` for your callback to be run under.

If you want to use a syntax similar to jQuery or other libraries you can also pass an object.

```
geoloqi.post({
  method: "trigger/create",
  data: {
    condition: {
      direction: "entering",
      geo: GeoJSON
    },
    action: {
      message: "You have arrived"
    },
    tags: ["geoloqiHQ"]
  },
  callback: callbackFunction
});
```

# geoloqi.request();
`geoloqi.request()` is the same as `geoloqi.get()` and `geoloqi.post()` but there is a new first parameter that specifies the type of request. This method also returns the `XMLHttpRequest` or `XDomainRequest` object in the callback insteed of `response` and `error`.

```
geoloqi.request("POST", "location/update", {
  latitude:  45,
  longitude: 45
}, function(xhr){
  console.log(xhr);
});
```

```
geoloqi.request("POST", {
  method: "location/update",
  data: {
    latitude: 12,
    longitude: 12
  },
  callback: function(xhr){
    console.log(xhr);
  }
});
```