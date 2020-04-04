# Spine
[![Build Status](https://img.shields.io/circleci/project/spine/spine/dev.svg?style=flat)](https://circleci.com/gh/spine/spine)
[![Gitter](https://img.shields.io/gitter/room/spine/spine.svg?style=flat)](https://gitter.im/spine/spine?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Spine is a lightweight MVC library for building JavaScript web applications. Spine gives you structure and then gets out of your way, allowing you to concentrate on the fun stuff: building awesome web applications.

Spine is opinionated in its approach to web application architecture and design. Spine's architecture complements patterns such as de-coupled components and CommonJS modules, markedly helping with code quality and maintainability.

The library is written in [CoffeeScript](http://coffeescript.org), and though it doesn't necessarily require CoffeeScript to develop applications - you can use whichever language you're most familiar with or prefer - the documentation and some associated tools like [Hem](https://github.com/spine/hem) and [spine.app](https://github.com/spine/spine.app) cater to those who prefer CoffeeScript's syntax.

## Learn it

Documentation is often incomplete or just lies waiting to happen. Approachable source code reduces knowledge dependencies. This is an area where Spine really excels compared to other MVC frameworks. Spine is tiny; the core library comes in at less than 700 lines of CoffeeScript code. It is written in such a way to prefer readability over terseness or clever tricks, and it is small enough that within a rather small timeframe you can understand how all the pieces work together. Expertise is achievable within days or weeks rather than months or years. For these reasons, remaining lightweight and simple is fundamental to Spine.

For documentation, usage, and examples, see: [spine.github.io](http://spine.github.io/)

The test suite can also occasionally provide additional useful examples, especially if you are looking for non-coffeescript examples.

# Contributing

## Reporting issues

To file a bug report, please visit the [GitHub issues page](https://github.com/spine/spine/issues).  It's great if you can attach code (test cases and fixes for bugs, and test cases and a proposed implementation for features), but reproducible bug reports are also welcome. 

For support or help with using spine please use the [Spine Google Group](https://groups.google.com/forum/#!forum/spinejs) and/or StackOverflow rather than opening an issue on Github. If you post in those places you are more likely to get more people to chime in, and others can benefit from it more readily.

## Cloning master and running the test suite

To get started contributing to Spine, first clone the repository and make sure you can run the test suite.  If you're not familiar with Git, visit the [Git homepage](http://git-scm.com) to download Git for your platform.

First, clone the repository:

```
$ git clone git://github.com/spine/spine.git
$ cd spine
```

Next, You will need node and npm to pull in the testing libraries. Once you're all set with those then from within the Spine repo directory run

```
$ npm install
```

This will install CoffeeScript and the [Karma test runner](http://karma-runner.github.io).

At this point you can easily run the complete test suite using

```
$ npm test
```

But this isn't very practical for development, since it runs the test suite multiple times against different versions of jQuery.

A better approach is to install the Karma CLI

```
$ npm install -g karma-cli
```

Then you can use `$ karma start` to run the tests using the latest stable version of jQuery. Karma will keep running in the background and re-run tests whenever you change any files.
When the Karma server is running, you can debug tests in your browser by visiting `http://localhost:9876/debug.html`.

It's also possible to test against a specific version of jQuery if needed: `$ JQUERY_VERSION=1.9.1 karma start`.

## Contributing to the Spine documentation

Perhaps the easiest way to get started with contributing is through the docs.  If you find typos, bugs, or omissions in the docs, please submit a pull request to fix.  [The Spine website](http://spine.github.io/), which is the primary documentation, is a very simple [Wintersmith](http://wintersmith.io/) app at [spine.github.io](https://github.com/spine/spine.github.io). Basic markdown  familiarity is probably all you need to be able to make changes.

## Contributing to the Spine code

This recommended contribution process is based on the [Ruby on Rails contribution guide](http://edgeguides.rubyonrails.org/contributing_to_ruby_on_rails.html#contributing-to-the-rails-code).  In general, please include tests with new features or bugfixes, work in a feature branch until you're ready to submit or discuss your code, then fork the repository, push to your fork, and issue a pull request.

### CoffeeScript

When submitting a pull request for code, please submit in CoffeeScript. Building the effected js files is required for testing sake, but submitting those js files is optional.

Assuming you have Node.js and npm already installed then proceed by installing local dev dependencies:

```
$ npm install
```

Then use the provided build scripts to compile your CoffeeScript files:

```
$ cake build
$ cake watch
```

These tasks use a locally installed copy of CoffeeScript to ensure all contributors use the same version of the compiler.

### Git

Let's say I'm going to submit a patch to add someFeatureFix:

```
$ git checkout dev
```

Feature branches should start from `dev` **not** `master`. If you branch off of, or do builds on the master branch you will get CoffeeScript source map files, which are cool, but tend to ruin automatic merges with git.

```
$ git checkout -b someFeatureFix
$ vim test/...
  # (...add tests...)
$ cake watch
  # (...this should recompile and changes you make in your CoffeeScript...)

-- figure out what spine module your changes belong in
$ vim src/spine.coffee
or
$ vim src/[otherSpineComponent].coffee
  # (...add the feature/fix...)
$ open test/index.html
  # (...make sure tests run for each component that was changed...)
  # (...test in other browsers with various jquery versions if you feel like there is risk... )
$ git commit -m "Add Some Feature Fix"
```

Then, [fork the Spine repository](https://github.com/spine/spine/fork), and push your branch to your fork:

```
$ git remote add <your user name> git@github.com:<your user name>/spine.git
$ git push <your user name> someFeatureFix
```

Finally, issue a pull request from inside the GitHub interface to the `dev` branch of spine, and your contribution is ready for consideration, discussion, and (hopefully) merging in!
