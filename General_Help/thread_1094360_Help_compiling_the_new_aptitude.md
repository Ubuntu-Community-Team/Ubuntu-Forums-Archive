---
title: "Help compiling the new aptitude"
date: 2009-03-12
forum: General Help
---

### Post by kernel_script on 2009-03-12
Hi folks, could someone help me compile the new aptitude with the new GTK GUI? I already have all required dependencies (i think...), here the error:

```

kernel-script@ubuntu-desktop:~$ hg clone http://hg.debian.org/hg/aptitude/head aptitude
requesting all changes
adding changesets
adding manifests
adding file changes
added 1660 changesets with 6324 changes to 770 files
updating working directory
653 files updated, 0 files merged, 0 files removed, 0 files unresolved
kernel-script@ubuntu-desktop:~$ cd aptitude
kernel-script@ubuntu-desktop:~/aptitude$ ./autogen.sh
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
src/Makefile.am: installing `./depcomp'
configure.ac:42: installing `./config.guess'
configure.ac:42: installing `./config.sub'
Makefile.am: installing `./INSTALL'
Makefile.am: installing `./COPYING'
kernel-script@ubuntu-desktop:~/aptitude$ ./configure && make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for po4a... /usr/bin/po4a
checking for initscr in -lncursesw... yes
checking for main in -lapt-pkg... yes
checking whether apt includes the automatic dependency removal patch (required)... yes
checking for main in -lpthread... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ept... no
checking for SIGC... yes
checking for CWIDGET... yes
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking apt-pkg/init.h usability... yes
checking apt-pkg/init.h presence... yes
checking for apt-pkg/init.h... yes
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking whether setlocale is declared... yes
checking whether apt supports ddtp... yes
checking whether apt supports the Homepage: field... yes
checking whether apt supports dpkg triggers... yes
checking for the name of the character traits template... char_traits
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for size_t... yes
checking for strdup... yes
configure: creating ./config.status
config.status: creating Doxyfile
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/cs/Makefile
config.status: creating doc/cs/images/Makefile
config.status: creating doc/de/Makefile
config.status: creating doc/en/Makefile
config.status: creating doc/en/images/Makefile
config.status: creating doc/fi/Makefile
config.status: creating doc/fi/images/Makefile
config.status: creating doc/fr/Makefile
config.status: creating doc/fr/images/Makefile
config.status: creating doc/ja/Makefile
config.status: creating doc/ja/images/Makefile
config.status: creating doc/po4a/Makefile
config.status: creating doc/po4a/po/Makefile
config.status: creating doc/po4a/add_de/Makefile
config.status: creating doc/po4a/add_fr/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: creating src/cmdline/Makefile
config.status: creating src/generic/Makefile
config.status: creating src/generic/apt/Makefile
config.status: creating src/generic/problemresolver/Makefile
config.status: creating src/generic/util/Makefile
config.status: creating src/mine/Makefile
config.status: creating tests/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
make  all-recursive
make[1]: Entrando no diretório `/home/kernel-script/aptitude'
Making all in src
make[2]: Entrando no diretório `/home/kernel-script/aptitude/src'
Making all in generic
make[3]: Entrando no diretório `/home/kernel-script/aptitude/src/generic'
Making all in util
make[4]: Entrando no diretório `/home/kernel-script/aptitude/src/generic/util'
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT temp.o -MD -MP -MF ".deps/temp.Tpo" -c -o temp.o temp.cc; \
	then mv -f ".deps/temp.Tpo" ".deps/temp.Po"; else rm -f ".deps/temp.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT undo.o -MD -MP -MF ".deps/undo.Tpo" -c -o undo.o undo.cc; \
	then mv -f ".deps/undo.Tpo" ".deps/undo.Po"; else rm -f ".deps/undo.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT util.o -MD -MP -MF ".deps/util.Tpo" -c -o util.o util.cc; \
	then mv -f ".deps/util.Tpo" ".deps/util.Po"; else rm -f ".deps/util.Tpo"; exit 1; fi
