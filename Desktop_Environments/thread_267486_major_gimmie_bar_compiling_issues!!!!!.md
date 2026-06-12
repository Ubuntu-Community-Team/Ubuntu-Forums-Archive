---
title: "major gimmie bar compiling issues!!!!!"
date: 2006-09-28
forum: Desktop Environments
---

### Post by searayman on 2006-09-28
first off, i am on ubuntu edgy eft. and i downloaded the cvs of the gimmie bar. i first did a ./configure then a make then did a ./gimmie.py and it wouldnt run. Below i will post results of my different terminal actions and i will post screen shots of my gimmie folder so you can see what files are in there, and such.

mike@mike-desktop:~$ cd Desktop
mike@mike-desktop:~/Desktop$ cd gimmie
mike@mike-desktop:~/Desktop/gimmie$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
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
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for headers required to compile python extensions... found
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GIMMIE... yes
checking for python module gmenu... yes
checking for pygtk-codegen-2.0... /usr/bin/pygtk-codegen-2.0
checking for pygtk defs... /usr/share/pygtk/2.0/defs
checking for intltool >= 0.33... 0.35.0 found
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
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  ca da de el en_GB es fi ja mk nb ru sv vi
configure: creating ./config.status
config.status: creating Makefile
config.status: creating gimmie_globals.py
config.status : creating egg/Makefile
config.status: creating gdmclient/Makefile
config.status: creating gnomedesktop/Makefile
config.status: creating gnomecups/Makefile
config.status: creating iconentry/Makefile
config.status : creating sexy/Makefile
config.status: creating wnck/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
mike@mike-desktop:~/Desktop/gimmie$ make
make  all-recursive
make[1]: Entering directory `/home/mike/Desktop/gimmie'
Making all in egg
make[2]: Entering directory `/home/mike/Desktop/gimmie/egg'
( cd . && glib-mkenums \
                        --fhead "#ifndef __EGG_TYPE_BUILTINS_H__\n#define __EGG_TYPE_BUILTINS_H__\n\n#include < glib-object.h>\n\nG_BEGIN_DECLS\n" \
                        --fprod "/* enumerations from \"@filename@\" */\n" \
                        --vhead "GType @enum_name@_get_type (void);\n#define EGG_TYPE_@ENUMSHORT@ (@enum_name@_get_type())\n" \
                        --ftail "G_END_DECLS\n\n#endif /* __EGG_TYPE_BUILTINS_H__ */" \
                egg-recent-item.h egg-recent-model.h eggtraymanager.h ) >> xgen-gtbh \
        && (cmp -s xgen-gtbh eggtypebuiltins.h || cp xgen-gtbh eggtypebuiltins.h ) \
        && rm -f xgen-gtbh \
        && echo timestamp > stamp-eggtypebuiltins.h
