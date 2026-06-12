---
title: "Upgrade X server?"
date: 2009-03-01
forum: General Help
---

### Post by MattPhillips on 2009-03-01
Hello,

I've been having a lot of opengl/graphics problems and I wonder if it has something to do with my X server.  The most recent X.Org version is X11R7.4 and X server is 1.4.2 ([www.x.org](www.x.org)), but

```
$ X -version

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux matt-laptop 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
```

and the directory X11R6 exists on my system in /usr, but there is no such X11R7 directory.  

My problem is that I don't really know what I'm doing re installing the new Xorg/Xserver versions, and I don't want to wreck my system.  Can anyone help me do this?  Thank you!

Matt

---

### Post by cariboo on 2009-03-01
You problem has more to do with your graphics driver, then with the xserver. What video driver are you using?

Jim

---

### Post by MattPhillips on 2009-03-01
Hi Jim,

Thanks for replying.  Problems indeed--take a look at my two most recent threads if you want to see a real journey through pain.  I've gone through the following driver specifications in different versions of my xorg.conf--no specification (what I get after sudo dpkg-reconfigure -phigh xserver-xorg), "i810", and "intel", all with essentially the same debilitating problems, opengl won't work at the very least.  

Recently, I downloaded this driver/patch

xf86-video-intel-4f5500abe209b92b39ae1f2d7a1118362ac95034.tar.gz

from here:

[http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=commit;h=4f5500abe209b92b39ae1f2d7a1118362ac95034](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-intel.git;a=commit;h=4f5500abe209b92b39ae1f2d7a1118362ac95034)

I installed it ($ autogen.sh) and added 

```
Driver   "intel"
```

to the "Device" section of the xorg.conf gotten by running dpkg-reconfigure -phigh xserver-xorg, but nothing changed.  (Same problems if I left that out, as well.)

Do you know anything left to try, driver-wise?  Thank you!

Matt

---

