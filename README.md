# Introduction

[![Angular 2 Style Guide](https://oscar141080.github.io/angular2-style-guide/images/badge.svg)](https://github.com/oscar141080/angular2-style-guide)
[![Build Status](https://travis-ci.org/oscar141080/marcelorestaurant.svg?branch=master)](https://travis-ci.org/oscar141080/marcelorestaurant)
[![Build Status](https://ci.appveyor.com/api/projects/status/github/oscar141080/marcelorestaurant?svg=true)](https://ci.appveyor.com/project/oscar141080/marcelorestaurant)
[![MIT license](http://img.shields.io/badge/license-MIT-brightgreen.svg)](http://opensource.org/licenses/MIT)
[![Dependency Status](https://david-dm.org/oscar141080/marcelorestaurant.svg)](https://david-dm.org/oscar141080/marcelorestaurant)
[![devDependency Status](https://david-dm.org/oscar141080/marcelorestaurant/dev-status.svg)](https://david-dm.org/oscar141080/marcelorestaurant#info=devDependencies)

A modular marcelorestaurant project for Angular 2 apps.

It is something similar to the Angular Quick Start but does the entire build with gulp.

`marcelorestaurant` provides the following features:

- Allows you to painlessly update the marcelorestaurant tasks of your already existing project.
- Ready to go, statically typed build system using gulp for working with TypeScript.
- Production and development builds.
- Sample unit tests with Jasmine and Karma including code coverage via [istanbul](https://gotwarlost.github.io/istanbul/).
- End-to-end tests with Protractor.
- Development server with Livereload.
- Following the [best practices for your application’s structure](https://github.com/oscar141080/angular2-style-guide).
- Manager of your type definitions using [typings](https://github.com/typings/typings).
- Has autoprefixer and css-lint support.
- Basic Service Worker, which implements "Cache then network strategy".

# How to start

**Note** that this marcelorestaurant project requires node v4.x.x or higher and npm 2.14.7.

**Here is how to [speedup the build on Windows](https://github.com/oscar141080/marcelorestaurant/wiki/Speed-up-the-build-on-Windows)**.

In order to start the marcelorestaurant use:


```bash
git clone --depth 1 https://github.com/oscar141080/marcelorestaurant.git
cd marcelorestaurant
# install the project's dependencies
npm install
# watches your files and uses livereload by default
npm start
# api document for the app
npm run docs

# dev build
npm run build.dev
# prod build
npm run build.prod
```

_Does not rely on any global dependencies._

# Table of Content

- [Introduction](#introduction)
- [How to start](#how-to-start)
- [Table of Content](#table-of-content)
- [Configuration](#configuration)
- [How to extend?](#how-to-extend)
- [Running tests](#running-tests)
- [Contributing](#contributing)
- [Advanced marcelorestaurant Option](#advanced-marcelorestaurant-option)
- [Examples](#examples)
- [Directory Structure](#directory-structure)
- [Contributors](#contributors)
- [Change Log](#change-log)
- [License](#license)

# Configuration

Default application server configuration

```javascript
var PORT             = 5555;
var LIVE_RELOAD_PORT = 4002;
var DOCS_PORT        = 4003;
var APP_BASE         = '/';
```

Configure at runtime

```bash
npm start -- --port 8080 --reload-port 4000 --base /my-app/
```

# How to extend?

Visit the [Wiki page](https://github.com/oscar141080/marcelorestaurant/wiki) of the project.

# Running tests

```bash
npm test

# Debug - In two different shell windows
npm run build.test.watch      # 1st window
npm run karma.start           # 2nd window

# code coverage (istanbul)
# auto-generated at the end of `npm test`
# view coverage report:
npm run serve.coverage

# e2e (aka. end-to-end, integration) - In three different shell windows
# Make sure you don't have a global instance of Protractor

# npm run webdriver-update <- You will need to run this the first time
npm run webdriver-start
npm run serve.e2e
npm run e2e

# e2e live mode - Protractor interactive mode
# Instead of last command above, you can use:
npm run e2e.live
```
You can learn more about [Protractor Interactive Mode here](https://github.com/angular/protractor/blob/master/docs/debugging.md#testing-out-protractor-interactively)

# Contributing

Please see the [CONTRIBUTING](https://github.com/oscar141080/marcelorestaurant/blob/master/.github/CONTRIBUTING.md) file for guidelines.

# Advanced Seed Option

An [advanced option to this marcelorestaurant exists here](https://github.com/NathanWalker/marcelorestaurant-advanced) which mirrors the latest changes here but adds core support for:

- [ngrx/store](https://github.com/ngrx/store) RxJS powered state management, inspired by **Redux**
- [ngrx-store-router](https://github.com/CodeSequence/ngrx-store-router) middleware for syncing state with Angular 2 Router.
- [ng2-translate](https://github.com/ocombe/ng2-translate) for i18n
- [lodash](https://lodash.com/) Helps reduce blocks of code down to single lines and enhances readability
- [NativeScript](https://www.nativescript.org/) cross platform mobile (w/ native UI) apps.
- More coming in the future...

You may use it to learn how to extend this marcelorestaurant for your own use cases or use the advanced marcelorestaurant if your project needs those features.

# Directory Structure

```
.
├── LICENSE
├── README.md
├── gulpfile.ts                <- configuration of the gulp tasks
├── karma.conf.js              <- configuration of the test runner
├── package.json               <- dependencies of the project
├── protractor.conf.js         <- e2e tests configuration
├── src                        <- source code of the application
│   ├── home
│   │   └── components
│   ├── index.html
│   ├── main.ts
│   ├── shared
│   │   └── services
│   │       ├── name-list...
│   │       └── name-list...
│   └── sw.js                  <- sample service worker
├── test-main.js               <- testing configuration
├── tools
│   ├── README.md              <- build documentation
│   ├── config
│   │   ├── project.config.ts  <- configuration of the specific project
│   │   ├── marcelorestaurant.config....
│   │   └── marcelorestaurant.config.ts     <- generic configuration of the marcelorestaurant project
│   ├── config.ts              <- exported configuration (merge both marcelorestaurant.config and project.config, project.config overrides marcelorestaurant.config)
│   ├── debug.ts
│   ├── manual_typings
│   │   ├── project            <- manual ambient typings for the project
│   │   │   └── sample.pac...
│   │   └── marcelorestaurant               <- marcelorestaurant manual ambient typings
│   │       ├── merge-stre..
│   │       └── slash.d.ts
│   ├── tasks                  <- gulp tasks
│   │   ├── project            <- project specific gulp tasks
│   │   │   └── sample.tas...
│   │   └── marcelorestaurant               <- marcelorestaurant generic gulp tasks. They can be overriden by the project specific gulp tasks
│   ├── utils                  <- build utils
│   │   ├── project            <- project specific gulp utils
│   │   │   └── sample_util...
│   │   ├── project.utils.ts
│   │   ├── marcelorestaurant               <- marcelorestaurant specific gulp utils
│   │   │   ├── clean.ts
│   │   │   ├── code_change...
│   │   │   ├── server.ts
│   │   │   ├── tasks_tools.ts
│   │   │   ├── template_loc...
│   │   │   ├── tsproject.ts
│   │   │   └── watch.ts
│   │   └── marcelorestaurant.utils.ts
│   └── utils.ts
├── tsconfig.json              <- configuration of the typescript project (ts-node, which runs the tasks defined in gulpfile.ts)
├── tslint.json                <- tslint configuration
├── typings                    <- typings directory. Contains all the external typing definitions defined with typings
├── typings.json
└── appveyor.yml
```

# Change Log

You can follow the [Angular 2 change log here](https://github.com/angular/angular/blob/master/CHANGELOG.md).

# License

MIT
