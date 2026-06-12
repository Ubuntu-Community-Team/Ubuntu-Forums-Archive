---
title: "Compiz Fusion plugins are broken"
date: 2007-09-24
forum: Desktop Effects &amp; Customization
---

### Post by Onay on 2007-09-24
I'm compiling from the source at git and there seems to be a broken package is my guess. All other components of compiz fusion compiled and installed beautifully, but the "plugins-extra", aka all of the plugins I want to use, seem to be broken, since I keep getting build errors...

It's a bit lengthy so bear with me. The only place I see errors are at the very end...
```
jordan@jordan-ubuntu:~/compiz/plugins-extra$ ./autogen.sh --prefix=/usr/local --disable-kde && make && sudo make install
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
metadata/Makefile.am:28: patsubst %.xml.in,compiz-%.schemas,$(xml_in_files: non-POSIX variable name
metadata/Makefile.am:28: (probably a GNU make extension)
metadata/Makefile.am:31: `%'-style pattern rules are a GNU make extension
metadata/Makefile.am:32: subst compiz-,,$*: non-POSIX variable name
metadata/Makefile.am:32: (probably a GNU make extension)
src/addhelper/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/addhelper/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/bench/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/bench/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/crashhandler/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/crashhandler/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/cubecaps/Makefile.am:27: `%'-style pattern rules are a GNU make extension
src/cubecaps/Makefile.am:30: `%'-style pattern rules are a GNU make extension
src/cubereflex/Makefile.am:27: `%'-style pattern rules are a GNU make extension
src/cubereflex/Makefile.am:30: `%'-style pattern rules are a GNU make extension
src/extrawm/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/extrawm/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/fadedesktop/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/fadedesktop/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/firepaint/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/firepaint/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/gears/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/gears/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/group/Makefile.am:36: `%'-style pattern rules are a GNU make extension
src/group/Makefile.am:39: `%'-style pattern rules are a GNU make extension
src/mblur/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/mblur/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/reflex/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/reflex/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/scalefilter/Makefile.am:25: `%'-style pattern rules are a GNU make extension
src/scalefilter/Makefile.am:28: `%'-style pattern rules are a GNU make extension
src/showdesktop/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/showdesktop/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/splash/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/splash/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/trailfocus/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/trailfocus/Makefile.am:26: `%'-style pattern rules are a GNU make extension
src/widget/Makefile.am:23: `%'-style pattern rules are a GNU make extension
src/widget/Makefile.am:26: `%'-style pattern rules are a GNU make extension
autoreconf: Leaving directory `.'
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
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
checking how to recognise dependent libraries... pass_all
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
checking the maximum length of command line arguments... 32768
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for intltool >= 0.35.0... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
configure: Using PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for COMPIZ... yes
checking for BCOP... yes
checking for GL_CFLAGS... 
checking for GL_LIBS... -lGL
checking for GROUP... yes
checking for COMPIZCUBE... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: creating ./config.status
config.status: creating Makefile
config.status: creating images/Makefile
config.status: creating metadata/Makefile
config.status: creating src/Makefile
config.status: creating src/addhelper/Makefile
config.status: creating src/bench/Makefile
config.status: creating src/crashhandler/Makefile
config.status: creating src/cubecaps/Makefile
config.status: creating src/cubereflex/Makefile
config.status: creating src/extrawm/Makefile
config.status: creating src/fadedesktop/Makefile
config.status: creating src/firepaint/Makefile
config.status: creating src/gears/Makefile
config.status: creating src/group/Makefile
config.status: creating src/mblur/Makefile
config.status: creating src/reflex/Makefile
config.status: creating src/scalefilter/Makefile
config.status: creating src/showdesktop/Makefile
config.status: creating src/splash/Makefile
config.status: creating src/trailfocus/Makefile
config.status: creating src/widget/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
make  all-recursive
make[1]: Entering directory `/home/jordan/compiz/plugins-extra'
Making all in metadata
make[2]: Entering directory `/home/jordan/compiz/plugins-extra/metadata'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jordan/compiz/plugins-extra/metadata'
Making all in po
make[2]: Entering directory `/home/jordan/compiz/plugins-extra/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/jordan/compiz/plugins-extra/po'
Making all in src
make[2]: Entering directory `/home/jordan/compiz/plugins-extra/src'
Making all in addhelper
make[3]: Entering directory `/home/jordan/compiz/plugins-extra/src/addhelper'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/local/include/compiz -DDATADIR='""' -DLIBDIR='"/usr/local/lib"' -DLOCALEDIR="\"/usr/local/share/locale\"" -DIMAGEDIR='"/usr/local/share/compiz"' -I../../include    -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT addhelper.lo -MD -MP -MF .deps/addhelper.Tpo -c -o addhelper.lo addhelper.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I/usr/local/include/compiz -DDATADIR=\"\" -DLIBDIR=\"/usr/local/lib\" -DLOCALEDIR=\"/usr/local/share/locale\" -DIMAGEDIR=\"/usr/local/share/compiz\" -I../../include -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fno-strict-aliasing -MT addhelper.lo -MD -MP -MF .deps/addhelper.Tpo -c addhelper.c  -fPIC -DPIC -o .libs/addhelper.o
addhelper.c:26:25: error: compiz-core.h: No such file or directory
In file included from addhelper.c:27:
addhelper_options.h:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:35: error: expected ')' before '*' token
addhelper_options.h:37: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:44: error: expected ')' before '*' token
addhelper_options.h:46: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:48: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:49: error: expected ')' before '*' token
addhelper_options.h:51: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:52: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:53: error: expected ')' before '*' token
addhelper_options.h:55: error: expected ')' before '*' token
addhelper_options.h:56: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:57: error: expected ')' before '*' token
addhelper_options.h:59: error: expected ')' before '*' token
addhelper_options.h:60: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:61: error: expected ')' before '*' token
addhelper_options.h:63: error: expected ')' before '*' token
addhelper_options.h:64: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
addhelper_options.h:65: error: expected ')' before '*' token
addhelper.c:50: error: expected specifier-qualifier-list before 'GLushort'
addhelper.c:63: error: expected specifier-qualifier-list before 'PaintWindowProc'
addhelper.c:68: error: expected specifier-qualifier-list before 'Bool'
addhelper.c:77: error: expected ')' before '*' token
addhelper.c:115: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperPaintWindow'
addhelper.c:158: error: expected ')' before '*' token
addhelper.c:181: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperToggle'
addhelper.c:197: error: expected ')' before '*' token
addhelper.c:219: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperInitWindow'
addhelper.c:238: error: expected ')' before '*' token
addhelper.c:247: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperInitScreen'
addhelper.c:273: error: expected ')' before '*' token
addhelper.c:284: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperInitDisplay'
addhelper.c:321: error: expected ')' before '*' token
addhelper.c:333: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperInitObject'
addhelper.c:347: error: expected ')' before '*' token
addhelper.c:361: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperInit'
addhelper.c:370: error: expected ')' before '*' token
addhelper.c:375: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'addhelperVTable'
addhelper.c:386: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make[3]: *** [addhelper.lo] Error 1
make[3]: Leaving directory `/home/jordan/compiz/plugins-extra/src/addhelper'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jordan/compiz/plugins-extra/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jordan/compiz/plugins-extra'
make: *** [all] Error 2
```

Is it a broken package or my mistake? I'd like to know since I'm missing two-thirds of my plugins. It's also asking me to add files. Any help is appreciated.

---

### Post by Onay on 2007-09-25
I just edited out all of the scalefilter plugins, they seem to be broken. Works now.

---

