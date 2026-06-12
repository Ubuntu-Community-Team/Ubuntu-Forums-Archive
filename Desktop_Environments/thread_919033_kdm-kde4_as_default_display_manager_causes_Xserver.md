---
title: "kdm-kde4 as default display manager causes Xserver crash"
date: 2008-09-13
forum: Desktop Environments
---

### Post by fvillars on 2008-09-13
I recently installed KDE4.1 in parallel to Gnome and KDE3.5. I decided KDE4.1, despite its many bugs, was stable enough to use as my default desktop environment and it has worked pretty well.

  The other that, if I am going with KDE4.1, I might as well make kdm-kde4 my default display manager  instead of gdm.  "Don't look back," as the KDE folks are now saying.

  Problem is, it doesn't look like kdm-kde4 is ready for the job, at least not on my system. During bootup, when kdm-kde4 tries to load, it fails to find and connect to the X server, then tries a failsafe or fallback way to initialize X, then finally freezes or sometimes drops back to a command prompt.

Here is the relevant portion of /var/log/kdm.log:


X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Zanadu 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 13 00:00:46 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "1024x768+0+0" is not supported on this GPU.
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "800x600+0+0" is not supported on this GPU.
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "640x480+0+0" is not supported on this GPU.
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "nvidia-auto-select" is not supported on this
(EE) NVIDIA(0):     GPU.
(EE) NVIDIA(0): Unable to use default mode "nvidia-auto-select".

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7f0d195cc100]
2: /usr/bin/X(miSetZeroLineBias+0x4b) [0x4e7b8b]
3: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f0d169f1b96]

Fatal server error:
Caught signal 11.  Server aborting

Warning:  Could not retrieve EDID because get-edid is not installed (1)
Warning:  Could not retreive PCI IDs because discover is not installed (1)
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X :10 -br -once -config /etc/X11/xorg.conf.failsafe


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Zanadu 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.10.log", Time: Sat Sep 13 00:00:52 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(WW) VESA: No matching Device section for instance (BusID PCI:2:9:0) found
(II) Module "ddc" already built-in
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Zanadu 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 13 00:01:05 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
kdmgreet(6645) KLocalePrivate::initEncoding: Cannot resolve system encoding, defaulting to ISO 8859-1. 
kdmgreet(6646) KLocalePrivate::initEncoding: Cannot resolve system encoding, defaulting to ISO 8859-1. 
kdmgreet: Fatal IO error: client killed
kdmgreet: Fatal IO error: client killed
xinit:  connection to X server lost.

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


xinit:  unexpected signal 15.


  I have rooted around in /etc/init.d and various other startup directories and files without success. Looking through various forums hasn't been too useful. I suspect this is a bug in kdm-kde4 or perhaps some incompatibility.
  Doe anyone in the forum have any insight into what is going on here?

---

### Post by &amp;wP*!) on 2008-09-13
> **fvillars said:**
> I recently installed KDE4.1 in parallel to Gnome and KDE3.5. I decided KDE4.1, despite its many bugs, was stable enough to use as my default desktop environment and it has worked pretty well.

  The other that, if I am going with KDE4.1, I might as well make kdm-kde4 my default display manager  instead of gdm.  "Don't look back," as the KDE folks are now saying.

  Problem is, it doesn't look like kdm-kde4 is ready for the job, at least not on my system. During bootup, when kdm-kde4 tries to load, it fails to find and connect to the X server, then tries a failsafe or fallback way to initialize X, then finally freezes or sometimes drops back to a command prompt.

Here is the relevant portion of /var/log/kdm.log:


X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Zanadu 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 13 00:00:46 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "1024x768+0+0" is not supported on this GPU.
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "800x600+0+0" is not supported on this GPU.
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "640x480+0+0" is not supported on this GPU.
(EE) NVIDIA(0): The requested configuration of display devices (CRT-0) in
(EE) NVIDIA(0):     MetaMode "nvidia-auto-select" is not supported on this
(EE) NVIDIA(0):     GPU.
(EE) NVIDIA(0): Unable to use default mode "nvidia-auto-select".

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x6a) [0x48402a]
1: /lib/libc.so.6 [0x7f0d195cc100]
2: /usr/bin/X(miSetZeroLineBias+0x4b) [0x4e7b8b]
3: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f0d169f1b96]

Fatal server error:
Caught signal 11.  Server aborting

Warning:  Could not retrieve EDID because get-edid is not installed (1)
Warning:  Could not retreive PCI IDs because discover is not installed (1)
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X :10 -br -once -config /etc/X11/xorg.conf.failsafe


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Zanadu 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.10.log", Time: Sat Sep 13 00:00:52 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(WW) VESA: No matching Device section for instance (BusID PCI:2:9:0) found
(II) Module "ddc" already built-in
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux Zanadu 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 13 00:01:05 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
kdmgreet(6645) KLocalePrivate::initEncoding: Cannot resolve system encoding, defaulting to ISO 8859-1. 
kdmgreet(6646) KLocalePrivate::initEncoding: Cannot resolve system encoding, defaulting to ISO 8859-1. 
kdmgreet: Fatal IO error: client killed
kdmgreet: Fatal IO error: client killed
xinit:  connection to X server lost.

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


xinit:  unexpected signal 15.


  I have rooted around in /etc/init.d and various other startup directories and files without success. Looking through various forums hasn't been too useful. I suspect this is a bug in kdm-kde4 or perhaps some incompatibility.
  Doe anyone in the forum have any insight into what is going on here?

While Window Manager is started, NVIDIA Video Driver raises an exception to KDE4.

Try to find the correct versions of KDE4 and NVIDIA. Try to update both KDE4 and NVIDIA.

---

### Post by fvillars on 2008-09-14
Seems as though you were right...at least partially.

Not to bore everyone, and getting down to the heart of the matter, kdm-kde4 does not do well with Xinerama.

My original xorg.conf has Xinerama enabled. No matter how I try to rewrite, re-tweak, reconfigure or otherwise redo this file to enable Xinerama, kdm-kde4 causes the Xserver to crash.

On the other hand, if I configure xorg.conf to use a single screen, kdm-kde4 works beautifully as the default display manager.

So, for the time being I am using gdm as the default display manager, at least until KDE4.1 learns how to deal with dual screens, something it does very badly at this point.

---

