---
title: "Compile error with Crystal Space"
date: 2006-08-10
forum: Desktop Environments
---

### Post by UltraSonicSite on 2006-08-10
ultrasonicsite@ubuntu:~/Desktop/cel$ sudo ./configure
Password:
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to create a directory... mkdir
checking how to create a directory tree... mkdir -p
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to treat C++ warnings as errors... -Werror
checking how to enable C++ PIC generation... -fPIC
checking if -shared is accepted... -shared
checking if -soname is accepted... yes
checking for install... install
checking for ranlib... ranlib
checking for doxygen... no
checking for dot... no
checking for texi2dvi... no
checking for texi2pdf... no
checking for dvips... no
checking for dvipdf... dvipdf
checking for makeinfo... no
checking for perl5... no
checking for perl... perl
checking for perl5... (cached) perl
checking for TemplateToolkit... no
checking for ttree... no
checking for swig... no
checking how to enable C++ compilation warnings... -Wall
checking how to suppress C++ unused variable warnings... -Wno-unused
checking how to suppress C++ uninitialized warnings... -Wno-uninitialized
checking for pthread... yes
checking for pthread recursive mutexes... PTHREAD_MUTEX_RECURSIVE
checking how to suppress C++ `long double' warnings... no
checking for python... python
checking for python SDK... yes
checking if python SDK is usable... no
checking for pkg-config... pkg-config
checking if pkg-config recognizes cppunit... no
checking for cppunit-config... no
checking for libcppunit... no
checking for pthread... (cached) yes
checking for pthread recursive mutexes... (cached) PTHREAD_MUTEX_RECURSIVE
checking if pkg-config recognizes NL... no
checking for NL-config... no
checking for libNL... no
checking for cs-config... /usr/bin/cs-config
checking if Crystal Space version >= 0.99... yes (version 0.99)
checking if Crystal Space SDK is usable... no
configure: error:
*** Crystal Space could not be found or was unusable. The latest version is
*** always available from [http://www.crystalspace3d.org/](http://www.crystalspace3d.org/)
*** Also, be sure that you have either installed Crystal Space or set the
*** CRYSTAL environment variable properly.
[/quote]
How is it not usable? It was install through synaptic along with everything else. Everything I've tried does not work.

---

### Post by UltraSonicSite on 2006-08-10
It seems like it could easily be fixed.

---

### Post by rne1223 on 2008-01-11
How?

---

### Post by lgambett on 2008-01-11
Most likely you have to install crystalspace-dev. This is always true when you compile something with dependencies; you have to install the development files, not only the binaries.

---

