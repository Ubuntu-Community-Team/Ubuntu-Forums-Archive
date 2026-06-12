---
title: "Latest xorg-core update broke X"
date: 2006-08-21
forum: Desktop Environments
---

### Post by anando on 2006-08-21
Hi

I updated xorg-core package when prompted by synaptic - now my X is broken. Has anybody else faced this problem ? Is there a way to go back to the previous version ?

Thanks,
Anando

---

### Post by chaosmx on 2006-08-21
I've gotten the same problem....I tried sudo dpkg-reconfigure xserver-xorg but it still doesn't work, Don't know what else to do.

---

### Post by hakune on 2006-08-21
same here no idea what broke

---

### Post by anando on 2006-08-21
I am sure this is a temporary problem and the bug fixed version will be rolled out soon. 

But *please hurry* - I got a paper to write :-k

---

### Post by jlx on 2006-08-21
Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

---

### Post by anando on 2006-08-21
Hi

Thanks a lot - I hope this fixes my xorg-core package. BTW - what is the latest (broken) xorg-core package version ?

- Anando.

---

### Post by oyvindaa on 2006-08-21
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.


I had the same problem, and your solution worked. Thanks!

---

### Post by oyvindaa on 2006-08-21
> **anando said:**
> Hi

Thanks a lot - I hope this fixes my xorg-core package. BTW - what is the latest (broken) xorg-core package version ?

- Anando.

1:1.0.2-0ubuntu10.3 isn't it?

---

### Post by evil_elman on 2006-08-21
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

Cheers for that!

Weird that an update messes up X in such a complete and efficient way... ;)

---

### Post by anando on 2006-08-21
> **oyvindaa said:**
> 1:1.0.2-0ubuntu10.3 isn't it?

Yes - that's what it is. I am glad that the solution given by jlx worked for me. Mondays - are bad for updates generally ;)

---

### Post by mlind on 2006-08-21
Could someone post a Xorg log that contains the error, so it could be attached to bug report?

---

### Post by abelthorne on 2006-08-21
> **mlind said:**
> Could someone post a Xorg log that contains the error, so it could be attached to bug report?

Where can this log be found ?

---

### Post by jlx on 2006-08-21
The log is in /var/log/Xorg.0.log

I have no error log. They were overwritten.
I remember that Xserver cannot find any screens. That was the error message I saw. That's all I can help. Not too much.:confused:

---

### Post by anodizer on 2006-08-21
```
X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux manolis 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 22 00:50:22 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: Found 0 domains.
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,006b card 1043,0c11 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0d:0: chip 10de,006e card 1043,809a rev a3 class 0c,00,10 hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x0000afff (0x2000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe3000000 - 0xe4ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x500fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xe1000000 - 0xe2ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xdfffffff (0x20000000) MX[B]
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
(II) PCI Memory resource overlap reduced 0xb0000000 from 0xbfffffff to 0xafffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe5085000 - 0xe508503f (0x40) MX[B]
	[1] -1	0	0xe5084000 - 0xe50847ff (0x800) MX[B]
	[2] -1	0	0xe5080000 - 0xe5080fff (0x1000) MX[B]
	[3] -1	0	0xe5000000 - 0xe507ffff (0x80000) MX[B]
	[4] -1	0	0xe5086000 - 0xe5086fff (0x1000) MX[B]
	[5] -1	0	0xe5083000 - 0xe50830ff (0x100) MX[B]
	[6] -1	0	0xe5082000 - 0xe5082fff (0x1000) MX[B]
	[7] -1	0	0xe5087000 - 0xe5087fff (0x1000) MX[B]
	[8] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe5085000 - 0xe508503f (0x40) MX[B]
	[1] -1	0	0xe5084000 - 0xe50847ff (0x800) MX[B]
	[2] -1	0	0xe5080000 - 0xe5080fff (0x1000) MX[B]
	[3] -1	0	0xe5000000 - 0xe507ffff (0x80000) MX[B]
	[4] -1	0	0xe5086000 - 0xe5086fff (0x1000) MX[B]
	[5] -1	0	0xe5083000 - 0xe50830ff (0x100) MX[B]
	[6] -1	0	0xe5082000 - 0xe5082fff (0x1000) MX[B]
	[7] -1	0	0xe5087000 - 0xe5087fff (0x1000) MX[B]
	[8] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[9] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[10] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[11] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
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
	[4] -1	0	0xe5085000 - 0xe508503f (0x40) MX[B]
	[5] -1	0	0xe5084000 - 0xe50847ff (0x800) MX[B]
	[6] -1	0	0xe5080000 - 0xe5080fff (0x1000) MX[B]
	[7] -1	0	0xe5000000 - 0xe507ffff (0x80000) MX[B]
	[8] -1	0	0xe5086000 - 0xe5086fff (0x1000) MX[B]
	[9] -1	0	0xe5083000 - 0xe50830ff (0x100) MX[B]
	[10] -1	0	0xe5082000 - 0xe5082fff (0x1000) MX[B]
	[11] -1	0	0xe5087000 - 0xe5087fff (0x1000) MX[B]
	[12] -1	0	0xb0000000 - 0xafffffff (0x0) MX[B]O
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 6.8.99.8, module version = 8.28.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9250/9200 Series (RV280 5961),
	RADEON 9250/9200 Series (RV280 5962),
	RADEON 9250/9200 Series (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 GTO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
	RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
	RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
	RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
	MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
	MOBILITY RADEON X700 XL (M26-XC 564F),
	RADEON 9000/9100 IGP Series (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000 IGP (RL300MB 7835),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
	RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
	RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1600 Series (RV515 7140), RADEON X1300 Series (RV515 7142),
	MOBILITY FireGL (M54 GL 7144), MOBILITY RADEON X1400 (M54 7145),
	RADEON X1300 Series (RV515 7146), MOBILITY RADEON X1300 (M52 7149),
	MOBILITY RADEON X1300 (M52 714A), RADEON X1300 Series (RV515 714D),
	RADEON X1300 Series (RV515 714E), FireGL V3300 (RV515 7152),
	RADEON X1300 Series (RV515 715E), RADEON X1300 (RV516 7180),
	RADEON X1600 Series (RV516 7181), RADEON X1300 (RV516 7183),
	MOBILITY RADEON X1450 (M64P 7186), RADEON X1300 (RV516 7187),
	MOBILITY RADEON X1350 (M62P 718B),
	MOBILITY RADEON X1350 (M62CSP 718C),
	MOBILITY RADEON X1450 (M64CSP 718D),
	MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
	RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
	RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
	RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
	RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
	RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
	RADEON X1900 (R580 724D), FireStream 2U (R580 724E),
	FireStream 2U (R580 724F), RADEON X1600 Series (RV530 71C0),
	RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
	MOBILITY RADEON X1600 (M56 71C5),
	RADEON X1600 Series (RV530 LE 71C6),
	RADEON X1600 Series (RV530 VE 71CE), FireGL V3400 (RV530 71D2),
	MOBILITY RADEON X1700 (M66-XT 71D6), FireGL V5200 (RV530 71DA),
	RADEON X1600 Series (RV530 SE 71DE), RADEON X1600 XT (RV535 XT 71C1),
	MOBILITY FireGL V5250 (M66GL 71D4),
	MOBILITY RADEON X1700 (M66-P 71D5), RADEON Xpress 1200 (RS600 7941),
	RADEON Xpress 1200 (RS600 7942)
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1                           
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:26:25
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161
[b](EE) No devices detected.

Fatal server error:
no screens found[/b]
```

---

### Post by abelthorne on 2006-08-21
It seems that I still have the log, but I don't know if it's really relevant. The only errors part at the end is this :
> (EE) No devices detected.

Fatal server error:
no screens found

On screen when trying to start X, it was followed by :
> XIO: fatal IO error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

---

### Post by logout on 2006-08-21
```

(II) VESA: driver for VESA chipsets: vesa
(EE) No devices detected.

Fatal server error:
no screens found

```

Me too.  I will try out the fix and see if it helps.

---

### Post by droogy on 2006-08-21
it's happened to me too... I suppose a lot of people will be mad about this one!  Luckily, I have my windows to check this forum!

---

### Post by shamrock_uk on 2006-08-21
Just adding a +1 voice here. Ouch, that's quite an update :)

---

### Post by unai_goiko on 2006-08-21
Same problem here ...

---

