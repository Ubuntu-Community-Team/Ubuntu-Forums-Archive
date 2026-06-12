---
title: "XOrg won't load on boot - but will after restarting"
date: 2009-01-03
forum: Desktop Environments
---

### Post by BlueNoteMKVI on 2009-01-03
I recently upgraded my machine from Hardy to Intrepid and I'm having some issues with the dual-screen setup in X.

Hardware:
Homebrewed Athlon 64 system.  The chip and motherboard are...who knows.  A K8 something or other, I think.  Was not top of the line when I bought it about 5 years ago.  Using the built-in sound and ethernet.
Generic CDROM burner bought from NewEgg several years ago
Generic DVD burner bought from a local shop a few years ago
Matrox Millenium P650 graphics card - capable of 3 outputs but I'm only using 2 of them.

This computer is my main work machine for web development - I don't need any eye candy or fast graphics, but the dual-screen setup is immensely helpful.I had dual-screen working well under Hardy.  I should've left well enough alone, I guess - silly me.  

I ran an apt upgrade through the KDE upgrade tool.  When the computer rebooted, the splash page came up, then was distorted with some horizontal green lines.  At that point I could not do anything with the machine.  Trying to switch to a text terminal (ctrl+alt+f1) did nothing.  Using my laptop I was able to SSH into the box but could not get my desktop back.

I did some looking and found that my graphics card is not supported by the latest xorg.  Apparently Matrox is terrible about Linux support (oops).  I had to downgrade to xorg 1.7.3, reinstall the mtx driver and tweak the xorg.conf.  Incidentally the outputs have apparently switched somehow, what was the left screen is now the right and vice versa.

Over the last several days I've tried a variety of things to get it back up and running.  Even disregarding the dual screens I could not get a desktop up on 8.10.  As a test I installed 8.04 to a second hard drive in the same box, after carefully tweaking my xorg.conf file I was able to get my dual screens working again.  On a whim, I copied that xorg.conf back to the 8.10 hard drive and rebooted.  On boot the same thing happened, splash screen, then distortion with horizontal lines, then nothing.  SSH still worked.
 I opened the xorg.conf to tweak it, don't recall making any changes - but when I restarted KDM (in order to restart X) it came up correctly:
```
/etc/init.d/kdm restart
```
Thinking that was done, I went about my business.  Next time I rebooted the computer, same thing - splash screen with horizontal lines.  I logged in from my laptop via SSH, restarted KDM and it came up just fine.  I can repeat this behavior very reliably.

