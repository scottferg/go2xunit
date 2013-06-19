==============
go2xunit 0.1.0
==============

This is a fork of https://bitbucket.org/tebeka/go2xunit/ altered to work with launchpad.net/gocheck
test results.

Converts `go test -gocheck.v` output to xunit compatible XML output. 


Install
=======
`go install github.org/scottferg/go2xunit`


Usage
=====
By default `go2xunit` reads data from standard input and emits XML to standard
output. However you can use `-input` and `-output` flags to change this.

The `-fail` switch will cause `go2xunit` to exit with non zero status if there
are failed tests.

::

    go test -gocheck.v | go2xunit -output tests.xml

Here's an example script (`run-tests.sh`) that can be used with Jenkins_.

::
    
    #!/bin/bash

    export GOPATH=$(dirname $(dirname $PWD))
    outfile=gotest.out

    go test -v | tee $outfile
    go2xunit -fail -input $outfile -output tests.xml


.. _Jenkins: http://jenkins-ci.org/
