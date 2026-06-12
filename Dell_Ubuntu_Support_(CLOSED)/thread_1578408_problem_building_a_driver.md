---
title: "problem building a driver"
date: 2010-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by naleri on 2010-09-20
Hi,

I'm a new Ubuntu user (10.04 LTS) and I have a problem installing a driver in a Linux Inspiron 11z to get my HDMI-to-VGA adapter working. It is an USB Graphics Adapter, similar to this one [http://plugable.com/products/uga-125/.]("http://plugable.com/products/uga-125/")

My husband previously posted this thread, but didn't get an answer. The problem is that I downloaded the manufacturer's driver (Linux Version), untared it and  followed instructions in the read me file, but it didn't work. 

This is the output for the first instruction (./configure):
```
natalia@Inspiron11z:~/Downloads$ cd libdlo-0.1.2/
natalia@Inspiron11z:~/Downloads/libdlo-0.1.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking how to run the C preprocessor... gcc -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking usb.h usability... yes
checking usb.h presence... yes
checking for usb.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for inline... inline
checking for int32_t... yes
checking for size_t... yes
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for uint8_t... yes
checking for usb_open in -lusb... yes
checking for usb_get_driver_np... yes
checking for usb_get_configuration... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking for gettimeofday... yes
checking for strchr... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating test/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

    libdlo 0.1.2
    ========

    prefix:            /usr/local
    exec_prefix:        ${prefix}
    libdir_name:        ${exec_prefix}/lib
    mandir:            ${datarootdir}/man
    includedir:        ${prefix}/include

    compiler:        gcc
    cflags:            -g -O2
    ldflags:        

    xsltproc:        

```

for the second one (sudo make install):