rm -f libgeneric-util.a
ar cru libgeneric-util.a temp.o undo.o util.o 
ranlib libgeneric-util.a
make[4]: Saindo do diretório `/home/kernel-script/aptitude/src/generic/util'
Making all in problemresolver
make[4]: Entrando no diretório `/home/kernel-script/aptitude/src/generic/problemresolver'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT test.o -MD -MP -MF ".deps/test.Tpo" -c -o test.o test.cc; \
	then mv -f ".deps/test.Tpo" ".deps/test.Po"; else rm -f ".deps/test.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT dummy_universe.o -MD -MP -MF ".deps/dummy_universe.Tpo" -c -o dummy_universe.o dummy_universe.cc; \
	then mv -f ".deps/dummy_universe.Tpo" ".deps/dummy_universe.Po"; else rm -f ".deps/dummy_universe.Tpo"; exit 1; fi
g++  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror   -o test  test.o dummy_universe.o ../../../src/generic/util/libgeneric-util.a -lapt-pkg -lncursesw  -lsigc-2.0   -lcwidget -lncursesw -lsigc-2.0    -lpthread
make[4]: Saindo do diretório `/home/kernel-script/aptitude/src/generic/problemresolver'
Making all in apt
make[4]: Entrando no diretório `/home/kernel-script/aptitude/src/generic/apt'
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT acqprogress.o -MD -MP -MF ".deps/acqprogress.Tpo" -c -o acqprogress.o acqprogress.cc; \
	then mv -f ".deps/acqprogress.Tpo" ".deps/acqprogress.Po"; else rm -f ".deps/acqprogress.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT aptcache.o -MD -MP -MF ".deps/aptcache.Tpo" -c -o aptcache.o aptcache.cc; \
	then mv -f ".deps/aptcache.Tpo" ".deps/aptcache.Po"; else rm -f ".deps/aptcache.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT apt.o -MD -MP -MF ".deps/apt.Tpo" -c -o apt.o apt.cc; \
	then mv -f ".deps/apt.Tpo" ".deps/apt.Po"; else rm -f ".deps/apt.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT aptitudepolicy.o -MD -MP -MF ".deps/aptitudepolicy.Tpo" -c -o aptitudepolicy.o aptitudepolicy.cc; \
	then mv -f ".deps/aptitudepolicy.Tpo" ".deps/aptitudepolicy.Po"; else rm -f ".deps/aptitudepolicy.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT aptitude_resolver.o -MD -MP -MF ".deps/aptitude_resolver.Tpo" -c -o aptitude_resolver.o aptitude_resolver.cc; \
	then mv -f ".deps/aptitude_resolver.Tpo" ".deps/aptitude_resolver.Po"; else rm -f ".deps/aptitude_resolver.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT aptitude_resolver_universe.o -MD -MP -MF ".deps/aptitude_resolver_universe.Tpo" -c -o aptitude_resolver_universe.o aptitude_resolver_universe.cc; \
	then mv -f ".deps/aptitude_resolver_universe.Tpo" ".deps/aptitude_resolver_universe.Po"; else rm -f ".deps/aptitude_resolver_universe.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT apt_undo_group.o -MD -MP -MF ".deps/apt_undo_group.Tpo" -c -o apt_undo_group.o apt_undo_group.cc; \
	then mv -f ".deps/apt_undo_group.Tpo" ".deps/apt_undo_group.Po"; else rm -f ".deps/apt_undo_group.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT config_signal.o -MD -MP -MF ".deps/config_signal.Tpo" -c -o config_signal.o config_signal.cc; \
	then mv -f ".deps/config_signal.Tpo" ".deps/config_signal.Po"; else rm -f ".deps/config_signal.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT download_manager.o -MD -MP -MF ".deps/download_manager.Tpo" -c -o download_manager.o download_manager.cc; \
	then mv -f ".deps/download_manager.Tpo" ".deps/download_manager.Po"; else rm -f ".deps/download_manager.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT download_install_manager.o -MD -MP -MF ".deps/download_install_manager.Tpo" -c -o download_install_manager.o download_install_manager.cc; \
	then mv -f ".deps/download_install_manager.Tpo" ".deps/download_install_manager.Po"; else rm -f ".deps/download_install_manager.Tpo"; exit 1; fi