### Post by mgpower0 on 2006-08-21
same problem here, got this fix at work, now have to wait 10 hours to get home and try it.:(

---

### Post by thoffland on 2006-08-21
All I have to say is THANK YOU SO MUCH for figuring this out. Being a newbie, I didn't even know the update was for the xorg-core... I just did and apt-get update and it was broken. 

Thanks again... I love Ubuntu, but it's things like this that really make me nervous... especially since I've ditched Windows and my main Desktop is Ubuntu.

Here's my Xorg.0.log.old  I'm on 64bit

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 x86_64
Current Operating System: Linux Whoopass 2.6.15-26-amd64-generic #1 SMP PREEMPT Thu Aug 3 02:52:35 UTC 2006 x86_64
Build Date: 16 March 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 21 15:34:34 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL 2005FPW"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(--) using VT number 7

(II) PCI: Found 0 domains.
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,005e card 1458,5000 rev a3 class 05,80,00 hdr 00
(II) PCI: 00:01:0: chip 10de,0050 card 1458,0c11 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0052 card 1458,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,005a card 1458,5004 rev a2 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,005b card 1458,5004 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,0053 card 1458,5002 rev f2 class 01,01,8a hdr 00
(II) PCI: 00:07:0: chip 10de,0054 card 1458,b003 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:08:0: chip 10de,0055 card 1458,b003 rev f3 class 01,01,85 hdr 00
(II) PCI: 00:09:0: chip 10de,005c card 0000,0000 rev a2 class 06,04,01 hdr 01
(II) PCI: 00:0a:0: chip 10de,0057 card 1458,e000 rev a3 class 06,80,00 hdr 00
(II) PCI: 00:0b:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,005d card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: End of PCI scan
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:9:0), (0,1,1), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00008000 - 0x00008fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf5000000 - 0xf57fffff (0x800000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xf3000000 - 0xf4ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00006000 - 0x00006fff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00007000 - 0x00007fff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:14:0), (0,5,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xf0000000 - 0xf2ffffff (0x3000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
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
	[0] -1	0	0xf5801000 - 0xf5801fff (0x1000) MX[B]
	[1] -1	0	0xf5804000 - 0xf5804fff (0x1000) MX[B]
	[2] -1	0	0xf5803000 - 0xf5803fff (0x1000) MX[B]
	[3] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[4] -1	0	0xf5800000 - 0xf5800fff (0x1000) MX[B]
	[5] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[6] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[7] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[8] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[9] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[10] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[12] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[13] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[14] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[15] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[18] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf5801000 - 0xf5801fff (0x1000) MX[B]
	[1] -1	0	0xf5804000 - 0xf5804fff (0x1000) MX[B]
	[2] -1	0	0xf5803000 - 0xf5803fff (0x1000) MX[B]
	[3] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[4] -1	0	0xf5800000 - 0xf5800fff (0x1000) MX[B]
	[5] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[6] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[7] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[8] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[9] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[10] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[12] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[13] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[14] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[15] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[16] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[17] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[18] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
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
	[4] -1	0	0xf5801000 - 0xf5801fff (0x1000) MX[B]
	[5] -1	0	0xf5804000 - 0xf5804fff (0x1000) MX[B]
	[6] -1	0	0xf5803000 - 0xf5803fff (0x1000) MX[B]
	[7] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[8] -1	0	0xf5800000 - 0xf5800fff (0x1000) MX[B]
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[12] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[13] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[14] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[15] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[16] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[17] -1	0	0x0000c000 - 0x0000c00f (0x10) IX[B]
	[18] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[19] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[20] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[21] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x00001c40 - 0x00001c7f (0x40) IX[B]
	[24] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8762
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 GT, GeForce 6800 GT,
	GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000, GeForce 6800 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 XT, GeForce Go 6800,
	GeForce Go 6800 Ultra, Quadro FX Go1400, Quadro FX 3450/4000 SDI,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, GeForce 6600 LE,
	GeForce 6600 VE, GeForce Go 6600, GeForce 6610 XL,
	GeForce Go 6600 TE/6200 TE, GeForce 6700 XL, GeForce Go 6600,
	GeForce Go 6600 GT, Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 7800 GTX, GeForce 7800 GTX, GeForce 7800 GT, GeForce 7800 GS,
	GeForce 7800 SLI, GeForce Go 7800, GeForce Go 7800 GTX,
	Quadro FX 4500, GeForce 7300 LE, GeForce Go 7200, GeForce Go 7300,
	GeForce Go 7400, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	Quadro FX 350, GeForce 7300 GS, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, Quadro FX 550M, GeForce Go 7900 GS,
	GeForce Go 7900 GTX, Quadro FX 2500M, Quadro FX 1500M, GeForce 6150,
	GeForce 6150 LE, GeForce 6100, GeForce Go 6150, GeForce Go 6100
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by Martin down under on 2006-08-21
I have just been bitten by this problem as well](*,) . 

I applied the software update and a short while later the screen just locked up dead. No keyboard or mouse input whatsoever. On rebooting the machine got to the point where it would start X and would then it would just lock dead.

However, I was able to reboot the machine into recovery mode, and then with another machine search the Internet for the cause. And I found this thread.

Thank heavens the fix worked! And thank you to it's poster!.

Attached is my Xorg.0.log

---

### Post by Martin down under on 2006-08-21
I find myself wondering if this upgrade shouldn't be pulled pronto!. If I didn't have access to a second machine so that I could find this thread I would have been right royally fried...

---

### Post by Jax55 on 2006-08-21
Yay - Thanks jlx - Worked a treat.   That little update took down all my working machines (the perils of auto-updates!)

---

### Post by Jax55 on 2006-08-21
Btw - Lines from Xorg.0.log

This happened on 2 machines - One desktop and one laptop - Both ATI cards.
--

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux seville 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 22 08:40:43 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: Found 0 domains.
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3340 card 1014,0529 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,3341 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1014,052d rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1014,052d rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1014,052e rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 1014,052d rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1014,052d rev 01 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1014,0554 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:6: chip 8086,24c6 card 1014,055a rev 01 class 07,03,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc0100000 - 0xc01fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,10), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
	[4] -1	0	0x00005000 - 0x000050ff (0x100) IX[B]
	[5] -1	0	0x00005400 - 0x000054ff (0x100) IX[B]
	[6] -1	0	0x00005800 - 0x000058ff (0x100) IX[B]
	[7] -1	0	0x00005c00 - 0x00005cff (0x100) IX[B]
	[8] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[9] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[10] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[11] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
	[12] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[13] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[14] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[15] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
	[16] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[17] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[18] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[19] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xc0200000 - 0xcfffffff (0xfe00000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[1] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[2] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[3] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[6] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[7] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[8] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[9] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[10] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[1] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[2] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[3] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[4] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[5] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[6] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[7] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[8] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[9] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[10] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
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
	[4] -1	0	0xc0000800 - 0xc00008ff (0x100) MX[B]
	[5] -1	0	0xc0000c00 - 0xc0000dff (0x200) MX[B]
	[6] -1	0	0x70000000 - 0x700003ff (0x400) MX[B]
	[7] -1	0	0xc0000000 - 0xc00003ff (0x400) MX[B]
	[8] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x00002000 - 0x0000207f (0x80) IX[B]
	[12] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018ff (0x40) IX[B]
	[14] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[15] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[16] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[17] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[18] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[19] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 6.5.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) ATI: ATI driver (version 6.5.8) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
	ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 LF (AGP),
	ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 ML (AGP),
	ATI Rage 128 Pro GL PA (PCI/AGP), ATI Rage 128 Pro GL PB (PCI/AGP),
	ATI Rage 128 Pro GL PC (PCI/AGP), ATI Rage 128 Pro GL PD (PCI),
	ATI Rage 128 Pro GL PE (PCI/AGP), ATI Rage 128 Pro GL PF (AGP),
	ATI Rage 128 Pro VR PG (PCI/AGP), ATI Rage 128 Pro VR PH (PCI/AGP),
	ATI Rage 128 Pro VR PI (PCI/AGP), ATI Rage 128 Pro VR PJ (PCI/AGP),
	ATI Rage 128 Pro VR PK (PCI/AGP), ATI Rage 128 Pro VR PL (PCI/AGP),
	ATI Rage 128 Pro VR PM (PCI/AGP), ATI Rage 128 Pro VR PN (PCI/AGP),
	ATI Rage 128 Pro VR PO (PCI/AGP), ATI Rage 128 Pro VR PP (PCI),
	ATI Rage 128 Pro VR PQ (PCI/AGP), ATI Rage 128 Pro VR PR (PCI),
	ATI Rage 128 Pro VR PS (PCI/AGP), ATI Rage 128 Pro VR PT (PCI/AGP),
	ATI Rage 128 Pro VR PU (PCI/AGP), ATI Rage 128 Pro VR PV (PCI/AGP),
	ATI Rage 128 Pro VR PW (PCI/AGP), ATI Rage 128 Pro VR PX (PCI/AGP),
	ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
	ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
	ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (PCI/AGP),
	ATI Rage 128 4X SF (PCI/AGP), ATI Rage 128 4X SG (PCI/AGP),
	ATI Rage 128 4X SH (PCI/AGP), ATI Rage 128 4X SK (PCI/AGP),
	ATI Rage 128 4X SL (PCI/AGP), ATI Rage 128 4X SM (AGP),
	ATI Rage 128 4X SN (PCI/AGP), ATI Rage 128 Pro ULTRA TF (AGP),
	ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (AGP),
	ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT (AGP?),
	ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. M10 NT [FireGL Mobility T2]".
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by swj on 2006-08-21
FYI

You could have always used Lynx! 

joking-but I did have to use lynx to find this thread..it was interesting.

;)

---

### Post by tdell on 2006-08-21
> **anando said:**
> Hi

I updated xorg-core package when prompted by synaptic - now my X is broken. Has anybody else faced this problem ? Is there a way to go back to the previous version ?

Thanks,
Anando

I saw this update and prior experience told me NOT to apply it. So I avoided the problem you are having.

---

### Post by dids22 on 2006-08-21
what version have with her the this problem?

---

### Post by guyg on 2006-08-21
Thanks a lot jlx, you're a life saver!

---

### Post by mlind on 2006-08-21
> **dids22 said:**
> what version have with her the this problem?

xserver-xorg-core=1:1.0.2-0ubuntu10.3

---

### Post by genbie on 2006-08-21
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

Thanks a lot jlx :) 

I bet many others are having this problem too. The update notification icon should be disabled until the update is fixed!

---

### Post by maxbaggi on 2006-08-21
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

The latest update broke my X server too.  Thank you for posting a fix :grin:

---

### Post by mycelo on 2006-08-21
Well, what a fiasco. :mad: Fortunately I still have Windows installed, so I could go here and get a solution. I was about to get rid of M$ things, but I suddenly changed my mind.

mycelo

---

### Post by Ijump2 on 2006-08-21
Thanks a million jlx =D> 

I lost my Linux cherry just last Saturday and have spent more time fixing error messages than playing...

so what will tomorrow bring?

---

### Post by tribaal on 2006-08-21
Hehe thanks a lot, again.

I hate mondays for a reason ;)

- trib'

---

### Post by evilghost on 2006-08-21
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

Many thanks, I'm currently posting this from Lynx.  I had tried to downgrade the version but I was unable to determine the previous version.  You saved me headache, it didn't work with the nvidia or the nv driver.

---

### Post by eems01 on 2006-08-21
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

Thanks for the fix.

---

### Post by cleentrax on 2006-08-21
Well, I successfully downgraded, but that didn't fix things for me.  When I boot, I get the xorg reconfigure screen, and then it freezes, and a shell login prompt gets drawn on top of it. If I log in and do "startx" then I get the nvidia logo splash and then a blank screen. The "nv" driver just gets me an "xorg improperly configured" error message. I have tried dpkg-reconfigure, but no luck.

**** **** ****. How do I get X up and running again?

---

### Post by Uentsuru on 2006-08-21
Thanks!  I hit this error just a few hours ago and was afraid that I'd have to reformat to fix everything.  You are a life saver, sir/ma'am!

---

### Post by evilghost on 2006-08-21
> **cleentrax said:**
> Well, I successfully downgraded, but that didn't fix things for me.  When I boot, I get the xorg reconfigure screen, and then it freezes, and a shell login prompt gets drawn on top of it. If I log in and do "startx" then I get the nvidia logo splash and then a blank screen. The "nv" driver just gets me an "xorg improperly configured" error message. I have tried dpkg-reconfigure, but no luck.

**** **** ****. How do I get X up and running again?

Try this:

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10 --reinstall
sudo apt-get install nvidia-glx --reinstall

---

### Post by amgeex on 2006-08-21
Thanks a lot!!! How can I prevent the installing of any further xorg-core updates? :mrgreen:

---

### Post by jimrz on 2006-08-21
does that version # Oubuntu10 start with the capitol letter "O" or the number zero?

---

### Post by LeighT on 2006-08-21
The update has broken my Dapper box as well, I am using PCLinuxOS live cd to post this message.
I will try the recomended work around, I am sure that it will work.
Below is my XOrg log file;

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.15-26-k7 #1 SMP PREEMPT Thu Aug 3 03:40:32 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 22 18:44:08 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: Found 0 domains.
(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01ea card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,0), BCTRL: 0x0008 (VGA_EN is set)
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
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd6000000 - 0xd6ffffff (0x1000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xcfffffff (0x20000000) MX[B]
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
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd3ffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xd7001000 - 0xd7001fff (0x1000) MX[B]
	[1] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[2] -1	0	0xd7005000 - 0xd70050ff (0x100) MX[B]
	[3] -1	0	0xd7004000 - 0xd7004fff (0x1000) MX[B]
	[4] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[7] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[8] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[9] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xd7001000 - 0xd7001fff (0x1000) MX[B]
	[1] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[2] -1	0	0xd7005000 - 0xd70050ff (0x100) MX[B]
	[3] -1	0	0xd7004000 - 0xd7004fff (0x1000) MX[B]
	[4] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[5] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[6] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[7] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[8] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[9] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[10] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
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
	[4] -1	0	0xd7001000 - 0xd7001fff (0x1000) MX[B]
	[5] -1	0	0xd7000000 - 0xd7000fff (0x1000) MX[B]
	[6] -1	0	0xd7005000 - 0xd70050ff (0x100) MX[B]
	[7] -1	0	0xd7004000 - 0xd7004fff (0x1000) MX[B]
	[8] -1	0	0xd7003000 - 0xd7003fff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
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
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 6.99.99.904, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) Wacom driver level: 47-0.7.2 $
(II) VESA: driver for VESA chipsets: vesa
(EE) No devices detected.

Fatal server error:
no screens found
Regards
Leigh

---

### Post by kpkeerthi on 2006-08-21
its a zero

---

### Post by jimrz on 2006-08-21
> **kpkeerthi said:**
> its a zero

thanks 

EDIT: that worked, using reistall for both X and nvidia-glx...thank you all

---

### Post by astoltz on 2006-08-21
I'm just wondering if this has anything to do with Xgl / Compiz?  Who here has the Xserver problem but does NOT have Xgl / Compiz installed?

---

### Post by emperor on 2006-08-21
Broke my laplap :frown:, and network-manager hijacks the wireless so had to  edit "/etc/network/interfaces" and restart "/etc/init.d/networking" so I could downgrade xorg server via the internet. Thanks much for the information on how to downgrade and fix the xserver!!! =D>

---

### Post by evilghost on 2006-08-21
> **astoltz said:**
> I'm just wondering if this has anything to do with Xgl / Compiz?  Who here has the Xserver problem but does NOT have Xgl / Compiz installed?

No compiz here, I'm an Nvidia user and waiting for the inclusion of glx_from_pixmap without the need for mesa in 1.0.9XXX.  Broke mine and my fathers systems (I'm NVIDIA, he's ATI).

---

### Post by Xirto on 2006-08-21
Thanks for the fix! I had to find my liveCD, hehe!

---

### Post by compmodder26 on 2006-08-21
> **astoltz said:**
> I'm just wondering if this has anything to do with Xgl / Compiz?  Who here has the Xserver problem but does NOT have Xgl / Compiz installed?

I don't have XGL/Compiz and the upgrade broke my X server.

---

### Post by smbm on 2006-08-21
> **swj said:**
> FYI

You could have always used Lynx! 

joking-but I did have to use lynx to find this thread..it was interesting.

;)

I used Lynx too. I guess this just underlines the fact that it is useful to learn how to use the command line.

---

### Post by cleentrax on 2006-08-21
> **evilghost said:**
> Try this:

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10 --reinstall
sudo apt-get install nvidia-glx --reinstall

No luck. I'm still dead in the water. Thanks for trying to help me out.

---

### Post by pross on 2006-08-21
> **astoltz said:**
> I'm just wondering if this has anything to do with Xgl / Compiz?  Who here has the Xserver problem but does NOT have Xgl / Compiz installed?

I have no Xgl just a standard xorg install with i810 driver..no problems with the update here...

---

### Post by evilghost on 2006-08-21
> **cleentrax said:**
> No luck. I'm still dead in the water. Thanks for trying to help me out.

Can you share your /var/log/Xorg.0.log?

---

### Post by SishGupta on 2006-08-21
Man, thanks so much to the guy who came up with the solution. I got the update at the same time that i started my installation of xgl and compiz and i thought that it was xgl/compiz's fault.

Anyway i am rather new to linux and i had no idea how to fix the solution. Luckily the live cd is the most brilliant piece of work ever and that is how i am reading the forums.

ill let you know if your solution worked in a sec...

edit: yup it worked. thanks jlx

---

### Post by kblood on 2006-08-21
Same problem here. I was able to try the joys of lynx and links2... Maybe it would be quite an idea to get links2 working in graphics mode for the next time... :)

By the way, I have an Nvidia card on a Sony Vaio VGN FS315M laptop, no XGL/Compiz.

So the issue is not related to XGL/Compiz.

Does anybody have a link to the bug in Launchpad?
I hope the maintainer has been notified already!

---

### Post by mojoguy on 2006-08-21
Thanks.  Had the same problem.  Was faced with the ugly prospect of having to start from scratch or tinker with vi and the config file until  I made things even worse.  ;P

I hope they fix the package soon.  

For the record, I have an ATI Rage Mobility in an old Compaq laptop.

---

### Post by evilghost on 2006-08-21
> **kblood said:**
> Does anybody have a link to the bug in Launchpad?
I hope the maintainer has been notified already!

[https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153)

---

### Post by martinrandau on 2006-08-21
This doesn't work for me. I had a fresh install and after upgraded the X server right upon first boot. From there on I was stuck. I'm currently re-installing and will not do the same upgrade again until a newer/patched version is out.

Never mind...

---

### Post by peabody on 2006-08-21
> **pross said:**
> I have no Xgl just a standard xorg install with i810 driver..no problems with the update here...

This is confirming my theory that this latest xserver-xorg-core update breaks proprietary drivers.  To my knowledge, the i810 uses an open source driver.

This is definitely one of those sticky situations.  The proprietary drivers can't really be supported by Canonical/Ubuntu officially, but so many people desperately need to use them.

---

### Post by Thund3rstruck on 2006-08-21
same thing happened on my Acer laptop, if these forums weren't around it may just have pissed me off enough to stop aggressibly working with Linux. I have become a huge advocate in the last few months but this really rattles me.

---

### Post by peabody on 2006-08-21
Well, my theory's shot.  Several people not running proprietary drivers have had their X blow up.  Weird.

For those who want to pin xserver-xorg-core from ever updating again:

