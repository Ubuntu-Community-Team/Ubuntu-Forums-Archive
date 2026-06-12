---
title: "How to install a xfce plugin"
date: 2017-06-06
forum: Desktop Environments
---

### Post by alberto-pranteddu on 2017-06-06
Hi everyone! I'm new in the forum and this is my first post ):P. I apologize in advance for my bad english.. 

The problem is that i'm trying to install a [xfce plugin]("https://git.xfce.org/panel-plugins/xfce4-sample-plugin/") but i can not understand how to. I'm writing a personal menu for the xfce panel, but i would not know how to build this sample.
I use **./autogen.sh**, **make **and **make install** but the plugin dont appear in the panel list.

These are the outputs:
```

$> ./autogen.sh 
Preparing package directory /home/tarenpudd/Scaricati/xfce4-sample-plugin-master...
Creating /home/tarenpudd/Scaricati/xfce4-sample-plugin-master/aclocal.m4...
Running glib-gettextize --force --copy...
Copying file po/Makefile.in.in


Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize --automake --copy --force
Patching file 'po/Makefile.in.in'
Running libtoolize --force --copy...
libtoolize: putting auxiliary files in '.'.
libtoolize: copying file './ltmain.sh'
libtoolize: You should add the contents of the following files to 'aclocal.m4':
libtoolize:   '/usr/share/aclocal/libtool.m4'
libtoolize:   '/usr/share/aclocal/ltoptions.m4'
libtoolize:   '/usr/share/aclocal/ltsugar.m4'
libtoolize:   '/usr/share/aclocal/ltversion.m4'
libtoolize:   '/usr/share/aclocal/lt~obsolete.m4'
libtoolize: Consider adding 'AC_CONFIG_MACRO_DIRS([m4])' to configure.ac,
libtoolize: and rerunning libtoolize and aclocal.
libtoolize: Consider adding '-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
Running aclocal   -I /usr/share/xfce4/dev-tools/m4macros -I /usr/share//xfce4/dev-tools/m4macros -I /usr/share/xfce4/dev-tools/m4macros...
configure.ac:50: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:50: the top level
configure.ac:50: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:50: the top level
Running autoheader...
configure.ac:50: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:50: the top level
configure.ac:50: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:50: the top level
Running automake --force-missing --add-missing --copy --gnu...
configure.ac:50: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:50: the top level
configure.ac:50: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:50: the top level
configure.ac:45: installing './compile'
configure.ac:45: installing './config.guess'
configure.ac:45: installing './config.sub'
configure.ac:36: installing './install-sh'
configure.ac:36: installing './missing'
Makefile.am: installing './INSTALL'
panel-plugin/Makefile.am:1: warning: 'INCLUDES' is the old name for 'AM_CPPFLAGS' (or '*_CPPFLAGS')
panel-plugin/Makefile.am: installing './depcomp'
Running autoconf...
configure.ac:50: warning: AC_COMPILE_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:50: the top level
configure.ac:50: warning: AC_RUN_IFELSE was called before AC_USE_SYSTEM_EXTENSIONS
../../lib/autoconf/specific.m4:436: AC_AIX is expanded from...
configure.ac:50: the top level


Running /home/tarenpudd/Scaricati/xfce4-sample-plugin-master/configure --enable-maintainer-mode ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether UID '1000' is supported by ustar format... yes
checking whether GID '1000' is supported by ustar format... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
checking whether make supports nested variables... (cached) yes
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking how to print strings... printf
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
checking whether gcc understands -c and -o together... yes
checking dependency style of gcc... gcc3
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
checking how to convert x86_64-pc-linux-gnu file names to x86_64-pc-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for a working dd... /bin/dd
checking how to truncate binary pipes... /bin/dd bs=4096 count=1
checking for mt... mt
checking if mt is a manifest tool... no
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking whether gcc understands -c and -o together... (cached) yes
checking dependency style of gcc... (cached) gcc3
checking for ld used by gcc... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking whether NLS is requested... yes
checking for intltool >= 0.35.0... 0.51.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.22.1
checking for XML::Parser... ok
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking stdio.h usability... yes
checking stdio.h presence... yes
checking for stdio.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for string.h... (cached) yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for memory.h... (cached) yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking sys/prctl.h usability... yes
checking sys/prctl.h presence... yes
checking for sys/prctl.h... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for bind_textdomain_codeset... yes
checking for locale.h... (cached) yes
checking for LC_MESSAGES... yes
checking for libintl.h... (cached) yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... (cached) yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for bind_textdomain_codeset... (cached) yes
checking for locales directory... ${datarootdir}/locale
checking for additional xgettext flags... --keyword=Q_ --from-code=UTF-8
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for main in -lX11... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for libxfce4ui-2 >= 4.12.0... 4.12.1
checking LIBXFCE4UI_CFLAGS... -pthread -I/usr/include/xfce4/libxfce4ui-2 -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/gtk-3.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/mirclient -I/usr/include/mircommon -I/usr/include/mircookie -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/xfce4 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include
checking LIBXFCE4UI_LIBS... -lxfce4ui-2 -lgtk-3 -lgdk-3 -lpangocairo-1.0 -lpango-1.0 -latk-1.0 -lcairo-gobject -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lgobject-2.0 -lxfce4util -lglib-2.0
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for libxfce4panel-2.0 >= 4.12.0... 4.12.0
checking LIBXFCE4PANEL_CFLAGS... -pthread -I/usr/include/xfce4/libxfce4panel-2.0 -I/usr/include/gtk-3.0 -I/usr/include/at-spi2-atk/2.0 -I/usr/include/at-spi-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/gtk-3.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/mirclient -I/usr/include/mircommon -I/usr/include/mircookie -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/harfbuzz -I/usr/include/pango-1.0 -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/xfce4 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include
checking LIBXFCE4PANEL_LIBS... -lxfce4panel-2.0 -lgtk-3 -lgdk-3 -lpangocairo-1.0 -lpango-1.0 -latk-1.0 -lcairo-gobject -lcairo -lgdk_pixbuf-2.0 -lgio-2.0 -lgobject-2.0 -Wl,--export-dynamic -lgmodule-2.0 -pthread -lxfce4util -lglib-2.0
checking whether to build with debugging support... minimum
checking PLATFORM_CPPFLAGS... 
checking PLATFORM_CFLAGS... 
checking PLATFORM_LDFLAGS... 
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating icons/Makefile
config.status: creating icons/48x48/Makefile
config.status: creating icons/scalable/Makefile
config.status: creating panel-plugin/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands


Build Configuration:


* Debug Support:    minimum


Now type "make" to compile.

```

