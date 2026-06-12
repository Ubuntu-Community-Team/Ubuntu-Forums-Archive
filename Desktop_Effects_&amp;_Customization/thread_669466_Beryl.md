---
title: "Beryl"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by lacroixmouz on 2008-01-16
I want to install beryl, but I don't understand a thing with the instructions on how to do it. However I understood that it has to do with the Terminal. Can you explain me what exactly do I have to do? ( sorry I am new)

These are the instructions for the install :

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Compilers and Options
=====================

Some systems require unusual options for compilation or linking that the
`configure' script does not know about.  Run `./configure --help' for
details on some of the pertinent environment variables.

   You can give `configure' initial values for configuration parameters
by setting variables in the command line or in the environment.  Here
is an example:

     ./configure CC=c89 CFLAGS=-O2 LIBS=-lposix

   *Note Defining Variables::, for more details.

---

### Post by FuturePilot on 2008-01-16
Beryl is no longer being developed. If you have installed Ubuntu 7.10 it has Compiz Fusion already installed. You just need to install the 3D driver for your graphics card. System>Administrator>Restricted Driver Manager.
Compiz Fusion is the result of the Compiz-Beryl merger.

---

### Post by lacroixmouz on 2008-01-16
I have done all these, but how can I set my own desktop effects, the only effects I have is those which are enabled from system->Prefrences-> appearnce-> visual effects

---

### Post by FuturePilot on 2008-01-16
```
sudo apt-get install compizconfig-settings-manager
```
System>Preferences>Appearance>Visual Effects. Select Custom.

---