[http://www.ubuntuforums.org/showpost.php?p=1406821&postcount=15](http://www.ubuntuforums.org/showpost.php?p=1406821&postcount=15)

---

### Post by azmrb on 2006-08-21
Thanks to checking and seeing this thread I have NOT installed the update because I am sure it will break mine too.  Thumbs up for ubuntu forum users

Now, this is a major fubar of an update.  I wonder how many new linux users will just give up and go back to windows because of this.  Better testing before pushing out these updates is going to have to be mandatory.

---

### Post by janbockaert on 2006-08-21
Thanks, after rolling back the x-server, x is back, but i'm unable to run nvidia-glx-config enable. ( i can run it, but it doesn't do anything) anyone an idea how i get my nvidia-glx driver back? (and compiz and xgl)

---

### Post by dmery on 2006-08-21
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.
Thanks for your help,=D> 
Regards,
dmery

---

### Post by jackkerouac on 2006-08-21
>  Originally Posted by jlx  View Post
Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

Dude, you rock.

I had to completely reboot however, as Compiz didn't work properly until I did.

I also locked the xserver-core so it wouldn't be 'updated.'

Sigh, I think this update needed to be beta'd a little more before release.

---

### Post by neymac on 2006-08-21
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

It worked fine, thank you.

---

### Post by mengfei on 2006-08-21
Haha, I was wondering why my reformat and reinstall of Ubuntu kept doing that after I downloaded the updates...

Thanks!

---

### Post by peabody on 2006-08-21
> **mengfei said:**
> Haha, I was wondering why my reformat and reinstall of Ubuntu kept doing that after I downloaded the updates...

Thanks!


Yes, my goodness!  Now must be a very bad time to perform an Install + Update of Ubuntu ;)

---

### Post by twistedwrench on 2006-08-21
Well for me it didn't work to fix X; I have to login on a failsafe session to get my stuff back the way I had it, AND I HAVE to be root for some stupid reason. Here;s a copy of my xorg:
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
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier "Dual Head Layout"
Screen "Screen 0" RightOf "Screen 1"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"

# path to defoma fonts
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"

# (the DGA extension is broken in the fglrx driver)
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "GLcore"
# Load "extmod" but omit DGA extension
SubSection "extmod"
Option "omit xfree86-dga"
EndSubSection
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Protocol" "ExplorerPS/2"
Option "Emulate3Buttons" "false"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"

# /dev/input/event
# for USB
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/wacom" # Change to
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Monitor"
Identifier "Xerox LCD"
HorizSync 31.0 - 65.0
VertRefresh 56.0 - 76.0
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Alphascan Monitor"
HorizSync 29.0 - 69.0
VertRefresh 55.0 - 70.0
Option "DPMS"
EndSection

Section "Device"

# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
#Option "NoDDC"
# === Video Overlay for the Xv extension ===
# Note: When OpenGL Overlay is enabled, Video Overlay
# will be disabled automatically
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
Identifier "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
Driver "fglrx"
Option "VideoOverlay" "on"
# === OpenGL Overlay ===
Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
Option "UseInternalAGPGART" "no"
Option "DesktopSetup" "horizontal,reverse"
BusID "PCI:1:0:0"
Screen 0
EndSection

Section "Device"

# If X refuses to use the screen resolution you asked for,
# uncomment this; see "Bugs and Workarounds" for details.
#Option "NoDDC"
# === Video Overlay for the Xv extension ===
# Note: When OpenGL Overlay is enabled, Video Overlay
# will be disabled automatically
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
Identifier "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro](Secondary)"
Driver "fglrx"
Option "VideoOverlay" "on"
# === OpenGL Overlay ===
Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
Option "UseInternalAGPGART" "no"
BusID "PCI:1:0:1"
Screen 1
EndSection

Section "Screen"
Identifier "Screen 0"
Device "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
Monitor "Xerox LCD"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Screen 1"
Device "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro](Secondary)"
Monitor "Alphascan Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "DRI"
Mode 0666
EndSection


Maybe someone can help here...I would appreciate it.

Also this is the kind of CRAP that makes people go back to windows!!!!
'end rant'

Thx\

---

### Post by cleentrax on 2006-08-21
Ack! Still not working for me. Am I the only one? 

With the nvidia driver, I get the nvidia splash, and then a blank screen. With the nv driver, I get a string of errors starting with "unable to find valid framebuffer device" and ending with "no available screen."

Any ideas?

---

### Post by cleentrax on 2006-08-21
> **evilghost said:**
> Can you share your /var/log/Xorg.0.log?

Not sure how. I can't get to that portion of the drive from Windows, and I don't know how to post a file using Lynx.

---

### Post by cleentrax on 2006-08-21
> **twistedwrench said:**
> 

Also this is the kind of CRAP that makes people go back to windows!!!!
'end rant'

Thx\

No kidding. Imagine the kind of grief Microsoft would get, if an automatic Windows update hosed your Windows install! If it wasn't for this forum, I would have given up on Ubuntu a long time ago.

---

### Post by remin8 on 2006-08-21
I love you guys and UBUNTU! can anyone else deliver up to the minute help like this?

---

### Post by peabody on 2006-08-21
> **cleentrax said:**
> No kidding. Imagine the kind of grief Microsoft would get, if an automatic Windows update hosed your Windows install! If it wasn't for this forum, I would have given up on Ubuntu a long time ago.

Oh my friend I have quite a few stories of that very thing happening (I worked as a Programmer/Tech for a University department for four years).  Admittedly, in most scenarios, it's due to the machine being riddled with virus'/spyware, but regardless, it worked before the update and shattered after it.  At least apt allows easy downgrades!  Updates in Windows are a one-way street.

---

### Post by fbi agent on 2006-08-21
> **cleentrax said:**
> Imagine the kind of grief Microsoft would get, if an automatic Windows update hosed your Windows install!

That's actually happened, many times.

Thanks to this thread I'm back up and running.:grin: 

Dell Inspiron 5100 with an ATI Radeon 7000

---

### Post by cleentrax on 2006-08-21
> **fbi agent said:**
> That's actually happened, many times.

Thanks to this thread I'm back up and running.:grin: 

Dell Inspiron 5100 with an ATI Radeon 7000

I've never had a Microsoft automatic update break my Windows. But that aside, I seem to be the only one unable to get back up and running. This forum is great, and the only reason I stick it out with Ubuntu. But I'm posting this from Lynx, which will likely get old very quickly.

---

### Post by fbi agent on 2006-08-21
> **cleentrax said:**
> I've never had a Microsoft automatic update break my Windows. But that aside, I seem to be the only one unable to get back up and running. This forum is great, and the only reason I stick it out with Ubuntu. But I'm posting this from Lynx, which will likely get old very quickly.

Did you just attempt to start Xorg after trying the suggested fix or did you do a full reboot/init 6?

---

### Post by tibiker1966 on 2006-08-21
Yikes!

Man, this forum is a lifesaver - same problem here.  FWIW: Radeon board w/xorg driver:

$ tail /var/log/Xorg.0.log.old
        ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
        ATI Radeon X850 XT (R480) (PCIE),
        ATI Radeon X850 XT PE (R480) (PCIE),
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon 9200 Pro (RV280)".
(EE) No devices detected.

Fatal server error:
no screens found
$

a "sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10"

and a "startx" did the trick!

Thanks all,

-K

---

### Post by Pyr3 on 2006-08-21
Gotta love the Linux community.

Something wrong? Fixed in a jiffy. Or thereabouts.

Microsoft - well, they've had problems for over 20 years.

*hands cookies to Jlx*

---

### Post by cleentrax on 2006-08-21
> **fbi agent said:**
> Did you just attempt to start Xorg after trying the suggested fix or did you do a full reboot/init 6?

I must have rebooted 20 times going back and forth between Ubuntu and Windows. I've edited (and reconfigured) my xorg.conf file with both the nvidia and nv drivers, and I've tried reinstalling the downgraded driver, and my nvidia-glx multiple times.

---

### Post by rodger on 2006-08-21
I had the same failure here. Thanks to JLX I am running again.
Is there a forum where we can see the devlopers working this?
It would be nice to at least see acknowledgement of the issue.


Using an old Compaq E500

---

### Post by fbi agent on 2006-08-21
> **cleentrax said:**
> I must have rebooted 20 times going back and forth between Ubuntu and Windows. I've edited (and reconfigured) my xorg.conf file with both the nvidia and nv drivers, and I've tried reinstalling the downgraded driver, and my nvidia-glx multiple times.

Damn, I'll keep an eye on this thread, curious to see what fixes your problem, and when an updated package is released.

---

### Post by Jax55 on 2006-08-21
Hi any Ubuntu developers there...  Any chance of pulling this patch until this gets a bit more sorted out.    At last count it has shagged 4 out of 4 possible Ubuntu machines at our site.   Adept and Synaptic both still have that update for download!

---

### Post by snumark on 2006-08-22
This got me back up and running after an entire afternoon of struggling with xorg stuff.  But, it did help me learn a lot more about the inner workings of Ubuntu.

---

### Post by Uncle Spellbinder on 2006-08-22
OK. Thank God for this forum and this thread in particular. I noticed the *xorg-core update* waiting and checked the forums first. I don't know if it would have broke my box or not. Everything is intel embedded with me. But to be on the VERY safe side, Luckily, I DID NOT INSTALL.

Now, which repo should I comment out until all is *hopefully* fixed so I don't continue to get this update notification.

---

### Post by Visceral Monkey on 2006-08-22
This should never have made it into the repos. Someone needs to address quality control after this matter is resolved.

---