```

$> make
make all-recursive
make[1]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master"
Making all in icons
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
Making all in 48x48
make[3]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/48x48"
make[3]: Nessuna operazione da eseguire per "all".
make[3]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/48x48"
Making all in scalable
make[3]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/scalable"
make[3]: Nessuna operazione da eseguire per "all".
make[3]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/scalable"
make[3]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
make[3]: Nessuna operazione da eseguire per "all-am".
make[3]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
Making all in panel-plugin
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/panel-plugin"
  CC       libsample_la-sample.lo
  CC       libsample_la-sample-dialogs.lo
  CCLD     libsample.la
  ITMRG  sample.desktop
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/panel-plugin"
Making all in po
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/po"
make[2]: Nessuna operazione da eseguire per "all".
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/po"
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master"
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master"
make[1]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master"

```

```

$> sudo make install
Making install in icons
make[1]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
Making install in 48x48
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/48x48"
make[3]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/48x48"
make[3]: Nessuna operazione da eseguire per "install-exec-am".
 /bin/mkdir -p '/usr/local/share/icons/hicolor/48x48/apps'
 /usr/bin/install -c -m 644 xfce4-sample-plugin.png '/usr/local/share/icons/hicolor/48x48/apps'
make[3]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/48x48"
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/48x48"
Making install in scalable
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/scalable"
make[3]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/scalable"
make[3]: Nessuna operazione da eseguire per "install-exec-am".
 /bin/mkdir -p '/usr/local/share/icons/hicolor/scalable/apps'
 /usr/bin/install -c -m 644 xfce4-sample-plugin.svg '/usr/local/share/icons/hicolor/scalable/apps'
make[3]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/scalable"
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons/scalable"
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
make[3]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
make[3]: Nessuna operazione da eseguire per "install-exec-am".
make  install-data-hook
make[4]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
Updating Gtk icon cache.
gtk-update-icon-cache: Cache file created successfully.
make[4]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
make[3]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
make[1]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/icons"
Making install in panel-plugin
make[1]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/panel-plugin"
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/panel-plugin"
make[2]: Nessuna operazione da eseguire per "install-exec-am".
 /bin/mkdir -p '/usr/local/share/xfce4/panel/plugins'
 /usr/bin/install -c -m 644 sample.desktop '/usr/local/share/xfce4/panel/plugins'
 /bin/mkdir -p '/usr/local/lib/xfce4/panel/plugins'
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libsample.la '/usr/local/lib/xfce4/panel/plugins'
libtool: install: /usr/bin/install -c .libs/libsample.so /usr/local/lib/xfce4/panel/plugins/libsample.so
libtool: install: /usr/bin/install -c .libs/libsample.lai /usr/local/lib/xfce4/panel/plugins/libsample.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin:/sbin" ldconfig -n /usr/local/lib/xfce4/panel/plugins
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/xfce4/panel/plugins


If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the '-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the 'LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the 'LD_RUN_PATH' environment variable
     during linking
   - use the '-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to '/etc/ld.so.conf'


See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/panel-plugin"
make[1]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/panel-plugin"
Making install in po
make[1]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/po"
linguas=""; \
for lang in $linguas; do \
  dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
  /bin/bash /home/tarenpudd/Scaricati/xfce4-sample-plugin-master/install-sh -d $dir; \
  if test -r $lang.gmo; then \
    /usr/bin/install -c -m 644 $lang.gmo $dir/xfce4-sample-plugin.mo; \
    echo "installing $lang.gmo as $dir/xfce4-sample-plugin.mo"; \
  else \
    /usr/bin/install -c -m 644 ./$lang.gmo $dir/xfce4-sample-plugin.mo; \
    echo "installing ./$lang.gmo as" \
     "$dir/xfce4-sample-plugin.mo"; \
  fi; \
  if test -r $lang.gmo.m; then \
    /usr/bin/install -c -m 644 $lang.gmo.m $dir/xfce4-sample-plugin.mo.m; \
    echo "installing $lang.gmo.m as $dir/xfce4-sample-plugin.mo.m"; \
  else \
    if test -r ./$lang.gmo.m ; then \
      /usr/bin/install -c -m 644 ./$lang.gmo.m \
    $dir/xfce4-sample-plugin.mo.m; \
      echo "installing ./$lang.gmo.m as" \
       "$dir/xfce4-sample-plugin.mo.m"; \
    else \
      true; \
    fi; \
  fi; \
done
make[1]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master/po"
make[1]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master"
make[2]: ingresso nella directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master"
make[2]: Nessuna operazione da eseguire per "install-exec-am".
make[2]: Nessuna operazione da eseguire per "install-data-am".
make[2]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master"
make[1]: uscita dalla directory "/home/tarenpudd/Scaricati/xfce4-sample-plugin-master"
```

Can anyone help me about this? The problem is related to the *Nothing to be done for "all"* (on italy in the code posted) in the output of **make **&#8203;comand?

---

