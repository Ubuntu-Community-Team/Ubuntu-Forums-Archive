---
title: "guys wats going on with my setup?"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by Myronray on 2008-02-27
i follow this kiba-dock installation >>>>> see this link [http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127) 

and i installed corectly the pakages, plugins etc

successfully intalled
cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..

but in the 2nd step

cd kiba-dock/
./autogen.sh
sudo make install <<<<<<<

root@myronray-desktop:/home/myronray/kiba-dock/kiba-dock# sudo make install
make: *** No rule to make target `install'.  Stop.

what happen guys? :(( plsss anybody can help and resolve this problem

thanks..

---

### Post by Achtung on 2008-02-27
Can you post the complete output of that autogen.sh command? It should explain what's going on. 
[This]("http://ubuntuforums.org/showthread.php?t=661363") user had a similar problem but it was easily solved with the complete output of the command.

---

### Post by Yellow Pasque on 2008-02-27
> make: *** No rule to make target `install'. Stop.
If you got this, it is probably because the configure script did not finish successfully and build the Makefile. What was the output from the autogen.sh step?

---

### Post by Myronray on 2008-02-27
guys here is my 1st installation of akamaru

root@myronray-desktop:/home/myronray/kiba-dock/akamaru# ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy
Putting files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'

Running './configure --prefix=/usr --exec-prefix=/usr' ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking the maximum length of command line arguments... 98304
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
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 22091: ./po/POTFILES.in: No such file or directory
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for sqrt... no
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for AKAMARU... yes
checking for GLIB... yes
configure: creating ./config.status
config.status: creating akamaru.pc
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
Now type `make' to compile akamaru
root@myronray-desktop:/home/myronray/kiba-dock/akamaru# sudo make install
Making install in src
make[1]: Entering directory `/home/myronray/kiba-dock/akamaru/src'
make[2]: Entering directory `/home/myronray/kiba-dock/akamaru/src'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libakamaru.la' '/usr/lib/libakamaru.la'
/usr/bin/install -c .libs/libakamaru.so.0.0.0 /usr/lib/libakamaru.so.0.0.0
(cd /usr/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so.0 || { rm -f libakamaru.so.0 && ln -s libakamaru.so.0.0.0 libakamaru.so.0; }; })
(cd /usr/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so || { rm -f libakamaru.so && ln -s libakamaru.so.0.0.0 libakamaru.so; }; })
/usr/bin/install -c .libs/libakamaru.lai /usr/lib/libakamaru.la
/usr/bin/install -c .libs/libakamaru.a /usr/lib/libakamaru.a
chmod 644 /usr/lib/libakamaru.a
ranlib /usr/lib/libakamaru.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/myronray/kiba-dock/akamaru/src'
make[1]: Leaving directory `/home/myronray/kiba-dock/akamaru/src'
Making install in include
make[1]: Entering directory `/home/myronray/kiba-dock/akamaru/include'
make[2]: Entering directory `/home/myronray/kiba-dock/akamaru/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/include/akamaru" || mkdir -p -- "/usr/include/akamaru"
 /usr/bin/install -c -m 644 'akamaru.h' '/usr/include/akamaru/akamaru.h'
make[2]: Leaving directory `/home/myronray/kiba-dock/akamaru/include'
make[1]: Leaving directory `/home/myronray/kiba-dock/akamaru/include'
make[1]: Entering directory `/home/myronray/kiba-dock/akamaru'
make[2]: Entering directory `/home/myronray/kiba-dock/akamaru'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'akamaru.pc' '/usr/lib/pkgconfig/akamaru.pc'
make[2]: Leaving directory `/home/myronray/kiba-dock/akamaru'
make[1]: Leaving directory `/home/myronray/kiba-dock/akamaru'

and the 2nd kiba-dock installation check this 

root@myronray-desktop:/home/myronray/kiba-dock/akamaru# cd ..
root@myronray-desktop:/home/myronray/kiba-dock# cd kiba-dock
root@myronray-desktop:/home/myronray/kiba-dock/kiba-dock# ./autogen.sh

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'

Running 'glib-gettextize'... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).


Running 'intltoolize'...

Running './configure ' ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
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
checking for stdlib.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for intltool >= 0.35.0... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for PANGO... yes
checking for GTK... yes
checking for CAIRO... yes
checking for LIBXML... yes
checking for DBUS... configure: error: Package requirements (dbus-glib-1) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@myronray-desktop:/home/myronray/kiba-dock/kiba-dock# sudo make install
make: *** No rule to make target `install'.  Stop.
root@myronray-desktop:/home/myronray/kiba-dock/kiba-dock# 

i think there was sumthing file missing or not install :( so how do i do?

---

### Post by Myronray on 2008-02-27
yeah yeah ACTUNG the same problem you post with phil setup :)

---

### Post by Yellow Pasque on 2008-02-27
> No package 'dbus-glib-1' found

Ok, so get the dbus-glib development packages.
```
sudo apt-get install libdbus-1-3 libdbus-1-dev libdbus-glib-1-2 libdbus-glib-1-dev
```

Then try again. :)

---

### Post by Myronray on 2008-02-27
waaaaaaaaaaaaaaaa!!!!!! the 3rd step was successfully installed but the 4th step >>>> misssing file how to update this pakage ehehehe

No package 'pygtk-2.0' found

---

### Post by Yellow Pasque on 2008-02-27
Ok.
```
sudo apt-get install python-gtk2-dev
```

---

### Post by Myronray on 2008-02-27
[SIZE="6"][SIZE="7"][FONT="Comic Sans MS"]oh god its working temujin weeeeeeeeeeeeeeeee!!!!!!!!! lah! lah! lah! la ahahahahaha thanks ur the man woootttttttttttt[/FONT][/SIZE][/SIZE]

---

### Post by Ofer80 on 2008-02-27
all other applications you can install like this... be happy :)

---

