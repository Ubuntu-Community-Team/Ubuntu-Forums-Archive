---
title: "./configure"
date: 2005-10-14
forum: Desktop Environments
---

### Post by LinkRJH on 2005-10-14
I'm trying to install this MUD client called Kildclient, but it's not working in a way I am not familiar with.

Any help would be appreciated. 

linkrjh@ubuntu:~/kildclient-2.2.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
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
checking for KILDCLIENT... configure: error: Package requirements (glib-2.0 >= 2.6.0
                              gtk+-2.0 >= 2.4.0
                              libglade-2.0 >= 2.4.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the KILDCLIENT_CFLAGS and KILDCLIENT_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
linkrjh@ubuntu:~/kildclient-2.2.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... none
checking dependency style of gcc... none
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
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
checking for KILDCLIENT... configure: error: Package requirements (glib-2.0 >= 2.6.0
                              gtk+-2.0 >= 2.4.0
                              libglade-2.0 >= 2.4.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the KILDCLIENT_CFLAGS and KILDCLIENT_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
linkrjh@ubuntu:~/kildclient-2.2.2$


I did a 'sudo apt-get install glib*', but that did not solve the problem. 

Thanks in advance,

Richard

---

### Post by chaumurky on 2005-10-14
**sudo apt-get install build-essential **I *think *that has the stuff you need.

EDIT: I chould've looked closer... >  checking for gcc... gcc :rolleyes:

---

### Post by darkmatter on 2005-10-14
You are missing developmental libraries, that is why you cannot successfully configure. You need to install the '-dev' packages for gtk+-2.0, glib and libglade.

---

### Post by nix4me on 2005-10-14
build-essential

---

### Post by LinkRJH on 2005-10-14
sudo apt-get install build-essential

It did it's thing, downloaded installed, etc.  Went back to it...same thing.  So I searched out and downloaded the source for all those things, glib, gtk+, etc.  Figured I'd do them in order...started with glib, then it asked me to get gettext, so I did that, ./configure'd glib again this time it's a go.  Do a make, good to go...get down to the last thing, make install, and doesn't work.

linkrjh@ubuntu:~/glib-2.8.3$ make install
make  install-recursive
make[1]: Entering directory `/home/linkrjh/glib-2.8.3'
Making install in .
make[2]: Entering directory `/home/linkrjh/glib-2.8.3'
make[3]: Entering directory `/home/linkrjh/glib-2.8.3'
/bin/sh ./mkinstalldirs /usr/local/bin
mkdir -p -- /usr/local/bin
mkdir: cannot create directory `/usr/local/bin': Permission denied
make[3]: *** [install-binSCRIPTS] Error 1
make[3]: Leaving directory `/home/linkrjh/glib-2.8.3'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/linkrjh/glib-2.8.3'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/linkrjh/glib-2.8.3'
make: *** [install] Error 2
linkrjh@ubuntu:~/glib-2.8.3$


Heeelp!

---

### Post by BoyOfDestiny on 2005-10-14
[QUOTE=LinkRJH]sudo apt-get install build-essential

It did it's thing, downloaded installed, etc.  Went back to it...same thing.  So I searched out and downloaded the source for all those things, glib, gtk+, etc.  Figured I'd do them in order...started with glib, then it asked me to get gettext, so I did that, ./configure'd glib again this time it's a go.  Do a make, good to go...get down to the last thing, make install, and doesn't work.

linkrjh@ubuntu:~/glib-2.8.3$ make install
make  install-recursive
make[1]: Entering directory `/home/linkrjh/glib-2.8.3'
Making install in .
make[2]: Entering directory `/home/linkrjh/glib-2.8.3'
make[3]: Entering directory `/home/linkrjh/glib-2.8.3'
/bin/sh ./mkinstalldirs /usr/local/bin
mkdir -p -- /usr/local/bin
mkdir: cannot create directory `/usr/local/bin': Permission denied
make[3]: *** [install-binSCRIPTS] Error 1
make[3]: Leaving directory `/home/linkrjh/glib-2.8.3'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/linkrjh/glib-2.8.3'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/linkrjh/glib-2.8.3'
make: *** [install] Error 2
linkrjh@ubuntu:~/glib-2.8.3$


Heeelp![/QUOTE]

Phew an easy one! 
it's sudo make install
not just make install :)

Anyway I'd recommend an apt-get install checkinstall

then do a sudo checkinstall
this allows you to make a deb and you can manage your homeade package with synaptic or dpkg...

---

### Post by az on 2005-10-15
You need to install libglade0-dev.  Use synaptic.  It will pull in the other -dev packages it needs.

---

### Post by David_Velden on 2005-10-28
I had the same problem, but that libglade0-dev thing did the trick!

Thanks,
David
(Holland)

---

