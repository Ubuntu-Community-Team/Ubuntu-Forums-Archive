---
title: "avant leopard style"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by isaacj87 on 2007-07-08
Hello

I'm trying to compile the svn version of avant and patch it in order to achieve the icon reflection. But I keep hitting obstacles. AWN works perfectly on my comp so I don't know what could be wrong. Here's what's happening.
First off I don't know if the patch is working correctly, here's the output:

> $ sudo patch -p1 < patch.diff
(Stripping trailing CRs from patch.)
patching file src/awn-bar.c
(Stripping trailing CRs from patch.)
patching file src/awn-bar.h
(Stripping trailing CRs from patch.)
patching file src/awn-gconf.c
(Stripping trailing CRs from patch.)
patching file src/awn-gconf.h
(Stripping trailing CRs from patch.)
patching file src/awn-task.c
(Stripping trailing CRs from patch.)
patching file src/awn-window.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 320 with fuzz 1.

then when I ./autogen.sh:

> $ ./autogen.sh
/usr/bin/gnome-autogen.sh

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.61

checking for automake >= 1.9...

  testing automake-1.10... 
not found.
  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.5...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.11

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.5

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.21

Checking for required M4 macros...


Checking for forbidden M4 macros...

**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.


Processing ./configure.in


Running libtoolize...

You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.

Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

[B]Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).[/B]


Running intltoolize...


Running aclocal-1.9...


Running autoconf...


Running autoheader...


Running automake-1.9...

configure.in: installing `./install-sh'
configure.in: installing `./missing'
applets/notification-area/Makefile.am: installing `./compile'
applets/notification-area/Makefile.am: installing `./depcomp'

Running ./configure --enable-maintainer-mode ...

./configure: line 2002: i: command not found
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.34... 0.35.5 found
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
checking for catalogs to be installed...  cs da de_DE el_GR en_GB es fi_FI fr_FR it_IT no_NO pt_BR sv ru
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... yes (version 2.12.11)
[B]checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto dbus-glib-1 libglade-2.0 xdamage xcomposite xrender) were not met:

No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found
No package 'dbus-glib-1' found
No package 'libglade-2.0' found
No package 'xdamage' found
No package 'xcomposite' found
No package 'xrender' found[/B]

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Notice the bold stuff...what's going wrong here. AWN from the repo works just fine. :confused:

thanks for any assistance in advance!

---

