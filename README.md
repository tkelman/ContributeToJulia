<a name="logo"/>
<div align="center">
<a href="http://julialang.org/" target="_blank">
<img src="http://julialang.org/images/logo_hires.png" alt="Julia Logo" width="210" height="142"></img>
</a>
<br>
<h1>Contributing To Julia</h1>
</div>


This document tracks some ways to get involved in the Julia ecosystem - the language itself,
packages, educational material, and more. You can contribute to this document by
[editing this file](https://github.com/IainNZ/ContributeToJulia/edit/master/README.md)
in your browser and submitting a pull request.


###  Some concepts and terminology

**Testing**: One way to make sure code works in the way we intend is to write *tests*.
Testing in Julia involves writing code that tries out various different inputs to your
functions, and makes sure the that the outputs are what we expect.
Tests for Julia packages (and Julia itself) live in their `test/` subdirectories, and
the tests may span many files. Whenever we refactor our code, we can have some confidence
that we didn't introduce bugs if the tests still pass. If we fix a bug, we can add a
new test to make sure further work doesn't reintroduce the bug. Finally, if we add
a new feature we aim to make sure that there are tests for it.

**Continuous integration**: While we could rely on contributors running tests before
they submit changes, there can be various reasons why even if someone does run tests
that the changes might not work on another machine. Julia itself and many packages use
at least one *continuous integration* service to ensure that all changes pass tests
at all times. These services automatically pull the code from Github and run the
tests on fresh virtual machine, and then report back whether they failed or not.
The popular service is [TravisCI](http://travis-ci.org), and packages will often have
a "badge" like this:
[![Build Status](https://travis-ci.org/JuliaLang/JSON.jl.svg)](https://travis-ci.org/JuliaLang/JSON.jl))
in their README to show their tests are passing (or not).

**Code coverage**: Even if tests are passing, the tests may not be checking all
possible ways the package can be used, and we might be missing broken code.
Julia can track the lines of code are executed when running a script by using a
command-line option: ``julia --code-coverage=user test/runtests.jl``.
This outputs a `.cov` file for every `.jl` file executed, with a count by each
line for how many times it was executed. Julia itself and many packages automatically
track their coverage by using [Coverage.jl](https://github.com/IainNZ/Coverage.jl)
to upload summaries of the `.cov` files to websites like
[Codecov.io](http://codecov.io) that display the coverage information in a color-coded
easy-to-read way. Many packages put a badge in their READMEs like this:
[![JSON.jl's coverage](http://codecov.io/github/JuliaLang/JSON.jl/coverage.svg?branch=master)](http://codecov.io/github/JuliaLang/JSON.jl?branch=master)).


## Help out with Julia itself

Developing new features or fixing bugs can be a tough way start, so we recommend
getting started by adding **tests** - Julia needs lots of tests!
We have an [issue](https://github.com/JuliaLang/julia/issues/11885) to track
Julia's test coverage, to help you get started, and to track overall progress.
Documentation of functions and the manual can always be improved as well. If
you think something is not explained clearly or correctly, please submit an
improved version.


## Help out with packages

Julia includes a standard library, `Base`, with a lot of useful functionality.
However large amounts of important functionality lives outside of `Base` in
various packages, many of which are small enough for even a new user to understand.
Contributing to these packages will benefit large numbers of people, as they are
depended on by large numbers of other packages directly and indirectly.
The best ways you can contribute, in roughly increasing order of difficulty, are:
* adding or clarifying documentation, adding comments in code, (:book:)
* adding missing tests to improve coverage, (:white_check_mark:)
* fixing bugs mentioned in the issue tracker, (:bug:)
* improving performance, (:hourglass:)
* and adding new features.

Almost all packages are developed by volunteers who have minimal spare time, so
make their job of accepting your changes as easy as possible. If you add code,
make sure it has comments and tests, and describe as clearly as possible in
the pull request what you are doing. In general you should **not** ask about
what features you should implement - as a rule of thumb, only implement new
features if you need them yourself. If you don't need it yourself then
the time required for a package maintainer to identify and help you will
probably be a bad use of everyones time - and someone has to maintain the new code.
If your changes aren't immediately reviewed and accepted, don't take it
personally: the maintainers might just be busy with their day-to-day work!

These packages have all been listed because they are depended on by
many other packages, directly or indirectly, or are popular packages.
If you are a package owner and would like to add your package here, please
submit a pull request.

Key:
* :white_check_mark: (has below 95% test coverage)
* :book: (code comments/documentation/examples are minimal)
* :hourglass: (possibility of performance improvements)
* :bug: (has bugs that need triaging and fixing)


### Miscellaneous packages

##### [JuliaLang/JSON.jl](https://github.com/JuliaLang/JSON.jl)
JSON parsing and printing.
:book: :hourglass:

##### [JuliaLang/DataStructures.jl](https://github.com/JuliaLang/DataStructures.jl)
Implementations of common data structures.
:white_check_mark: :hourglass:


### HPC/Parallel packages

##### [JuliaParallel/MPI.jl](https://github.com/JuliaParallel/MPI.jl)
Wrappers around the MPI library for distributed memory computing.
:book:

##### [JuliaGPU/CUSPARSE.jl](https://github.com/JuliaGPU/CUSPARSE.jl)
Wrappers around the CUSPARSE library for GPU-based sparse linear algebra.
:book: :hourglass: :white_check_mark:


### Graphics and visulization packages

##### [JuliaLang/Color.jl](https://github.com/JuliaLang/Color.jl)
Color manipulation functionality, used by many visualization packages.
:white_check_mark:

##### [dcjones/Compose.jl](https://github.com/dcjones/Compose.jl)
Declarative vector graphics library, used by Gadfly and other packages.
:book: :white_check_mark:


### WWW/Internet-related packages

##### [JuliaWeb/URIParser.jl](https://github.com/JuliaWeb/URIParser.jl)
Parses Uniform Resource Identifiers (URIs).
More packages directly or indirectly dependent on this package than any other!
:white_check_mark:

##### [JuliaWeb/HttpCommon.jl](https://github.com/JuliaWeb/HttpCommon.jl)
Types and functions for working with HTTP.
:white_check_mark: :bug:


### Statistics packages

##### [JuliaStats/StatsBase.jl](https://github.com/JuliaStats/StatsBase.jl)
Functionality shared across statistics-related packages.
:white_check_mark:
