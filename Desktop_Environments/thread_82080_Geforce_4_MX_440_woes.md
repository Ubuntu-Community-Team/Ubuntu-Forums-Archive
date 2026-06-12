---
title: "Geforce 4 MX 440 woes"
date: 2005-10-25
forum: Desktop Environments
---

### Post by vordrax on 2005-10-25
I'm working on my sister's PC, which has a Geforce MX 440. Mine has a Geforce 6800, so I figure I'll use the same techniques, right?

Wrong.

I read the "How to install Latest Nvidia Drivers" guide, same one I used for mine, and X is refusing to start on her PC. I tried GLX from Synaptic, doesn't work. I tried the legacy driver (7174 or whatever) even though it's not on the legacy list, no dice.

All I keep getting is a large grey-and-blue error screen, unless I run dpkg-reconfigure on the xserver and switch it back to "nv." I'm not sure where the log file is, or I'd copy and paste it here. I did notice that the error it had was "nVidia module cannot be loaded: No screens detected" or something of that nature.

This is irksome. It shouldn't take more to work than my 6800 (both should be supported by the unified drivers and by nvidia-glx, and mine is working perfectly after following the guide).

---

### Post by Moonbuzz on 2005-10-25
I have the exact same card, and those instructions worked for me.
After installing the nvidia-glx and nvidia-settings, run sudo dpkg-reconfigure xserver-xorg.

---

### Post by vordrax on 2005-10-26
I just did, Moonbuzz. Xserver refuses to start with the device set to "nvidia" and "dri" disabled. I'm stumped.

---

### Post by vordrax on 2005-10-27
Bump. Anyone have any ideas?

---

### Post by Pathogenix on 2005-10-27
Also running the same card, without problems. Is this the first time you've installed the drivers on that box, or did you reinstall over the old ones?

---

### Post by vordrax on 2005-10-27
This is the first time I've installed video card drivers on her PC. I installed the NForce drivers successfully (not video card drivers, of course, but it uses the same installer, and went off without a hitch.) I'm baffled.

---

### Post by GIBson3 on 2005-10-27
Could you post your xorg.conf and the Error that is being dumped via x.org's logs?

I had a simular problem, until I went hopping through the error logs. Compaired to the XF86 logs I'm used to x.org is a God send :D

---

### Post by Drakx on 2005-10-27
Hi What you need to do is install the nvidia-glx-legacy drivers then run sudo nvidia-glx-config enable.

---

### Post by vordrax on 2005-10-27
After going through the logs, I found out that she has a Geforce 4 MX 420, not a 440 (not sure if it makes a difference, driver-wise.) And she's running Hoary instead of Breezy. I'll need to upgrade her system to Breezy today.

Here's the log:

```
X Window System Version 6.8.2 (Ubuntu 6.8.2-10.1 20050831033957 root@)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux nikki 2.6.10-5-386 #1 Mon Oct 10 11:15:41 UTC 2005 i686
Build Date: 31 August 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Oct 10 11:15:41 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 27 12:14:27 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV17 [GeForce4 MX 420]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80ac rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 01:0a:0: chip 104c,8400 card 1186,3b01 rev 00 class 02,80,00 hdr 00
(II) PCI: 02:00:0: chip 10de,0172 card 1545,0035 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xec000000 - 0xedffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xebffffff (0x8000000) MX[B]
(--) PCI:*(2:0:0) nVidia Corporation NV17 [GeForce4 MX 420] rev 163, Mem @ 0xec000000/24, 0xe4000000/26, 0xe8000000/19
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xee000000 - 0xee00ffff (0x10000) MX[B]
	[1] -1	0	0xee010000 - 0xee010fff (0x1000) MX[B]
	[2] -1	0	0xef001000 - 0xef001fff (0x1000) MX[B]
	[3] -1	0	0xef000000 - 0xef000fff (0x1000) MX[B]
	[4] -1	0	0xef005000 - 0xef0050ff (0x100) MX[B]
	[5] -1	0	0xef004000 - 0xef004fff (0x1000) MX[B]
	[6] -1	0	0xef003000 - 0xef003fff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xee000000 - 0xee00ffff (0x10000) MX[B]
	[1] -1	0	0xee010000 - 0xee010fff (0x1000) MX[B]
	[2] -1	0	0xef001000 - 0xef001fff (0x1000) MX[B]
	[3] -1	0	0xef000000 - 0xef000fff (0x1000) MX[B]
	[4] -1	0	0xef005000 - 0xef0050ff (0x100) MX[B]
	[5] -1	0	0xef004000 - 0xef004fff (0x1000) MX[B]
	[6] -1	0	0xef003000 - 0xef003fff (0x1000) MX[B]
	[7] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[8] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[9] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
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
	[5] -1	0	0xee000000 - 0xee00ffff (0x10000) MX[B]
	[6] -1	0	0xee010000 - 0xee010fff (0x1000) MX[B]
	[7] -1	0	0xef001000 - 0xef001fff (0x1000) MX[B]
	[8] -1	0	0xef000000 - 0xef000fff (0x1000) MX[B]
	[9] -1	0	0xef005000 - 0xef0050ff (0x100) MX[B]
	[10] -1	0	0xef004000 - 0xef004fff (0x1000) MX[B]
	[11] -1	0	0xef003000 - 0xef003fff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[14] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
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
	compiled for 4.0.2, module version = 1.0.7667
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
	compiled for 4.0.2, module version = 1.0.7667
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
(II) NVIDIA X Driver  1.0-7667  Fri Jun 17 07:03:12 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xee000000 - 0xee00ffff (0x10000) MX[B]
	[6] -1	0	0xee010000 - 0xee010fff (0x1000) MX[B]
	[7] -1	0	0xef001000 - 0xef001fff (0x1000) MX[B]
	[8] -1	0	0xef000000 - 0xef000fff (0x1000) MX[B]
	[9] -1	0	0xef005000 - 0xef0050ff (0x100) MX[B]
	[10] -1	0	0xef004000 - 0xef004fff (0x1000) MX[B]
	[11] -1	0	0xef003000 - 0xef003fff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[14] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[19] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[21] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xee000000 - 0xee00ffff (0x10000) MX[B]
	[6] -1	0	0xee010000 - 0xee010fff (0x1000) MX[B]
	[7] -1	0	0xef001000 - 0xef001fff (0x1000) MX[B]
	[8] -1	0	0xef000000 - 0xef000fff (0x1000) MX[B]
	[9] -1	0	0xef005000 - 0xef0050ff (0x100) MX[B]
	[10] -1	0	0xef004000 - 0xef004fff (0x1000) MX[B]
	[11] -1	0	0xef003000 - 0xef003fff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[14] -1	0	0xe4000000 - 0xe7ffffff (0x4000000) MX[B](B)
	[15] -1	0	0xec000000 - 0xecffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```

EDIT: Forgot, here is her Xorg.conf (before I had to run dpkg-reconfigure on her PC):

```
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
	#Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
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
```

---

