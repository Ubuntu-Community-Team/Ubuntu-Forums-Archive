---
title: "Gnome Shell build error"
date: 2010-09-09
forum: Desktop Environments
---

### Post by Ampi on 2010-09-09
This is the fourth time or so I tried to install Gnome Shell. In the beginning I thought the heavy development stage won't help. 
So I waited for a couple of months. Now I actually would like to try it out as it's coming really soon.. Still I get the same errors. 
After searching the internet I thought building from source is the best, but the errors are the same. Anyone any idea how I can fix this? I put the whole terminal story in code...

P.S. These errors won't stay with the actual install of 10.10, right?

```

ry-1.0'
test -z "/home/amparo/gnome-shell/install/share/vala/vapi" || /bin/mkdir -p "/home/amparo/gnome-shell/install/share/vala/vapi"
 /usr/bin/install-check -m 644 dconf.vapi dconf.deps '/home/amparo/gnome-shell/install/share/vala/vapi'
make  install-data-hook
make[3]: Entering directory `/home/amparo/gnome-shell/source/dconf/client'
ln -fs libdconf.so.0.0.0 /home/amparo/gnome-shell/install/lib64/libdconf.so.0
ln -fs libdconf.so.0.0.0 /home/amparo/gnome-shell/install/lib64/libdconf.so
make[3]: Leaving directory `/home/amparo/gnome-shell/source/dconf/client'
make[2]: Leaving directory `/home/amparo/gnome-shell/source/dconf/client'
make[1]: Leaving directory `/home/amparo/gnome-shell/source/dconf/client'
Making install in bin
make[1]: Entering directory `/home/amparo/gnome-shell/source/dconf/bin'
make[2]: Entering directory `/home/amparo/gnome-shell/source/dconf/bin'
test -z "/home/amparo/gnome-shell/install/bin" || /bin/mkdir -p "/home/amparo/gnome-shell/install/bin"
  /usr/bin/install-check dconf '/home/amparo/gnome-shell/install/bin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/amparo/gnome-shell/source/dconf/bin'
make[1]: Leaving directory `/home/amparo/gnome-shell/source/dconf/bin'
Making install in engine
make[1]: Entering directory `/home/amparo/gnome-shell/source/dconf/engine'
make[2]: Entering directory `/home/amparo/gnome-shell/source/dconf/engine'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/amparo/gnome-shell/install/include/dconf" || /bin/mkdir -p "/home/amparo/gnome-shell/install/include/dconf"
 /usr/bin/install-check -m 644 dconf-readtype.h dconf-resetlist.h dconf-engine.h '/home/amparo/gnome-shell/install/include/dconf'
make[2]: Leaving directory `/home/amparo/gnome-shell/source/dconf/engine'
make[1]: Leaving directory `/home/amparo/gnome-shell/source/dconf/engine'
Making install in common
make[1]: Entering directory `/home/amparo/gnome-shell/source/dconf/common'
make[2]: Entering directory `/home/amparo/gnome-shell/source/dconf/common'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/home/amparo/gnome-shell/install/include/dconf" || /bin/mkdir -p "/home/amparo/gnome-shell/install/include/dconf"
 /usr/bin/install-check -m 644 dconf-paths.h '/home/amparo/gnome-shell/install/include/dconf'
