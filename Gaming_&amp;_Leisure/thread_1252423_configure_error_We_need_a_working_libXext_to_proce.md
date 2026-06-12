---
title: "configure: error: We need a working libXext to proceed"
date: 2009-08-28
forum: Gaming &amp; Leisure
---

### Post by Captain_Glen on 2009-08-28
Hi,

I am trying to run the Space Hulk game on Ubuntu 9.04.  I downloaded it from: [http://r.vinot.free.fr/spacehulk/index.html](http://r.vinot.free.fr/spacehulk/index.html)

It says it runs on linux.  The instructions for installing are:
./configure
make
sudo make install

But when I run ./configure I get this error: configure: error: We need a working libXext to proceed

Here is the output of ./configure:

glen@glen-desktop:~/Documents/Space Hulk/spacehulk-1.5-beta1$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc   ) works... yes
checking whether the C compiler (gcc   ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for c++... c++
checking whether the C++ compiler (c++   ) works... yes
checking whether the C++ compiler (c++   ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking whether c++ supports -fno-exceptions... yes
checking whether c++ supports -fno-check-new... yes
checking whether c++ supports -fexceptions... yes
checking how to run the C++ preprocessor... c++ -E
checking whether c++ supports -frepo... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking for ranlib... ranlib
checking for strip... strip
checking for Cygwin environment... no
checking for mingw32 environment... no
updating cache ./config.cache
loading cache ./config.cache within ltconfig
checking whether -lc should be explicitly linked in... yes
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
finding the maximum length of command line arguments... 73729
checking if gcc supports -c -o file.o... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlopen in -ldl... yes
checking for dlfcn.h... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
creating libtool
updating cache ./config.cache
loading cache ./config.cache
loading cache ./config.cache within ltconfig
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
ltcf-cxx: with_gcc=yes ; with_gnu_ld=yes
checking for objdir... .libs
checking for c++ option to produce PIC... -fPIC -DPIC
checking if c++ PIC flag -fPIC -DPIC works... yes
checking if c++ static flag -static works... yes
finding the maximum length of command line arguments... (cached) 73729
checking if c++ supports -c -o file.o... (cached) yes
checking if c++ supports -fno-rtti -fno-exceptions ... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlfcn.h... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
appending configuration tag "CXX" to libtool
checking for object suffix... o
checking for executable suffix... no
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for res_init... no
checking for killpg in -lucb... no
checking size of int... 4
checking size of long... 4
checking size of char *... 4
checking size of char... 1
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... no
configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either.

---

### Post by BoyOfDestiny on 2009-08-28
You have a lot of "... missing" errors. So in that case you just need to install what's needed.

Grab these from Synaptic or from Terminal

```
sudo apt-get install libxext-dev autoconf automake build-essential
```

You probably have build-essential installed already, but just to be safe. :)

---

### Post by Captain_Glen on 2009-08-28
Thanks for the reply.

I have installed those packages and now I get a different error:
checking for Qt... configure: error: Qt (>= Qt 3.0.1) (headers and libraries) not found. Please check your installation!

I presume I have to install QT.  But I have looked in synaptic and it says I have libqt4-qt3support installed.  I can't find a qt3 package.

Here is the full output of ./configure
glen@glen-desktop:~/Documents/Space Hulk/spacehulk-1.5-beta1$ ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking whether the C compiler (gcc   ) works... yes
checking whether the C compiler (gcc   ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for c++... c++
checking whether the C++ compiler (c++   ) works... yes
checking whether the C++ compiler (c++   ) is a cross-compiler... no
checking whether we are using GNU C++... yes
checking whether c++ accepts -g... yes
checking whether c++ supports -fno-exceptions... yes
checking whether c++ supports -fno-check-new... yes
checking whether c++ supports -fexceptions... yes
checking how to run the C++ preprocessor... c++ -E
checking whether c++ supports -frepo... yes
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking for ranlib... ranlib
checking for strip... strip
checking for Cygwin environment... no
checking for mingw32 environment... no
updating cache ./config.cache
loading cache ./config.cache within ltconfig
checking whether -lc should be explicitly linked in... yes
checking for objdir... .libs
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
finding the maximum length of command line arguments... 73729
checking if gcc supports -c -o file.o... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlopen in -ldl... yes
checking for dlfcn.h... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
creating libtool
updating cache ./config.cache
loading cache ./config.cache
loading cache ./config.cache within ltconfig
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
ltcf-cxx: with_gcc=yes ; with_gnu_ld=yes
checking for objdir... .libs
checking for c++ option to produce PIC... -fPIC -DPIC
checking if c++ PIC flag -fPIC -DPIC works... yes
checking if c++ static flag -static works... yes
finding the maximum length of command line arguments... (cached) 73729
checking if c++ supports -c -o file.o... (cached) yes
checking if c++ supports -fno-rtti -fno-exceptions ... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlfcn.h... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
appending configuration tag "CXX" to libtool
checking for object suffix... o
checking for executable suffix... no
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for res_init... no
checking for killpg in -lucb... no
checking size of int... 4
checking size of long... 4
checking size of char *... 4
checking size of char... 1
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... no
configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either.
glen@glen-desktop:~/Documents/Space Hulk/spacehulk-1.5-beta1$ make
make: *** No targets specified and no makefile found.  Stop.
glen@glen-desktop:~/Documents/Space Hulk/spacehulk-1.5-beta1$ ./make
bash: ./make: No such file or directory
glen@glen-desktop:~/Documents/Space Hulk/spacehulk-1.5-beta1$ emerge -D libXext
bash: emerge: command not found
glen@glen-desktop:~/Documents/Space Hulk/spacehulk-1.5-beta1$ ./make
bash: ./make: No such file or directory
glen@glen-desktop:~/Documents/Space Hulk/spacehulk-1.5-beta1$ make
make: *** No targets specified and no makefile found.  Stop.
glen@glen-desktop:~/Documents/Space Hulk/spacehulk-1.5-beta1$ ./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal-1.4... missing
checking for working autoconf... found
checking for working automake-1.4... missing
checking for working autoheader... found
checking for working makeinfo... missing
checking for gcc... (cached) gcc
checking whether the C compiler (gcc   ) works... yes
checking whether the C compiler (gcc   ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for c++... (cached) c++
checking whether the C++ compiler (c++   ) works... yes
checking whether the C++ compiler (c++   ) is a cross-compiler... no
checking whether we are using GNU C++... (cached) yes
checking whether c++ accepts -g... (cached) yes
checking whether c++ supports -fno-exceptions... (cached) yes
checking whether c++ supports -fno-check-new... (cached) yes
checking whether c++ supports -fexceptions... (cached) yes
checking how to run the C++ preprocessor... (cached) c++ -E
checking whether c++ supports -frepo... (cached) yes
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for /usr/bin/ld option to reload object files... (cached) -r
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
checking whether ln -s works... (cached) yes
checking how to recognise dependant libraries... (cached) pass_all
checking for ranlib... (cached) ranlib
checking for strip... (cached) strip
checking for Cygwin environment... (cached) no
checking for mingw32 environment... (cached) no
loading cache ./config.cache within ltconfig
checking whether -lc should be explicitly linked in... (cached) yes
checking for objdir... .libs
checking for gcc option to produce PIC...  -fPIC -DPIC
checking if gcc PIC flag  -fPIC -DPIC works... (cached) yes
checking if gcc static flag -static works... (cached) yes
finding the maximum length of command line arguments... (cached) 73729
checking if gcc supports -c -o file.o... (cached) yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlfcn.h... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
creating libtool
loading cache ./config.cache
loading cache ./config.cache within ltconfig
checking host system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
ltcf-cxx: with_gcc=yes ; with_gnu_ld=yes
checking for objdir... .libs
checking for c++ option to produce PIC... -fPIC -DPIC
checking if c++ PIC flag -fPIC -DPIC works... yes
checking if c++ static flag -static works... yes
finding the maximum length of command line arguments... (cached) 73729
checking if c++ supports -c -o file.o... (cached) yes
checking if c++ supports -fno-rtti -fno-exceptions ... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking command to parse /usr/bin/nm -B output... ok
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for dlfcn.h... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) no
appending configuration tag "CXX" to libtool
checking for object suffix... o
checking for executable suffix... no
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for res_init... no
checking for killpg in -lucb... no
checking size of int... 4
checking size of long... 4
checking size of char *... 4
checking size of char... 1
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for Xinerama... no
checking for pthread_create in -lpthread... yes
checking for libpng... no
checking for libjpeg6b... no
checking for libjpeg... no
configure: warning: libjpeg not found. disable JPEG support.
checking for Qt... configure: error: Qt (>= Qt 3.0.1) (headers and libraries) not found. Please check your installation!

---

### Post by BoyOfDestiny on 2009-08-28
> **Captain_Glen said:**
> Thanks for the reply.

I have installed those packages and now I get a different error:
checking for Qt... configure: error: Qt (>= Qt 3.0.1) (headers and libraries) not found. Please check your installation!

I presume I have to install QT.  But I have looked in synaptic and it says I have libqt4-qt3support installed.  I can't find a qt3 package.

The packages are there, do you have all the repositories enabled? Go to System -> Administration -> Software Sources to make sure...

Anyway, I'm not sure which you need but:
libqt4-dev
libqt3-headers
libqt3-mt-dev

---

### Post by Captain_Glen on 2009-08-29
I have installed those packages but I am still getting the same error.

Here is the config.log:

This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

configure:625: checking host system type
configure:646: checking target system type
configure:664: checking build system type
configure:705: checking for a BSD compatible install
configure:762: checking for -p flag to install
configure:785: checking whether build environment is sane
configure:842: checking whether make sets ${MAKE}
configure:888: checking for working aclocal-1.4
configure:901: checking for working autoconf
configure:914: checking for working automake-1.4
configure:927: checking for working autoheader
configure:940: checking for working makeinfo
configure:1046: checking for gcc
configure:1159: checking whether the C compiler (gcc   ) works
configure:1175: gcc -o conftest     conftest.c  1>&5
configure:1201: checking whether the C compiler (gcc   ) is a cross-compiler
configure:1206: checking whether we are using GNU C
configure:1234: checking whether gcc accepts -g
configure:1267: checking how to run the C preprocessor
configure:1380: checking for c++
configure:1412: checking whether the C++ compiler (c++   ) works
configure:1433: rm -rf SunWS_cache; c++ -o conftest     conftest.C  1>&5
configure:1459: checking whether the C++ compiler (c++   ) is a cross-compiler
configure:1464: checking whether we are using GNU C++
configure:1492: checking whether c++ accepts -g
configure:1981: checking whether c++ supports -fno-exceptions
configure:2039: checking whether c++ supports -fno-check-new
configure:2097: checking whether c++ supports -fexceptions
configure:2614: checking how to run the C++ preprocessor
configure:2717: checking whether c++ supports -frepo
configure:2970: checking for ld used by GCC
configure:3038: checking if the linker (/usr/bin/ld) is GNU ld
configure:3055: checking for /usr/bin/ld option to reload object files
configure:3067: checking for BSD-compatible nm
configure:3105: checking whether ln -s works
configure:3126: checking how to recognise dependant libraries
configure:3447: checking for ranlib
configure:3514: checking for strip
configure:3686: checking for Cygwin environment
configure:3719: checking for mingw32 environment
ltconfig:678:checking for gcc option to produce PIC
ltconfig:687:checking that gcc PIC flag  -fPIC -DPIC works.
ltconfig:749: checking if gcc static flag -static works
ltconfig:780: finding the maximum length of command line arguments
ltconfig:@lineno@: result: 73729
ltconfig:883: checking if gcc supports -fno-rtti -fno-exceptions
ltconfig:884: gcc -c -O2   -fno-rtti -fno-exceptions -c conftest.c  conftest.c 1>&5
ltconfig:1423: checking if global_symbol_pipe works
ltconfig:1424: gcc -c -O2    conftest.c 1>&5
ltconfig:1427: eval "/usr/bin/nm -B conftest.o | sed -n -e 's/^.*[ 	]\([ABCDGISTW]\)[ 	][ 	]*\(\)\([_A-Za-z][_A-Za-z0-9]*\)$/  /p' > conftest.nm"
ltconfig:1479: gcc -o conftest -O2   -fno-builtin   conftest.c conftstm.o 1>&5
ltconfig:1863: checking for dlfcn.h
ltconfig:1902: checking whether a program can dlopen itself
ltconfig:1976: checking whether a statically linked program can dlopen itself
c++ -E conftest.cc
ltconfig:678:checking for c++ option to produce PIC
ltconfig:687:checking that c++ PIC flag -fPIC -DPIC works.
ltconfig:697: c++ -c -O2 -fno-exceptions -fno-check-new -fPIC -DPIC -DPIC  conftest.cc 1>&5
ltconfig:749: checking if c++ static flag -static works
ltconfig:758: c++ -o conftest -O2 -fno-exceptions -fno-check-new   -static conftest.cc  1>&5
ltconfig:780: finding the maximum length of command line arguments
ltconfig:@lineno@: result: 73729
ltconfig:883: checking if c++ supports -fno-rtti -fno-exceptions
ltconfig:884: c++ -c -O2 -fno-exceptions -fno-check-new -fno-rtti -fno-exceptions -c conftest.cc  conftest.cc 1>&5
ltconfig:1423: checking if global_symbol_pipe works
ltconfig:1424: c++ -c -O2 -fno-exceptions -fno-check-new  conftest.cc 1>&5
ltconfig:1427: eval "/usr/bin/nm -B conftest.o | sed -n -e 's/^.*[ 	]\([ABCDGISTW]\)[ 	][ 	]*\(\)\([_A-Za-z][_A-Za-z0-9]*\)$/  /p' > conftest.nm"
ltconfig:1479: c++ -o conftest -O2 -fno-exceptions -fno-check-new -fno-builtin -fno-rtti -fno-exceptions   conftest.cc conftstm.o 1>&5
ltconfig:1863: checking for dlfcn.h
ltconfig:1902: checking whether a program can dlopen itself
ltconfig:1976: checking whether a statically linked program can dlopen itself
configure:3866: checking for object suffix
configure:3872: gcc -c -O2    conftest.c 1>&5
configure:3892: checking for executable suffix
configure:3902: gcc -o conftest -O2     conftest.c  1>&5
configure:4019: checking for main in -lutil
configure:4034: gcc -o conftest -O2     conftest.c -lutil   1>&5
configure:4055: checking for main in -lcompat
configure:4070: gcc -o conftest -O2     conftest.c -lcompat   1>&5
/usr/bin/ld: cannot find -lcompat
collect2: ld returned 1 exit status
configure: failed program was:
#line 4063 "configure"
#include "confdefs.h"

int main() {
main()
; return 0; }
configure:4092: checking for crypt in -lcrypt
configure:4111: gcc -o conftest -O2     conftest.c -lcrypt   1>&5
configure:4186: checking for socklen_t
configure:4216: c++ -c -O2 -fno-exceptions -fno-check-new  conftest.C 1>&5
configure:4283: checking for dnet_ntoa in -ldnet
configure:4302: gcc -o conftest -O2     conftest.c -ldnet   1>&5
/usr/bin/ld: cannot find -ldnet
collect2: ld returned 1 exit status
configure: failed program was:
#line 4291 "configure"
#include "confdefs.h"
/* Override any gcc2 internal prototype to avoid an error.  */
/* We use char because int might match the return type of a gcc2
    builtin and then its argument prototype would still apply.  */
char dnet_ntoa();

int main() {
dnet_ntoa()
; return 0; }
configure:4324: checking for dnet_ntoa in -ldnet_stub
configure:4343: gcc -o conftest -O2     conftest.c -ldnet_stub   1>&5
/usr/bin/ld: cannot find -ldnet_stub
collect2: ld returned 1 exit status
configure: failed program was:
#line 4332 "configure"
#include "confdefs.h"
/* Override any gcc2 internal prototype to avoid an error.  */
/* We use char because int might match the return type of a gcc2
    builtin and then its argument prototype would still apply.  */
char dnet_ntoa();

int main() {
dnet_ntoa()
; return 0; }
configure:4365: checking for inet_ntoa
configure:4393: gcc -o conftest -O2     conftest.c  1>&5
configure:4455: checking for connect
configure:4483: gcc -o conftest -O2     conftest.c  1>&5
configure:4546: checking for remove
configure:4574: gcc -o conftest -O2     conftest.c  1>&5
configure:4638: checking for shmat
configure:4666: gcc -o conftest -O2     conftest.c  1>&5
configure:4730: checking for res_init
configure:4758: gcc -o conftest -O2     conftest.c  1>&5
/tmp/cceNnSpL.o: In function `main':
conftest.c:(.text+0x12): undefined reference to `res_init'
collect2: ld returned 1 exit status
configure: failed program was:
#line 4735 "configure"
#include "confdefs.h"
/* System header to define __stub macros and hopefully few prototypes,
    which can conflict with char res_init(); below.  */
#include <assert.h>
/* Override any gcc2 internal prototype to avoid an error.  */
/* We use char because int might match the return type of a gcc2
    builtin and then its argument prototype would still apply.  */
char res_init();

int main() {

/* The GNU C library defines this for functions which it implements
    to always fail with ENOSYS.  Some functions are actually named
    something starting with __ and the normal name is an alias.  */
#if defined (__stub_res_init) || defined (__stub___res_init)
choke me
#else
res_init();
#endif

; return 0; }
configure:4793: gcc -o conftest -O2     conftest.c   -lresolv 1>&5
configure:4818: checking for killpg in -lucb
configure:4837: gcc -o conftest -O2     conftest.c -lucb   1>&5
/usr/bin/ld: cannot find -lucb
collect2: ld returned 1 exit status
configure: failed program was:
#line 4826 "configure"
#include "confdefs.h"
/* Override any gcc2 internal prototype to avoid an error.  */
/* We use char because int might match the return type of a gcc2
    builtin and then its argument prototype would still apply.  */
char killpg();

int main() {
killpg()
; return 0; }
configure:4906: checking size of int
configure:4925: gcc -o conftest -O2     conftest.c  1>&5
configure: In function 'main':
configure:4919: warning: incompatible implicit declaration of built-in function 'exit'
configure:4944: checking size of long
configure:4963: gcc -o conftest -O2     conftest.c  1>&5
configure: In function 'main':
configure:4957: warning: incompatible implicit declaration of built-in function 'exit'
configure:4982: checking size of char *
configure:5001: gcc -o conftest -O2     conftest.c  1>&5
configure: In function 'main':
configure:4995: warning: incompatible implicit declaration of built-in function 'exit'
configure:5020: checking size of char
configure:5039: gcc -o conftest -O2     conftest.c  1>&5
configure: In function 'main':
configure:5033: warning: incompatible implicit declaration of built-in function 'exit'
configure:5060: checking for dlopen in -ldl
configure:5104: checking for shl_unload in -ldld
configure:5123: gcc -o conftest -O2     conftest.c -ldld   1>&5
/usr/bin/ld: cannot find -ldld
collect2: ld returned 1 exit status
configure: failed program was:
#line 5112 "configure"
#include "confdefs.h"
/* Override any gcc2 internal prototype to avoid an error.  */
/* We use char because int might match the return type of a gcc2
    builtin and then its argument prototype would still apply.  */
char shl_unload();

int main() {
shl_unload()
; return 0; }
configure:5152: checking for extra includes
configure:5183: checking for extra libs
configure:5217: checking for libz
configure:5243: gcc -o conftest -O2        conftest.c    -lz  -lresolv 1>&5
configure:5296: checking for X
configure:5335: gcc -E  conftest.c >/dev/null 2>conftest.out
configure:5411: gcc -o conftest -O2     conftest.c -lXt  1>&5
configure:5585: checking for IceConnectionNumber in -lICE
configure:5604: gcc -o conftest -O2     -L/usr/lib conftest.c -lICE  -lresolv  1>&5
configure:5633: checking for libXext
configure:5659: gcc -o conftest -O2     -L/usr/lib  conftest.c -lXext -lX11  -lresolv 1>&5
configure:5686: checking for Xinerama
configure:5798: checking for pthread_create in -lpthread
configure:5817: gcc -o conftest -O2     conftest.c -lpthread   1>&5
configure:6093: checking for libpng
configure:6127: gcc -o conftest -O2   -I.   -D_REENTRANT  conftest.c  -L/usr/lib  -lpng -lz -lm -lX11  -lresolv 1>&5
configure:6159: checking for libjpeg6b
configure:6197: gcc -o conftest -O2   -I.   -D_REENTRANT  conftest.c -L/usr/lib  -ljpeg6b -lm 1>&5
/usr/bin/ld: cannot find -ljpeg6b
collect2: ld returned 1 exit status
configure: failed program was:
#line 6176 "configure"
#include "confdefs.h"
/* Override any gcc2 internal prototype to avoid an error.  */
struct jpeg_decompress_struct;
typedef struct jpeg_decompress_struct * j_decompress_ptr;
typedef int size_t;
#ifdef __cplusplus
extern "C" {
#endif
    void jpeg_CreateDecompress(j_decompress_ptr cinfo,
                                    int version, size_t structsize);
#ifdef __cplusplus
}
#endif
/* We use char because int might match the return type of a gcc2
    builtin and then its argument prototype would still apply.  */

int main() {
jpeg_CreateDecompress(0L, 0, 0);
; return 0; }
configure:6220: checking for libjpeg
configure:6258: gcc -o conftest -O2   -I.   -D_REENTRANT  conftest.c -L/usr/lib  -ljpeg -lm 1>&5
configure: 6298: /usr/include/jpeglib.h
taking that
configure:6461: checking for Qt
configure: 6525: /usr/lib/qt3/include/qstyle.h
configure: 6525: /usr/lib/qt3/qstyle.h
configure: 6525: /usr/lib/qt/include/qstyle.h
configure: 6525: /usr/lib/qt/qstyle.h
configure: 6525: /usr/local/qt/include/qstyle.h
configure: 6525: /usr/include/qt/qstyle.h
configure: 6525: /usr/include/qstyle.h
configure: 6525: /usr/X11R6/include/X11/qt/qstyle.h
configure: 6525: /usr/X11R6/include/qt/qstyle.h
configure: 6525: /usr/X11R6/include/qt2/qstyle.h
configure: 6525: ./qstyle.h
tried NO
tried /usr/lib/qt3/lib
tried /usr/lib/qt3
tried /usr/lib/qt/lib
tried /usr/lib/qt
tried /usr/X11R6/lib
configure:6637: rm -rf SunWS_cache; c++ -o conftest -O2 -fno-exceptions -fno-check-new -INO -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -L/usr/lib -L/usr/lib   conftest.C  -lqt-mt -lpng -lz -lm -ljpeg -ldl  -lXext -lX11 -lSM -lICE  -lresolv -lpthread 1>&5
conftest.C:2:21: error: qglobal.h: No such file or directory
conftest.C:3:26: error: qapplication.h: No such file or directory
conftest.C:4:21: error: qcursor.h: No such file or directory
conftest.C:5:27: error: qstylefactory.h: No such file or directory
conftest.C:6:34: error: private/qucomextra_p.h: No such file or directory
conftest.C:8:2: error: #error 1
conftest.C: In function 'int main()':
conftest.C:12: error: 'QStyleFactory' was not declared in this scope
conftest.C:12: error: expected `;' before '::' token
conftest.C:13: error: 'QCursor' was not declared in this scope
conftest.C:13: error: expected `;' before 'c'
configure: failed program was:
#include "confdefs.h"
#include <qglobal.h>
#include <qapplication.h>
#include <qcursor.h>
#include <qstylefactory.h>
#include <private/qucomextra_p.h>
#if ! (QT_VERSION >= 301)
#error 1
#endif

int main() {
    (void)QStyleFactory::create(QString::null);
    QCursor c(Qt::WhatsThisCursor);
    return 0;
}

---

### Post by Perfect Storm on 2009-08-29
It properly needs a re-write the config files. It havn't been updated since 2004 and a lot of stuff have happened since then.

---

