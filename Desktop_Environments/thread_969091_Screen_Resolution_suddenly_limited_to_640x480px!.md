---
title: "Screen Resolution suddenly limited to 640x480px?!"
date: 2008-11-03
forum: Desktop Environments
---

### Post by Weissbier on 2008-11-03
Hi, something strange happened today.
Im using Ubuntu 8.04 X86_64 without problems, having installed the Nvidia Drivers for my GeeForce 9600GT a few days ago (wanted to get rid of the cooling-noise).
Since then i have made NO changes to anything in Ubuntu, no apt-get updates/upgrades whatsoever.

But as i started today the system, there came a strange error message before i could enter the Desktop, that they couldn't find the Nvidia Drivers for GLX anymore.
Also screen resolution was suddenly fixed to 640.x480 and my graphics-card was making much cooling-noise(100% fan speed) so i was sure the drivers aren't loaded.

So i downloaded the same drivers again, and installed them. Installer said they were already installed but get overwritten.
After intalled and starting G-Nome again, driver-stuff was working again, but i still can not choose higher resolution than 640x480 - on a 24" Screen.

Lofile G-Nome:
```
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  3 11:56:10 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(II) Module "ddc" already built-in
(WW) VESA(0): Failed to set up write-combining range (0xe5c00000,0x200000)
(WW) VESA(0): Failed to set up write-combining range (0xe5800000,0x600000)
(WW) VESA(0): Failed to set up write-combining range (0xe5000000,0xe00000)
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
SetClientVersion: 0 9
```

