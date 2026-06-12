---
title: "SVN installation problem"
date: 2009-05-08
forum: General Help
---

### Post by geraldvillorente on 2009-05-08
Anyone who can shed me some light please!

ERROR:

> 
root@wizardsides:/tmp/subversion-1.6.1# ./configure --with-ssl --enable-javahl --with-jdk=/usr/lib/jvm/java-6-sun
configure: Configuring Subversion 1.6.1
configure: creating config.nice
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether ln -s works... yes
checking for a BSD-compatible install... /usr/bin/install -c
configure: Apache Portable Runtime (APR) library configuration
checking for APR... yes
checking APR version... 1.2.12
configure: Apache Portable Runtime Utility (APRUTIL) library configuration
checking for APR-util... yes
checking APR-UTIL version... 1.2.12
checking for pkg-config... /usr/bin/pkg-config
configure: checking neon library
checking neon library version... 0.28.2
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
configure: looking for apr_memcache as part of apr-util
checking apr_memcache.h usability... no
checking apr_memcache.h presence... no
checking for apr_memcache.h... no
checking for Apache module support via DSO through APXS... no
==================================================================
WARNING: skipping the build of mod_dav_svn
         try using --with-apxs
==================================================================
configure: checking sqlite library
amalgamation not found at /tmp/subversion-1.6.1/sqlite-amalgamation/sqlite3.c
checking sqlite3.h usability... yes
checking sqlite3.h presence... yes
checking for sqlite3.h... yes
checking sqlite library version (via header)... okay
checking for sqlite3_close in -lsqlite3... yes
configuring libtool now
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether libtool needs -no-undefined... no
checking whether to avoid circular linkage at all costs... no
checking for trang... none
checking for socket in -lsocket... no
checking for availability of Berkeley DB... no
checking whether to look for SASL... yes
configure: Looking in default locations
checking sasl/sasl.h usability... no
checking sasl/sasl.h presence... no
checking for sasl/sasl.h... no
checking for sasl/sasl.h... (cached) no
checking for availability of Cyrus SASL v2... no
checking for Mac OS KeyChain Services... no
checking whether APR has support for DSOs... yes
checking for D-Bus .pc file... no
checking whether to look for GNOME Keyring... no
checking for msgfmt... none
checking for msgmerge... none
checking for xgettext... none
checking whether to look for KWallet... no
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking for size_t... yes
checking for working memcmp... yes
checking for vprintf... yes
checking for _doprnt... no
checking for symlink... yes
checking for readlink... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for inflate in -lz... yes
checking for python... /usr/bin/python
checking for JDK... configure: WARNING: no JNI header files found.
no
checking for perl... /usr/bin/perl
checking for ruby... none
checking for swig... none
configure: Configuring python swig binding
checking for Python includes... -I/usr/include/python2.6
checking for compiling Python extensions... gcc -pthread -fPIC
checking for linking Python extensions... gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions
checking for linking Python libraries... -Wl,-O1 -Wl,-Bsymbolic-functions
checking for apr_int64_t Python/C API format string... L
checking perl version... 5010000
checking for ctypesgen.py... none
[COLOR="Indigo"]configure: error: Cannot compile JavaHL without a suitable JDK.
                  Please specify a suitable JDK using the --with-jdk [/COLOR]option.


Please guide me how to get rid in this problem...:)

---

### Post by soro2005 on 2009-05-09
Says you don't have a java development kit (jdk) installed. You could open Synaptic and install one. :-D

Or alternatively, try skipping the last flag in the configure line. Perhaps it's trying to force a jdk which you don't have.

Like so:
```
 ./configure --with-ssl --enable-javahl
```

---

### Post by geraldvillorente on 2009-05-09
thank you man...you rock...problem solved...

cheers,

---