Looking at the xorg log files I don't see much that helps me troubleshoot, maybe someone here can help out.  Comparing them side by side I see the usual output about loading modules, fonts, etc.  In the GOOD log file I see a PCI scan that isn't in the bad file.  This would lead me to believe that maybe something is stopping X from loading before the PCI scan happens (something that wouldn't show up in the logs?) or that somehow X is starting before the graphics card is completely ready and drivers loaded.  Looking in dmesg and /var/log/messages I see NO log entries about the mtx driver at startup, but several log entries when I restart KDM.  As long as I have my laptop with me I can SSH in and restart KDM to get my desktop back.  While that's a short-term workaround it's not a valid long-term solution.

Relevant log files and conf files are below.  What's my next step to troubleshoot this?

From Xorg.0.log - immediately after booting, I copied the Xorg.0.log to a different directory, then restarted KDM (which overwrites any existing Xorg.0.log in the /var/log/ directory).  This section is in both Xorg.0.log files, exactly the same except for the timestamp.

```


This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux coltrane 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan  3 11:19:24 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Display 1" (0)
(**) |   |-->Monitor "Philips 190B 1"
(**) |   |-->Device "Matrox P750 1"
(**) |-->Screen "Display 2" (1)
(**) |   |-->Monitor "Philips 190B 2"
(**) |   |-->Device "Matrox P750 3"
(**) Option "Xinerama" "on"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7
```

The following output is only in the good file (the one that results in a usable desktop).
  
```
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0755 card 1019,1891 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0002 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1019,1891 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1019,1891 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1019,1891 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1019,1891 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 1019,1891 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1019,1891 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1019,1891 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0180 card 1019,1891 rev 01 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10ec,8139 card 16ec,00ff rev 10 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 102b,2537 card 102b,1820 rev 02 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000e (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) Matrox Graphics, Inc. Millenium P650/P750 rev 2, Mem @ 0xe8000000/26, 0xec000000/13
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe7ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xee025000 - 0xee0250ff (0x100) MX[B]
	[1] -1	0	0xee023000 - 0xee023fff (0x1000) MX[B]
	[2] -1	0	0xee022000 - 0xee022fff (0x1000) MX[B]
	[3] -1	0	0xee021000 - 0xee021fff (0x1000) MX[B]
	[4] -1	0	0xee020000 - 0xee020fff (0x1000) MX[B]
	[5] -1	0	0xee024000 - 0xee024fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xec000000 - 0xec001fff (0x2000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[9] -1	0	0x0000e900 - 0x0000e9ff (0x100) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[11] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[12] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[13] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[15] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[16] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[17] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xee025000 - 0xee0250ff (0x100) MX[B]
	[1] -1	0	0xee023000 - 0xee023fff (0x1000) MX[B]
	[2] -1	0	0xee022000 - 0xee022fff (0x1000) MX[B]
	[3] -1	0	0xee021000 - 0xee021fff (0x1000) MX[B]
	[4] -1	0	0xee020000 - 0xee020fff (0x1000) MX[B]
	[5] -1	0	0xee024000 - 0xee024fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xec000000 - 0xec001fff (0x2000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[9] -1	0	0x0000e900 - 0x0000e9ff (0x100) IX[B]
	[10] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[11] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[12] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[13] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[15] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[16] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[17] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
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
	[4] -1	0	0xee025000 - 0xee0250ff (0x100) MX[B]
	[5] -1	0	0xee023000 - 0xee023fff (0x1000) MX[B]
	[6] -1	0	0xee022000 - 0xee022fff (0x1000) MX[B]
	[7] -1	0	0xee021000 - 0xee021fff (0x1000) MX[B]
	[8] -1	0	0xee020000 - 0xee020fff (0x1000) MX[B]
	[9] -1	0	0xee024000 - 0xee024fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xec000000 - 0xec001fff (0x2000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e900 - 0x0000e9ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[17] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[18] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[19] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[22] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[23] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[25] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="Matrox Graphics Inc. - x86_32 - Release v1.4.6 - Mar 12 23:47:26 2008"
	compiled for 1.4.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mtx"
(II) Loading /usr/lib/xorg/modules/drivers//mtx_drv.so
(II) Module mtx: vendor="Matrox Graphics Inc. - x86_32 - Release v1.4.6 - Mar 12 22:23:51 2008"
	compiled for 7.3.0, module version = 1.4.6
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) Loading extension MTXGamma
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) MTX: Driver for Matrox chipsets: P-Series Family A, P-Series Family B,
	P-Series Family C, P-Series Family D, P-Series Family E
(II) Primary Device is: PCI 01:00:0
(--) Chipset P-Series Family C found
(--) Chipset P-Series Family C found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xee025000 - 0xee0250ff (0x100) MX[B]
	[5] -1	0	0xee023000 - 0xee023fff (0x1000) MX[B]
	[6] -1	0	0xee022000 - 0xee022fff (0x1000) MX[B]
	[7] -1	0	0xee021000 - 0xee021fff (0x1000) MX[B]
	[8] -1	0	0xee020000 - 0xee020fff (0x1000) MX[B]
	[9] -1	0	0xee024000 - 0xee024fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xec000000 - 0xec001fff (0x2000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000e900 - 0x0000e9ff (0x100) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[17] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[18] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[19] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[22] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[23] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[25] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xee025000 - 0xee0250ff (0x100) MX[B]
	[5] -1	0	0xee023000 - 0xee023fff (0x1000) MX[B]
	[6] -1	0	0xee022000 - 0xee022fff (0x1000) MX[B]
	[7] -1	0	0xee021000 - 0xee021fff (0x1000) MX[B]
	[8] -1	0	0xee020000 - 0xee020fff (0x1000) MX[B]
	[9] -1	0	0xee024000 - 0xee024fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xec000000 - 0xec001fff (0x2000) MX[B](B)
	[12] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e900 - 0x0000e9ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[20] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[21] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[22] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[25] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[26] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[28] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(--) MTX(0): Linear framebuffer at 0xE8000000
(--) MTX(0): MMIO registers at 0xEC000000
(II) MTX(0): BIOS at 0xC0000
(II) MTX(0): Device Id [2537] Subsys Id [1820]
(II) MTX(0): Device Name [P750 64MB]
(--) MTX(0): Total Video RAM: 65536 kByte
(==) MTX(0): Write-combining range (0xe8000000,0x4000000)
(**) MTX(0): Depth 16, (--) framebuffer bpp 16
(==) MTX(0): Default visual is TrueColor
(**) MTX(0): Depth 16, (--) framebuffer bpp 16
(==) MTX(0): Default visual is TrueColor
(==) MTX(0): RGB weight 565
(**) MTX(0): Option "THI" "on"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) MTX(0): Initializing int10
(II) MTX(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) MTX(0): MTX Monitor info: 0x9364c18
(II) MTX(0): Manufacturer: PTS  Model: 6a5  Serial#: 16843009
(II) MTX(0): Year: 2006  Week: 51
(II) MTX(0): EDID Version: 1.3
(II) MTX(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) MTX(0): Sync:  Separate
(II) MTX(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) MTX(0): Gamma: 2.50
(II) MTX(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MTX(0): First detailed timing is preferred mode
(II) MTX(0): redX: 0.630 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) MTX(0): blueX: 0.148 blueY: 0.098   whiteX: 0.310 whiteY: 0.330
(II) MTX(0): Supported VESA Video Modes:
(II) MTX(0): 720x400@70Hz
(II) MTX(0): 640x480@60Hz
(II) MTX(0): 640x480@67Hz
(II) MTX(0): 640x480@72Hz
(II) MTX(0): 640x480@75Hz
(II) MTX(0): 800x600@56Hz
(II) MTX(0): 800x600@60Hz
(II) MTX(0): 800x600@72Hz
(II) MTX(0): 800x600@75Hz
(II) MTX(0): 832x624@75Hz
(II) MTX(0): 1024x768@60Hz
(II) MTX(0): 1024x768@70Hz
(II) MTX(0): 1024x768@75Hz
(II) MTX(0): 1280x1024@75Hz
(II) MTX(0): Manufacturer's mask: 0
(II) MTX(0): Supported Future Video Modes:
(II) MTX(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MTX(0): Supported additional Video Mode:
(II) MTX(0): clock: 108.0 MHz   Image Size:  337 x 270 mm
(II) MTX(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) MTX(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) MTX(0): Supported additional Video Mode:
(II) MTX(0): clock: 78.8 MHz   Image Size:  337 x 270 mm
(II) MTX(0): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) MTX(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) MTX(0): Ranges: V min: 60  V max: 75 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) MTX(0): Serial No: F6EU6C092598U
(II) MTX(0): EDID (in hex):
(II) MTX(0): 	00ffffffffffff004293a50601010101
(II) MTX(0): 	3310010308221b96ea6e06a1544c9926
(II) MTX(0): 	194f54bfef0081800101010101010101
(II) MTX(0): 	010101010101302a009851002a403070
(II) MTX(0): 	1300510e1100001ec31e002041002030
(II) MTX(0): 	10601300510e11000000000000fd003c
(II) MTX(0): 	4b1e500e000a202020202020000000ff
(II) MTX(0): 	00463645553643303932353938550028
(II) MTX(0): EDID vendor "PTS", prod id 1701
(II) MTX(0): DDCModeFromDetailedTiming: 1024x768 Warning: We only handle seperate sync.
(II) MTX(0): Using hsync ranges from config file
(II) MTX(0): Using vrefresh ranges from config file
(II) MTX(0): Printing DDC gathered Modelines:
(II) MTX(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MTX(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
(II) MTX(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MTX(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) MTX(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MTX(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) MTX(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) MTX(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MTX(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MTX(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MTX(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) MTX(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) MTX(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MTX(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) MTX(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MTX(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) MTX(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) MTX(0): end of MTX Monitor info
(II) MTX(0): Monitor maximum supported pixel clock is 140 MHz
(II) MTX(0): Monitor Input Type = 1
(==) MTX(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) MTX(0): Acceleration is enabled
(WW) MTX(0): Using software cursor
(II) MTX(0): -- Using monitors max pixel clock to verify modes.     --
(II) MTX(0): -- To override use 'Option "OCC"' in the device section. --
(II) MTX(0): Philips 190B 1: Using hsync range of 31.00-80.00 kHz
(II) MTX(0): Philips 190B 1: Using vrefresh range of 60.00-75.00 Hz
(II) MTX(0): Philips 190B 1: Using maximum pixel clock of 140.00 MHz
(II) MTX(0): Clock range:  12.00 to 140.00 MHz
(II) MTX(0): Not using default mode "640x350" (vrefresh out of range)
(II) MTX(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x400" (vrefresh out of range)
(II) MTX(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "720x400" (vrefresh out of range)
(II) MTX(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x480" (vrefresh out of range)
(II) MTX(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "800x600" (vrefresh out of range)
(II) MTX(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "800x600" (vrefresh out of range)
(II) MTX(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MTX(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MTX(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1792x1344" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1792x1344" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1856x1392" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1856x1392" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1152x768" (vrefresh out of range)
(II) MTX(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1152x864" (vrefresh out of range)
(II) MTX(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1400x1050" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1400x1050" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1400x1050" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1400x1050" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1440x900" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1600x1024" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1680x1050" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1920x1200" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1920x1200" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) MTX(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MTX(0): Not using driver mode "800x600" (vrefresh out of range)
(**) MTX(0): Display dimensions: (340, 270) mm
(**) MTX(0): DPI set to (95, 96)
(--) MTX(0): Virtual size is 1280x1024 (pitch 2048)
(**) MTX(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MTX(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MTX(0): Total Memory for Onscreen and Offscreen : 0x3c0000
(II) MTX(0): Cursor Offset at 0x00000000
(II) MTX(0): Cursor Aperture at 0x00000000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) MTX(0): Busmastering is enabled
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(--) MTX(1): Linear framebuffer at 0xE8000000
(--) MTX(1): MMIO registers at 0xEC000000
(II) MTX(1): BIOS at 0xC0000
(II) MTX(1): Device Id [2537] Subsys Id [1820]
(II) MTX(1): Device Name [P750 64MB]
(--) MTX(1): Total Video RAM: 65536 kByte
(**) MTX(1): Depth 16, (--) framebuffer bpp 16
(==) MTX(1): Default visual is TrueColor
(**) MTX(1): Depth 16, (--) framebuffer bpp 16
(==) MTX(1): Default visual is TrueColor
(==) MTX(1): RGB weight 565
(**) MTX(1): Option "THI" "on"
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) MTX(1): MTX Monitor info: 0x9366c58
(II) MTX(1): Manufacturer: PTS  Model: 6a5  Serial#: 16843009
(II) MTX(1): Year: 2006  Week: 51
(II) MTX(1): EDID Version: 1.3
(II) MTX(1): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) MTX(1): Sync:  Separate
(II) MTX(1): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) MTX(1): Gamma: 2.50
(II) MTX(1): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MTX(1): First detailed timing is preferred mode
(II) MTX(1): redX: 0.630 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) MTX(1): blueX: 0.148 blueY: 0.098   whiteX: 0.310 whiteY: 0.330
(II) MTX(1): Supported VESA Video Modes:
(II) MTX(1): 720x400@70Hz
(II) MTX(1): 640x480@60Hz
(II) MTX(1): 640x480@67Hz
(II) MTX(1): 640x480@72Hz
(II) MTX(1): 640x480@75Hz
(II) MTX(1): 800x600@56Hz
(II) MTX(1): 800x600@60Hz
(II) MTX(1): 800x600@72Hz
(II) MTX(1): 800x600@75Hz
(II) MTX(1): 832x624@75Hz
(II) MTX(1): 1024x768@60Hz
(II) MTX(1): 1024x768@70Hz
(II) MTX(1): 1024x768@75Hz
(II) MTX(1): 1280x1024@75Hz
(II) MTX(1): Manufacturer's mask: 0
(II) MTX(1): Supported Future Video Modes:
(II) MTX(1): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MTX(1): Supported additional Video Mode:
(II) MTX(1): clock: 108.0 MHz   Image Size:  337 x 270 mm
(II) MTX(1): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) MTX(1): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) MTX(1): Supported additional Video Mode:
(II) MTX(1): clock: 78.8 MHz   Image Size:  337 x 270 mm
(II) MTX(1): h_active: 1024  h_sync: 1040  h_sync_end 1136 h_blank_end 1312 h_border: 0
(II) MTX(1): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 800 v_border: 0
(II) MTX(1): Ranges: V min: 60  V max: 75 Hz, H min: 30  H max: 80 kHz, PixClock max 140 MHz
(II) MTX(1): Serial No: F6EU6C092606U
(II) MTX(1): EDID (in hex):
(II) MTX(1): 	00ffffffffffff004293a50601010101
(II) MTX(1): 	3310010308221b96ea6e06a1544c9926
(II) MTX(1): 	194f54bfef0081800101010101010101
(II) MTX(1): 	010101010101302a009851002a403070
(II) MTX(1): 	1300510e1100001ec31e002041002030
(II) MTX(1): 	10601300510e11000000000000fd003c
(II) MTX(1): 	4b1e500e000a202020202020000000ff
(II) MTX(1): 	00463645553643303932363036550032
(II) MTX(1): EDID vendor "PTS", prod id 1701
(II) MTX(1): DDCModeFromDetailedTiming: 1024x768 Warning: We only handle seperate sync.
(II) MTX(1): Using hsync ranges from config file
(II) MTX(1): Using vrefresh ranges from config file
(II) MTX(1): Printing DDC gathered Modelines:
(II) MTX(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MTX(1): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
(II) MTX(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MTX(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) MTX(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MTX(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) MTX(1): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) MTX(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MTX(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MTX(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MTX(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) MTX(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) MTX(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MTX(1): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) MTX(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MTX(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) MTX(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) MTX(1): end of MTX Monitor info
(II) MTX(1): Monitor maximum supported pixel clock is 140 MHz
(II) MTX(1): Monitor Input Type = 1
(==) MTX(1): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(II) MTX(1): Acceleration is enabled
(WW) MTX(1): Using software cursor
(II) MTX(1): -- Using monitors max pixel clock to verify modes.     --
(II) MTX(1): -- To override use 'Option "OCC"' in the device section. --
(II) MTX(1): Philips 190B 2: Using hsync range of 31.00-80.00 kHz
(II) MTX(1): Philips 190B 2: Using vrefresh range of 60.00-75.00 Hz
(II) MTX(1): Philips 190B 2: Using maximum pixel clock of 140.00 MHz
(II) MTX(1): Clock range:  12.00 to 140.00 MHz
(II) MTX(1): Not using default mode "640x350" (vrefresh out of range)
(II) MTX(1): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x400" (vrefresh out of range)
(II) MTX(1): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "720x400" (vrefresh out of range)
(II) MTX(1): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x480" (vrefresh out of range)
(II) MTX(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "800x600" (vrefresh out of range)
(II) MTX(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "800x600" (vrefresh out of range)
(II) MTX(1): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1024x768" (vrefresh out of range)
(II) MTX(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1024x768" (vrefresh out of range)
(II) MTX(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1600x1200" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1792x1344" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1792x1344" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1856x1392" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1856x1392" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1152x768" (vrefresh out of range)
(II) MTX(1): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1152x864" (vrefresh out of range)
(II) MTX(1): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1400x1050" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1400x1050" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1400x1050" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1400x1050" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1440x900" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1600x1024" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1680x1050" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1920x1200" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1920x1200" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "1920x1440" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) MTX(1): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MTX(1): Not using driver mode "800x600" (vrefresh out of range)
(**) MTX(1): Display dimensions: (340, 270) mm
(**) MTX(1): DPI set to (95, 96)
(--) MTX(1): Virtual size is 1280x1024 (pitch 2048)
(**) MTX(1): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MTX(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) MTX(1): Total Memory for Onscreen and Offscreen : 0x3c0000
(II) MTX(1): Cursor Offset at 0x00000000
(II) MTX(1): Cursor Aperture at 0x00000000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(II) MTX(1): Busmastering is enabled
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xec000000 - 0xec001fff (0x2000) MX[B]
	[1] 0	0	0xe8000000 - 0xebffffff (0x4000000) MX[B]
	[2] 0	0	0xec000000 - 0xec001fff (0x2000) MX[B]
	[3] 0	0	0xe8000000 - 0xebffffff (0x4000000) MX[B]
	[4] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xee025000 - 0xee0250ff (0x100) MX[B]
	[9] -1	0	0xee023000 - 0xee023fff (0x1000) MX[B]
	[10] -1	0	0xee022000 - 0xee022fff (0x1000) MX[B]
	[11] -1	0	0xee021000 - 0xee021fff (0x1000) MX[B]
	[12] -1	0	0xee020000 - 0xee020fff (0x1000) MX[B]
	[13] -1	0	0xee024000 - 0xee024fff (0x1000) MX[B]
	[14] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[15] -1	0	0xec000000 - 0xec001fff (0x2000) MX[B](B)
	[16] -1	0	0xe8000000 - 0xebffffff (0x4000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000e900 - 0x0000e9ff (0x100) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e87f (0x80) IX[B]
	[24] -1	0	0x0000e700 - 0x0000e70f (0x10) IX[B]
	[25] -1	0	0x0000e600 - 0x0000e603 (0x4) IX[B]
	[26] -1	0	0x0000e500 - 0x0000e507 (0x8) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[28] -1	0	0x0000e300 - 0x0000e307 (0x8) IX[B]
	[29] -1	0	0x0000e200 - 0x0000e2ff (0x100) IX[B]
	[30] -1	0	0x0000e100 - 0x0000e17f (0x80) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[32] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) MTX(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) MTX(0): Cannot read colourmap from VGA.  Will restore with default
(WW) MTX(0): Cannot stop Matrox xform.
(WW) MTX(0): Error occured while starting the Matrox xform.
(II) MTX(0): Cursor Aperture location 0x680000.
(II) MTX(0): Cursor Surface location 0x1f60000.
(II) MTX(0): Parhelia device started.
(==) MTX(0): Default visual is TrueColor
(II) MTX(0): Using 512 lines for offscreen memory.
(II) MTX(0): Memory manager initialized to (0,0) (1280,1536)
(II) MTX(0): Largest offscreen area available: 1280 x 512
(II) MTX(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
	Driver provided FillSolidSpans replacement
	Driver provided WritePixmap replacement
	Driver provided ReadPixmap replacement
	Setting up tile and stipple cache:
		20 128x128 slots
		5 256x256 slots
(==) MTX(0): Backing store disabled
(==) MTX(0): Silken mouse enabled
(II) MTX(0): Using SW cursor
(**) Option "dpms"
(**) MTX(0): DPMS enabled
(II) MTX(0): Using blitting for video
(==) RandR enabled
(II) MTX(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) MTX(1): Cannot stop Matrox xform.
(WW) MTX(1): Error occured while starting the Matrox xform.
(II) MTX(1): Cursor Aperture location 0x680000.
(II) MTX(1): Cursor Surface location 0x1f60000.
(II) MTX(1): Parhelia device started.
(==) MTX(1): Default visual is TrueColor
(II) MTX(1): Using 512 lines for offscreen memory.
(II) MTX(1): Memory manager initialized to (0,0) (1280,1536)
(II) MTX(1): Largest offscreen area available: 1280 x 512
(II) MTX(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
	Driver provided FillSolidSpans replacement
	Driver provided WritePixmap replacement
	Driver provided ReadPixmap replacement
	Setting up tile and stipple cache:
		20 128x128 slots
		5 256x256 slots
(==) MTX(1): Backing store disabled
(==) MTX(1): Silken mouse enabled
(II) MTX(1): Using SW cursor
(**) Option "dpms"
(**) MTX(1): DPMS enabled
(II) MTX(1): Using blitting for video
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) LoadModule: "evdev"
(WW) Warning, couldn't open module evdev
(II) UnloadModule: "evdev"
(EE) Failed to load module "evdev" (module does not exist, 0)
(EE) No input driver matching `evdev'
(II) LoadModule: "evdev"
(WW) Warning, couldn't open module evdev
(II) UnloadModule: "evdev"
(EE) Failed to load module "evdev" (module does not exist, 0)
(EE) No input driver matching `evdev'
(II) LoadModule: "evdev"
(WW) Warning, couldn't open module evdev
(II) UnloadModule: "evdev"
(EE) Failed to load module "evdev" (module does not exist, 0)
(EE) No input driver matching `evdev'
```

Here's the relevant output from dmesg and /var/log/messages.  The timestamps indicate that these log entries came only after restarting KDM, not when it was originally started at bootup.

```

chris@coltrane:/var/log/Xorg.tmp$ grep mtx /var/log/messages                                          
                                               


Jan  3 11:19:25 coltrane kernel: [  103.133686] mtx: module license 'Copyright (c) 2002, 2004, Matrox Graphics Inc.' taints kernel.                  
Jan  3 11:19:25 coltrane kernel: [  103.138509] [mtx] Unofficial MTX driver v1.4.6.2 by tuxx-home.at                                                 
Jan  3 11:19:25 coltrane kernel: [  103.139633] [mtx] Allocated a MTX agp driver structure                                                           
Jan  3 11:19:25 coltrane kernel: [  103.140666] mtx 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                         
Jan  3 11:19:25 coltrane kernel: [  103.141762] [mtx] 0x2537(sub:0xffffffff) board found at 01:00.0                                                  
Jan  3 11:19:26 coltrane kernel: [  103.949004] [mtx] Registers at 0xec000000, size: 8K, flags: 131584, knl_addr: 0xf8ccc000                         
Jan  3 11:19:26 coltrane kernel: [  103.949398] [mtx] Framebuffer at 0xe8000000, size: 64M, flags: 135688, knl_addr: 0x00000000, write-combining: YES
Jan  3 11:19:26 coltrane kernel: [  103.949405] [mtx] Enabling AGP: agp_status: 0xff00020b                                                           
Jan  3 11:19:26 coltrane kernel: [  103.950410] mtx 0000:01:00.0: putting AGP V3 device into 8x mode                                                 
Jan  3 11:19:26 coltrane kernel: [  103.955206] [mtx] AGP aperture at 0xe0000000, size: 131072K, rate: 8X, write-combining: YES                      
Jan  3 11:19:26 coltrane kernel: [  103.955212] [mtx] Busmastering flags:                                                                            
Jan  3 11:19:26 coltrane kernel: [  103.955214] [mtx]   Board type detected: AGP                                                                     
Jan  3 11:19:26 coltrane kernel: [  103.955216] [mtx]   Chipset 0x2537:0x102b was detected                                                           
Jan  3 11:19:26 coltrane kernel: [  103.955218] [mtx]   ISA chipset was detected                                                                     
Jan  3 11:19:26 coltrane kernel: [  103.955220] [mtx]   AGP chipset was detected                                                                     
Jan  3 11:19:26 coltrane kernel: [  103.955222] [mtx]   PCI transfers available for read write
Jan  3 11:19:26 coltrane kernel: [  103.955224] [mtx]   AGP transfers available
Jan  3 11:19:26 coltrane kernel: [  103.955226] [mtx]   AGP serialize is used
Jan  3 11:19:26 coltrane kernel: [  103.961602] [mtx] Parhelia patches applied: PowerM Cap66Mhz CompBypass
Jan  3 11:19:26 coltrane kernel: [  103.962713] [mtx] Registers at 0xec000000, size: 8K, flags: 131584, knl_addr: 0xf8ccc000
Jan  3 11:19:26 coltrane kernel: [  103.963851] [mtx] Framebuffer at 0xe8000000, size: 64M, flags: 135688, knl_addr: 0x00000000, write-combining: YES
Jan  3 11:19:26 coltrane kernel: [  103.963858] [mtx] Enabling AGP: agp_status: 0xff00020b
Jan  3 11:19:26 coltrane kernel: [  103.963899] mtx 0000:01:00.0: putting AGP V3 device into 8x mode
Jan  3 11:19:26 coltrane kernel: [  103.968653] [mtx] AGP aperture at 0xe0000000, size: 131072K, rate: 8X, write-combining: YES
Jan  3 11:19:26 coltrane kernel: [  103.968659] [mtx] Busmastering flags:
Jan  3 11:19:26 coltrane kernel: [  103.968661] [mtx]   Board type detected: AGP
Jan  3 11:19:26 coltrane kernel: [  103.968663] [mtx]   Chipset 0x2537:0x102b was detected
Jan  3 11:19:26 coltrane kernel: [  103.968665] [mtx]   ISA chipset was detected
Jan  3 11:19:26 coltrane kernel: [  103.968667] [mtx]   AGP chipset was detected
Jan  3 11:19:26 coltrane kernel: [  103.968669] [mtx]   PCI transfers available for read write
Jan  3 11:19:26 coltrane kernel: [  103.968671] [mtx]   AGP transfers available
Jan  3 11:19:26 coltrane kernel: [  103.968673] [mtx]   AGP serialize is used
Jan  3 11:19:26 coltrane kernel: [  103.975106] [mtx] Parhelia patches applied: PowerM Cap66Mhz CompBypass
chris@coltrane:/var/log/Xorg.tmp$ dmesg | grep mtx
[  103.133686] mtx: module license 'Copyright (c) 2002, 2004, Matrox Graphics Inc.' taints kernel.
[  103.138509] [mtx] Unofficial MTX driver v1.4.6.2 by tuxx-home.at
[  103.139633] [mtx] Allocated a MTX agp driver structure
[  103.140666] mtx 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  103.141762] [mtx] 0x2537(sub:0xffffffff) board found at 01:00.0
[  103.949004] [mtx] Registers at 0xec000000, size: 8K, flags: 131584, knl_addr: 0xf8ccc000
[  103.949398] [mtx] Framebuffer at 0xe8000000, size: 64M, flags: 135688, knl_addr: 0x00000000, write-combining: YES
[  103.949405] [mtx] Enabling AGP: agp_status: 0xff00020b
[  103.950410] mtx 0000:01:00.0: putting AGP V3 device into 8x mode
[  103.955206] [mtx] AGP aperture at 0xe0000000, size: 131072K, rate: 8X, write-combining: YES
[  103.955212] [mtx] Busmastering flags:
[  103.955214] [mtx]   Board type detected: AGP
[  103.955216] [mtx]   Chipset 0x2537:0x102b was detected
[  103.955218] [mtx]   ISA chipset was detected
[  103.955220] [mtx]   AGP chipset was detected
[  103.955222] [mtx]   PCI transfers available for read write
[  103.955224] [mtx]   AGP transfers available
[  103.955226] [mtx]   AGP serialize is used
[  103.961602] [mtx] Parhelia patches applied: PowerM Cap66Mhz CompBypass
[  103.962713] [mtx] Registers at 0xec000000, size: 8K, flags: 131584, knl_addr: 0xf8ccc000
[  103.963851] [mtx] Framebuffer at 0xe8000000, size: 64M, flags: 135688, knl_addr: 0x00000000, write-combining: YES
[  103.963858] [mtx] Enabling AGP: agp_status: 0xff00020b
[  103.963899] mtx 0000:01:00.0: putting AGP V3 device into 8x mode
[  103.968653] [mtx] AGP aperture at 0xe0000000, size: 131072K, rate: 8X, write-combining: YES
[  103.968659] [mtx] Busmastering flags:
[  103.968661] [mtx]   Board type detected: AGP
[  103.968663] [mtx]   Chipset 0x2537:0x102b was detected
[  103.968665] [mtx]   ISA chipset was detected
[  103.968667] [mtx]   AGP chipset was detected
[  103.968669] [mtx]   PCI transfers available for read write
[  103.968671] [mtx]   AGP transfers available
[  103.968673] [mtx]   AGP serialize is used
[  103.975106] [mtx] Parhelia patches applied: PowerM Cap66Mhz CompBypass
chris@coltrane:/var/log/Xorg.tmp$

