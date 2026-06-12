---
title: "Nasty hard crash of KDE. Now KDE is borked"
date: 2005-11-28
forum: Desktop Environments
---

### Post by StueyB on 2005-11-28
Hi peeps.

Im hoping someone can help me here. Earlier this evening i installed KDE via a term and did:

sudo apt-get install kde-desktop

All was fine after a cold reboot. However, on playing with desktop settings, ie icon size etc it became unresponsive, as in totally unresponsive. Nothing at all worked.

So i did a hard power off and rebooted. It allows me to login to KDE but then when after restoring session etc, disk activity goes absolutly wild and the whole thing goes so slow as to be unusable and the toolbar starts but no icons and it tells me X is checking files, starting with trash:/ and it never moves.

I rebooted into single user mode and did a fsck and it was all clean.

Rebooted and still had the same issue. I can log into Gnome no probs. So after a little research i deleted the .kde/cache files etc but to no avail. It still doesnt do anything.

Im running Ubuntu 5.10 upgraded to KDE via method above on a Toshiba Portege  T9100 with 756 MB Ram.

The Gnome was v stable and never had any issues with it. Any ideas on how to fix this. Below is my kdm.log

```

********************************************************************************
Note that your system uses syslog. All of kdm's internally generated messages
(i.e., not from libraries and external programs/scripts it uses) go to the
daemon.* syslog facility; check your syslog configuration to find out to which
file(s) it is logged. PAM logs messages related to authentication to authpriv.*.
********************************************************************************


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 21:01:03 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
    [10e] 320 x 200, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz, 100Hz
    [117] 1024 x 768, 60Hz, 75Hz, 85Hz, 100Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz
    [11d] 640 x 400, 70Hz
    [122] 1600 x 1200, 60Hz, 75Hz, 85Hz
    [133] 320 x 240, 72Hz
    [138] 1920 x 1440, 60Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [173] 720 x 480, 75Hz
    [17e] 720 x 576, 75Hz
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
SetClientVersion: 0 9

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 21:37:33 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
    [10e] 320 x 200, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz, 100Hz
    [117] 1024 x 768, 60Hz, 75Hz, 85Hz, 100Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz
    [11d] 640 x 400, 70Hz
    [122] 1600 x 1200, 60Hz, 75Hz, 85Hz
    [133] 320 x 240, 72Hz
    [138] 1920 x 1440, 60Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [173] 720 x 480, 75Hz
    [17e] 720 x 576, 75Hz
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
SetClientVersion: 0 9

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 21:46:51 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
    [10e] 320 x 200, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz, 100Hz
    [117] 1024 x 768, 60Hz, 75Hz, 85Hz, 100Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz
    [11d] 640 x 400, 70Hz
    [122] 1600 x 1200, 60Hz, 75Hz, 85Hz
    [133] 320 x 240, 72Hz
    [138] 1920 x 1440, 60Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [173] 720 x 480, 75Hz
    [17e] 720 x 576, 75Hz
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
SetClientVersion: 0 9

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 21:51:59 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
    [10e] 320 x 200, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz, 100Hz
    [117] 1024 x 768, 60Hz, 75Hz, 85Hz, 100Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz
    [11d] 640 x 400, 70Hz
    [122] 1600 x 1200, 60Hz, 75Hz, 85Hz
    [133] 320 x 240, 72Hz
    [138] 1920 x 1440, 60Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [173] 720 x 480, 75Hz
    [17e] 720 x 576, 75Hz
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
SetClientVersion: 0 9

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 23:27:24 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
    [10e] 320 x 200, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz, 100Hz
    [117] 1024 x 768, 60Hz, 75Hz, 85Hz, 100Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz
    [11d] 640 x 400, 70Hz
    [122] 1600 x 1200, 60Hz, 75Hz, 85Hz
    [133] 320 x 240, 72Hz
    [138] 1920 x 1440, 60Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [173] 720 x 480, 75Hz
    [17e] 720 x 576, 75Hz
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
SetClientVersion: 0 9

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 23:38:52 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
    [10e] 320 x 200, 70Hz
    [111] 640 x 480, 60Hz, 75Hz, 85Hz, 100Hz
    [114] 800 x 600, 60Hz, 75Hz, 85Hz, 100Hz
    [117] 1024 x 768, 60Hz, 75Hz, 85Hz, 100Hz
    [11a] 1280 x 1024, 60Hz, 75Hz, 85Hz
    [11d] 640 x 400, 70Hz
    [122] 1600 x 1200, 60Hz, 75Hz, 85Hz
    [133] 320 x 240, 72Hz
    [138] 1920 x 1440, 60Hz
    [13c] 1400 x 1050, 60Hz, 75Hz
    [143] 400 x 300, 72Hz
    [153] 512 x 384, 70Hz
    [173] 720 x 480, 75Hz
    [17e] 720 x 576, 75Hz
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Synaptics Touchpad no synaptics event device found (checked 4 nodes)
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image

```

Any ideas?

Cheers

Stu

---

### Post by ltmon on 2005-11-28
Instead of installing "kde-desktop" you might do better with installing "kubuntu-desktop".  Possibly you are missing a vital package or two.

To get everything back on track:

1. Delete ~/.kde and all subdirectories.  This will lose all your kde settings and the settings for any kde program you might have installed (k3b, amarok etc.).

2. If you don't want to do this try deleting only the following directories (EDIT: i just saw that you already tried this):

~/.kde/cache-<hostname>
~/.kde/socket-<hostname>
~/.kde/tmp-<hostname>

3. If it still doesn't work, another step you can try is deleting individual "rc" files.  This will erase the settings for individual applications. 

e.g.

~/.kde/share/config/kdesktoprc

is the file which contains settings for icon positioning, sizes etc.

Cheers,

L.

---

### Post by StueyB on 2005-11-28
Hi there !

Wow that worked (Deleting the entire .kde dir) ty, oh guru :)

I shall see if i can recreate to file a bug.

---

