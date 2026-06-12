---
title: "[ANN] new GSL Shell release with graphics module"
date: 2009-12-27
forum: Education &amp; Science
---

### Post by fr4nko on 2009-12-27
Hi all,

I'm proud to announce the release 0.9.5 of GSL Shell. This new release introduce a new powerful and flexible module to produce graphical plots and diagrams.

The new module is very flexible and let the user produce almost any kind of graphics to represent data or functions. The most basic usage is just to plot a function or multiple functions but the most advanced users will be able to do almost anything by using the powerful graphical primitives.

The module is based on the excellent Anti-Grain Geometry (AGG) library by Maxim Shemanarev.

You can find [here]("https://savannah.nongnu.org/files/?group=gsl-shell") the source code as well as a windows executable. In order to test the software you can type:

> dofile('examples/plot.lua')
> dofile('examples/graphics.lua')

The basic [documentation]("http://www.nongnu.org/gsl-shell/graphics.html") for the module is already available in the website. You can find also a [couple of examples]("http://www.nongnu.org/gsl-shell/examples.html").

The compilation with Windows is tricky and there is a bug in a mingw library that will raise an error during the linkage. If you are interested in compiling the code under windows please contact me directly.

I'm sure that there are still a lot of problems and there are a lot of features that should be added. As usual any suggestion or criticism is welcome.

I'm also looking for volunteers so if you want to help don't hesitate to contact the author.

Enjoy,
Francesco

---

### Post by v.cecchetto on 2010-05-23
To install in Lucid amd64:

- install the dependencies 

$ sudo apt-get install libgsl0-dbg libgsl0-dev libgsl0ldbl gsl-bin libreadline-dev libreadline6 libreadline6-dbg libreadline6-dev liblua5.1-0 liblua5.1-0-dbg liblua5.1-0-dev libagg-dev

- download the latest (actually: gsl-shell-0.9.6-src.tgz) source from:

[https://savannah.nongnu.org/files/?group=gsl-shell](https://savannah.nongnu.org/files/?group=gsl-shell)

- extract the .tgz

- edit the file makeconfig (set linux platform)

..............................................
ENABLE_COMPLEX = yes
ENABLE_AGG_PLOT = yes
BUILD_LUA_DLL = no

# PLATFORM should can be linux or mingw
PLATFORM = linux
..............................................

- open a terminal and cd into the gsl-shell directory

$ cd gsl-shell

- compile

$ make

Now you can run it by:

$ ./gsl-shell

:KS

---

