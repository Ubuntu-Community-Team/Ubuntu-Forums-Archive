---
title: "./configure + make"
date: 2005-09-06
forum: Desktop Environments
---

### Post by celluloid on 2005-09-06
Hey guys, Thanks heaps for recent help.
Not sure if this is the correct place to ask this question.

I'm trying to install the BMP-Docklet plugin in XFCE4 running Hoary.
I've install build-essentials and XML::Parser for the install but still getting errors on ./configure

The end few lines showing the error in ./configure are

checking for GTK+ - version >= 2.4.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking pkg-config is at least version 0.9.0... yes
checking for BEEP_CFLAGS...
checking for BEEP_LIBS...
Package bmp was not found in the pkg-config search path.
Perhaps you should add the directory containing `bmp.pc'
to the PKG_CONFIG_PATH environment variable
No package 'bmp' found
configure: error: BMP >= 0.9.7 development package not installed
root@ubuntu:/home/grant/bmp-docklet-1.3 #

Though can't find the dev packages for BMP? not sure if this is what I need, but i'm totally lost. Have looked on google, xfce.org and in the bmp support pages.
Any help would be fantastic.

---

### Post by az on 2005-09-06
sudo apt-get install build-essential beep-media-player-dev


Here it is:
[http://packages.ubuntu.com/hoary/devel/beep-media-player-dev](http://packages.ubuntu.com/hoary/devel/beep-media-player-dev)


You probably need gtk headers too.  Maybe not.

---