make[2]: Leaving directory `/home/amparo/gnome-shell/source/dconf/common'
make[1]: Leaving directory `/home/amparo/gnome-shell/source/dconf/common'
Making install in docs
make[1]: Entering directory `/home/amparo/gnome-shell/source/dconf/docs'
make[2]: Entering directory `/home/amparo/gnome-shell/source/dconf/docs'
make[2]: Nothing to be done for `install-exec-am'.
-- Nothing to install
make[2]: Leaving directory `/home/amparo/gnome-shell/source/dconf/docs'
make[1]: Leaving directory `/home/amparo/gnome-shell/source/dconf/docs'
Making install in editor
make[1]: Entering directory `/home/amparo/gnome-shell/source/dconf/editor'
make[2]: Entering directory `/home/amparo/gnome-shell/source/dconf/editor'
test -z "/home/amparo/gnome-shell/install/bin" || /bin/mkdir -p "/home/amparo/gnome-shell/install/bin"
  /usr/bin/install-check dconf-editor '/home/amparo/gnome-shell/install/bin'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/amparo/gnome-shell/source/dconf/editor'
make[1]: Leaving directory `/home/amparo/gnome-shell/source/dconf/editor'
make[1]: Entering directory `/home/amparo/gnome-shell/source/dconf'
make[2]: Entering directory `/home/amparo/gnome-shell/source/dconf'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/amparo/gnome-shell/source/dconf'
make[1]: Leaving directory `/home/amparo/gnome-shell/source/dconf'
*** Checking out gnome-desktop-3 *** [18/20]
git clone git://git.gnome.org/gnome-desktop gnome-desktop-3
Initialized empty Git repository in /home/amparo/gnome-shell/source/gnome-desktop-3/.git/
remote: Counting objects: 36406, done.
remote: Compressing objects: 100% (8435/8435), done.
remote: Total 36406 (delta 28949), reused 34560 (delta 27718)
Receiving objects: 100% (36406/36406), 20.32 MiB | 1.57 MiB/s, done.
Resolving deltas: 100% (28949/28949), done.
git pull --rebase
Current branch master is up to date.
*** Configuring gnome-desktop-3 *** [18/20]
./autogen.sh --prefix /home/amparo/gnome-shell/install --libdir '/home/amparo/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
/usr/bin/gnome-autogen.sh
Error copying file http://api.gnome.org/gnome-about/foundation-members: Operation not supported
Error copying file http://git.fedorahosted.org/git/?p=hwdata.git;a=blob_plain;f=pnp.ids;hb=HEAD: Operation not supported
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.65
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.1
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6b
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.25.16
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gtk-doc >= 1.0...
  testing gtkdocize... found 1.14
checking for gnome-doc-utils >= 0.4.2...
  testing gnome-doc-prepare... found 0.20.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gtkdocize...
Running gnome-doc-prepare...
You should add the contents of '/usr/share/aclocal/gnome-doc-utils.m4' to 'aclocal.m4'.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.11...
Running autoconf...
Running autoheader...
Running automake-1.11...
configure.ac:43: installing `./config.guess'
configure.ac:43: installing `./config.sub'
configure.ac:15: installing `./install-sh'
configure.ac:15: installing `./missing'
libgnome-desktop/Makefile.am: installing `./depcomp'
Running ./configure --enable-maintainer-mode --prefix /home/amparo/gnome-shell/install --libdir /home/amparo/gnome-shell/install/lib64 --disable-static --disable-gtk-doc ...
checking for a BSD-compatible install... /usr/bin/install-check
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
checking whether NLS is requested... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for intltool >= 0.40.0... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
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
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether gcc understands -Wno-sign-compare... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare
checking what language compliance flags to pass to the C compiler... 
checking for libstartup-notification... yes
checking for X... libraries , headers 
checking for XLIB... yes
checking for xrandr... yes
checking for GNOME_DESKTOP... configure: error: Package requirements (gdk-pixbuf-2.0 >= 2.21.3 gtk+-3.0 >= 2.90.2 glib-2.0 >= 2.19.1 gio-2.0 >= 2.19.1 gconf-2.0 >= 2.0.0 libstartup-notification-1.0 xrandr) were not met:

No package 'gtk+-3.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GNOME_DESKTOP_CFLAGS
and GNOME_DESKTOP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