```

Here is my xorg.conf file.  This is an amalgam of the file that the mtx driver install generated for me and the conf file from my 8.04 install:

```
# xorg.conf (X.Org X Window System server configuration file)
#                                                            
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.                                         
#                                                                           
# Edit this file with caution, and see the xorg.conf manual page.           
# (Type "man xorg.conf" at the shell prompt.)                               
#                                                                           
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg    
# package.                                                                  
#                                                                           
# If you have edited this file but would like it to be automatically updated
# again, run the following command:                                         
#   sudo dpkg-reconfigure -phigh xserver-xorg                               
Section "Module"                                                            
        Load    "bitmap"                                                    
        Load    "dbe"                                                       
        Load    "ddc"                                                       
        Load    "dri"                                                       
        Load    "extmod"                                                    
        Load    "freetype"                                                  
        Load    "glx"                                                       
        Load    "int10"                                                     
        Load    "record"                                                    
        Load    "vbe"                                                       
EndSection                                                                  

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"             
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"   
EndSection                                     

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"           
        Option          "CorePointer"     
EndSection                                

Section "Device"
        Identifier      "Matrox P750 1"
        Driver          "mtx"          
        BusID           "PCI:1:0:0"    
        Option "THI" "on"              
        Screen 0                       
EndSection                             