make  all-am
make[3]: Entering directory `/home/mike/Desktop/gimmie/egg'
( cd . && glib-mkenums \
                        --fhead "#include \"egg-recent-item.h\"\n#include \"egg-recent-model.h\ "" \
                        --fprod "\n/* enumerations from \"@filename@\" */" \
                        --vhead "GType\n@enum_name@_get_type (void)\n{\n  static GType etype = 0;\n  if (etype == 0) {\n    static const G@Type@Value values[] = {" \
                        --vprod "      { @VALUENAME@, \"@VALUENAME@\", \"@valuenick@\" }," \
                        --vtail "      { 0, NULL, NULL }\n    };\n    etype = g_@type@_register_static (\"@EnumName@\", values);\n  }\n  return etype;\n}\n" \
                egg-recent-item.h egg-recent-model.h eggtraymanager.h ) > xgen-gtbc \
        && cp xgen-gtbc eggtypebuiltins.c  \
        && rm -f xgen-gtbc
if /bin/bash ../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/python2.4 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0 -I/usr/include/gnome-desktop-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/startup-notification-1.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonoboui-2.0 -I/usr/include/gnome- vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/freetype2 -I/usr/include/libxml2 -I/usr/include/libgnomecups-1 -I/usr/include/libwnck- 1.0   -DEGG_COMPILATION    -g -O2 -MT eggtypebuiltins.lo -MD -MP -MF ".deps/eggtypebuiltins.Tpo" -c -o eggtypebuiltins.lo eggtypebuiltins.c; \
        then mv -f ".deps/eggtypebuiltins.Tpo" ".deps/eggtypebuiltins.Plo"; else rm -f ".deps/eggtypebuiltins.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/python2.4 -DORBIT2=1 -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib- 2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pygtk-2.0 -I/usr/include/gnome-python-2.0 -I/usr/include/gnome-desktop-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/startup-notification-1.0 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas- 2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/libbonoboui-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/gnome-keyring-1 -I/usr/include/orbit-2.0 -I/usr/include/libbonobo- 2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/freetype2 -I/usr/include/libxml2 -I/usr/include/libgnomecups-1 -I/usr/include/libwnck-1.0 -DEGG_COMPILATION -g -O2 -MT eggtypebuiltins.lo -MD -MP -MF .deps/eggtypebuiltins.Tpo -c eggtypebuiltins.c  -fPIC -DPIC -o .libs/eggtypebuiltins.o
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o _egg.la -rpath /usr/local/lib/python2.4/site-packages/gimmie/egg -module -avoid-version -export-symbols-regex init_egg egg-recent-item.lo egg-recent-model.lo eggtraymanager.lo eggmarshalers.lo eggtypebuiltins.lo _eggmodule.lo _egg.lo -pthread -lgnome-desktop-2 -lgnomeui-2 -lSM -lICE -lstartup-notification-1 -lbonoboui-2 -lgnome-keyring -lxml2 -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 - lpangoft2-1.0 -lbonobo-2 -lgnomevfs-2 -lbonobo-activation -lgconf-2 -lORBit-2 -lgthread-2.0 -lgnomecups-1.0 -lcups -lgnutls -lz -lpthread -lcrypt -lwnck-1 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
rm -fr  .libs/_egg.exp .libs/_egg.la .libs/_egg.lai .libs/_egg.so .libs/_egg.ver
generating symbol list for `_egg.la'
/usr/bin/nm -B  .libs/egg-recent-item.o .libs/egg-recent-model.o .libs/eggtraymanager.o .libs/eggmarshalers.o .libs/eggtypebuiltins.o .libs/_eggmodule.o .libs/_egg.o  | sed -n -e 's/^.*[      ]\([ABCDGIRSTW][ABCDGIRSTW]*\)[         ][     ]*\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2 \2/p' | /bin/sed 's/.* //' | sort | uniq > .libs/_egg.exp
/bin/grep -E -e "init_egg" ".libs/_egg.exp" > ".libs/_egg.expT"
mv -f ".libs/_egg.expT" ".libs/_egg.exp"
echo "{ global:" > .libs/_egg.ver
 cat .libs/_egg.exp | sed -e "s/\(.*\)/\1;/" >> .libs/_egg.ver
 echo "local: *; };" >> .libs/_egg.ver
 gcc -shared  .libs/egg-recent-item.o .libs/egg-recent-model.o .libs/eggtraymanager.o .libs/eggmarshalers.o .libs/eggtypebuiltins.o .libs/_eggmodule.o .libs/_egg.o  -lgnome-desktop-2 /usr/lib/libgnomeui- 2.so -lSM -lICE /usr/lib/libstartup-notification-1.so /usr/lib/libbonoboui-2.so /usr/lib/libgnome-keyring.so /usr/lib/libxml2.so /usr/lib/libgnomecanvas-2.so /usr/lib/libgnome-2.so /usr/lib/libpopt.so /usr/lib/libart_lgpl_2.so /usr/lib/libpangoft2- 1.0.so /usr/lib/libbonobo-2.so /usr/lib/libgnomevfs-2.so /usr/lib/libbonobo-activation.so /usr/lib/libgconf-2.so /usr/lib/libORBit-2.so /usr/lib/libgthread-2.0.so -lgnomecups-1.0 -lcups /usr/lib/libgnutls.so -lz -lpthread -lcrypt -lwnck-1 /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango- 1.0.so /usr/lib/libcairo.so -lX11 /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so  -pthread -Wl,-soname -Wl,_egg.so -Wl,-version-script -Wl,.libs/_egg.ver -o .libs/_egg.so