```
Making install in src
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT libdlo_la-dlo_grfx.lo -MD -MP -MF .deps/libdlo_la-dlo_grfx.Tpo -c -o libdlo_la-dlo_grfx.lo `test -f 'dlo_grfx.c' || echo './'`dlo_grfx.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT libdlo_la-dlo_grfx.lo -MD -MP -MF .deps/libdlo_la-dlo_grfx.Tpo -c dlo_grfx.c  -fPIC -DPIC -o .libs/libdlo_la-dlo_grfx.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT libdlo_la-dlo_grfx.lo -MD -MP -MF .deps/libdlo_la-dlo_grfx.Tpo -c dlo_grfx.c -o libdlo_la-dlo_grfx.o >/dev/null 2>&1
mv -f .deps/libdlo_la-dlo_grfx.Tpo .deps/libdlo_la-dlo_grfx.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT libdlo_la-dlo_mode.lo -MD -MP -MF .deps/libdlo_la-dlo_mode.Tpo -c -o libdlo_la-dlo_mode.lo `test -f 'dlo_mode.c' || echo './'`dlo_mode.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT libdlo_la-dlo_mode.lo -MD -MP -MF .deps/libdlo_la-dlo_mode.Tpo -c dlo_mode.c  -fPIC -DPIC -o .libs/libdlo_la-dlo_mode.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT libdlo_la-dlo_mode.lo -MD -MP -MF .deps/libdlo_la-dlo_mode.Tpo -c dlo_mode.c -o libdlo_la-dlo_mode.o >/dev/null 2>&1
mv -f .deps/libdlo_la-dlo_mode.Tpo .deps/libdlo_la-dlo_mode.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT libdlo_la-dlo_usb.lo -MD -MP -MF .deps/libdlo_la-dlo_usb.Tpo -c -o libdlo_la-dlo_usb.lo `test -f 'dlo_usb.c' || echo './'`dlo_usb.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT libdlo_la-dlo_usb.lo -MD -MP -MF .deps/libdlo_la-dlo_usb.Tpo -c dlo_usb.c  -fPIC -DPIC -o .libs/libdlo_la-dlo_usb.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT libdlo_la-dlo_usb.lo -MD -MP -MF .deps/libdlo_la-dlo_usb.Tpo -c dlo_usb.c -o libdlo_la-dlo_usb.o >/dev/null 2>&1
mv -f .deps/libdlo_la-dlo_usb.Tpo .deps/libdlo_la-dlo_usb.Plo
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT libdlo_la-libdlo.lo -MD -MP -MF .deps/libdlo_la-libdlo.Tpo -c -o libdlo_la-libdlo.lo `test -f 'libdlo.c' || echo './'`libdlo.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT libdlo_la-libdlo.lo -MD -MP -MF .deps/libdlo_la-libdlo.Tpo -c libdlo.c  -fPIC -DPIC -o .libs/libdlo_la-libdlo.o
libdlo.c: In function &#8216;parse_cmdline&#8217;:
libdlo.c:488: warning: assignment discards qualifiers from pointer target type
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -MT libdlo_la-libdlo.lo -MD -MP -MF .deps/libdlo_la-libdlo.Tpo -c libdlo.c -o libdlo_la-libdlo.o >/dev/null 2>&1
mv -f .deps/libdlo_la-libdlo.Tpo .deps/libdlo_la-libdlo.Plo
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -lusb -version-info 1:0:1  -o libdlo.la -rpath /usr/local/lib libdlo_la-dlo_grfx.lo libdlo_la-dlo_mode.lo libdlo_la-dlo_usb.lo libdlo_la-libdlo.lo  -lusb 
libtool: link: rm -fr  .libs/libdlo.a .libs/libdlo.la .libs/libdlo.lai .libs/libdlo.so .libs/libdlo.so.0 .libs/libdlo.so.0.1.0
libtool: link: gcc -shared  .libs/libdlo_la-dlo_grfx.o .libs/libdlo_la-dlo_mode.o .libs/libdlo_la-dlo_usb.o .libs/libdlo_la-libdlo.o   /usr/lib/libusb.so    -Wl,-soname -Wl,libdlo.so.0 -o .libs/libdlo.so.0.1.0
libtool: link: (cd ".libs" && rm -f "libdlo.so.0" && ln -s "libdlo.so.0.1.0" "libdlo.so.0")
libtool: link: (cd ".libs" && rm -f "libdlo.so" && ln -s "libdlo.so.0.1.0" "libdlo.so")
libtool: link: ar cru .libs/libdlo.a  libdlo_la-dlo_grfx.o libdlo_la-dlo_mode.o libdlo_la-dlo_usb.o libdlo_la-libdlo.o
libtool: link: ranlib .libs/libdlo.a
libtool: link: ( cd ".libs" && rm -f "libdlo.la" && ln -s "../libdlo.la" "libdlo.la" )
make[2]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/src'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include" || /bin/mkdir -p "/usr/local/include"
 /usr/bin/install -c -m 644 'libdlo.h' '/usr/local/include/libdlo.h'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libdlo.la' '/usr/local/lib/libdlo.la'
libtool: install: /usr/bin/install -c .libs/libdlo.so.0.1.0 /usr/local/lib/libdlo.so.0.1.0
libtool: install: (cd /usr/local/lib && { ln -s -f libdlo.so.0.1.0 libdlo.so.0 || { rm -f libdlo.so.0 && ln -s libdlo.so.0.1.0 libdlo.so.0; }; })
libtool: install: (cd /usr/local/lib && { ln -s -f libdlo.so.0.1.0 libdlo.so || { rm -f libdlo.so && ln -s libdlo.so.0.1.0 libdlo.so; }; })
libtool: install: /usr/bin/install -c .libs/libdlo.lai /usr/local/lib/libdlo.la
libtool: install: /usr/bin/install -c .libs/libdlo.a /usr/local/lib/libdlo.a
libtool: install: chmod 644 /usr/local/lib/libdlo.a
libtool: install: ranlib /usr/local/lib/libdlo.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/src'
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/src'
Making install in test
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/test'
gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -MT test1.o -MD -MP -MF .deps/test1.Tpo -c -o test1.o test1.c
mv -f .deps/test1.Tpo .deps/test1.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2   -o test1 test1.o ../src/libdlo.la -lusb -lusb 
libtool: link: gcc -g -O2 -o .libs/test1 test1.o  ../src/.libs/libdlo.so /usr/lib/libusb.so
make[2]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/test'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /bin/bash ../libtool   --mode=install /usr/bin/install -c 'test1' '/usr/local/bin/test1'
libtool: install: /usr/bin/install -c .libs/test1 /usr/local/bin/test1
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2'
make[2]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/doc/libdlo" || /bin/mkdir -p "/usr/local/share/doc/libdlo"
 /usr/bin/install -c -m 644 'README' '/usr/local/share/doc/libdlo/README'
make[2]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2'
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2'
```

So here I see some Leaving Directory messages... Is that wrong/bad? What should I do?

And finally, the output for make check is:

```
Making check in src
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/src'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/src'
Making check in test
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[1]: Nothing to be done for `check'.
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2/test'
make[1]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2'
make  check-TESTS
make[2]: Entering directory `/home/natalia/Downloads/libdlo-0.1.2'
test: argv[0]: /home/natalia/Downloads/libdlo-0.1.2/test/.libs/lt-test1
test: init...
test: no DisplayLink devices found
test: error 0 'Successful'
FAIL: test/test1
=======================================
1 of 1 test failed
Please report to libdlo@displaylink.com
=======================================
make[2]: *** [check-TESTS] Error 1
make[2]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2'
make[1]: *** [check-am] Error 2
make[1]: Leaving directory `/home/natalia/Downloads/libdlo-0.1.2'
make: *** [check-recursive] Error 1
```
Any ideas on what's the cause of these errors, or any way to fix them? Help and/or advices are highly appreciated. 


Best regards :)

---

### Post by mikewhatever on 2010-09-21
> LINUX COMPATIBILITY:
As of Linux kernel 2.6.31, this adapter has open source drivers in the official kernel staging tree. Configuration of X Windows for USB displays is still distribution and scenario dependent, however, and only for very adventurous users.

As Lucid has the 2.6.32 kernel, you probably didn't need to install the driver from source. Anyway, there were no errors while compiling, but rather during the consequent testing. Unfortunately, there isn't any info on how to configure that specific device.

---