Logfile x-server:
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
Current Operating System: Linux christian-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64
Build Date: 13 June 2008  01:10:57AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  3 12:14:26 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
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

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2e20 card 1458,5000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2e21 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,3a37 card 1458,5004 rev 00 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,3a38 card 1458,5004 rev 00 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,3a39 card 1458,5004 rev 00 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,3a3c card 1458,5006 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,3a3e card 1458,a002 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,3a40 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,3a46 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,3a48 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,3a34 card 1458,5004 rev 00 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,3a35 card 1458,5004 rev 00 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,3a36 card 1458,5004 rev 00 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,3a3a card 1458,5006 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 90 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,3a16 card 1458,5001 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,3a22 card 1458,b005 rev 00 class 01,06,01 hdr 00
(II) PCI: 00:1f:3: chip 8086,3a30 card 1458,5001 rev 00 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0622 card 10de,0545 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1458,b000 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1458,b000 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 10ec,8168 card 1458,e000 rev 02 class 02,00,00 hdr 00
(II) PCI: 05:07:0: chip 104c,8024 card 1458,1000 rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xe9000000 - 0xe90fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:4), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe8ffffff (0x1000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xe9100000 - 0xe91fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xe9200000 - 0xe92fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0622) rev 161, Mem @ 0xe6000000/24, 0xd0000000/28, 0xe4000000/25, I/O @ 0xb000/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xe9200000 - 0xe9203fff (0x4000) MX[B]
	[1] -1	0	0xe9204000 - 0xe92047ff (0x800) MX[B]
	[2] -1	0	0xe9100000 - 0xe910ffff (0x10000) MX[B]
	[3] -1	0	0xe9110000 - 0xe9110fff (0x1000) MX[B]
	[4] -1	0	0xe9000000 - 0xe9001fff (0x2000) MX[B]
	[5] -1	0	0xe9307000 - 0xe93070ff (0x100) MX[B]
	[6] -1	0	0xe9306000 - 0xe93067ff (0x800) MX[B]
	[7] -1	0	0xe9304000 - 0xe93043ff (0x400) MX[B]
	[8] -1	0	0xe9300000 - 0xe9303fff (0x4000) MX[B]
	[9] -1	0	0xe9305000 - 0xe93053ff (0x400) MX[B]
	[10] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[15] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[16] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[17] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[20] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[21] -1	0	0x0000e900 - 0x0000e903 (0x4) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[23] -1	0	0x0000e700 - 0x0000e703 (0x4) IX[B]
	[24] -1	0	0x0000e600 - 0x0000e607 (0x8) IX[B]
	[25] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[29] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[30] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe9200000 - 0xe9203fff (0x4000) MX[B]
	[1] -1	0	0xe9204000 - 0xe92047ff (0x800) MX[B]
	[2] -1	0	0xe9100000 - 0xe910ffff (0x10000) MX[B]
	[3] -1	0	0xe9110000 - 0xe9110fff (0x1000) MX[B]
	[4] -1	0	0xe9000000 - 0xe9001fff (0x2000) MX[B]
	[5] -1	0	0xe9307000 - 0xe93070ff (0x100) MX[B]
	[6] -1	0	0xe9306000 - 0xe93067ff (0x800) MX[B]
	[7] -1	0	0xe9304000 - 0xe93043ff (0x400) MX[B]
	[8] -1	0	0xe9300000 - 0xe9303fff (0x4000) MX[B]
	[9] -1	0	0xe9305000 - 0xe93053ff (0x400) MX[B]
	[10] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[15] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[16] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[17] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[19] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[20] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[21] -1	0	0x0000e900 - 0x0000e903 (0x4) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[23] -1	0	0x0000e700 - 0x0000e703 (0x4) IX[B]
	[24] -1	0	0x0000e600 - 0x0000e607 (0x8) IX[B]
	[25] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[28] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[29] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[30] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[31] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
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
	[4] -1	0	0xe9200000 - 0xe9203fff (0x4000) MX[B]
	[5] -1	0	0xe9204000 - 0xe92047ff (0x800) MX[B]
	[6] -1	0	0xe9100000 - 0xe910ffff (0x10000) MX[B]
	[7] -1	0	0xe9110000 - 0xe9110fff (0x1000) MX[B]
	[8] -1	0	0xe9000000 - 0xe9001fff (0x2000) MX[B]
	[9] -1	0	0xe9307000 - 0xe93070ff (0x100) MX[B]
	[10] -1	0	0xe9306000 - 0xe93067ff (0x800) MX[B]
	[11] -1	0	0xe9304000 - 0xe93043ff (0x400) MX[B]
	[12] -1	0	0xe9300000 - 0xe9303fff (0x4000) MX[B]
	[13] -1	0	0xe9305000 - 0xe93053ff (0x400) MX[B]
	[14] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[22] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[23] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[26] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[27] -1	0	0x0000e900 - 0x0000e903 (0x4) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[29] -1	0	0x0000e700 - 0x0000e703 (0x4) IX[B]
	[30] -1	0	0x0000e600 - 0x0000e607 (0x8) IX[B]
	[31] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[33] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[35] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[36] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  177.80  Wed Oct  1 15:09:29 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  177.80  Wed Oct  1 14:50:00 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9200000 - 0xe9203fff (0x4000) MX[B]
	[5] -1	0	0xe9204000 - 0xe92047ff (0x800) MX[B]
	[6] -1	0	0xe9100000 - 0xe910ffff (0x10000) MX[B]
	[7] -1	0	0xe9110000 - 0xe9110fff (0x1000) MX[B]
	[8] -1	0	0xe9000000 - 0xe9001fff (0x2000) MX[B]
	[9] -1	0	0xe9307000 - 0xe93070ff (0x100) MX[B]
	[10] -1	0	0xe9306000 - 0xe93067ff (0x800) MX[B]
	[11] -1	0	0xe9304000 - 0xe93043ff (0x400) MX[B]
	[12] -1	0	0xe9300000 - 0xe9303fff (0x4000) MX[B]
	[13] -1	0	0xe9305000 - 0xe93053ff (0x400) MX[B]
	[14] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[20] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[21] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[22] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[23] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[24] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[25] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[26] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[27] -1	0	0x0000e900 - 0x0000e903 (0x4) IX[B]
	[28] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[29] -1	0	0x0000e700 - 0x0000e703 (0x4) IX[B]
	[30] -1	0	0x0000e600 - 0x0000e607 (0x8) IX[B]
	[31] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[32] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[33] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[35] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[36] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[37] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9200000 - 0xe9203fff (0x4000) MX[B]
	[5] -1	0	0xe9204000 - 0xe92047ff (0x800) MX[B]
	[6] -1	0	0xe9100000 - 0xe910ffff (0x10000) MX[B]
	[7] -1	0	0xe9110000 - 0xe9110fff (0x1000) MX[B]
	[8] -1	0	0xe9000000 - 0xe9001fff (0x2000) MX[B]
	[9] -1	0	0xe9307000 - 0xe93070ff (0x100) MX[B]
	[10] -1	0	0xe9306000 - 0xe93067ff (0x800) MX[B]
	[11] -1	0	0xe9304000 - 0xe93043ff (0x400) MX[B]
	[12] -1	0	0xe9300000 - 0xe9303fff (0x4000) MX[B]
	[13] -1	0	0xe9305000 - 0xe93053ff (0x400) MX[B]
	[14] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[25] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[26] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[29] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[30] -1	0	0x0000e900 - 0x0000e903 (0x4) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[32] -1	0	0x0000e700 - 0x0000e703 (0x4) IX[B]
	[33] -1	0	0x0000e600 - 0x0000e607 (0x8) IX[B]
	[34] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.94.11.00.04
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:1:0:0:
(--) NVIDIA(0):     NTS MB24W (DFP-1)
(--) NVIDIA(0): NTS MB24W (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): NTS MB24W (DFP-1): Internal Dual Link TMDS
(WW) NVIDIA(0): The EDID for NTS MB24W (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1600x1200" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid HorizSync range (30.000-74.000 kHz) would exclude
(WW) NVIDIA(0):     this mode's HorizSync (75.0 kHz); ignoring HorizSync check
(WW) NVIDIA(0):     for mode "1600x1200".
(WW) NVIDIA(0): The EDID for NTS MB24W (DFP-1) contradicts itself: mode
(WW) NVIDIA(0):     "1600x1200" is specified in the EDID; however, the EDID's
(WW) NVIDIA(0):     valid HorizSync range (30.000-74.000 kHz) would exclude
(WW) NVIDIA(0):     this mode's HorizSync (75.0 kHz); ignoring HorizSync check
(WW) NVIDIA(0):     for mode "1600x1200".
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "640x480@60"
(**) NVIDIA(0): Virtual screen size configured to be 640 x 480
(--) NVIDIA(0): DPI set to (31, 38); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9200000 - 0xe9203fff (0x4000) MX[B]
	[5] -1	0	0xe9204000 - 0xe92047ff (0x800) MX[B]
	[6] -1	0	0xe9100000 - 0xe910ffff (0x10000) MX[B]
	[7] -1	0	0xe9110000 - 0xe9110fff (0x1000) MX[B]
	[8] -1	0	0xe9000000 - 0xe9001fff (0x2000) MX[B]
	[9] -1	0	0xe9307000 - 0xe93070ff (0x100) MX[B]
	[10] -1	0	0xe9306000 - 0xe93067ff (0x800) MX[B]
	[11] -1	0	0xe9304000 - 0xe93043ff (0x400) MX[B]
	[12] -1	0	0xe9300000 - 0xe9303fff (0x4000) MX[B]
	[13] -1	0	0xe9305000 - 0xe93053ff (0x400) MX[B]
	[14] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xe6000000 - 0xe6ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[24] -1	0	0x0000c300 - 0x0000c303 (0x4) IX[B]
	[25] -1	0	0x0000c200 - 0x0000c207 (0x8) IX[B]
	[26] -1	0	0x0000c100 - 0x0000c103 (0x4) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[28] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[29] -1	0	0x0000ea00 - 0x0000ea1f (0x20) IX[B]
	[30] -1	0	0x0000e900 - 0x0000e903 (0x4) IX[B]
	[31] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[32] -1	0	0x0000e700 - 0x0000e703 (0x4) IX[B]
	[33] -1	0	0x0000e600 - 0x0000e607 (0x8) IX[B]
	[34] -1	0	0x0000e500 - 0x0000e51f (0x20) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[36] -1	0	0x0000e300 - 0x0000e31f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x0000e200 - 0x0000e21f (0x20) IX[B]
	[39] -1	0	0x0000e100 - 0x0000e11f (0x20) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B](B)
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "640x480@60"
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(II) 3rd Button detected: disabling emulate3Button
```

What can i do? Its very annoying in that resolution....

---

### Post by Weissbier on 2008-12-01
[SIZE="1"]Can't anyone help me?
I can't even kill/stop x-server/gdm anymore.... 640x480 is really bad and i won't install linux again.

Linux is very very frustrating to use as a desktop OS.

Such stuff never happened with Windows for me (using it since Version 2), this whole driver thing must be made way more easy in order that Linux has a real chance at the common users.[/SIZE]
EDIT: Solved it with a few downparts.

What i restored is screen resolution and working nvidia drivers.

Downpart is suddenly english keyboard again

What i did:
1. Pressed CRTL+ALT+F1
2. typed ps-aux | grep "x"
3. typed ps-aux | grep "gdm"
4. killed every process pids from gdm and x
5. Let a default xorg.conf file created by entering "sudo dpkg-reconfigure -phigh xserver-xorg"
6. started Nvidia driver-install with "sudo sh NVIDIA-Linux-x86_64-177.82-pkg2.run@
7. Let Nvidia Installer create xorg.conf file aswell as OpenGL extension
8. Reboot and everything is working again...

However now i have only english keyboard, no matter how i set it in Ubuntu.
Any advice for me?

Thanks.

---