### Post by Uncle Spellbinder on 2006-08-22
> **Visceral Monkey said:**
> This should never have made it into the repos. Someone needs to address quality control after this matter is resolved.

Indeed. How something so obviously flawed made it into the repos, I'll never know.

---

### Post by mentok on 2006-08-22
I had just finished a fresh install of Kubuntu and I didn't read the list of updates since I expected there to be many updates for a fresh install.

TDFK
(Thank $Deity For Knoppix):mrgreen:

---

### Post by Visceral Monkey on 2006-08-22
It's been dugg. Vote for it if you get the chance.

[http://digg.com/linux_unix/Latest_Ubuntu_xorg_core_update_breaks_X#c2779919](http://digg.com/linux_unix/Latest_Ubuntu_xorg_core_update_breaks_X#c2779919)

---

### Post by cleentrax on 2006-08-22
I have finally been able to get X to start, in recovery mode, if I use the nvidia driver. But I still can't get X to start in regular boot mode, with either driver. I tried an old xorg.conf backup file from June, that used to work, but it made no difference. So apparently it's not a problem with my xorg.conf settings. I am truly stumped, and quite annoyed at losing four hours of my afternoon/evening.

Anyone else having the same issues?

---

### Post by JoseStefan on 2006-08-22
I originally used this method, which looks more standard-ish:
sudo apt-get install xserver-xorg-core/dapper

But it ends up installing the same version stated at the beginning:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

Finally, I dedicded to use the method stated within "ubotu"
(Reference: [http://www.ubuntu.com/community/irc](http://www.ubuntu.com/community/irc))

> 
<JoseStefan> xorgbug
<ubotu> If X is broken after a recent update you can downgrade. '/msg ubotu xorgbugfix' (or xorgbugfix-amd64 or xorgbugfix-ppc). Bug report - [https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57158](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57158)
<JoseStefan> xorgbugfix
<ubotu> wget http:*//*archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb && sudo dpkg -i xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb


---

### Post by Uncle Spellbinder on 2006-08-22
> **Visceral Monkey said:**
> It's been dugg. Vote for it if you get the chance.

[http://digg.com/linux_unix/Latest_Ubuntu_xorg_core_update_breaks_X#c2779919](http://digg.com/linux_unix/Latest_Ubuntu_xorg_core_update_breaks_X#c2779919)

Thanks! :D

---

### Post by saladasalad on 2006-08-22
Not once in my 5 years as a full time linux user have I felt the need to rant about a bug but this is the most unbelievable ****-up that I have ever witnessed in the open source world.

Just imagine for a moment all of those non-technical users who are new to linux and have been convinced by their friends/family that linux is the best thing since sliced bread. They turn their computer on one day and a little icon sits on their panel telling them that "There is 1 updated package available", they install said package then next time they boot their computer, NOTHING. No error message, NOTHING. What the **** are they supposed to do?

This is an *upgrade*? What strange motherfucking planet do these idiots come from where an UPDATE thouroughly breaks things that previously worked?

That rant might have sounded a bit harsh but I am mightily pissed off (less so now thanks to jlx's advice) and I can imagine many many other people are pissed off but they will never know about these forums and this thread. So consider this post as *their* voice.

---

### Post by Saibot on 2006-08-22
*Whew* that was close.  I downloaded the update but didn't restart right away and just continued running.  Went over to the compiz forums and got the warning there with the instructions to revert to the old version so I did that pronto.  I just now rebooted and everything is fine - but I was sure holding my breath hoping that nothing was screwed.

---

### Post by randell6564 on 2006-08-22
Well, luckily I came here before rebooting after the update!

I wrote down the instructions for downgrading, and sure enough, xserver was broke!!

This kinda pisses me off!  What if I did'nt write down those instructions.
Someone with only one computer would be FUC##$!!

Why in the hell would all of us get a damn update package so easily that screws us all up?!  Are these packages not tested before release?

I Love using ubuntu, but I gotta tell ya, it's real stressful when updating!
Something usually gets uninstalled, reconfigured or just plain broke!

I sure hope that that changes some day!

---

### Post by cleentrax on 2006-08-22
trying to attach my xorg.0.log with Lynx...

---

### Post by peabody on 2006-08-22
> **Visceral Monkey said:**
> This should never have made it into the repos. Someone needs to address quality control after this matter is resolved.

> **Uncle Spellbinder said:**
> Indeed. How something so obviously flawed made it into the repos, I'll never know.

> **saladasalad said:**
> Not once in my 5 years as a full time linux user have I felt the need to rant about a bug but this is the most unbelievable ****-up that I have ever witnessed in the open source world.

Just imagine for a moment all of those non-technical users who are new to linux and have been convinced by their friends/family that linux is the best thing since sliced bread. They turn their computer on one day and a little icon sits on their panel telling them that "There is 1 updated package available", they install said package then next time they boot their computer, NOTHING. No error message, NOTHING. What the **** are they supposed to do?

This is an *upgrade*? What strange motherfucking planet do these idiots come from where an UPDATE thouroughly breaks things that previously worked?

That rant might have sounded a bit harsh but I am mightily pissed off (less so now thanks to jlx's advice) and I can imagine many many other people are pissed off but they will never know about these forums and this thread. So consider this post as *their* voice.

The icing on the cake is that plenty of users are going to try and reinstall to fix this.  As soon as they update, they're going to end up right smack where they were.  They might blame themselves at first, but how's it gonna be when all of these disgruntled users find out IT WAS THE OFFICIAL MAINTAINERS FAULT!

The silence from the official Ubuntu camp about this right now is highly disconcerting.

---

### Post by saladasalad on 2006-08-22
> **peabody said:**
> The silence from the official Ubuntu camp about this right now is highly disconcerting.

Very convenient time for [Launchpad]("https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/57153") to go offline for maintenance too.

---

### Post by garenasix on 2006-08-22
that was fun all.. spending most the nite fixing 15 PCs after an update now instead of ubuntu on all of them i now have ubuntu on five of them PC-BSD on the other 5 and freakin windows 2000 on the other five ... funny thing is i still see they got that update up so the funs not over yet

thanks to jlx's post theres a fix ... very big thank you jlx's

[http://www.ubuntuforums.org/showthread.php?t=240957](http://www.ubuntuforums.org/showthread.php?t=240957)

---

### Post by randell6564 on 2006-08-22
Yes indeed! THANK YOU jlx!!

---

### Post by mlind on 2006-08-22
> **saladasalad said:**
> Not once in my 5 years as a full time linux user have I felt the need to rant about a bug but this is the most unbelievable ****-up that I have ever witnessed in the open source world.

Just imagine for a moment all of those non-technical users who are new to linux and have been convinced by their friends/family that linux is the best thing since sliced bread. They turn their computer on one day and a little icon sits on their panel telling them that "There is 1 updated package available", they install said package then next time they boot their computer, NOTHING. No error message, NOTHING. What the **** are they supposed to do?

This is an *upgrade*? What strange motherfucking planet do these idiots come from where an UPDATE thouroughly breaks things that previously worked?

That rant might have sounded a bit harsh but I am mightily pissed off (less so now thanks to jlx's advice) and I can imagine many many other people are pissed off but they will never know about these forums and this thread. So consider this post as *their* voice.

lol :mrgreen:

I think it would be nice to have ${distirbution}-updates-testing repository where packages would be promoted to ${distirbution}-updates repository after a week or so. Maybe it would prevent problems like these.

Well, at least some folks have learned how to downgrade packages with apt-get/aptitude.

---

### Post by spockrock on 2006-08-22
ok so I updated, read all the problems, but thought maybe its a fixed version no harm in rebooting incase it works and if not I have the fix.  well x didnt start.  I did the downgrade fix x works perfectly.

I read the update details it supposed to fix something for intel integrated graphics.  so I imagine this update works for them but broke everyone elses X.

anyways thanks for the fix.

---

### Post by Uncle Spellbinder on 2006-08-22
> **mlind said:**
> lol :mrgreen:Well, at least some folks have learned how to downgrade packages with apt-get/aptitude.

Or at least check these forums *before* updating. :D

---

### Post by Uncle Spellbinder on 2006-08-22
> **spockrock said:**
> I read the update details it supposed to fix something for intel integrated graphics.  so I imagine this update works for them but broke everyone elses X.

I have intel embedded graphics. I just don't have the guts to try. I'll wait for a fix from the devs.

---

### Post by saladasalad on 2006-08-22
> **spockrock said:**
> I read the update details it supposed to fix something for intel integrated graphics.

Where do I find update details? That's something I've been looking for for a while. Do you use Ubuntu or Kubuntu?

---

### Post by mlind on 2006-08-22
Here's howto pin the orginal xserver-xorg-core package, so that it won't get upgraded for now.

create **/etc/apt/preferences** if it doesn't exist and insert
```

Package: xserver-xorg-core
Pin: release a=**dapper**
Pin-Priority: 600

```

---

### Post by djSeverin on 2006-08-22
I would very much appreciate a formal reply/update/post by the Ubuntu team with regard to this rather large blunder.

The last thing I really needed today was to be haunted by all those who I have converted to Ubuntu Linux.

I still love my Ubuntu, but damn - this was a rather all-mighty breakage...

A rollback script might be a useful addition to upcoming Ubuntu releases. If something like this happens, new users would benefit from the similicity and security of being able to type "rollback" at the shell and have their most recent changes undone.

---

### Post by JoseStefan on 2006-08-22
NOTE:

While jlx's early response is appreciated, that method will downgrade to the release version of xserver-xorg-core. Currently, two versions down.

In contrast, The method specified on the IRC, just goes back to the previous working version. Which I find is more appropriate.

Either way, Both methods are effective at getting X up and running. It shouldn't be long for a "newer" package to show up.
In the mean time stay away from:
_1.0.2-0ubuntu10.3_

Reference to IRC info:
[http://www.ubuntuforums.org/showthread.php?t=240957&page=10#92](http://www.ubuntuforums.org/showthread.php?t=240957&page=10#92)

---

### Post by randell6564 on 2006-08-22
> **saladasalad said:**
> Where do I find update details? That's something I've been looking for for a while. Do you use Ubuntu or Kubuntu?

When your looking at your update manager, highlite the package and then click on the description tab.

---

### Post by cleentrax on 2006-08-22
I may be narrowing in on the problem. Now when I try "dpkg-reconfigure xserver-xorg" I get the following error:

```
GDM: Xserver not found: /usr/bin/Xgl :0 :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
Error: Command could not be executed!
Please install the X server or correct GDM configuration and restart GDM.
```

Is this now a compiz/xgl issue?

---

### Post by saladasalad on 2006-08-22
> **randell6564 said:**
> When your looking at your update manager, highlite the package and then click on the description tab.

Adept (in Kubuntu) doesn't appear to have that feature. :???:

---

### Post by asplode on 2006-08-22
Wow... good thing I saw this thread before I rebooted.  I just upgraded the xserver packages, but luckily I got to downgrade them from a nice shiny GUI instead of the CLI, without getting to watch xserver crash. (again)  But its usually my own fault.

---

### Post by mlind on 2006-08-22
> **saladasalad said:**
> Where do I find update details? That's something I've been looking for for a while. Do you use Ubuntu or Kubuntu?

```

aptitude changelog xserver-xorg-core

```


There was 3 patches added compared to last version
[https://lists.ubuntu.com/archives/dapper-changes/2006-August/011977.html](https://lists.ubuntu.com/archives/dapper-changes/2006-August/011977.html)
[https://lists.ubuntu.com/archives/dapper-changes/2006-August/011978.html](https://lists.ubuntu.com/archives/dapper-changes/2006-August/011978.html)

---

### Post by peabody on 2006-08-22
> **mlind said:**
> lol :mrgreen:

I think it would be nice to have ${distirbution}-updates-testing repository where packages would be promoted to ${distirbution}-updates repository after a week or so. Maybe it would prevent problems like these.

Well, at least some folks have learned how to downgrade packages with apt-get/aptitude.

Seriously, all that needs to be done is some type of formal prioritizing of the testing of packages.  I'm sure it's slightly insane to apply something so rigerous to the 16,000+ packages in Ubuntu.  I can sympathize there.  If something like say "wget" breaks, it's likely to affect a very small minority.  That's tolerable; s*** happens.

What I can't sympathize with is how something that seems to affect hundreds (maybe thousands) of users just "slipped" right past any sort of testing and QA at good 'ol canonical.  This really does not look good to users.  It basically means that, at best, there is a very informal prioritizing for testing and at worst, there's none at all :( with upstream updates just being pushed, without hardly any verification.  THAT IS NOT A GOOD THING!

I can sympathize if the devs were trying to get X on Dapper to work on more hardware.  But if the speed of this update was at the cost of the vast majority of their users, that was a terrible decision.  I've been a Linux guy for a long time.  This was hardly an inconvenience to me.  However, this is sure to be a show stopper for many potential new Linux users and that saddens me.

---

### Post by siriusnova on 2006-08-22
broken for me too, thinkpad t30 with radeon 7500 mobility using "ati" driver..

---

### Post by saladasalad on 2006-08-22
> **cleentrax said:**
> Is this now a compiz/xgl issue?
I don't have compiz installed so I guess not.

[QUOTE=mlind]

```
aptitude changelog xserver-xorg-core
```

[/QUOTE]
Excellent, thanks for that.

---

### Post by stoeptegel on 2006-08-22
> **cleentrax said:**
> 
Is this now a compiz/xgl issue?

I just did a fresh install of 6.06.1 && dist-upgrade, having the same problem so i guess not.

---

### Post by JoseStefan on 2006-08-22
> **cleentrax said:**
> Is this now a compiz/xgl issue?

cleentrax,
To my understanding, it was only the last update which broke your setup. The version of xserver-xorg-core you downgraded to might be too old for your current setup. So if you can go back to just before the update, things should be fine...

Try the following:
First try to undo any config changes you might have created in "trial-and-error" try to revert to your "regular" config. I hope you have a backup, you may be lucky and find more backups in:
/var/backups/xorg/
/etc/X11
(i would take a glimpse within them just to be sure)

Now, you'll want to revert to a "not so old" version of xserver-xorg-core. You'll essentially want the "previous" working version:
[http://www.ubuntuforums.org/showthread.php?t=240957&page=10#92](http://www.ubuntuforums.org/showthread.php?t=240957&page=10#92)

That "should" revert your system to how it was.

---

### Post by jimmysz on 2006-08-22
Despite all the hullabaloo this is causing, that little orange sphincter is still sitting in my tray mocking me with that flakey update. Shouldn't pulling  the update be a #1 priority?

---

### Post by cleentrax on 2006-08-22
Well, it appears that my xserver-xgl got hosed somehow in the upgrade/downgrade of xserver-xorg-core. I finally did a complete uninstall/reinstall of all compiz-related files, which is how I found the culprit. I now have my GUI back. Thanks to everyone who helped me troubleshoot.

And whoever screwed this up at Canonical -- you owe me a beer! :rolleyes:

---

### Post by oyvindaa on 2006-08-22
> **astoltz said:**
> I'm just wondering if this has anything to do with Xgl / Compiz?  Who here has the Xserver problem but does NOT have Xgl / Compiz installed?

I don't have Xgl / Compiz installed..

---

### Post by peabody on 2006-08-22
> **oyvindaa said:**
> I don't have Xgl / Compiz installed..

It affects everyone.  It's an official package as well as the worst support blunder I've ever seen a high quality distro make.

---

### Post by Major_Stitch on 2006-08-22
Thank you so much for this fix! I didn't know what to do...you really saved me. Thank once again!

---

### Post by oyvindaa on 2006-08-22
> It affects everyone. It's an official package as well as the worst support blunder I've ever seen a high quality distro make.

Haha, yeah I guess you can say that!

---

### Post by Visceral Monkey on 2006-08-22
What this really does is highlight the need for a backup system users can can turn to if an update borks their install. Something like a restore/snapshot point that can be accessed from grub should something like this occur again. It should be a priority for the Ubuntu team because of the nature of the distro, its users and its ability to auto-update packages. This could and will happen again at some point in the future. In addition there should be a sandbox of machines that these updates are tested before publishing.

---

### Post by Major_Stitch on 2006-08-22
> **Visceral Monkey said:**
> What this really does is highlight the need for a backup system users can can turn to if an update borks their install. Something like a restore/snapshot point that can be accessed from grub should something like this occur again. It should be a priority for the Ubuntu team because of the nature of the distro, its users and its ability to auto-update packages. This could and will happen again at some point in the future. In addition there should be a sandbox of machines that these updates are tested before publishing.

You're right.
I can't say it's a shame, because the people after Ubuntu are really doing their guts out, but I think this shouldn't happen to a distro that goes as one of the more stable and simpler.

---

### Post by shadowpool on 2006-08-22
Yeah wow, that was pretty bad.  640 x 480 in lynx looking for how to fix X.

sudo apt-get get install xserver-xorg-core=1:1.0.2-0ubuntu10

Did the trick^^

Shouldn't this be stickied or something?

---

### Post by ShamusPatt on 2006-08-22
Thanks - I was completely stymied, but the downgrade did the trick. It's a good thing I had "lynx" so I could get the fix.

I'm using an ATI Radeon 9200, if it's relevant. Whatever's broke in the latest xserver-core is bad news; I hope it gets fixed real soon.

---

### Post by r4ik on 2006-08-22
It is a bad mistake and should not happen.
I feel sorry for the users affected by it but also for the people that made this  mistake.

---

### Post by nocturn on 2006-08-22
> **peabody said:**
> Oh my friend I have quite a few stories of that very thing happening (I worked as a Programmer/Tech for a University department for four years).  Admittedly, in most scenarios, it's due to the machine being riddled with virus'/spyware, but regardless, it worked before the update and shattered after it.  At least apt allows easy downgrades!  Updates in Windows are a one-way street.

Actually, it does not allow easy downgrades.  
I have an installed machine for a friend that has almost no computer experience.  She cannot make a text login let alone a downgrade command so her laptop will be effectively broken.

I just mailed her not to upgrade and pray that she hasn't done so already or it will mean a 50km trip for me while my wife is in her last days of her pregnancy...  I'm not happy.

---

### Post by nocturn on 2006-08-22
> **Visceral Monkey said:**
> This should never have made it into the repos. Someone needs to address quality control after this matter is resolved.

I hate to say this, but I agree with you.

I love Ubuntu and I can fix such breakage, but I'm installing Dapper for a lot of non technical friends who will be dead in the water by such an event and their image of Linux will be severely damaged by it.

It took a lot of convincing for them to switch.

---

### Post by Typhoon on 2006-08-22
> **nocturn said:**
> Actually, it does not allow easy downgrades.  
I have an installed machine for a friend that has almost no computer experience.  She cannot make a text login let alone a downgrade command so her laptop will be effectively broken.

I just mailed her not to upgrade and pray that she hasn't done so already or it will mean a 50km trip for me while my wife is in her last days of her pregnancy...  I'm not happy.

I live in Australia and have been helping a friend with Ubuntu. The friend lives in Ohio, USA. I was able to talk him through installing ssh and then performed the downgrade for him over the ssh link.

Quite a disaster though.

---

### Post by nocturn on 2006-08-22
> **Typhoon said:**
> I live in Australia and have been helping a friend with Ubuntu. The friend lives in Ohio, USA. I was able to talk him through installing ssh and then performed the downgrade for him over the ssh link.

Quite a disaster though.

I thought about that, but there's a Dlink router inbetween and she doesn't have a fixed IP.

And to add to the sorrow, NetworkManager hijacks interfaces, they are only brought up after login, which doesn't happen when X is down.  (She's on a laptop, wireless).

---

### Post by dr.drake on 2006-08-22
> **mycelo said:**
> Well, what a fiasco. :mad: Fortunately I still have Windows installed, so I could go here and get a solution. I was about to get rid of M$ things, but I suddenly changed my mind.

mycelo

why do people keep saying that?
"luckily I still had Windows installed"...
what's wrong with using an Ubuntu LIVE CD ???

FYI
.

---

### Post by nocturn on 2006-08-22
> **dr.drake said:**
> why do people keep saying that?
"luckily I still had Windows installed"...
what's wrong with using an Ubuntu LIVE CD ???

FYI
.


I agree with you, but still, this should not happen in an LTS version!

---

### Post by cleentrax on 2006-08-22
> **dr.drake said:**
> why do people keep saying that?
"luckily I still had Windows installed"...
what's wrong with using an Ubuntu LIVE CD ???

FYI
.

I can't speak for mycelo, but the Live CD doesn't work right out of the box for me. I have to tweak several things like WPA wireless, mouse settings, etc. So a Windows partition is good to have around -- not to mention it runs the software I need! (photoshop, dreamweaver, sonar, etc.)

---

### Post by Uncle Spellbinder on 2006-08-22
> **nocturn said:**
> I agree with you, but still, this should not happen in an LTS version!

Amen to that. I got lucky and checked the forum before updating. I've since commented out all Ubuntu and/or Canonical instances in my sources.list until the storm subsides. Shame. A real shame.

---

### Post by dr.drake on 2006-08-22
> **cleentrax said:**
> I can't speak for mycelo, but the Live CD doesn't work right out of the box for me. I have to tweak several things like WPA wireless, mouse settings, etc. So a Windows partition is good to have around -- not to mention it runs the software I need! (photoshop, dreamweaver, sonar, etc.)

VMware ???  

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

---

### Post by jmflyer on 2006-08-22
Thank god I still had an install of Gentoo.  And just to think I was about to switch everything to Dapper cuz I'm getting lazy in my old age. :-D 

This brought something to my attention.  Why don't they include the misc xorg bins like, say, xorgconf?  Why do we HAVE to use dexconf or write it out by hand?  :-k

---

### Post by Uncle Spellbinder on 2006-08-22
Most "typical" users come from the "average user" world of Windows and probably have no idea of VMWare and such. There's not a damned thing wrong with dual booting Win/Linux. A good idea, really. As most average users who worked hard to get dual booted now have a way to get to the forums without running to the library in the morning, writing down/printing all kinds of "howto's" on how to get X back. Let's stop dumping on Windows and fix our own STUPID mistake (dreadful mistake) in Linux.

---

### Post by tseliot on 2006-08-22
> **jmflyer said:**
> Thank god I still had an install of Gentoo.  And just to think I was about to switch everything to Dapper cuz I'm getting lazy in my old age. :-D 

This brought something to my attention.  Why don't they include the misc xorg bins like, say, xorgconf?  Why do we HAVE to use dexconf or write it out by hand?  :-k

Uh??? Don't you know dpkg-reconfigure xserver-xorg?

---

### Post by cleentrax on 2006-08-22
> **dr.drake said:**
> VMware ???  

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

Nice in theory, but not in practice. First of all, I have no XP install CD --  my Dell came with a recovery CD that I have long since misplaced. 

Second, I have hardware that will not work with Ubuntu or VMware, including audio devices and a scanner.

---

### Post by tseliot on 2006-08-22
I have stickied a warning about the recent updates of the Xserver:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by jmflyer on 2006-08-22
> 
Uh??? Don't you know dpkg-reconfigure xserver-xorg?

I think you're missing the point...

---

### Post by Uncle Spellbinder on 2006-08-22
> **tseliot said:**
> I have stickied a warning about the recent updates of the Xserver:
[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

Shouldn't that be stickied in "Desktop Support" as most users will check there first. Just a thought. If I'm out of line...Apologies.

---

### Post by hexion on 2006-08-22
Same problem here, resolved myself.

I'll tell how I did it because it's simple and work all times with this kind of failures.

- You make an update, aptitude tells you it's going to update **xxx** package.

- After rebooting, system is off. This makes you think last update was buggy. Ok, no problem, you remember the name of the package updated.

> cd /var/cache/apt/archives
ls **xxx***

- Mmmm, theres at least 2 versions of that package, one earlier than other. i.e., in this case, we had xserver-xorg-core_1%3a1.0.2-0ubuntu10.**1**_i386.deb and xserver-xorg-core_1%3a1.0.2-0ubuntu10.**3**_i386.deb

- All we have to do is downgrade to the inmediate-earlier version than last (if we had 3 packages, the previous version to the last)

> sudo dpkg -i **xxx-...-ubuntuxx.x_i386**

- After that the problem must be solved.


I hope this is usefull for people having to boot with windows and such to solve their problem.

---

### Post by statue on 2006-08-22
Damn bug, hours of my life I'll never get back. I hope in the future before anyone releases so called "updates", they have the foresight to test them more thoroughly.

---

### Post by jimscafe on 2006-08-22
I think this is highly embarrassing, not to mention irresponsible - I see the package still prompted me to download!! It should have been removed I think by now.

How do we have confidence when prompted for the next download? Last week I finally managed to move all my applications from Windows to ubuntu - and heaved a sigh of relief - this has just soured that feeling. Like others I used Windows to get to the forum and find the solution.

If something like this happens to Windows (and it does) they have to take a lot of stick - so some humble pie eating is required now. 

Can we volunteer to pre-test upgrades like this - what can we do to help?

It will have a very negative effect for people with little technical ability who have been finally wooed to Linux. What a shame - such an excellent os too.

---

### Post by scheuri on 2006-08-22
> **jlx said:**
> Solution:
When your Xserver crash and you are at text console type this:
sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

When finnish, reboot or just type startx. To reboot type:
sudo shutdown -r now

Now xserver-xorg-core is downgraded to prior working version. 

First I thought it was something wrong with XGL/Compiz Quinn's packages. But I upgraded xserver-xorg-core in my laptop that has no compiz installed and Xserver was broken too. So it has to be a problem with dapper packages. Hope Ubuntu boys will fix it soon.

Regards.

Thousand thanks.
Had the same issue...no X after starting the PC again this morning (after upgrading in the night before).
Your solution worked for me...so downgrading is the way to go for a fast solution.

thanks again

---

### Post by nocturn on 2006-08-22
> **jimscafe said:**
> I think this is highly embarrassing, not to mention irresponsible - I see the package still prompted me to download!! It should have been removed I think by now.

How do we have confidence when prompted for the next download? Last week I finally managed to move all my applications from Windows to ubuntu - and heaved a sigh of relief - this has just soured that feeling. Like others I used Windows to get to the forum and find the solution.


I agree fully!  I'm still asking in the bugreport to pull the current update.

Latest news is that there will be a new update in one or two hours that fixes this regression.

We still need to think about how to handle these situations in the future though, a lot of non-technical users are now left without X login, so they cannot install the upgrade that fixes the issue...

---

### Post by Gerry Atric on 2006-08-22
Copped the same problem after updating Ubuntu
Tried the fix 

sudo apt-get install xserver-xorg-core=1:1.02-0ubuntu10 without any success still just boots to the command line. 
Says that nothing installed, nothing upgraded nothing found etc.
Any Ideas please apart from reinstalling the whole system again?

Followed the instructions several times on this thread.

---

### Post by nocturn on 2006-08-22
> **Gerry Atric said:**
> Copped the same problem after updating Ubuntu
Tried the fix 

sudo apt-get install xserver-xorg-core=1:1.02-0ubuntu10 without any success still just boots to the command line. 
Says that nothing installed, nothing upgraded nothing found etc.
Any Ideas please apart from reinstalling the whole system again?

Followed the instructions several times on this thread.

You could wait out the fix (one or two hours) and apt-get update; apt-get upgrade.

It's definately easier then reinstalling.

---

### Post by peabody on 2006-08-22
> **nocturn said:**
> 
Latest news is that there will be a new update in one or two hours that fixes this regression.


Alright, who's willing to be the guinea pigs?  We need a couple of brave souls!  Them waters be shark infested!

---

### Post by abelthorne on 2006-08-22
> **Gerry Atric said:**
> Tried the fix 

sudo apt-get install xserver-xorg-core=1:1.02-0ubuntu10 without any success still just boots to the command line. 
Says that nothing installed, nothing upgraded nothing found etc.
Any Ideas please apart from reinstalling the whole system again?

If you really typed this, you forgot the dot between "0" and "2".
The correct syntax is "sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10".

---

### Post by nocturn on 2006-08-22
> **peabody said:**
> Alright, who's willing to be the guinea pigs?  We need a couple of brave souls!  Them waters be shark infested!

Well, they people that didn't recover with the fix have little to loose.

I'm willing to try it on my work PC too (main OS is Windows anyway).

---

### Post by frup on 2006-08-22
gotta feel sorry for the untechnical people this affects.. could seriously harm the userbase you reckon?

---

### Post by statue on 2006-08-22
It has seriously made me more worried about future updates, I think I will wait and check this forum before updating from now on...especially for xorg. For all the windows bashing that goes on in the linux community, I have to say that when windows releases updates, they generally do what they are intended to do. This xorg "update" acted more like a virus than a fix.

EDIT: Fair enough, I can only state from my own experience. I can't recall a time when I downloaded a windows update only to reboot and find my computer stuck at a DOS prompt telling me windows can't load due to blahblhablah. linux on the other hand...

---

### Post by nocturn on 2006-08-22
> **statue said:**
> It has seriously made me more worried about future updates, I think I will wait and check this forum before updating from now on...especially for xorg. For all the windows bashing that goes on in the linux community, I have to say that when windows releases updates, they generally do what they are intended to do. This xorg "update" acted more like a virus than a fix.

I agree that this highlights a serious fault in the quality control of Ubuntu patches (not Linux, just Ubuntu).

But about Windows update, they do break a lot of things too (which is no defense for a Linux distro to do the same) and don't forget that the WGA spyware was installed this way on unsuspecting users, a lot of who's computers subsequently froze even though they had a valid license.

---

### Post by tseliot on 2006-08-22
> **Uncle Spellbinder said:**
> Shouldn't that be stickied in "Desktop Support" as most users will check there first. Just a thought. If I'm out of line...Apologies.

I think the most appropriate section is the Video & sound. But good point anyway.

I'll sticky a link to that thread also in the Desktop support section

EDIT: done!

---

### Post by logout on 2006-08-22
I have been using Linux for probably 8 years now, and by far I think this is the best distro I've used yet.  For the first maybe 5 years of using Linux, I thought spending all night trying to get this or that working was great fun, a good challenge, geeking out with it was great.

When I auto-upgraded from hedgehog to dapper, it broke my wireless, and my audio.  I have been soo not in the mood for this shit lately, so I used Windows for the past month for the first time in years.

Finally, I have the patience to reinstall Ubuntu from CD and move all my work back over.  Dapper is seriously awesome, I'm impressed.  Then one day later it breaks,  And of course everyone one I've converted to Ubuntu has theirs break as well.

I have almost, almost, an infinite amount of patience for Linux and this distro in particular, but the fact that the update is still sitting there and being downloaded by people right now and breaking their x servers is crazy.

The regular joe user does not hang out at Ubuntu forums, nor should they have to to have a working OS.

If the update was up there for like a couple hours and then taken down, sure that's a mistake, that's excusable, but it's still there now!

Sorry, End Rant.

---

### Post by hexion on 2006-08-22
I agree with "logout".

Ok, quality controls have failed. Ok, a terrible mistake but we're all humans.

But the fact is that when this was discovered, the packet **should have been removed ** to avoid new systems are broken.

But still now, hours and hours after this issue has been reported **the buggy packet is still there to be updated**.

This is even a bigger error (unexcusable I think) than the first.

I, as "logout", have a lot of patience so for me isn't a great problem. But this kind of errors make the famous "bug #1" impossible to reach. Because this damages ubuntu's image more than nothing. And that's important to reach the first objetive of ubuntu (as set on bug #1).

Please, to developers and whoever wants to read this, this kind of things cannot happen again. If an updated package breaks something and it's reported, it **has to be removed inmediately** to avoid new systems break.

---

### Post by milkmaid on 2006-08-22
same problem after xorg upgrade here 
"dlopen failed to load /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXlastContext
Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
Failed to load module :GLcore" (loader failed, 7)
No devices detected"



:/

---

### Post by janbockaert on 2006-08-22
> **cleentrax said:**
> Not sure how. I can't get to that portion of the drive from Windows, and I don't know how to post a file using Lynx.

look here to acces your linux drives under windows: [http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

however, it is not very stable, so from time to time windows will ask you to format your linux drives :)

---

### Post by janbockaert on 2006-08-22
> **nocturn said:**
> I agree that this highlights a serious fault in the quality control of Ubuntu patches (not Linux, just Ubuntu).
.

Even worse, it is the second time in less than a week, an update broke my system. First synaptic went down, now this. 

However, it is also the second time in less than a week, this forum solved the problem within minutes. I missed suse's sax2 this night, but it is the community that keeps me staying with ubuntu!

thanks.

---

### Post by KhaaL on 2006-08-22
I too agree that this package should be removed for the time being, until a working one replaces it. I had many problems with dapper in the past, and this "update" made me want to stomp my *buntu CD's to oblivion... 

It's ok if a faulty update is made to other applications, but many linux newcomers (like me) still haven't learned the console completely and are dependant on the GUI to do their tasks.

---

### Post by mycelo on 2006-08-22
What REALLY surprises me is that the upgrade is still on-line! Common! I can forgive the mistake, no one is perfect, but do something about it!

mycelo

---

### Post by anodizer on 2006-08-22
> **janbockaert said:**
> Even worse, it is the second time in less than a week, an update broke my system. First synaptic went down, now this.

The Synaptic issue is irrelevant, it happened after an update from compiz repos.
Come on guys, the bug entry in launchpad is marked as "fix released".

---

### Post by carontis on 2006-08-22
Unfortunatly for me that bug crashed my system too. So I've followed the solution on this thread and finally I found by myself that I had to erase the bad package. I used the live CD to download the old one, 'cause inserting the  installation cd I used long ago (my cpu is an AMD and I used the alternate), it was never known... So after downloaded the good package in deb format, I shut down the pc and boot again in terminal and finally, after making a copy of the new one in the /var/cache/apt/archives i simply launched dpkg -i and installed the old one. I have a question: how many times new packages are checked before giving them as good? This shouldn't happens expecially with updates, or what kind of updates could they be?

Thanks to the one ( jlx) who gave at first the help!

---

### Post by azmrb on 2006-08-22
Well it looks like the update ( 10.4 ) has been posted, with a low ugency

[B]
Re: xorg-server 1:1.0.2-0ubuntu10.3 breaks X: "no screens found" from Rodrigo Novo at 2006-08-22 09:37:21 UTC

Closing bug, package uploaded to the archives:

 xorg-server (1:1.0.2-0ubuntu10.4) dapper-updates; urgency=low
 .
   * Reverted patch 005_pci_domain.dpatch -> breaks PCI setup for many users.
     This patch will need further work before it is reintegrated into
     xorg-server again.
[/B]

I guess I can't see 1. why it is low urgency
                    2. why the bug report has been closed before finding                                  
                       out if it fixed the problem.

---

### Post by anando on 2006-08-22
There should be a simple tool to revert back on a package. It would have been nice to have something like :

```
sudo apt-get revert xserver-xorg-core
```

such that it would install the previous (hopefully working) version of the xserver package which caused the problem. This would save non-experts from having to remember the package version prior to update (and pain).

What do you guys think about it ?

Cheers,
Anand.

---

### Post by anodizer on 2006-08-22
> **azmrb said:**
> 
                    2. why the bug report has been closed before finding                                  
                       out if it fixed the problem.

It is fixed, you can download the new .deb from [here](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb) and see for yourself.

---

### Post by macstevejb on 2006-08-22
I just cant believe this broken update is STILL showing in automatic software updates!!! :( 

If anything is going to turn people away from using Ubuntu/Linux, especially newcomers, then this unfortunate episode couldn't have done a better job!

---

### Post by azmrb on 2006-08-22
> **anando said:**
> There should be a simple tool to revert back on a package. It would have been nice to have something like :

```
sudo apt-get revert xserver-xorg-core
```

such that it would install the previous (hopefully working) version of the xserver package which caused the problem. This would save non-experts from having to remember the package version prior to update (and pain).

What do you guys think about it ?

Cheers,
Anand.

Agreed!  Ubuntu needs some kind of recovery system that takes a snapshot of critical files every day and allow easy reversion, kind of like, dare I say it "System Restore"

---

### Post by carontis on 2006-08-22
That's a good idea, azmrb, 'cause in windows there is something like you say and is used when something goes wrong; a classical *restore* tha everyone can use to jump to the "before" situation, so from there you can erase the bad you isntalled. I think this could be a better way to restore the OS in case it's broken or damaged. Unfortunatly I'm not a programmer also if I'm starting in these days to do something. I hope someone read this one you told and may be starts to prepare something as you sayd.
It's not a bad idea!

---

### Post by spockrock on 2006-08-22
> **anodizer said:**
> It is fixed, you can download the new .deb from [here](http://people.ubuntu.com/~rodarvus/packages/dapper/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb) and see for yourself.


Yep the deb you posted works thank you very much.

---

### Post by ubuntu_demon on 2006-08-22
I closed this thread. People with problems should go here :

[B]PLEASE READ: The Latest Updates Break the Xserver!
[http://ubuntuforums.org/showthread.php?t=241254](http://ubuntuforums.org/showthread.php?t=241254)[/B]

---

### Post by ubuntu-geek on 2006-08-22
More information can be found here as well [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