*** Error during phase configure of gnome-desktop-3: ########## Error running ./autogen.sh --prefix /home/amparo/gnome-shell/install --libdir '/home/amparo/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [18/20]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 2
*** Building gnome-desktop-3 *** [18/20]
make  
make: *** No targets specified and no makefile found.  Stop.
*** Error during phase build of gnome-desktop-3: ########## Error running make   *** [18/20]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 2
*** Installing gnome-desktop-3 *** [18/20]
make install
make: *** No rule to make target `install'.  Stop.
*** Error during phase install of gnome-desktop-3: ########## Error running make install *** [18/20]

  [1] Rerun phase install
  [2] Ignore error and continue to next module
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
choice: 2
*** Checking out gnome-shell *** [19/20]
git clone git://git.gnome.org/gnome-shell
Initialized empty Git repository in /home/amparo/gnome-shell/source/gnome-shell/.git/
remote: Counting objects: 12089, done.
remote: Compressing objects: 100% (5227/5227), done.
remote: Total 12089 (delta 9203), reused 8828 (delta 6623)
Receiving objects: 100% (12089/12089), 2.76 MiB | 570 KiB/s, done.
Resolving deltas: 100% (9203/9203), done.
git pull --rebase
Current branch master is up to date.
*** Configuring gnome-shell *** [19/20]
./autogen.sh --prefix /home/amparo/gnome-shell/install --libdir '/home/amparo/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc 
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.65
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.1
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6b
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.25.16
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 2.28.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
Running libtoolize...
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: copying file `config/ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gnome-doc-common...
Running aclocal-1.11...
Running autoconf...
Running autoheader...
Running automake-1.11...
configure.ac:17: installing `config/compile'
configure.ac:21: installing `config/config.guess'
configure.ac:21: installing `config/config.sub'
configure.ac:9: installing `config/install-sh'
configure.ac:9: installing `config/missing'
src/Makefile.am: installing `config/depcomp'
Running ./configure --enable-maintainer-mode --prefix /home/amparo/gnome-shell/install --libdir /home/amparo/gnome-shell/install/lib64 --disable-static --disable-gtk-doc ...
configure: WARNING: unrecognized options: --disable-gtk-doc
checking for a BSD-compatible install... /usr/bin/install-check
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking whether NLS is requested... yes
checking for intltool >= 0.26... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.22... yes
checking for gconftool-2... /home/amparo/gnome-shell/install/bin/gconftool-2
Using config source xml:merged:/home/amparo/gnome-shell/install/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for a Python interpreter with version >= 2.5... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking for GStreamer (needed for recording functionality)... yes
checking for TEST_SHELL_RECORDER... configure: error: Package requirements (gstreamer-0.10 gstreamer-base-0.10 xfixes clutter-1.0) were not met:

No package 'clutter-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables TEST_SHELL_RECORDER_CFLAGS
and TEST_SHELL_RECORDER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

*** Error during phase configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/amparo/gnome-shell/install --libdir '/home/amparo/gnome-shell/install/lib64'  --disable-static --disable-gtk-doc  *** [19/20]

  [1] Rerun phase configure
  [2] Ignore error and continue to build
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "clean"
  [8] Go to phase "distclean"
choice: 2
*** Building gnome-shell *** [19/20]
make  
make: *** No targets specified and no makefile found.  Stop.
*** Error during phase build of gnome-shell: ########## Error running make   *** [19/20]

  [1] Rerun phase build
  [2] Ignore error and continue to install
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
  [6] Go to phase "wipe directory and start over"
  [7] Go to phase "configure"
  [8] Go to phase "clean"
  [9] Go to phase "distclean"
choice: 2
*** Installing gnome-shell *** [19/20]
make install
make: *** No rule to make target `install'.  Stop.
*** Error during phase install of gnome-shell: ########## Error running make install *** [19/20]

  [1] Rerun phase install
  [2] Ignore error and continue to next module
  [3] Give up on module
  [4] Start shell
  [5] Reload configuration
choice: 2
*** success *** [20/20]
amparo@amparo-desktop:~$ 


```

---

