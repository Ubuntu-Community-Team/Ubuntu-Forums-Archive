---
title: "Compilation of XOOPIC"
date: 2009-10-22
forum: Education &amp; Science
---

### Post by LowDepth on 2009-10-22
Hey there, After successful configuring I'm trying to "make" the mentioned software. This is the error message I get:

```
stefan@laptop:~/Downloads/PhysikProgramme/xoopic$ make
make  all-recursive
make[1]: Betrete Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic'
Making all in otools
make[2]: Betrete Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic/otools'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic/otools'
Making all in physics
make[2]: Betrete Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic/physics'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic/physics'
Making all in advisor
make[2]: Betrete Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic/advisor'
make[2]: Für das Ziel »all« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic/advisor'
Making all in xg
make[2]: Betrete Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic/xg'
g++ -DHAVE_CONFIG_H -I. -I../. -I../otools -I../otools -I../physics -I../advisor -I../config -I/usr/local/xgrafix/include      -Wall -Wno-unused  -g -O2 -pipe -g -O2 -pipe   -DUNIX     -c -o main.o main.cpp
In file included from ../physics/boundary.h:55,
                 from ../physics/grid.h:63,
                 from ../physics/fields.h:81,
                 from ../physics/sptlrgn.h:75,
                 from main.cpp:13:
../physics/spacetimefunc.h: In constructor »SpaceTimeFunction::SpaceTimeFunction(float, float, float, float, float, float, float, float, float, float, ostring, int)«:
../physics/spacetimefunc.h:124: Warnung: veraltete Konvertierung von Zeichenkettenkonstante in »char*«
../physics/spacetimefunc.h:125: Warnung: veraltete Konvertierung von Zeichenkettenkonstante in »char*«
main.cpp: In function »int main(int, char**)«:
main.cpp:192: nicht implementiert: »inline« beim Aufruf von »int printf(const char*, ...)« gescheitert: redefined extern inline functions are not considered for inlining
main.cpp:63: nicht implementiert: von hier aufgerufen
main.cpp:192: nicht implementiert: »inline« beim Aufruf von »int printf(const char*, ...)« gescheitert: redefined extern inline functions are not considered for inlining
main.cpp:64: nicht implementiert: von hier aufgerufen
main.cpp:192: nicht implementiert: »inline« beim Aufruf von »int printf(const char*, ...)« gescheitert: redefined extern inline functions are not considered for inlining
main.cpp:65: nicht implementiert: von hier aufgerufen
main.cpp:192: nicht implementiert: »inline« beim Aufruf von »int printf(const char*, ...)« gescheitert: redefined extern inline functions are not considered for inlining
main.cpp:66: nicht implementiert: von hier aufgerufen
main.cpp:192: nicht implementiert: »inline« beim Aufruf von »int printf(const char*, ...)« gescheitert: redefined extern inline functions are not considered for inlining
main.cpp:67: nicht implementiert: von hier aufgerufen
main.cpp:192: nicht implementiert: »inline« beim Aufruf von »int printf(const char*, ...)« gescheitert: redefined extern inline functions are not considered for inlining
main.cpp:82: nicht implementiert: von hier aufgerufen
main.cpp:192: nicht implementiert: »inline« beim Aufruf von »int printf(const char*, ...)« gescheitert: redefined extern inline functions are not considered for inlining
main.cpp:83: nicht implementiert: von hier aufgerufen
main.cpp:192: nicht implementiert: »inline« beim Aufruf von »int printf(const char*, ...)« gescheitert: redefined extern inline functions are not considered for inlining
main.cpp:102: nicht implementiert: von hier aufgerufen
make[2]: *** [main.o] Fehler 1
make[2]: Verlasse Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic/xg'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/stefan/Downloads/PhysikProgramme/xoopic'
make: *** [all] Fehler 2

```

Any suggestions?

---

### Post by jmrk on 2009-10-23
Hi Stefan,

after spending some hours we finally got it running ;). Xoopic won't compile with your g++ version. You need the following packages and you have to manually install them with

sudo dpkg -i *
(run that in the dir into which you downloaded them)

cpp-3.4_3.4.6-1ubuntu2_i386.deb
g++-3.4_3.4.6-1ubuntu2_i386.deb
gcc-3.4_3.4.6-1ubuntu2_i386.deb
gcc-3.4-base_3.4.6-1ubuntu2_i386.deb
libstdc++6-dev_3.4.6-1ubuntu2_i386.deb