cc1plus: warnings being treated as errors
download_install_manager.cc: In member function ‘download_manager::result download_install_manager::execute_install_run(pkgAcquire::RunResult, OpProgress&)’:
download_install_manager.cc:156: error: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result
make[4]: ** [download_install_manager.o] Erro 1
make[4]: Saindo do diretório `/home/kernel-script/aptitude/src/generic/apt'
make[3]: ** [all-recursive] Erro 1
make[3]: Saindo do diretório `/home/kernel-script/aptitude/src/generic'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretório `/home/kernel-script/aptitude/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/kernel-script/aptitude'
make: ** [all] Erro 2
kernel-script@ubuntu-desktop:~/aptitude$
```

---

### Post by uylug on 2010-08-05
> **kernel_script said:**
> Hi folks, could someone help me compile the new aptitude with the new GTK GUI? I already have all required dependencies (i think...), here the error:

```

kernel-script@ubuntu-desktop:~$ hg clone http://hg.debian.org/hg/aptitude/head aptitude
requesting all changes
adding changesets
adding manifests
adding file changes
added 1660 changesets with 6324 changes to 770 files
updating working directory
653 files updated, 0 files merged, 0 files removed, 0 files unresolved
kernel-script@ubuntu-desktop:~$ cd aptitude
kernel-script@ubuntu-desktop:~/aptitude$ ./autogen.sh
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
src/Makefile.am: installing `./depcomp'
configure.ac:42: installing `./config.guess'
configure.ac:42: installing `./config.sub'
Makefile.am: installing `./INSTALL'
Makefile.am: installing `./COPYING'
kernel-script@ubuntu-desktop:~/aptitude$ ./configure && make
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for po4a... /usr/bin/po4a
checking for initscr in -lncursesw... yes
checking for main in -lapt-pkg... yes
checking whether apt includes the automatic dependency removal patch (required)... yes
checking for main in -lpthread... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ept... no
checking for SIGC... yes
checking for CWIDGET... yes
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/ioctl.h usability... yes
checking sys/ioctl.h presence... yes
checking for sys/ioctl.h... yes
checking for unistd.h... (cached) yes
checking apt-pkg/init.h usability... yes
checking apt-pkg/init.h presence... yes
checking for apt-pkg/init.h... yes
checking execinfo.h usability... yes
checking execinfo.h presence... yes
checking for execinfo.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking whether setlocale is declared... yes
checking whether apt supports ddtp... yes
checking whether apt supports the Homepage: field... yes
checking whether apt supports dpkg triggers... yes
checking for the name of the character traits template... char_traits
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for size_t... yes
checking for strdup... yes
configure: creating ./config.status
config.status: creating Doxyfile
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/cs/Makefile
config.status: creating doc/cs/images/Makefile
config.status: creating doc/de/Makefile
config.status: creating doc/en/Makefile
config.status: creating doc/en/images/Makefile
config.status: creating doc/fi/Makefile
config.status: creating doc/fi/images/Makefile
config.status: creating doc/fr/Makefile
config.status: creating doc/fr/images/Makefile
config.status: creating doc/ja/Makefile
config.status: creating doc/ja/images/Makefile
config.status: creating doc/po4a/Makefile
config.status: creating doc/po4a/po/Makefile
config.status: creating doc/po4a/add_de/Makefile
config.status: creating doc/po4a/add_fr/Makefile
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: WARNING:  po/Makefile.in.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: creating src/cmdline/Makefile
config.status: creating src/generic/Makefile
config.status: creating src/generic/apt/Makefile
config.status: creating src/generic/problemresolver/Makefile
config.status: creating src/generic/util/Makefile
config.status: creating src/mine/Makefile
config.status: creating tests/Makefile
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: creating po/POTFILES
config.status: creating po/Makefile
make  all-recursive
make[1]: Entrando no diretório `/home/kernel-script/aptitude'
Making all in src
make[2]: Entrando no diretório `/home/kernel-script/aptitude/src'
Making all in generic
make[3]: Entrando no diretório `/home/kernel-script/aptitude/src/generic'
Making all in util
make[4]: Entrando no diretório `/home/kernel-script/aptitude/src/generic/util'
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT temp.o -MD -MP -MF ".deps/temp.Tpo" -c -o temp.o temp.cc; \
    then mv -f ".deps/temp.Tpo" ".deps/temp.Po"; else rm -f ".deps/temp.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT undo.o -MD -MP -MF ".deps/undo.Tpo" -c -o undo.o undo.cc; \
    then mv -f ".deps/undo.Tpo" ".deps/undo.Po"; else rm -f ".deps/undo.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT util.o -MD -MP -MF ".deps/util.Tpo" -c -o util.o util.cc; \
    then mv -f ".deps/util.Tpo" ".deps/util.Po"; else rm -f ".deps/util.Tpo"; exit 1; fi
rm -f libgeneric-util.a
ar cru libgeneric-util.a temp.o undo.o util.o 
ranlib libgeneric-util.a
make[4]: Saindo do diretório `/home/kernel-script/aptitude/src/generic/util'
Making all in problemresolver
make[4]: Entrando no diretório `/home/kernel-script/aptitude/src/generic/problemresolver'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT test.o -MD -MP -MF ".deps/test.Tpo" -c -o test.o test.cc; \
    then mv -f ".deps/test.Tpo" ".deps/test.Po"; else rm -f ".deps/test.Tpo"; exit 1; fi
if g++ -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT dummy_universe.o -MD -MP -MF ".deps/dummy_universe.Tpo" -c -o dummy_universe.o dummy_universe.cc; \
    then mv -f ".deps/dummy_universe.Tpo" ".deps/dummy_universe.Po"; else rm -f ".deps/dummy_universe.Tpo"; exit 1; fi
g++  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror   -o test  test.o dummy_universe.o ../../../src/generic/util/libgeneric-util.a -lapt-pkg -lncursesw  -lsigc-2.0   -lcwidget -lncursesw -lsigc-2.0    -lpthread
make[4]: Saindo do diretório `/home/kernel-script/aptitude/src/generic/problemresolver'
Making all in apt
make[4]: Entrando no diretório `/home/kernel-script/aptitude/src/generic/apt'
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT acqprogress.o -MD -MP -MF ".deps/acqprogress.Tpo" -c -o acqprogress.o acqprogress.cc; \
    then mv -f ".deps/acqprogress.Tpo" ".deps/acqprogress.Po"; else rm -f ".deps/acqprogress.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT aptcache.o -MD -MP -MF ".deps/aptcache.Tpo" -c -o aptcache.o aptcache.cc; \
    then mv -f ".deps/aptcache.Tpo" ".deps/aptcache.Po"; else rm -f ".deps/aptcache.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT apt.o -MD -MP -MF ".deps/apt.Tpo" -c -o apt.o apt.cc; \
    then mv -f ".deps/apt.Tpo" ".deps/apt.Po"; else rm -f ".deps/apt.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT aptitudepolicy.o -MD -MP -MF ".deps/aptitudepolicy.Tpo" -c -o aptitudepolicy.o aptitudepolicy.cc; \
    then mv -f ".deps/aptitudepolicy.Tpo" ".deps/aptitudepolicy.Po"; else rm -f ".deps/aptitudepolicy.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT aptitude_resolver.o -MD -MP -MF ".deps/aptitude_resolver.Tpo" -c -o aptitude_resolver.o aptitude_resolver.cc; \
    then mv -f ".deps/aptitude_resolver.Tpo" ".deps/aptitude_resolver.Po"; else rm -f ".deps/aptitude_resolver.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT aptitude_resolver_universe.o -MD -MP -MF ".deps/aptitude_resolver_universe.Tpo" -c -o aptitude_resolver_universe.o aptitude_resolver_universe.cc; \
    then mv -f ".deps/aptitude_resolver_universe.Tpo" ".deps/aptitude_resolver_universe.Po"; else rm -f ".deps/aptitude_resolver_universe.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT apt_undo_group.o -MD -MP -MF ".deps/apt_undo_group.Tpo" -c -o apt_undo_group.o apt_undo_group.cc; \
    then mv -f ".deps/apt_undo_group.Tpo" ".deps/apt_undo_group.Po"; else rm -f ".deps/apt_undo_group.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT config_signal.o -MD -MP -MF ".deps/config_signal.Tpo" -c -o config_signal.o config_signal.cc; \
    then mv -f ".deps/config_signal.Tpo" ".deps/config_signal.Po"; else rm -f ".deps/config_signal.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT download_manager.o -MD -MP -MF ".deps/download_manager.Tpo" -c -o download_manager.o download_manager.cc; \
    then mv -f ".deps/download_manager.Tpo" ".deps/download_manager.Po"; else rm -f ".deps/download_manager.Tpo"; exit 1; fi
if g++ -DLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_CONFIG_H -I. -I. -I../../.. -I../../.. -I. -I../../.. -I../../../src  -DHELPDIR=\"/usr/local/share/aptitude\" -DPKGDATADIR=\"/usr/local/share/aptitude\"  -g -O2 -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include   -I/usr/lib/cwidget -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include    -D_REENTRANT -Wall -Werror -MT download_install_manager.o -MD -MP -MF ".deps/download_install_manager.Tpo" -c -o download_install_manager.o download_install_manager.cc; \
    then mv -f ".deps/download_install_manager.Tpo" ".deps/download_install_manager.Po"; else rm -f ".deps/download_install_manager.Tpo"; exit 1; fi
cc1plus: warnings being treated as errors
download_install_manager.cc: In member function ‘download_manager::result download_install_manager::execute_install_run(pkgAcquire::RunResult, OpProgress&)’:
download_install_manager.cc:156: error: ignoring return value of ‘int system(const char*)’, declared with attribute warn_unused_result
make[4]: ** [download_install_manager.o] Erro 1
make[4]: Saindo do diretório `/home/kernel-script/aptitude/src/generic/apt'
make[3]: ** [all-recursive] Erro 1
make[3]: Saindo do diretório `/home/kernel-script/aptitude/src/generic'
make[2]: ** [all-recursive] Erro 1
make[2]: Saindo do diretório `/home/kernel-script/aptitude/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/kernel-script/aptitude'
make: ** [all] Erro 2
kernel-script@ubuntu-desktop:~/aptitude$
```

Better late than never I guess?

Edit the generic/apt/download_install_manager.cc file

Add this line before the switch line:
```

int foo = 0;
```And edit this line:

```
system("DPKG_NO_TSTP=1 dpkg --configure -a");
```To look like this:

```
foo = system("DPKG_NO_TSTP=1 dpkg --configure -a");
```Save and recompile! :)

Mine looks like this:

```
pthread_sigmask(SIG_UNBLOCK, &allsignals, &oldsignals);
  pkgPackageManager::OrderResult pmres = pm->DoInstall(aptcfg->FindI("APT::Status-Fd", -1));
  int foo = 0;
  switch(pmres)
    {
    case pkgPackageManager::Failed:
      _error->DumpErrors();
      cerr << _("A package failed to install.  Trying to recover:") << endl;
      
      foo = system("DPKG_NO_TSTP=1 dpkg --configure -a");
      _error->Discard();
      
      rval = failure;
      break;
    case pkgPackageManager::Completed:
      break;

    case pkgPackageManager::Incomplete:
      rval = do_again;
      break;
    }

  pthread_sigmask(SIG_SETMASK, &oldsignals, NULL);
  post_install_hook(pmres);
```

---

