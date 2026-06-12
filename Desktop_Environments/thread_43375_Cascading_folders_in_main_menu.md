---
title: "Cascading folders in main menu"
date: 2005-06-21
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-21
Places > Computer, then use nautilus to get where I'm going. That's ok for a while, but I'm tired of it now. It takes ages. I'd like to have the places menu cascade to every level so i can get to a file or folder without even opening nautilus. 

Now that's not going to be a script i dont' think, so i think i'm about to learn something new?  :smile:

---

### Post by intangible on 2005-06-21
Looks like there was already an applet to do what you want, but nobody's updated it in a while:

[https://www.zoned.net/~xkahn/file_menu_applet/](https://www.zoned.net/~xkahn/file_menu_applet/)

---

### Post by Dave_is_sexy on 2005-06-21
OK Awesome.

I did this:


```
dave@D5:~$ cd ./Desktop
dave@D5:~/Desktop$ sudo alien file_menu_applet-0.5-ximian.1.i386.rpm
file-menu-applet_0.5-1_i386.deb generated
dave@D5:~/Desktop$ sudo dpkg -i file-menu-applet_0.5-1_i386.deb
Selecting previously deselected package file-menu-applet.
(Reading database ... 68010 files and directories currently installed.)
Unpacking file-menu-applet (from file-menu-applet_0.5-1_i386.deb) ...
Setting up file-menu-applet (0.5-1) ...
dave@D5:~/Desktop$
```

But nothing happened. I did something wrong didn't i?

---

### Post by Dave_is_sexy on 2005-06-21
Somebody else said this:

[I]I tried to compile it by myself (after downloading from the internet)
but it seems too old to work with gnome2.
Is there something similar or planned for the Gnome2 platform?
In my opinion that would be very usefull... the "Open recent" sometimes
comes in help but it's a different thing... just think that in KDE such
a feature is present and I even used it many times with gnome 1.4.
What do you think? Any suggestion?[/I]

from: [http://mail.gnome.org/archives/usability/2004-July/msg00035.html](http://mail.gnome.org/archives/usability/2004-July/msg00035.html)

---

### Post by ow50 on 2005-06-21
[bookmark-applet](http://gnomefiles.org/app.php?soft_id=278)
[nautilus-menu](http://www.bitpoetry.com/programs/nautilusmenu/) 

You can try these, but they are somewhat buggy, if they work at all.

---

### Post by Dave_is_sexy on 2005-06-21
OK. I think I need a C compiler? 

Pastey pastey (good ol' clipboard-daemon)

```
dave@D5:~/Desktop/bookmark-applet-0.9.tar.gz_FILES/bookmark-applet-0.9$ ./configure checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
dave@D5:~/Desktop/bookmark-applet-0.9.tar.gz_FILES/bookmark-applet-0
```.9$

---

### Post by shakin on 2005-06-21
To get gcc and other tools you need to compile apps:

```

$ sudo apt-get build-essential

```

FWIW, KDE has this functionality built-in. A large part of why I switched to KDE at work is that it seems more complete. That is to say that while Gnome's features are often implemented the same or better than KDE's similar features, KDE has quite a few features that Gnome does not. It seems like I can do more with KDE without searching for addons (which by my experience, don't often work very well).

---

### Post by Dave_is_sexy on 2005-06-21
I like things like Gaim and Nautilus, and the desktop "stretch icon" thing. And the way it doesn't try to fob me off with Koffice just cos it starts with a K  ;-)

After a number of error messages (xml perl parsing etc), I'm stuck on this one.

```
libgnomeui-2.0... Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found

configure: error: Library requirements (
glib-2.0 >= 2.4.0
gtk+-2.0 >= 2.4.0
gnome-vfs-2.0 >= 2.4.0
libgnomeui-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
dave@D5:~/Desktop/bookmark-applet-0.9.tar.gz_FILES/bookmark-applet-0.9$
```

---

### Post by Dave_is_sexy on 2005-06-24
glib-2.0.pc is not on my computer OR on apt-get

---

### Post by Dave_is_sexy on 2007-05-05
*bump*

Anything on this yet? I'm not using Gnome atm, but XFCE can run Gnome applets finr

---

