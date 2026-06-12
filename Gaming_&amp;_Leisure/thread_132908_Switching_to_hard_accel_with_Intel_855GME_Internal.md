---
title: "Switching to hard accel with Intel 855GME Internal Graphics"
date: 2006-02-19
forum: Gaming &amp; Leisure
---

### Post by aljones15 on 2006-02-19
hey folks,

I have an intel 855GME internal graphics card.
when I run games it runs mesa indirect i.e. software
rendering. is it possible to run open gl with hardware
accel using this card? how do I switch to it? device
manager lists the intel 855gme card twice for some
reason btw.

peace,
A

---

### Post by aljones15 on 2006-02-19
should have searched before I posted

[http://ubuntuforums.org/showthread.php?t=40865&highlight=Intel+855GME](http://ubuntuforums.org/showthread.php?t=40865&highlight=Intel+855GME)

haven't quite found a good fix here, but I'm only 1 page into the thread.

-
A

---

### Post by Ubuntuud on 2006-02-19
I can tell you that it is very hard, I've a 915GM myself, and I've been trying to get it to work for 8 weeks now. I had it working for one day, but after rebooting it was gone.
You've probably already done this, but just to make sure, have you loaded the "drm" module?

---

### Post by aljones15 on 2006-02-19
yeah got the drm or libdrm1 i think just installed the dev files.
anyway, just upgraded to 686 kernel and will try the savage method
after restart.

peace,
A

---

### Post by Mikecore on 2006-02-19
[QUOTE=Ubuntuud]I can tell you that it is very hard, I've a 915GM myself, and I've been trying to get it to work for 8 weeks now. I had it working for one day, but after rebooting it was gone.
You've probably already done this, but just to make sure, have you loaded the "drm" module?[/QUOTE]

I have that same card (915GM) and 3D works just fine. Make sure you are using the i810 driver from xorg. And make sure you have your xorg.conf setup correctly.

I have notice some people have had problems with this card. I don't understand why 
cause I installed Breezy and everything just worked. I didn't have to do anything.

---

### Post by aljones15 on 2006-02-19
I got it working using the [Savage DRI FAQ]("http://www.ubuntuforums.org/showthread.php?t=32043")
basically upgrade to linux kernel 686, remove 386, 
get the new driver for your card from here:
[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)
and then install. I had to install a newer version
of GCC to get it work too.

---

### Post by aljones15 on 2006-02-19
Just for future reference
Open up Syanpatic package manager.
search 686
install all the 686 kernel files.
download the driver for the i915 i.e. intel 855gme driver
from 
[http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/)
the original faq also says to get the latest
common file from the snapshots to hence you need as of today:
[http://dri.freedesktop.org/snapshots/common-20060206-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/common-20060206-linux.i386.tar.bz2")
[http://dri.freedesktop.org/snapshots/i915-20060206-linux.i386.tar.bz2]("http://dri.freedesktop.org/snapshots/i915-20060206-linux.i386.tar.bz2")
untar the common and i915.
restart your computer so you're now running the 686 kernel.
when you restart you can
uname -r to make sure you're now running 686.
Syanpatic un-install the 386 kernel if you're now
running 686. feel safe for a moment before you compile
a new module for your new 686 based kernel.
relax.
when you untarred the common and i915 they created
directories. Go into the i915 directory and
sudo ./install.sh
this will bring up the dri install script.
module installs as does the driver.
restart and run glxinfo
should get something like:
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 852GM/855GM 20050225
OpenGL version string: 1.3 Mesa 6.3.2


if you have any problems with the script
look in the log file and post them here.
Mine is working after about 2 months of putting around
trying to fix this. anyway, will be in E.T. and maybe second life
shortly.

---