from:
[http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-3.4/)

After that you probably need:
in /usr/bin
sudo ln -s g++-3.4 g++

Additionally, we had to install the package
zlib1g-dev
(ld complained about the missing library).

Best regards,

Jörgen

---

### Post by LowDepth on 2009-10-26
Hello Jörgen, thank you very much for your reply. Your instructions worked perfectly ;).

---

### Post by kocmodpom on 2010-03-15
How lucky you are! I can't even get past the ./configure stage to install it.

I have already installed both dfftw-dev and libfftw2-dev in an attempt to crush the dfftw and sfftw warnings without success

I have spent the last two days on #ubuntu IRC and have gotten nowhere.

Here are my ./configure errors

```
kocmodpom@kocmodpom-laptop:~/Downloads/xoopic$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
using HDF5? ... yes
checking for hdf5.h... /usr/include/hdf5.h
checking for libhdf5.a... /usr/lib/libhdf5.a
checking for libgpfs.a... no
checking for libgpfs... no
checking for h5diff... no
Using C++ compiler g++
Using C compiler gcc
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking whether time.h and sys/time.h may both be included... yes
checking for BSD-compatible nm... 
/usr/bin/nm -B
Setting the flags per system and C++ compiler: g++
checking for g++... /usr/bin/g++
Serial C++ compiler is `g++'
checking g++ version... g++
configure: WARNING: Caution: version  is not known to work.
checking for -fsquangle... no
checking how to build libraries... with ar cr  
checking for gcc... /usr/bin/gcc
Serial C compiler is `gcc'
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking iostream usability... yes
checking iostream presence... yes
checking for iostream... yes
checking strstream usability... yes
checking strstream presence... yes
checking for strstream... yes
checking fstream usability... yes
checking fstream presence... yes
checking for fstream... yes
checking sstream usability... yes
checking sstream presence... yes
checking for sstream... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
Calling config/macros.m4
Calling config/cxx.m4
checking whether c++ compiler supports exception handling... yes
checking whether c++ compiler supports typename... yes
checking whether c++ compiler can explicitly instantiate templates... yes
checking whether c++ compiler supports RTTI... yes
checking whether c++ compiler supports namespaces... yes
checking whether c++ compiler has complex in the namespace std... yes
checking whether c++ compiler has streams in the namespace std... yes
checking whether c++ compiler can overload const type conversions... yes
checking whether c++ compiler knows mutable... yes
checking whether template friends need brackets... yes
checking whether nontype template operators are allowed... no
checking whether static variables can be declared generally... yes
config/cxx.m4 finished
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking what the library suffix is... .a
checking how to install libraries... with ${INSTALL} -m 644
configure: WARNING: x11.m4 is obsolete.  Please use AC_PATH_X or AC_PATH_XTRA.
checking for X11/Xlib.h... /usr/include/X11/Xlib.h
checking for libX11.a... /usr/lib/libX11.a
checking for libXpm.a... /usr/lib/libXpm.a
checking for libXGC250.a... /usr/local/lib/libXGC250.a
checking for xgrafix.h... /usr/local/include/xgrafix.h
checking for xgscalar.h... /usr/local/include/xgscalar.h
checking for SCALAR in /usr/local/include/xgscalar.h... #define SCALAR double
checking for tclsh... /usr/bin/tclsh
checking for tclConfig.sh... /usr/lib/tclConfig.sh
checking for tkConfig.sh... /usr/lib/tkConfig.sh
checking for libtcl8.4.a... /usr/lib/libtcl8.4.a
checking for libtk8.4.a... /usr/lib/libtk8.4.a
checking for up-to-date Tcl version in tcl.h... 8.4
checking for up-to-date Tk version in tk.h... 8.4
Checking for fftw...
checking for dfftw.h... no
configure: WARNING: dfftw.h not found in /home/kocmodpom/include:/usr/local/fftw/include:/loc/fftw/include:/local/fftw/include:/usr/common/usg/include:/usr/include.  Set location with --with-dfftw-incdir=
checking for sfftw.h... no
configure: WARNING: sfftw.h not found in /home/kocmodpom/include:/usr/local/fftw/include:/loc/fftw/include:/local/fftw/include:/usr/common/usg/include:.  Set location with --with-sfftw-incdir=
Making Makefiles
configure: creating ./config.status
config.status: creating Makefile
config.status: creating otools/Makefile
config.status: creating advisor/Makefile
config.status: creating physics/Makefile
config.status: creating xg/Makefile
config.status: creating config/Makefile
config.status: creating ./config.h
config.status: ./config.h is unchanged
config.status: executing depfiles commands
kocmodpom@kocmodpom-laptop:~/Downloads/xoopic$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
using HDF5? ... yes
checking for hdf5.h... /usr/include/hdf5.h
checking for libhdf5.a... /usr/lib/libhdf5.a
checking for libgpfs.a... no
checking for libgpfs... no
checking for h5diff... no
Using C++ compiler g++
Using C compiler gcc
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking whether time.h and sys/time.h may both be included... yes
checking for BSD-compatible nm... 
/usr/bin/nm -B
Setting the flags per system and C++ compiler: g++
checking for g++... /usr/bin/g++
Serial C++ compiler is `g++'
checking g++ version... g++
configure: WARNING: Caution: version  is not known to work.
checking for -fsquangle... no
checking how to build libraries... with ar cr  
checking for gcc... /usr/bin/gcc
Serial C compiler is `gcc'
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking iostream usability... yes
checking iostream presence... yes
checking for iostream... yes
checking strstream usability... yes
checking strstream presence... yes
checking for strstream... yes
checking fstream usability... yes
checking fstream presence... yes
checking for fstream... yes
checking sstream usability... yes
checking sstream presence... yes
checking for sstream... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
Calling config/macros.m4
Calling config/cxx.m4
checking whether c++ compiler supports exception handling... yes
checking whether c++ compiler supports typename... yes
checking whether c++ compiler can explicitly instantiate templates... yes
checking whether c++ compiler supports RTTI... yes
checking whether c++ compiler supports namespaces... yes
checking whether c++ compiler has complex in the namespace std... yes
checking whether c++ compiler has streams in the namespace std... yes
checking whether c++ compiler can overload const type conversions... yes
checking whether c++ compiler knows mutable... yes
checking whether template friends need brackets... yes
checking whether nontype template operators are allowed... no
checking whether static variables can be declared generally... yes
config/cxx.m4 finished
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ranlib... ranlib
checking what the library suffix is... .a
checking how to install libraries... with ${INSTALL} -m 644
configure: WARNING: x11.m4 is obsolete.  Please use AC_PATH_X or AC_PATH_XTRA.
checking for X11/Xlib.h... /usr/include/X11/Xlib.h
checking for libX11.a... /usr/lib/libX11.a
checking for libXpm.a... /usr/lib/libXpm.a
checking for libXGC250.a... /usr/local/lib/libXGC250.a
checking for xgrafix.h... /usr/local/include/xgrafix.h
checking for xgscalar.h... /usr/local/include/xgscalar.h
checking for SCALAR in /usr/local/include/xgscalar.h... #define SCALAR double
checking for tclsh... /usr/bin/tclsh
checking for tclConfig.sh... /usr/lib/tclConfig.sh
checking for tkConfig.sh... /usr/lib/tkConfig.sh
checking for libtcl8.4.a... /usr/lib/libtcl8.4.a
checking for libtk8.4.a... /usr/lib/libtk8.4.a
checking for up-to-date Tcl version in tcl.h... 8.4
checking for up-to-date Tk version in tk.h... 8.4
Checking for fftw...
checking for dfftw.h... no
configure: WARNING: dfftw.h not found in /home/kocmodpom/include:/usr/local/fftw/include:/loc/fftw/include:/local/fftw/include:/usr/common/usg/include:/usr/include.  Set location with --with-dfftw-incdir=
checking for sfftw.h... no
configure: WARNING: sfftw.h not found in /home/kocmodpom/include:/usr/local/fftw/include:/loc/fftw/include:/local/fftw/include:/usr/common/usg/include:.  Set location with --with-sfftw-incdir=
Making Makefiles
configure: creating ./config.status
config.status: creating Makefile
config.status: creating otools/Makefile
config.status: creating advisor/Makefile
config.status: creating physics/Makefile
config.status: creating xg/Makefile
config.status: creating config/Makefile
config.status: creating ./config.h
config.status: ./config.h is unchanged
config.status: executing depfiles commands
kocmodpom@kocmodpom-laptop:~/Downloads/xoopic$ 
```

---