creating _egg.la
(cd .libs && rm -f _egg.la && ln -s ../_egg.la _egg.la)
make[3]: Leaving directory `/home/mike/Desktop/gimmie/egg'
make[2]: Leaving directory `/home/mike/Desktop/gimmie/egg'
Making all in gdmclient
make[2]: Entering directory `/home/mike/Desktop/gimmie/gdmclient'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gimmie/gdmclient'
Making all in gnomedesktop
make[2]: Entering directory `/home/mike/Desktop/gimmie/gnomedesktop'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gimmie/gnomedesktop'
Making all in gnomecups
make[2]: Entering directory `/home/mike/Desktop/gimmie/gnomecups'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gimmie/gnomecups'
Making all in iconentry
make[2]: Entering directory `/home/mike/Desktop/gimmie/iconentry'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gimmie/iconentry'
Making all in sexy
make[2]: Entering directory `/home/mike/Desktop/gimmie/sexy'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gimmie/sexy'
Making all in wnck
make[2]: Entering directory `/home/mike/Desktop/gimmie/wnck'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gimmie/wnck'
Making all in po
make[2]: Entering directory `/home/mike/Desktop/gimmie/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/mike/Desktop/gimmie/po'
make[2]: Entering directory `/home/mike/Desktop/gimmie'
make[2]: Leaving directory `/home/mike/Desktop/gimmie'
make[1]: Leaving directory `/home/mike/Desktop/gimmie'
mike@mike-desktop:~/Desktop/gimmie$ ./gimmie.py
Traceback (most recent call last):
  File "./gimmie.py", line 14, in ?
    from gimmie_bar import GimmieBarDock
  File "/home/mike/Desktop/gimmie/gimmie_bar.py", line 5, in ?
    from gimmie_base import IOrientationAware
  File "/home/mike/Desktop/gimmie/gimmie_base.py", line 10, in ?
    from gimmie_util import bookmarks, icon_factory, launcher
  File "/home/mike/Desktop/gimmie/gimmie_util.py", line 17, in ?
    import egg
  File "/home/mike/Desktop/gimmie/egg/__init__.py", line 1, in ?
    from _egg import *
ImportError: No module named _egg
mike@mike-desktop:~/Desktop/gimmie$



Pictures located at these links of the files in my gimmie folder.

