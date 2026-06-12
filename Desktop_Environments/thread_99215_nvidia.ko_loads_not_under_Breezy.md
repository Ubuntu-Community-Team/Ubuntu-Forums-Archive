---
title: "nvidia.ko loads not under Breezy"
date: 2005-12-05
forum: Desktop Environments
---

### Post by AndreasT on 2005-12-05
Hello, for some time I try to install the 7676 driver for my Gforce2 under Ubuntu Breezy. Everythings seems to work fine, the new module is compiled but want not load.

I told the nvidia install script:
the kernel-source-path
the kernel-install-path
changed to gcc 3.4
removed all nvidia packages and config files

still I got the message that the module can not be loaded due to wrong kernel version. A nvidia.ko compiled an placed in /lib/modules/2.6.12-10-386/volantile/. I can load this module by sudo insmod. There is no /usr/bin/nvidia-bug-report.sh

I tried to change the driver from nv to nvidia, no result but black screen
There is nvidia in /etc/modules

Andreas:(

---

### Post by 23meg on 2005-12-05
Please post the contents of your Xorg.0.log file.

---

### Post by AndreasT on 2005-12-05
attached you'll find the Xorg.0.log file

Andreas

---

### Post by 23meg on 2005-12-05
Well, I can't see your file attached. If you're having trouble attaching it, paste its contents here and post the url: [http://sh.nu/p/](http://sh.nu/p/)

---

### Post by AndreasT on 2005-12-05
Part 1 as follows:


X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-10-386 #1 Fri Nov 18 11:51:02 UTC 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Fri Nov 18 11:51:02 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec  5 15:13:01 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL M991"
(**) |   |-->Device "NVIDIA Corporation NV15 [GeForce2 GTS/Pro]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) No FontPath specified.  Using compiled-in default.
(==) FontPath set to "/usr/share/X11/fonts/misc"
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
(II) PCI: 00:00:0: chip 8086,1130 card 0000,0000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 8086,4541 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 8086,4541 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 8086,4541 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0150 card 10de,002e rev a4 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 1282,9102 card 4554,434e rev 31 class 02,00,00 hdr 00
(II) PCI: 02:0c:0: chip 1274,5880 card 1274,2000 rev 03 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4600000 - 0xf46fffff (0x10100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4700000 - 0xf47fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV15 [GeForce2 GTS/Pro] rev 164, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfe9f0000/16
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[1] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[2] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[3] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[4] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[7] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[8] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[9] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[1] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[2] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[3] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[4] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[6] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[7] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[8] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[9] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[15] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
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
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
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
(II) LoadModule: "nv"
(II) Loading /usr/X11R6/lib/modules/drivers/nv_drv.o
(II) Module nv: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro4 NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 280 NVS, Quadro4 380 XGL, Quadro NVS 50 PCI, GeForce4 448 Go,
	GeForce4 MX Integrated GPU, GeForce3, GeForce3 Ti 200,
	GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600, GeForce4 Ti 4400,
	0x0252, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, 0x0313, GeForce FX 5600SE,
	0x0316, 0x0317, GeForce FX Go5600, GeForce FX Go5650,
	Quadro FX Go700, 0x031D, 0x031E, 0x031F, GeForce FX 5200,
	GeForce FX 5200 Ultra, GeForce FX 5200, GeForce FX 5200SE,
	GeForce FX Go5200, GeForce FX Go5250, GeForce FX 5500,
	GeForce FX 5100, GeForce FX Go5200 32M/64M, 0x0329,
	Quadro NVS 280 PCI, Quadro FX 500/600 PCI, GeForce FX Go53xx Series,
	GeForce FX Go5100, 0x032F, GeForce FX 5900 Ultra, GeForce FX 5900,
	GeForce FX 5900XT, GeForce FX 5950 Ultra, Quadro FX 700,
	GeForce FX 5900ZT, Quadro FX 3000, GeForce FX 5700 Ultra,
	GeForce FX 5700, GeForce FX 5700LE, GeForce FX 5700VE, 0x0345,
	GeForce FX Go5700, GeForce FX Go5700, 0x0349, 0x034B,
	Quadro FX Go1000, Quadro FX 1100, 0x034F, GeForce 6800 Ultra,
	GeForce 6800, GeForce 6800 LE, 0x0043, GeForce 6800 GT, 0x0049,
	Quadro FX 4000, 0x00C0, GeForce 6800, GeForce 6800 LE,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400, 0x00CD,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, 0x0142, 0x0143,
	GeForce Go 6600, GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, 0x0147,
	GeForce Go 6600, 0x0149, 0x014B, 0x014C, 0x014D, Quadro FX 540,
	GeForce 6200, 0x0160, GeForce 6200 TurboCache(TM), 0x0162, 0x0163,
	GeForce Go 6200, 0x0163, GeForce Go 6250, GeForce Go 6200,
	GeForce Go 6250, 0x0169, 0x016B, 0x016C, 0x016D, 0x016E, 0x0210,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, 0x0220, 0x0221,
	0x0222, 0x0228
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce2 GTS found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[14] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[15] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[16] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[6] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[7] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[8] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[18] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[21] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

---

### Post by AndreasT on 2005-12-05
part 2 as follows:

(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce2 GTS"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE8000000
(--) NV(0): MMIO registers at 0xFD000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/X11R6/lib/modules/libi2c.a
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: DEL  Model: 7001  Serial#: 1211184464
(II) NV(0): Year: 2000  Week: 50
(II) NV(0): EDID Version: 1.2
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max H-Image Size [cm]: horiz.: 36  vert.: 27
(II) NV(0): Gamma: 2.76
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.625 redY: 0.340   greenX: 0.285 greenY: 0.606
(II) NV(0): blueX: 0.150 blueY: 0.065   whiteX: 0.283 whiteY: 0.297
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) NV(0): #2: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #3: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #4: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 94.5 MHz   Image Size:  355 x 265 mm
(II) NV(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) NV(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) NV(0): Serial No: 52TNU0CCH15P
(II) NV(0): Monitor name: DELL  M991
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 96 kHz, PixClock max 210 MHz
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 32768 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): DELL M991: Using hsync range of 30.00-96.00 kHz
(II) NV(0): DELL M991: Using vrefresh range of 50.00-160.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,DELL M991) mode clock 218.3MHz exceeds DDC maximum 210MHz
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,DELL M991) mode clock 234MHz exceeds DDC maximum 210MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1200,DELL M991) mode clock 230MHz exceeds DDC maximum 210MHz
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,DELL M991) mode clock 266.95MHz exceeds DDC maximum 210MHz
(II) NV(0): Not using default mode "2048x1536" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(--) NV(0): Virtual size is 1280x1024 (pitch 1280)
(**) NV(0): *Default mode "1280x1024": 157.5 MHz, 91.1 kHz, 85.0 Hz
(II) NV(0): Modeline "1280x1024"  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "640x480": 74.2 MHz, 85.9 kHz, 85.1 Hz (D)
(II) NV(0): Modeline "640x480"   74.25  640 672 752 864  480 480 482 505 doublescan +hsync +vsync
(**) NV(0):  Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0):  Default mode "1280x960": 148.5 MHz, 85.9 kHz, 85.0 Hz
(II) NV(0): Modeline "1280x960"  148.50  1280 1344 1504 1728  960 961 964 1011 +hsync +vsync
(**) NV(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) NV(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) NV(0):  Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz
(II) NV(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync
(**) NV(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) NV(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) NV(0):  Default mode "1152x768": 65.0 MHz, 44.2 kHz, 54.8 Hz
(II) NV(0): Modeline "1152x768"   65.00  1152 1178 1314 1472  768 771 777 806 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 133.5 MHz, 95.3 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "1024x768"  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync
(**) NV(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.1 Hz (I)
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) NV(0):  Default mode "960x720": 117.0 MHz, 90.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "960x720"  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync
(**) NV(0):  Default mode "928x696": 109.2 MHz, 86.4 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "928x696"  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync
(**) NV(0):  Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "896x672"  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync
(**) NV(0):  Default mode "960x600": 115.0 MHz, 91.0 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "960x600"  115.00  960 968 1048 1264  600 600 602 625 doublescan -hsync -vsync
(**) NV(0):  Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "960x600"   96.58  960 1024 1128 1296  600 600 602 621 doublescan
(**) NV(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Default mode "800x600": 101.2 MHz, 93.8 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "800x600"  101.25  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) NV(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Default mode "800x600": 94.5 MHz, 87.5 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "800x600"   94.50  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) NV(0):  Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) NV(0): Modeline "800x600"   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) NV(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "800x600"   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) NV(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) NV(0):  Default mode "700x525": 92.0 MHz, 93.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "700x525"   92.00  700 732 828 980  525 525 527 550 doublescan +hsync +vsync
(**) NV(0):  Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) NV(0): Modeline "700x525"   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync
(**) NV(0):  Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "700x525"   75.50  700 732 828 980  525 525 527 550 doublescan +hsync +vsync
(**) NV(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x512": 78.8 MHz, 91.1 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "640x512"   78.75  640 672 752 864  512 512 514 536 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "640x512"   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) NV(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0):  Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0):  Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0):  Default mode "576x432": 60.8 MHz, 77.5 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "576x432"   60.75  576 608 672 784  432 432 434 455 doublescan +hsync -vsync
(**) NV(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) NV(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0):  Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0):  Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0):  Default mode "512x384": 22.4 MHz, 35.5 kHz, 87.1 Hz (D)
(II) NV(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) NV(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0):  Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0):  Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) NV(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0):  Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) NV(0):  Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(--) NV(0): Display dimensions: (360, 270) mm
(--) NV(0): DPI set to (90, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[8] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[9] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[10] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[19] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[20] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[21] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xe8000000,0x2000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
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
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "dk"
(**) Generic Keyboard: XkbLayout: "dk"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
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

---

### Post by 23meg on 2005-12-05
Do you currently not have "nvidia" instead of "nv" in your xorg.conf? If not, change your driver to "nvidia" and post your log again. Use the site I linked to in my last post instead of pasting here.

---

### Post by AndreasT on 2005-12-05
Hello again, I will drop this case, because the glx-legacy driver works fine and I'm not so sure, that the original driver will do so much better.

I can get a FX5200 258Mb for less than 40€, so live is to short for more experiments. The old Gforce2 was underpowered anyway.

Thank you for taking care of my problems

Andreas;)

---

