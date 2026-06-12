---
title: "Build wp_tray from source - problems"
date: 2006-12-01
forum: Desktop Environments
---

### Post by the_joker on 2006-12-01
Hi all,

I tried to install the newest version of wp_tray from the web site at [http://planetearthworm.com/projects/wp_tray/index.php](http://planetearthworm.com/projects/wp_tray/index.php)

To do this, I performed the following commands:

```
[joker@host] $ ./configure --prefix=/usr --with-boostfilesystem=/usr/lib/libboost_filesystem.so --with-boostregex=/usr/lib/libboost_regex.so
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)sudo make
Making all in src
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make  all-am
make[2]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make[2]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
Making all in po
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/po'
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3'
joker@godbox:~/downloads/apps/wp_tray-0.5.3 $ sudo make install
Making install in src
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make[2]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
test -z "/usr/libexec" || mkdir -p -- "/usr/libexec"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'wp_tray' '/usr/libexec/wp_tray'
/usr/bin/install -c wp_tray /usr/libexec/wp_tray
test -z "/usr/share/wp_tray/glade" || mkdir -p -- "/usr/share/wp_tray/glade"
 /usr/bin/install -c -m 644 'wp_tray_conf.glade' '/usr/share/wp_tray/glade/wp_tray_conf.glade'
 /usr/bin/install -c -m 644 'wp_tray_search.glade' '/usr/share/wp_tray/glade/wp_tray_search.glade'
make[2]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
Making install in po
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/po'
if test -n ""; then \
           /usr/share; \
        else \
          /bin/sh ../mkinstalldirs /usr/share; \
        fi
installing en_GB.gmo as /usr/share/locale/en_GB/LC_MESSAGES/wp_tray.mo
if test "wp_tray" = "glib"; then \
          if test -n ""; then \
             /usr/share/glib-2.0/gettext/po; \
          else \
            /bin/sh ../mkinstalldirs /usr/share/glib-2.0/gettext/po; \
          fi; \
          /usr/bin/install -c -m 644 ./Makefile.in.in \
                          /usr/share/glib-2.0/gettext/po/Makefile.in.in; \
        else \
          : ; \
        fi
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/po'
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3'
make[2]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3'
make[2]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults \
        gconftool-2 --makefile-install-rule wp_tray.schemas
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
Attached schema `/schemas/apps/wp_tray/b_follow_links' to key `/apps/wp_tray/b_follow_links'
Installed schema `/schemas/apps/wp_tray/b_follow_links' for locale `C'
Attached schema `/schemas/apps/wp_tray/b_img_check' to key `/apps/wp_tray/b_img_check'
Installed schema `/schemas/apps/wp_tray/b_img_check' for locale `C'
Attached schema `/schemas/apps/wp_tray/b_timeout' to key `/apps/wp_tray/b_timeout'
Installed schema `/schemas/apps/wp_tray/b_timeout' for locale `C'
Attached schema `/schemas/apps/wp_tray/b_wp_logon' to key `/apps/wp_tray/b_wp_logon'
Installed schema `/schemas/apps/wp_tray/b_wp_logon' for locale `C'
Attached schema `/schemas/apps/wp_tray/dir_list' to key `/apps/wp_tray/dir_list'
Installed schema `/schemas/apps/wp_tray/dir_list' for locale `C'
Attached schema `/schemas/apps/wp_tray/n_timeout' to key `/apps/wp_tray/n_timeout'
Installed schema `/schemas/apps/wp_tray/n_timeout' for locale `C'
gconftool-2 --shutdown
test -z "/usr/share/pixmaps" || mkdir -p -- "/usr/share/pixmaps"
 /usr/bin/install -c -m 644 'wp_tray-applet.png' '/usr/share/pixmaps/wp_tray-applet.png'
test -z "/usr/etc/gconf/schemas" || mkdir -p -- "/usr/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'wp_tray.schemas' '/usr/etc/gconf/schemas/wp_tray.schemas'
test -z "/usr/lib/bonobo/servers" || mkdir -p -- "/usr/lib/bonobo/servers"
 /usr/bin/install -c -m 644 'wp_tray.server' '/usr/lib/bonobo/servers/wp_tray.server'
make[2]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3'
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3'
/gconf/schemas as install directory for schema files
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
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
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
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
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... yes
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
checking for catalogs to be installed...  en_GB
checking whether to enable maintainer-specific portions of Makefiles... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating po/Makefile.in
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing intltool commands
config.status: executing depfiles commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

```

```
[joker@host] $ sudo make
Making all in src
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make  all-am
make[2]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make[2]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
Making all in po
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/po'
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3'
```

```
[joker@host] $ sudo make install
Making install in src
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make[2]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
test -z "/usr/libexec" || mkdir -p -- "/usr/libexec"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'wp_tray' '/usr/libexec/wp_tray'
/usr/bin/install -c wp_tray /usr/libexec/wp_tray
test -z "/usr/share/wp_tray/glade" || mkdir -p -- "/usr/share/wp_tray/glade"
 /usr/bin/install -c -m 644 'wp_tray_conf.glade' '/usr/share/wp_tray/glade/wp_tray_conf.glade'
 /usr/bin/install -c -m 644 'wp_tray_search.glade' '/usr/share/wp_tray/glade/wp_tray_search.glade'
make[2]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/src'
Making install in po
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3/po'
if test -n ""; then \
           /usr/share; \
        else \
          /bin/sh ../mkinstalldirs /usr/share; \
        fi
installing en_GB.gmo as /usr/share/locale/en_GB/LC_MESSAGES/wp_tray.mo
if test "wp_tray" = "glib"; then \
          if test -n ""; then \
             /usr/share/glib-2.0/gettext/po; \
          else \
            /bin/sh ../mkinstalldirs /usr/share/glib-2.0/gettext/po; \
          fi; \
          /usr/bin/install -c -m 644 ./Makefile.in.in \
                          /usr/share/glib-2.0/gettext/po/Makefile.in.in; \
        else \
          : ; \
        fi
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3/po'
make[1]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3'
make[2]: Entering directory `/home/joker/downloads/apps/wp_tray-0.5.3'
make[2]: Nothing to be done for `install-exec-am'.
GCONF_CONFIG_SOURCE=xml:merged:/etc/gconf/gconf.xml.defaults \
        gconftool-2 --makefile-install-rule wp_tray.schemas
Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a writable configuration source at position 0
Attached schema `/schemas/apps/wp_tray/b_follow_links' to key `/apps/wp_tray/b_follow_links'
Installed schema `/schemas/apps/wp_tray/b_follow_links' for locale `C'
Attached schema `/schemas/apps/wp_tray/b_img_check' to key `/apps/wp_tray/b_img_check'
Installed schema `/schemas/apps/wp_tray/b_img_check' for locale `C'
Attached schema `/schemas/apps/wp_tray/b_timeout' to key `/apps/wp_tray/b_timeout'
Installed schema `/schemas/apps/wp_tray/b_timeout' for locale `C'
Attached schema `/schemas/apps/wp_tray/b_wp_logon' to key `/apps/wp_tray/b_wp_logon'
Installed schema `/schemas/apps/wp_tray/b_wp_logon' for locale `C'
Attached schema `/schemas/apps/wp_tray/dir_list' to key `/apps/wp_tray/dir_list'
Installed schema `/schemas/apps/wp_tray/dir_list' for locale `C'
Attached schema `/schemas/apps/wp_tray/n_timeout' to key `/apps/wp_tray/n_timeout'
Installed schema `/schemas/apps/wp_tray/n_timeout' for locale `C'
gconftool-2 --shutdown
test -z "/usr/share/pixmaps" || mkdir -p -- "/usr/share/pixmaps"
 /usr/bin/install -c -m 644 'wp_tray-applet.png' '/usr/share/pixmaps/wp_tray-applet.png'
test -z "/usr/etc/gconf/schemas" || mkdir -p -- "/usr/etc/gconf/schemas"
 /usr/bin/install -c -m 644 'wp_tray.schemas' '/usr/etc/gconf/schemas/wp_tray.schemas'
test -z "/usr/lib/bonobo/servers" || mkdir -p -- "/usr/lib/bonobo/servers"
 /usr/bin/install -c -m 644 'wp_tray.server' '/usr/lib/bonobo/servers/wp_tray.server'
make[2]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3'
make[1]: Leaving directory `/home/joker/downloads/apps/wp_tray-0.5.3'

```

Everything seems to have compiled OK, but I can't figure out where the app has actually been installed to.

The INSTALL file says that the applications should be installed to /usr/local/bin, but I've over-ridden that with the --prefix=/usr option.

Shouldn't the application be available in /usr/bin? Searching the directory for wp* doesn't show any binary or executable files, but it does show the application icon.

Any help would be greatly appreciated.

---

### Post by lloyd_b on 2006-12-01
Take a look in "/usr/libexec" - it's putting something called "wp_tray" in there....

Lloyd B.

---

### Post by the_joker on 2006-12-01
> **lloyd_b said:**
> Take a look in "/usr/libexec" - it's putting something called "wp_tray" in there....

Lloyd B.
Thanks. I found the executable (and found the line that told me where it was installing in the make output).

However, when I run it from a terminal, nothing seems to happen.

---

### Post by the_joker on 2006-12-04
Ah! Problem solved.

Silly me - the application complied and installed successfully, but is not designed to run as a program.

The new version is a panel applet, and shows up when adding an item to a GNOME panel, under Utilities.

Thanks for your help. I feel so silly :/

---

### Post by ArrowApollo on 2006-12-10
What do I do with all that code?paste it in the terminal? sorry i'm new.

---

### Post by the_joker on 2006-12-12
> **ArrowApollo said:**
> What do I do with all that code?paste it in the terminal? sorry i'm new.
You will need to install the program from the source code available on the web site.

Once you have downloaded the source code, extract it to a directory in your home folder, and use the following commands as root:

./configure
make
make install

you may need to install some extra packages - my first attempt failed to configure correctly due to missing *..so files, but I can't remember what they are right now. As soon as I can remember what the packages were, I will post an update.

Hope this helps.

---

### Post by blair on 2006-12-28
I tried to compile this and received several errors. It appears there are inconsistencies between installed package names and the package names the compile process is looking for. For example:

Compile Error 1: No package 'libpanel-applet2-0' found, yet Synaptic shows libpanel-applet2-0 package as available. Installing this did not fix the error. 

Compile Error 2: no package 'libxml++-2.6' found, yet Synaptic shows libxml++2.6c2a and libxml++2.6-dev packages as available. After installing these, this error went away.

Compile Error 3: No package 'libnotify' found, yet Synaptic shows libnotify1 package as available. After installing these, this error went away. 


Any idea how to fix this? I tried changing string names in the configure shell script file, but it didn't work. There are likely multiple references in other files. 

thanks

---

### Post by bigsuccess on 2007-01-04
> **blair said:**
> I tried to compile this and received several errors. It appears there are inconsistencies between installed package names and the package names the compile process is looking for. 

This is exactly what I'm experiencing. Being a noob I'm not too sure what to do.

In my case the configure script asks for -
```
No package 'libgnomeuimm-2.6' found
No package 'gconfmm-2.6' found
No package 'gtkmm-2.4' found
No package 'libgnomecanvasmm-2.6' found
No package 'libglademm-2.4' found
No package 'libpanelapplet-2.0' found
No package 'libxml++-2.6' found
No package 'libnotify' found
```

I started at the top and using apt-cache search I found that the closest match to the first one was-
```
libgnomeuimm-2.6-1c2a - C++ wrappers for libgnomeui (shared library)
libgnomeuimm-2.6-dev - C++ wrappers for libgnomeui (development files)
libbakery-2.3-16 - A C++ Application Framework (shared libraries)
libbakery-2.3-common - A C++ Application Framework (common files)
libbakery-2.3-dev - A C++ Application Framework (development files)
libbakery-2.4-1 - A C++ Application Framework (shared libraries)
libbakery-2.4-common - A C++ Application Framework (common files)
libbakery-2.4-dev - A C++ Application Framework (development files)
```

So I installed the first and re-ran configure. It still won't 'pick it up'. What do I do?

---

### Post by fa_pa on 2007-01-07
> **bigsuccess said:**
> 
In my case the configure script asks for -
```
No package 'libgnomeuimm-2.6' found
No package 'gconfmm-2.6' found
No package 'gtkmm-2.4' found
No package 'libgnomecanvasmm-2.6' found
No package 'libglademm-2.4' found
No package 'libpanelapplet-2.0' found
No package 'libxml++-2.6' found
No package 'libnotify' found
```


You need to install all these packages + libboost-filesystem and libboost-regex and then you have to run the config like this: 

> ./configure --with-boostfilesystem=/usr/lib/libboost_filesystem.so --with-boostregex=/usr/lib/libboost_regex.so


after that it compiles just fine.

---

### Post by BaCkFiRe on 2007-01-08
> **the_joker said:**
> Ah! Problem solved.

Silly me - the application complied and installed successfully, but is not designed to run as a program.

The new version is a panel applet, and shows up when adding an item to a GNOME panel, under Utilities.

Thanks for your help. I feel so silly :/
Hi,
I've just finished the compilation and everything seems fine but I can't find it. I looked in the Utilities section of the "Add to Panel" window but it's not there. Did I miss something ?

---

### Post by the_joker on 2007-01-14
Sorry - I'm running Windows at the moment (finally got some time for gaming!)

Check the very bottom of the "Add to Panel" window. I may have advised that it was in the wrong section. It should be the very last applet listed.

---

### Post by kkram13 on 2007-02-04
Backfire - did you manage to find the applet anywhere? I've been having the same problems: it installed okay after sorting out dependencies, but can't see the application in the Add to Panel bit. It does show up in Applications -> System Tools -> Configuration editor and then under apps, but changing things there doesn't make a difference.

Anybody have any ideas? I'm using Edgy...

Cheers peeps!

Mark

P.S. Alternatively: how would I go about uninstalling the program? Does sudo make uninstall work?

|\/|<

---

### Post by sv452 on 2007-05-07
anyone interested check my post here - maybe it will help

[http://ubuntuforums.org/showthread.php?p=2607366#post2607366](http://ubuntuforums.org/showthread.php?p=2607366#post2607366)

:D

---

