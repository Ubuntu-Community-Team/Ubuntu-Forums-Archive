---
title: "Errors building xorg from cvs"
date: 2005-12-09
forum: Desktop Environments
---

### Post by 23meg on 2005-12-09
I'm trying to build xorg from cvs using [these instructions]("http://xorg.freedesktop.org/wiki/CvsPage") and I'm stuck on the make stage. Here are the errors I get
```
$ sudo make World

Building Release 6.8.

I hope you checked the configuration parameters in ./config/cf
to see if you need to pass BOOTSTRAPCFLAGS.

Fri Dec  9 17:29:38 EET 2005

cd ./config/imake && make  -f Makefile.ini BOOTSTRAPCFLAGS="" CC="cc" clean
make[1]: Entering directory `/usr/src/xc/config/imake'
rm -f ccimake imake.o imake
rm -f *.CKP *.ln *.BAK *.bak *.o core errs ,* *~ *.a tags TAGS make.log \#*
rm -f -r Makefile.proto Makefile Makefile.dep bootstrap
rm -f imakemdep_cpp.h
make[1]: Leaving directory `/usr/src/xc/config/imake'
make  Makefile.boot
make[1]: Entering directory `/usr/src/xc'
cd ./config/imake && make -w -f Makefile.ini BOOTSTRAPCFLAGS="" CC="cc"
make[2]: Entering directory `/usr/src/xc/config/imake'
making imake with BOOTSTRAPCFLAGS= and CROSSCOMPILEFLAGS=-DCROSSCOMPILEDIR="" in config/imake
cc -o ccimake -DCROSSCOMPILEDIR=\"\"  -O -I../../include -I../../imports/x11/include/X11 -DMONOLITH ccimake.c
if [ -n "" ] ; then \
/cc -E `./ccimake` \
-DCROSSCOMPILE_CPP imakemdep.h > imakemdep_cpp.h; \
else touch imakemdep_cpp.h; fi
cc -c  -O -I../../include -I../../imports/x11/include/X11 -DMONOLITH `./ccimake` imake.c
cc -o imake  -O -I../../include -I../../imports/x11/include/X11 -DMONOLITH imake.o
make[2]: Leaving directory `/usr/src/xc/config/imake'
rm -f ./config/makedepend/Makefile.proto
./config/imake/imake -I./config/cf  -s ./config/makedepend/Makefile.proto -f ./config/makedepend/Imakefile -DTOPDIR=../.. -DCURDIR=./config/makedepend
cd ./config/makedepend && rm -f -r Makefile Makefile.dep makedepend *.o bootstrap
cd ./config/makedepend && make -f Makefile.proto bootstrap
make[2]: Entering directory `/usr/src/xc/config/makedepend'
Makefile.proto:36: *** missing `endef', unterminated `define'.  Stop.
make[2]: Leaving directory `/usr/src/xc/config/makedepend'
make[1]: *** [depend.bootstrap] Error 2
make[1]: Leaving directory `/usr/src/xc'
make: *** [World] Error 2

```

Any ideas?

---

### Post by David Jaša on 2005-12-09
```
Makefile.proto:36: *** missing `endef', unterminated `define'.  Stop.
```
Here's the problem but I don't know anything else about it (can't try myself).

---

