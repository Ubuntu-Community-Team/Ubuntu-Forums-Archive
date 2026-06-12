---
title: "screen saver crash the computer"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Paul Chang on 2006-09-03
I got some serious problems after the recent update:

(1) When I got to "System --> Preference --> Screen Saver", the system crashed and go back to GUI login window;

(2) If I don't move the mouse for a little while, the system is automatically shut down;

(3) If I play some flash in firefox (with audio), and then play video using mplayer, I got an message "can not open/initialize audio device -> no sound".

Anyone has some idea to fix this problem? Thanks a lot in advance!

---

### Post by Paul Chang on 2006-09-15
I am alone here?

---

### Post by Paul Chang on 2006-12-21
Anybody solved the screen saver problem? Really appreciate if you could show how to fix the problem.

---

### Post by Krash1201 on 2007-01-08
having a similar problem, though i turned off the screen saver and that stopped gdm from restarting.  basically, whenever the screensaver started up, gdm restarted.  think it may be a problem with x, but i am not sure.

---

### Post by partylion on 2007-01-10
same problem after updating. gdm restarts if screensaver starts, even if i try to change settings in the menu.

I think there was an update for x-server included. before, I did a backup of my xorg.conf. but the new one after the update seems to be the same (no diffs with [FONT="Courier New"]cmp[/FONT] command.

so I removed all packages related to screensaver.
then I reinstalled the gnome screensavers. it works!

then I had the idea that it hase something to do with 3d support.
after I installed some 3d-screensavers I was sure.

what I need now is an explanation why?
is the new x-server some kind of bugy?

maybe something to do with my video card driver?
got a GeForce 7600GT an the nvidia driver installed.

solution: do not install any 3d screensaver.
it works but does not make me happy :( 

(sorry for my english, it's my first post here :mrgreen: )

[FONT="Courier New"]Driver         "nvidia"[/FONT]

[FONT="Courier New"]Xorg -version

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux neutron-server 2.6.15-27-386 #1 PREEMPT Sat Sep 16 01:51:59 UTC 2006 i686
Build Date: 16 March 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present[/FONT]

---

### Post by J-Rod on 2007-01-12
I am having the exact same issue just now. I am trying your idea of reinstalling all the screensaver stuff, I also have an nvidia card, if that matters.

---

### Post by mattengland on 2007-01-13
I appear to be experiencing the same symptoms.

I have a NVIDIA e-GeForce 7600 GTS card with a dual-monitor, TwinView setup.

I installed Dapper 6.06.1 Desktop on my computer, and I had zero problems with my screensaver until I upgraded my software packages today.  Now I get the symptoms described above.

partylion or anyone else- How can I install the gnome-screensaver without installing the 3d screensavers...assuming this is a workaround?

Also, I'm going to try uninstalling all the screensaver stuff I can find, then installing the screensaver from a 6.06.1 Desktop CD and see if I can "get back" to the working configuration I had before.  If not, I'm going to try re-installing my OS back to native 6.06.1.

It would be nice if we could somehow get Ubuntu's or Nvidia's attention on this.  This is troublesome for me; I can't even change the screensave settings, for the preview of the screen saver that runs when the screen saver preferences display plops up appears to crash the X server.  *sigh*

-Matt

---

### Post by mattengland on 2007-01-13
I reloaded back to a fresh Dapper 6.06.1 (with the alternative CD) again, and my screen saver now works again.  No more cross-the-board upgrades for me on this system, at least.

This is a pretty old thread; is it time for some dev/integrator to address this?  Where can I log a bug?  Launchpad.net?

-Matt

---

### Post by mattengland on 2007-01-13
I posted a bug here:

[https://bugs.launchpad.net/ubuntu/+bug/79160](https://bugs.launchpad.net/ubuntu/+bug/79160)

-Matt

---

### Post by Jesse121 on 2007-01-13
I am also having this issue. When I go into Control Panel and open up Screen Saver I see the window briefly then my computer logs out. It also does this when I open up the Nvidia Display Settings dialog and click on "openGL/GLX information". I am not sure when this problem started but I just noticed it today. I know that both the Screen Saver and the Nvidia options were working fine a few days ago. I recently installed mplayer and some codecs and I am running Fluxbox so maybe it is something to do with these programs.
I am running Ubuntu v6.10(64bit) and I have an Nvidia Geforce 4. Anyone know of a solution I would appreciate it.

---

### Post by wilsonag on 2007-01-13
You can fix this problem by reloading the NVidia driver if you used the one off their website.  I had the problem and noticed that when anything tried to do anything with OpenGL that the computer crashed/went back to the login screen.  A quick test would be to run glxgears and see if it crashed.  If it does then you know its the driver and you need to reload it.  To run glxgears open a terminal and type glxgears

---

### Post by mattengland on 2007-01-13
I loaded my nvidia driver via envy (and automated driver-loading gizmo for nvidia cards):

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Any ideas how I can reload the driver on my system (in case I ever want to try this again)?

-Matt

---

### Post by wilsonag on 2007-01-14
Mattengland,
  I'm not an expert in how things work but you should be able to run the script do an uninstall then just run it again and do an install and it should fix the problem in the future.  I know this is a pain in the rear, but getting things running again is always a nice feeling.

---

### Post by miceagol on 2007-01-16
> **wilsonag said:**
> Mattengland,
  I'm not an expert in how things work but you should be able to run the script do an uninstall then just run it again and do an install and it should fix the problem in the future.  I know this is a pain in the rear, but getting things running again is always a nice feeling.

The first thing I did  after a fresh Ubuntu installation was to install the nVidia drivers (no support for 8800 GTS in Edgy). I don't understand why it helps to reload the drivers? 

Anyway, I might give it a try. :)

---

### Post by miceagol on 2007-01-16
Thanks, guys! Screensavers and all other problemmakers are now no longer causing problems. :D I just uninstalled the drivers, and reinstalled them using method 2 of [this guide.]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy")

---

### Post by Paul Chang on 2007-01-25
I noticed that "Automatix" has a functionality to install the driver of NVIDIA cards. Has anyone tried that?

---

### Post by TremerePuck on 2007-02-10
I'm having a similar problem. It only happens in Gnome, not in KDE. It doesn't happen when running a screen saver only randomly when previewing screen savers in the screen saver settings dialog. 

I'm using a Nvidia GeForce 4 Ti4200 Driver 9631 (The newest one that supports the GeForce4  before it became a legacy device, which they don't bother telling you on the site)

I have a dual monitor setup using Xinerama.

I'm using Kubuntu with the ubuntu-desktop installed.

All GLX programs work perfectly fine.

I've tried reinstalling the driver. I haven't tried the older legacy driver for this problem as it performs horribly for me.

Here's my log:

```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux puck 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 10 19:59:45 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "mouse0"
(WW) The directory "/usr/share/fonts/X11/TTF/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/OTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/CID/" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "Xinerama" "1"
(**) Xinerama: enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3099 card 147b,7411 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b099 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:08:0: chip 109e,036e card 0000,0000 rev 11 class 04,00,00 hdr 80
(II) PCI: 00:08:1: chip 109e,0878 card 0000,0000 rev 11 class 04,80,00 hdr 80
(II) PCI: 00:0b:0: chip 1102,0004 card 1102,0051 rev 03 class 04,01,00 hdr 80
(II) PCI: 00:0b:1: chip 1102,7003 card 1102,0040 rev 03 class 09,80,00 hdr 80
(II) PCI: 00:0b:2: chip 1102,4001 card 1102,0010 rev 00 class 0c,00,10 hdr 80
(II) PCI: 00:0d:0: chip 1033,0035 card 0caf,a600 rev 41 class 0c,03,10 hdr 80
(II) PCI: 00:0d:1: chip 1033,0035 card 0caf,a600 rev 41 class 0c,03,10 hdr 00
(II) PCI: 00:0d:2: chip 1033,00e0 card 0caf,a6e0 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:0f:0: chip 1317,0985 card 1317,0570 rev 11 class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 1106,3147 card 1106,3147 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1106,0571 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:2: chip 1106,3038 card 147b,7411 rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:3: chip 1106,3038 card 147b,7411 rev 23 class 0c,03,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0253 card 1462,8702 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:8:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xe7005000/12
(--) PCI:*(1:0:0) nVidia Corporation NV25 [GeForce4 Ti 4200] rev 162, Mem @ 0xe4000000/24, 0xd0000000/27, 0xd8000000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe7009000 - 0xe70093ff (0x400) MX[B]
	[1] -1	0	0xe7008000 - 0xe70080ff (0x100) MX[B]
	[2] -1	0	0xe7007000 - 0xe7007fff (0x1000) MX[B]
	[3] -1	0	0xe7006000 - 0xe7006fff (0x1000) MX[B]
	[4] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[5] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[6] -1	0	0xe700a000 - 0xe700afff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe7005000 - 0xe7005fff (0x1000) MX[B](B)
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe7009000 - 0xe70093ff (0x400) MX[B]
	[1] -1	0	0xe7008000 - 0xe70080ff (0x100) MX[B]
	[2] -1	0	0xe7007000 - 0xe7007fff (0x1000) MX[B]
	[3] -1	0	0xe7006000 - 0xe7006fff (0x1000) MX[B]
	[4] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[5] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[6] -1	0	0xe700a000 - 0xe700afff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[9] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe7005000 - 0xe7005fff (0x1000) MX[B](B)
	[12] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[13] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[14] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[15] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[16] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7009000 - 0xe70093ff (0x400) MX[B]
	[5] -1	0	0xe7008000 - 0xe70080ff (0x100) MX[B]
	[6] -1	0	0xe7007000 - 0xe7007fff (0x1000) MX[B]
	[7] -1	0	0xe7006000 - 0xe7006fff (0x1000) MX[B]
	[8] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[9] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[10] -1	0	0xe700a000 - 0xe700afff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe7005000 - 0xe7005fff (0x1000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7009000 - 0xe70093ff (0x400) MX[B]
	[5] -1	0	0xe7008000 - 0xe70080ff (0x100) MX[B]
	[6] -1	0	0xe7007000 - 0xe7007fff (0x1000) MX[B]
	[7] -1	0	0xe7006000 - 0xe7006fff (0x1000) MX[B]
	[8] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[9] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[10] -1	0	0xe700a000 - 0xe700afff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe7005000 - 0xe7005fff (0x1000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7009000 - 0xe70093ff (0x400) MX[B]
	[5] -1	0	0xe7008000 - 0xe70080ff (0x100) MX[B]
	[6] -1	0	0xe7007000 - 0xe7007fff (0x1000) MX[B]
	[7] -1	0	0xe7006000 - 0xe7006fff (0x1000) MX[B]
	[8] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[9] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[10] -1	0	0xe700a000 - 0xe700afff (0x1000) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe7005000 - 0xe7005fff (0x1000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "MetaModes" "CRT-0: 2048x1536 +0+0; CRT-0: 1600x1200 +0+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.25.00.29.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4200 at PCI:1:0:0:
(--) NVIDIA(0):     IBM P260 (CRT-0)
(--) NVIDIA(0):     HP MX70 (CRT-1)
(--) NVIDIA(0): IBM P260 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(0): HP MX70 (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:2048x1536+0+0"
(II) NVIDIA(0):     "CRT-0:1600x1200+0+0"
(II) NVIDIA(0):     "CRT-0:1280x1024+0+0"
(II) NVIDIA(0):     "CRT-0:1024x768+0+0"
(II) NVIDIA(0):     "CRT-0:800x600+0+0"
(II) NVIDIA(0):     "CRT-0:640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 2048 x 1536
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "MetaModes" "CRT-1: 1280x1024_60 +0+0"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce4 Ti 4200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 131072 kBytes
(--) NVIDIA(1): VideoBIOS: 04.25.00.29.00
(II) NVIDIA(1): Detected AGP rate: 4X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce4 Ti 4200 at PCI:1:0:0:
(--) NVIDIA(1):     IBM P260 (CRT-0)
(--) NVIDIA(1):     HP MX70 (CRT-1)
(--) NVIDIA(1): IBM P260 (CRT-0): 350.0 MHz maximum pixel clock
(--) NVIDIA(1): HP MX70 (CRT-1): 350.0 MHz maximum pixel clock
(II) NVIDIA(1): Display Device found referenced in MetaMode: CRT-1
(II) NVIDIA(1): Assigned Display Device: CRT-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "CRT-1:1280x1024_60+0+0"
(II) NVIDIA(1): Virtual screen size determined to be 1280 x 1024
(++) NVIDIA(1): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) LoadModule: "rac"
(II) Loading /usr/lib/xorg/modules/librac.so
(II) Module rac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after preInit:
	[0] 0	0	0xd8000000 - 0xd807ffff (0x80000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] 0	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe7009000 - 0xe70093ff (0x400) MX[B]
	[8] -1	0	0xe7008000 - 0xe70080ff (0x100) MX[B]
	[9] -1	0	0xe7007000 - 0xe7007fff (0x1000) MX[B]
	[10] -1	0	0xe7006000 - 0xe7006fff (0x1000) MX[B]
	[11] -1	0	0xe7000000 - 0xe7003fff (0x4000) MX[B]
	[12] -1	0	0xe7004000 - 0xe70047ff (0x800) MX[B]
	[13] -1	0	0xe700a000 - 0xe700afff (0x1000) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xe4000000 - 0xe4ffffff (0x1000000) MX[B](B)
	[18] -1	0	0xe7005000 - 0xe7005fff (0x1000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d407 (0x8) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[30] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[31] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "CRT-0:2048x1536+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "CRT-1:1280x1024_60+0+0"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) mouse0: Device: "/dev/input/mice"
(**) mouse0: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) mouse0: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Buttons" "7"
(**) Option "Emulate3Buttons" "true"
(**) mouse0: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) mouse0: ZAxisMapping: buttons 4 and 5
(**) Option "ButtonMapping" "1 2 3 6 7"
(**) mouse0: Buttons: 11
(II) XINPUT: Adding extended input device "mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc105)" };
(II) mouse0: ps2EnableDataReporting: succeeded

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]

Fatal server error:
Caught signal 11.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources

```

Here's my conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:56:12 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "mouse0"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice" 
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "7" 
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "IBM P260"
    HorizSync       30.0 - 121.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP MX70"
    HorizSync       30.0 - 70.0
    VertRefresh     47.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4200"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT-0: 2048x1536 +0+0; CRT-0: 1600x1200 +0+0; CRT-0: 1280x1024 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "CRT-1: 1280x1024_60 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

