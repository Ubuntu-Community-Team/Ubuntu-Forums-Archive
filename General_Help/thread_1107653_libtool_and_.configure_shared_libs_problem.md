---
title: "libtool and ./configure shared libs problem"
date: 2009-03-27
forum: General Help
---

### Post by scootklein on 2009-03-27
Hey all,

I'm trying to cross-compile shared libs for an app called TSlib (touchscreen library) that will go on an embedded arm-linux board.  The configure script should be detecting that I am able to accept shared libraries and i believe its using libtools to do so.

scott@SCOTTKLEINLTUBUNTU:~$ libtool --features
host: i686-pc-linux-gnu
enable shared libraries
enable static libraries

scott@SCOTTKLEINLTUBUNTU:~$ ./configure CONFIG_SITE=arm-linux.autogen --host=arm-linux --prefix=/share/tslib --disable-inputapi --enable-shared=yes --enable-static=no
...
...
checking if libtool supports shared libraries... no
checking whether to build shared libraries... no
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by arm-linux-g++... /share/eldk/usr/arm-linux-gnueabi/bin/ld
...
...



Are there any standard flags withe the GNU configure to force allow shared libraries to be created?  Right now I'm getting a bunch of .la files instead of .so.  I've cross-compiled other apps before with the host same descriptor and shared libraries come through without a problem.

Thanks,
Scott

---

