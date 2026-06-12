---
title: "glib-2.0 problem"
date: 2009-06-09
forum: Desktop Environments
---

### Post by Lostin60's on 2009-06-09
I just did a reinstall of Intrepid. I downloaded and installed screenlets from the terminal.  It downloaded with no errors. But when I tried to run it from the terminal, I got the following message.
> No module RSVG , graphics will not be so good
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 28, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 51, in <module>
    from options import *
  File "/usr/lib/python2.5/site-packages/screenlets/options.py", line 216, in <module>
    import gnomekeyring
ImportError: No module named gnomekeyring

So, I hunted the gnome-keyring, and went to install it, and got this message.
> checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.16.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I could only find one glib between 2.0 and 2.16.0.  If I remember right it was at sourceforge. It had a .bin and a .lib folder, and I can't figure out how to install it, as it has no configure file. I tried using glib 2.2 but gnome-keyring wouldn't accept it.  If anyone has any advice, it will be greatly appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by jkoval on 2009-06-19
trying to compile winefish
get message  
checking for glib-2.0 >= 2.2... no
configure: error: glib-2.0 version 2.2 or higher is required


tried 
apt-get install libc6-dev g++ gcc
and 
apt-get install build-essential

apt-get install glib-2.0 
gets
 E: Couldn't find package glib-2.0


I do have something called glib-sharp-2.0!!

---