### Post by xfile087 on 2007-07-08
I think you may find [http://ubuntuforums.org/showthread.php?t=492971](http://ubuntuforums.org/showthread.php?t=492971) and [http://ubuntuforums.org/showthread.php?p=2307772](http://ubuntuforums.org/showthread.php?p=2307772) useful for getting it working...

see attached for a screenshot of mine :D

---

### Post by isaacj87 on 2007-07-08
Haha...I like the background! And actually the thread about compiling AWN helped me, I can't believe I looked at it and didn't realize it (doh!)...I finally got it working...see the pic.

---

### Post by Nekiruhs on 2007-07-09
> **isaacj87 said:**
> Haha...I like the background! And actually the thread about compiling AWN helped me, I can't believe I looked at it and didn't realize it (doh!)...I finally got it working...see the pic.

I have the same issue, could you tell me how you fixed it??

---

### Post by isaacj87 on 2007-07-09
are you having trouble during the compiling part?

missing dependencies?

---

### Post by andrewsomething on 2007-07-10
If you are having problems compiling, there is is a deb availiable for download at [http://download.tuxfamily.org/syzygy42/static/misc/packages/awn214reflect/](http://download.tuxfamily.org/syzygy42/static/misc/packages/awn214reflect/)

Just remember, this is still considered unstable. Also, you'll have to uninstall the repo version first which means no more automatic updates.

---

### Post by Izobalax on 2007-07-14
I'm having a problem in that even though I've removed AWN using Synaptic, and removed the repo channel, I can still see and use AWN.

Any ideas how to get rid of it COMPLETELY so that I can try this version out?

/izo

---

### Post by walkerk on 2007-07-14
sorry to thread jack a bit but to the guys that have it working.. i have it all working correctly with reflection and all but when i enable auto-hide upon un-hiding the icon_offset (not in gconf.. just while this process of awn is running) returns to 0.. if i reload of course the icon_offset is correct and there is reflection..

are you guys having similar issues? i can't stand awn on top all the time.. gets in the way...

---

### Post by andrewsomething on 2007-07-14
> **Izobalax said:**
> I'm having a problem in that even though I've removed AWN using Synaptic, and removed the repo channel, I can still see and use AWN.

Any ideas how to get rid of it COMPLETELY so that I can try this version out?

/izo

As of today those patches have been committed to the source and are now included in the  newest repo version! So now you don't have to compile or use the static deb I pointed to up thread. Just upgrade to new version in the repo. As of writing  this, it should be version  0.1.2-svn218.

You still need to adjust the bar angle and icon offset  in gconfig, it hasn't been added into the normal preference menu yet...

---

### Post by Izobalax on 2007-07-14
> **andrewsomething said:**
> As of today those patches have been committed to the source and are now included in the  newest repo version! So now you don't have to compile or use the static deb I pointed to up thread. Just upgrade to new version in the repo. As of writing  this, it should be version  0.1.2-svn218.

You still need to adjust the bar angle and icon offset  in gconfig, it hasn't been added into the normal preference menu yet...
That solved it! Marvellous stuff!:grin:

One more question:

How do I add launchers onto the dock? Previous AWN versions I had to add the launchers to the desktop and AWN would use those launchers and would remember it. How do I do it in this version?

/izo

---

### Post by andrewsomething on 2007-07-14
> **Izobalax said:**
> 
How do I add launchers onto the dock? Previous AWN versions I had to add the launchers to the desktop and AWN would use those launchers and would remember it. How do I do it in this version?

/izo

Just drag the icon from your applications menu onto the bar... :)

---

### Post by Izobalax on 2007-07-14
> **andrewsomething said:**
> Just drag the icon from your applications menu onto the bar... :)
Does it remember that? Because the older versions always forgot once I restarted the computer, for example?

ETA: YES! It DOES remember it! AWN is now officially AWESOME!:grin:

/izo

---

### Post by isaacj87 on 2007-07-14
yeah...it's pretty sweet now!!! 

I've got a working copy of svn-226 running now. With the amarok plugin and gaim plugin working as well.

Pretty cool stuff!

:)

---

### Post by walkerk on 2007-07-19
> **walkerk said:**
> sorry to thread jack a bit but to the guys that have it working.. i have it all working correctly with reflection and all but when i enable auto-hide upon un-hiding the icon_offset (not in gconf.. just while this process of awn is running) returns to 0.. if i reload of course the icon_offset is correct and there is reflection..

are you guys having similar issues? i can't stand awn on top all the time.. gets in the way...

fixed w/ svn 227.

---

### Post by Bofur on 2007-07-20
> **andrewsomething said:**
> As of today those patches have been committed to the source and are now included in the  newest repo version! So now you don't have to compile or use the static deb I pointed to up thread. Just upgrade to new version in the repo. As of writing  this, it should be version  0.1.2-svn218.

You still need to adjust the bar angle and icon offset  in gconfig, it hasn't been added into the normal preference menu yet...

I have the newest version and I went into gconfig and changed the bar_angle to 45, icon_offset to 10 but its not reflecting. Any ideas? Thanks

---

### Post by pjones0404 on 2007-07-20
got another question for everyone.

when i add the trach icon tho the dock it uses a different trash then the one included w/ my icon set. how can i change it? can i do it in gconf-editor somewhere?

---

### Post by isaacj87 on 2007-07-21
The way I did it was to link the icons from my theme to the icons that AWN uses (which are the nasty looking ones found in tango or original gnome or something).

Within terminal, go to your icon theme (usually in your home folder @ .icons/youriconpack/) then find your trash full and trash empty icons (probably in the folder "Places"). Here's an example of how I linked mine:

```
ln -s user-trash-empty.png gnome-stock-trash.png



ln -s user-trash-full.png gnome-stock-trash-full.png
```

Keep in mind that if your trash empty and trash full icons are a different you have to change that.

---

