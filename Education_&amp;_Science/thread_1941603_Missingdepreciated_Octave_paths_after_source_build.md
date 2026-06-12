---
title: "Missing/depreciated Octave paths after source build"
date: 2012-03-16
forum: Education &amp; Science
---

### Post by dwdarkstar on 2012-03-16
Hello, I compiled Octave 3.6.1 in my 10.04 platform, however when I run Octave there is a sizeable list of errors pertaining to missing paths for the various basic call functions within Octave.  Stranger still is that it's apparently missing them repeatedly for two fairly outdated versions of Octave, 3.0 and 3.0.5  ...?

Before building 3.6.1 from source I installed Octave 3.2 via apt-get but got the exact same errors regarding missing paths ??

What's going on here???  See post build terminal output below.  Thanxs!!

```
Octave successfully built.  Now choose from the following:

   ./run-octave    - to run in place to test before installing
   make check      - to run the tests
   make install    - to install (PREFIX=/usr/local)

make[3]: Entering directory `/home/farstar/octave-3.6.1'
Makefile:2486: warning: overriding commands for target `check'
Makefile:2077: warning: ignoring old commands for target `check'
make[3]: Nothing to be done for `install-exec-am'.
/bin/mkdir -p /usr/local/share/octave/site/m /usr/local/share/octave/site/api-v48+/m /usr/local/share/octave/3.6.1/site/m /usr/local/lib/octave/site/oct/x86_64-unknown-linux-gnu /usr/local/lib/octave/site/oct/api-v48+/x86_64-unknown-linux-gnu /usr/local/lib/octave/3.6.1/site/oct/x86_64-unknown-linux-gnu /usr/local/libexec/octave/site/exec/x86_64-unknown-linux-gnu /usr/local/libexec/octave/api-v48+/site/exec/x86_64-unknown-linux-gnu /usr/local/libexec/octave/3.6.1/site/exec/x86_64-unknown-linux-gnu
test -z "/usr/local/include/octave-3.6.1/octave" || /bin/mkdir -p "/usr/local/include/octave-3.6.1/octave"
 /usr/bin/install -c -m 644 config.h '/usr/local/include/octave-3.6.1/octave'
test -z "/usr/local/share/octave/3.6.1/etc" || /bin/mkdir -p "/usr/local/share/octave/3.6.1/etc"
 /usr/bin/install -c -m 644 NEWS '/usr/local/share/octave/3.6.1/etc'
make[3]: Leaving directory `/home/farstar/octave-3.6.1'
make[2]: Leaving directory `/home/farstar/octave-3.6.1'
make[1]: Leaving directory `/home/farstar/octave-3.6.1'

farstar@go-bot:~/octave-3.6.1$ ./run-octave

GNU Octave, version 3.6.1
Copyright (C) 2012 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type `warranty'.

Octave was configured for "x86_64-unknown-linux-gnu".

Additional information about Octave is available at http://www.octave.org.

Please contribute if you find this software useful.
For more information, visit http://www.octave.org/help-wanted.html

Read http://www.octave.org/bugs.html to learn how to submit bug reports.

For information about changes from previous versions, type `news'.

warning: addpath: /usr/local/share/octave/site-m: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/physicalconstants-0.1.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/linear-algebra-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/linear-algebra-1.0.7: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7/testfun: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7/test: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/integration-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/graceplot-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/graceplot-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/io-1.0.8/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/io-1.0.8: No such file or directory
warning: addpath: /usr/lib/octave/packages/3.0/general-1.0.7/x86_64-pc-linux-gnu-api-v32: No such file or directory
warning: addpath: /usr/share/octave/packages/3.0/general-1.0.7: No such file or directory
warning: addpath: /usr/lib/octave/3.0.5/oct/x86_64-pc-linux-gnu: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/specfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/finance: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/quaternion: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/audio: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/elfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/time: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/path: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/special-matrix: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/tests: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/models: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/base: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/statistics/distributions: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/strings: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/startup: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/polynomial: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/plot: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/set: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/linear-algebra: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/sparse: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/general: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/signal: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/io: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/testfun: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/hinf: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/system: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/obsolete: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/util: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/control/base: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/image: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/optimization: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/pkg: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/deprecated: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/geometry: No such file or directory
warning: addpath: /usr/share/octave/3.0.5/m/miscellaneous: No such file or directory
octave:1> exit

error: feval: function `unimplemented' not found
error: feval: function `unimplemented' not found

farstar@go-bot:~/octave-3.6.1$

```

---

