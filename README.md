# Benchmark.js

A [robust](http://calendar.perfplanet.com/2010/bulletproof-javascript-benchmarks/ "Bulletproof JavaScript benchmarks") benchmarking library that works on nearly all JavaScript platforms, supports high-resolution timers, and returns statistically significant results. As seen on [jsPerf](http://jsperf.com/).

## Documentation

The documentation for Benchmark.js can be viewed here: <http://benchmarkjs.com/docs>

For a list of upcoming features, check out our [roadmap](https://github.com/mathiasbynens/benchmark.js/wiki/Roadmap).

## Installation and usage

In a browser or Adobe AIR:

    <script src="benchmark.js"></script>

Optionally, add the `nanoTime` Java applet to the `<body>`:

    <applet code="nano" archive="nano.jar"></applet>

Via [npm](http://npmjs.org/):

    npm install benchmark

In [Node.js](http://nodejs.org/):

    var Benchmark = require('benchmark');

In [Narwhal](http://narwhaljs.org/) and [RingoJS](http://ringojs.org/):

    var Benchmark = require('benchmark').Benchmark;

In [Rhino](http://www.mozilla.org/rhino/):

    load('benchmark.js');

Usage example:

    var suite = new Benchmark.Suite;
    
    // add tests
    suite.add('RegExp#test', function() {
      /o/.test('Hello World!');
    })
    .add('String#indexOf', function() {
      'Hello World!'.indexOf('o') > -1;
    })
    // add listeners
    .on('cycle', function(bench) {
      console.log(String(bench));
    })
    .on('complete', function() {
      console.log('Fastest is ' + this.filter('fastest').pluck('name'));
    })
    // run async
    .run(true);
    
    // logs:
    // > RegExp#test × 4,161,532 ±0.99% (59 cycles)
    // > String#indexOf × 6,139,623 ±1.00% (131 cycles)
    // > Fastest is String#indexOf

## Cloning this repo

To clone this repository including all submodules, using git 1.6.5 or later:

    git clone --recursive https://github.com/mathiasbynens/benchmark.js.git

For older git versions, just use:

    git clone https://github.com/mathiasbynens/benchmark.js.git
    cd benchmark.js
    git submodule update --init

Feel free to fork if you see possible improvements!

## Authors

* [Mathias Bynens](http://mathiasbynens.be/)
* [John-David Dalton](http://allyoucanleet.com/)