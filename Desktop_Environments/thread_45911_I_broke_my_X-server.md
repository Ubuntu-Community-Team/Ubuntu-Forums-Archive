---
title: "I broke my X-server"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Firli on 2005-07-02
erm....I broke my x-server. Well, I updated to hoary by changing all the packet-sources and then updating, next time I restarted it was broken, didn't start. Said something about an error with the x-server, and whether I wished to get more info, wich I didn't get (I guess the ok-button didn't work).

I'm on windows now. I can still get in command line, any package I should try to reinstall? (with aptitude, I don't know any other command line package handler except getting it with aptget and installing manually)

I tried reinstalling x-server-common but it didn't help.

---

### Post by Xian on 2005-07-02
The first thing I would try is just reconfiguring X.
If that doesn't work you might post your /etc/X11/xorg.conf file.
```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Firli on 2005-07-02
I just tried it... I reconfigured some stuff (mainly using autodetect). It seemed okay, but it still doesn't start.

Thanks for the advice though, it might be interesting for future stuff :).

---

### Post by varunus on 2005-07-02
Can you post your /etc/X11/xorg.conf and your /var/log/Xorg.0.log?

---

### Post by Firli on 2005-07-02
**/var/log/Xorg.0.log:**

X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux Sartek 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 16:53:01 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul  2 22:06:02 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "PHILIPS 107S"
(**) |   |-->Device "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "be"
(**) XKB: layout: "be"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,
/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0691 card 0000,0000 rev c4 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8598 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0686 card 1106,0000 rev 22 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 0000,0000 rev 10 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3038 card 0925,1234 rev 10 class 0c,03,00 hdr 00
(II) PCI: 00:07:4: chip 1106,3057 card 0000,0000 rev 30 class 06,80,00 hdr 00
(II) PCI: 00:07:5: chip 1106,3058 card 1106,4511 rev 20 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 13f6,0111 card 13f6,0111 rev 10 class 04,01,00 hdr 00
(II) PCI: 00:0a:0: chip 1033,0035 card 1033,0035 rev 43 class 0c,03,10 hdr 80
(II) PCI: 00:0a:1: chip 1033,0035 card 1033,0035 rev 43 class 0c,03,10 hdr 00
(II) PCI: 00:0a:2: chip 1033,00e0 card 0ee4,3383 rev 04 class 0c,03,20 hdr 00
(II) PCI: 00:0b:0: chip 1011,0009 card 0000,0000 rev 22 class 02,00,00 hdr 00
(II) PCI: 00:0c:0: chip 10ec,8029 card 1186,0300 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,002d card 0000,0000 rev 15 class 03,00,00 hdr 00
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
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] rev 21, Mem @ 0xd4000000/24, 0xd2000000/25
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd1ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd7002000 - 0xd70021ff (0x200) MX[B]
	[1] -1	0	0xd7001000 - 0xd70010ff (0x100) MX[B]
	[2] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[3] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[6] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000ddff (0x200) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[12] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd7002000 - 0xd70021ff (0x200) MX[B]
	[1] -1	0	0xd7001000 - 0xd70010ff (0x100) MX[B]
	[2] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[3] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[6] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[7] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[8] -1	0	0x0000dc00 - 0x0000ddff (0x200) IX[B]
	[9] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[10] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[11] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[12] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[13] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[14] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[15] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd7002000 - 0xd70021ff (0x200) MX[B]
	[6] -1	0	0xd7001000 - 0xd70010ff (0x100) MX[B]
	[7] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[8] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000ddff (0x200) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7174
	Module class: XFree86 Server Extension
	ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nvidia"
(II) Loading /usr/X11R6/lib/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.7174
	Module class: XFree86 Video Driver
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7174  Tue Mar 22 06:48:37 PST 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd7002000 - 0xd70021ff (0x200) MX[B]
	[6] -1	0	0xd7001000 - 0xd70010ff (0x100) MX[B]
	[7] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[8] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000ddff (0x200) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[18] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xd7002000 - 0xd70021ff (0x200) MX[B]
	[6] -1	0	0xd7001000 - 0xd70010ff (0x100) MX[B]
	[7] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[8] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[11] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000ddff (0x200) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD2000000
(--) NVIDIA(0): MMIO registers at 0xD4000000
(II) NVIDIA(0): NVIDIA GPU detected as: RIVA TNT2 Model 64/Model 64 Pro
(--) NVIDIA(0): VideoBIOS: 02.05.17.03.00
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 0X
(--) NVIDIA(0): VideoRAM: 32768 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 250 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 250 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 215 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(WW) NVIDIA(0): Failure reading EDID parameters for display device CRT-0
(II) NVIDIA(0): PHILIPS 107S: Using default hsync range of 28.00-33.00 kHz
(II) NVIDIA(0): PHILIPS 107S: Using default vrefresh range of 43.00-72.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 215.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x175" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x400" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "720x400" (hsync out of range)
(II) NVIDIA(0): Not using default mode "360x200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x240" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x240" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "320x240" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "400x300" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "832x624" (hsync out of range)
(II) NVIDIA(0): Not using default mode "416x312" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x800" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x400" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1440x900" (hsync out of range)
(II) NVIDIA(0): Not using default mode "720x450" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using mode "1280x1024" (no mode of this name)
(II) NVIDIA(0): Not using mode "1152x864" (no mode of this name)
(II) NVIDIA(0): Not using mode "1024x768" (no mode of this name)
(II) NVIDIA(0): Not using mode "832x624" (no mode of this name)
(II) NVIDIA(0): Not using mode "800x600" (no mode of this name)
(II) NVIDIA(0): Not using mode "720x400" (no mode of this name)
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(==) NVIDIA(0): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
	[1] 0	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xd7002000 - 0xd70021ff (0x200) MX[B]
	[8] -1	0	0xd7001000 - 0xd70010ff (0x100) MX[B]
	[9] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[10] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B](B)
	[13] -1	0	0xd4000000 - 0xd4ffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[20] -1	0	0x0000dc00 - 0x0000ddff (0x200) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d403 (0x4) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d003 (0x4) IX[B]
	[24] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[26] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "640x480"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used
(==) RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
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

---

### Post by Firli on 2005-07-02
**/etc/X11/xorg.conf:**

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"PHILIPS 107S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"PHILIPS 107S"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Xian on 2005-07-02
Let's try and narrow this down by eliminating some possibilities.
Open your xorg.conf file and change the Driver to "vesa".

Restart X or reboot and post back with changes.

```
Section "Device"
Identifier "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
[color=red]Driver "vesa"[/color]
BusID "PCI:1:0:0"
Option "UseFBDev" "true"
EndSection
```

---

### Post by Omnios on 2005-07-02
According to the latest nvidia read me "dri" should be commented out this was causing a configration problem with my system and helped a bit! probably wont solve your problem though!

---

### Post by Quest-Master on 2005-07-02
If all else fails, do this.

sudo rm -rf /etc/X11/X

If you are able to rename /etc/X11/X to /etc/X11/X.backup first though, that'd be better. I wasn't able to though as I was getting I/O errors, so a simple complete removal of the file fixed everything.

---

### Post by Firli on 2005-07-03
Thanks Xian, it starts again :). The view kinda changed, but I updated to hoary just before it stopped working so I guess this is the new view.

And thanks Omnius and Quest-Master, I'll keep your advice in mind for future problems :).

btw, what's this vesa driver? (I'm just curious)

---

### Post by Xian on 2005-07-03
[QUOTE=Firli]Thanks Xian, it starts again :). The view kinda changed, but I updated to hoary just before it stopped working so I guess this is the new view.

btw, what's this vesa driver? (I'm just curious)[/QUOTE]
My working theory before telling you to make that last change was that you had upgraded your kernel and in the process your nvidia drivers had not been properly configured. So, by using the 'vesa' (which is a general setting that contains no hardware acceleration) entry you were in effect bypassing all of that, and at the same time allowing me to see if we could determine the specific cause of your problem.

Now that you have discovered that the nvidia driver is not configured for your new kernel, you may want to go about reinstalling that according to the [starter guide](http://ubuntuguide.org/#installnvidiadriver). Just be sure to install the linux-restricted-modules that match your linux-image before starting the process.

---

### Post by Firli on 2005-07-04
Yup, I noticed it was the general setting when I tried to play a movie.

Thanks for the link with instructions, works like a charm now :). Excepting that it did give an error during the configuration of the driver: on postfix (not configured), on at, on postfix-tls, on mutt and mailx because they depends on postfix and on exim4 (not installed).
I don't know if the errors pose any real problem 'cause everything seems to work fine.

Thanks again for all your help :).

---