[http://img149.imageshack.us/my.php?image=gimmiedirectoryax0.png]("http://img149.imageshack.us/my.php?image=gimmiedirectoryax0.png")


[http://img99.imageshack.us/my.php?image=eggdirectoryxg0.png]("http://img99.imageshack.us/my.php?image=eggdirectoryxg0.png")


[http://img149.imageshack.us/my.php?image=eggslibsuv8.png]("http://img149.imageshack.us/my.php?image=eggslibsuv8.png")

---

### Post by searayman on 2006-09-28
i am thinking maybe gimmie was made for the older version on gnome witch is in Ubuntu dapper, and sinc ei am in ubuntu edgy its not compatible? I dont know this is a guesse. Can somone help me i really want this to work!

---

### Post by searayman on 2006-09-28
ok imoved the _egg from .libs into gimmie and i now get a different error.


mike@mike-desktop:~/Desktop/gimmie$ ./gimmie.py
Traceback (most recent call last):
  File "/home/mike/Desktop/gimmie/gimmie_util.py", line 717, in do_reload
    for line in file(self._bookmarks_path):
IOError: [Errno 2] No such file or directory: '/home/mike/.gtk-bookmarks'
Traceback (most recent call last):
  File "./gimmie.py", line 14, in ?
    from gimmie_bar import GimmieBarDock
  File "/home/mike/Desktop/gimmie/gimmie_bar.py", line 6, in ?
    from gimmie_gui import EdgeWindow, AnchoredWindow, TopicRunningList, TopicButton
  File "/home/mike/Desktop/gimmie/gimmie_gui.py", line 8, in ?
    import sexy
  File "/home/mike/Desktop/gimmie/sexy/__init__.py", line 1, in ?
    from _sexy import *
ImportError: No module named _sexy
mike@mike-desktop:~/Desktop/gimmie$

---

### Post by searayman on 2006-09-28
ok i moved a crap load of stuff aorudn and now got this error:

mike@mike-desktop:~/Desktop/gimmie-0.1.1$ ./gimmie.py
[Errno 2] No such file or directory: '/home/mike/.gtk-bookmarks'
Traceback (most recent call last):
  File "./gimmie.py", line 83, in ?
    topics = [ApplicationsTopic(), DocumentsTopic(), PeopleTopic(), ComputerTopic()]
  File "/home/mike/Desktop/gimmie-0.1.1/gimmie_applications.py", line 424, in __init__
    self.set_running_source(RunningNoSettingsApplications())
  File "/home/mike/Desktop/gimmie-0.1.1/gimmie_applications.py", line 144, in __init__
    RunningApplications.__init__(self)
  File "/home/mike/Desktop/gimmie-0.1.1/gimmie_applications.py", line 28, in __init__
    RunningItemSource.__init__(self, "Running Applications")
  File "/home/mike/Desktop/gimmie-0.1.1/gimmie_running.py", line 151, in __init__
    self.screen = wnck.screen_get(0)
AttributeError: 'module' object has no attribute 'screen_get'
mike@mike-desktop:~/Desktop/gimmie-0.1.1$

---

### Post by .nat on 2006-10-19
i think that is across gtk-themes.  then i change my gtk-themes-gimmie runs.
--
sory my english.

---

### Post by zechi on 2006-11-11
how did you change your gtk themes? would be nice if you could explain me because i get the same error .. 

this is the error

[I]zechi@christoph:~/Desktop/gimmie$ ./gimmie.py
Traceback (most recent call last):
  File "./gimmie.py", line 83, in ?
    topics = [ApplicationsTopic(), DocumentsTopic(), PeopleTopic(), ComputerTopic()]
  File "/home/zechi/Desktop/gimmie/gimmie_applications.py", line 424, in __init__
    self.set_running_source(RunningNoSettingsApplications())
  File "/home/zechi/Desktop/gimmie/gimmie_applications.py", line 144, in __init__
    RunningApplications.__init__(self)
  File "/home/zechi/Desktop/gimmie/gimmie_applications.py", line 28, in __init__
    RunningItemSource.__init__(self, "Running Applications")
  File "/home/zechi/Desktop/gimmie/gimmie_running.py", line 151, in __init__
    self.screen = wnck.screen_get(0)
AttributeError: 'module' object has no attribute 'screen_get'[/I]

i use edgy on an amd64 system

thanks, zechi

---

### Post by nicky.7 on 2006-11-27
I have the same problem. I think it is because gimmie is actually using another version of wnck that is somewhere in my (and every ubuntu box) system.
I can say it because i don't have to copy the wnck.so file from .libs while i have to do this in order to make gimmie find all the other modules...
I tried change my gtk-theme but it does not work.
How can we do?

---

### Post by henrique on 2007-01-05
I linked every _egg|_gnomecups|etc.so like this:

cd egg;
ln -s .libs/_egg.so _egg.so
...

including wnck and it worked.

---