Section "Device"
        Identifier      "Matrox P750 2"
        Driver          "mtx"          
        BusID           "PCI:1:0:0"    
        Option "THI" "on"              
        Screen          2              
EndSection                             

Section "Device"
        Identifier      "Matrox P750 3"
        Driver          "mtx"          
        BusID           "PCI:1:0:0"    
        Option "THI" "on"              
        Screen          1              
EndSection                             

Section "Monitor"
        Identifier      "Philips 190B 1"
        VendorName      "PHL"           
        Option          "DPMS"          
        HorizSync    31.0 - 80.0        
        VertRefresh  60.0 - 75.0        
EndSection                              

Section "Monitor"
        Identifier      "Philips 190B 2"
        VendorName      "PHL"           
        Option          "DPMS"          
        HorizSync    31.0 - 80.0        
        VertRefresh  60.0 - 75.0        
EndSection                              

Section "Screen"
        Identifier      "Display 1"
        Device          "Matrox P750 1"
        Monitor         "Philips 190B 1"
        DefaultDepth    16              
        SubSection "Display"            
                Depth           1       
                Modes           "1280x1024"
        EndSubSection                      
        SubSection "Display"               
                Depth           4          
                Modes           "1280x1024"
        EndSubSection                      
        SubSection "Display"               
                Depth           8          
                Modes           "1280x1024"
        EndSubSection                      
        SubSection "Display"               
                Depth           15         
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection
Section "Screen"
        Identifier      "Display 2"
        Device          "Matrox P750 3"
        Monitor         "Philips 190B 2"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Display 1" 0 0
        Screen          "Display 2" RightOf "Display 1"
        Option          "xinerama" "on"
EndSection

Section "DRI"
        Mode    0666
EndSection


```

---

