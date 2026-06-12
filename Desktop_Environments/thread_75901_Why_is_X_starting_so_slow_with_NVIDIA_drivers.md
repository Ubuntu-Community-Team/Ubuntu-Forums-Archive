---
title: "Why is X starting so slow with NVIDIA drivers?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Biffy on 2005-10-14
Ok, so i just installed breezy and i've got a problem. When i am using the NVIDIA-drivers, X takes very long time to start. Its just plain black on the screen, and after a couple of minutes, the NVIDIA-logo appears and it works fine. Its just that i dont want to wait that long.

Ive been trying with and without gdm. Only the NVIDIA-drivers does this.

Any ideas?

By the way, its an old computer. AMD-K6 350 mhz. But that does not matter, it didnt do this back in hoary.

---

### Post by xeta on 2005-10-14
It could be the resolution you are starting with. Maybe go with something a bit lower and see if that ups your response time.

---

### Post by riggsd on 2005-10-14
Please post the contents of your /var/log/Xorg.0.log

---

### Post by Biffy on 2005-10-17
[QUOTE=xeta]It could be the resolution you are starting with. Maybe go with something a bit lower and see if that ups your response time.[/QUOTE]

I dont think that's the problem. I am running 1024x768@16  , that shouldt be a problem.

riggsd: Ok, here it is. Its kinda long tough, sorry about that:

```
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i586
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 17 16:12:16 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc105"
(**) XKB: model: "pc105"
(**) Option "XkbLayout" "se"
(**) XKB: layout: "se"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0598 card 0000,0000 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,8598 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1106,0586 card 1106,0000 rev 47 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 1106,0571 card 0000,0000 rev 06 class 01,01,8a hdr 00
(II) PCI: 00:07:2: chip 1106,3038 card 0925,1234 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 1106,3040 card 0000,0000 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:08:0: chip 10ec,8139 card 1429,d010 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:09:0: chip 1274,1371 card 1274,1371 rev 06 class 04,01,00 hdr 00
(II) PCI: 00:0a:0: chip 11c1,5802 card 11c1,5802 rev 10 class 0c,03,10 hdr 00
(II) PCI: 01:00:0: chip 10de,0110 card 1554,1081 rev b2 class 03,00,00 hdr 00
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
	[0] -1	0	0xdc000000 - 0xddffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Host-to-PCI bridge:
(II) Bus -1: bridge is at (0:7:3), (-1,-1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus -1 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus -1 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus -1 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 178, Mem @ 0xdc000000/24, 0xd0000000/27
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
(II) PCI Memory resource overlap reduced 0xd8000000 from 0xdbffffff to 0xd7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xde001000 - 0xde001fff (0x1000) MX[B]
	[1] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[2] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[3] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xde001000 - 0xde001fff (0x1000) MX[B]
	[1] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[2] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[3] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[4] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[6] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[7] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[8] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
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
	[5] -1	0	0xde001000 - 0xde001fff (0x1000) MX[B]
	[6] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[7] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
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
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xde001000 - 0xde001fff (0x1000) MX[B]
	[6] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[7] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[11] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[12] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[15] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xde001000 - 0xde001fff (0x1000) MX[B]
	[6] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[7] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[10] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[11] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[12] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[19] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[20] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16
(==) NVIDIA(0): RGB weight 565
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xDC000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce2 MX/MX 400
(--) NVIDIA(0): VideoBIOS: 03.11.01.30.00
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 1X
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0, TV-0
(WW) NVIDIA(0): Multiple displays connected, but only one display allowed;
(WW) NVIDIA(0):      using first display
(--) NVIDIA(0): CRT-0: maximum pixel clock: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NVIDIA(0): Primary V_BIOS segment is: 0xc000
(II) NVIDIA(0): Generic Monitor: Using hsync range of 31.00-60.00 kHz
(II) NVIDIA(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "640x350" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x175" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "720x400" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "360x200" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
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
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
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
(II) NVIDIA(0): Not using default mode "1600x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(++) NVIDIA(0): DPI set to (100, 100)
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
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[1] 0	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xde001000 - 0xde001fff (0x1000) MX[B]
	[8] -1	0	0xde000000 - 0xde0000ff (0x100) MX[B]
	[9] -1	0	0xd8000000 - 0xd7ffffff (0x0) MX[B]O
	[10] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0xdc000000 - 0xdcffffff (0x1000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec3f (0x40) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e00f (0x10) IX[B]
	[21] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[22] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "se"
(**) Generic Keyboard: XkbLayout: "se"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(==) Configured Mouse: Buttons: 3
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
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
```

---

### Post by Biffy on 2005-10-17
BTW: Here is my xorg.conf:

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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	64000
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-60
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" 
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

### Post by CastleKingSide on 2005-10-18
I am facing the same problem, and I do not think it has anything to do with the starting resolution, on other distros I had my x starting super fast @1024x768, I belive there are some things that shoud be tunned up, when I go to the nvidia settings i does not say anything about my monitor (a samsung sync master 550) like it did on other distro...so i belive there is a problem there (i can not get it solved) also looks like nivida driver suffer on boot...
-/var/log/Xorg.0.log (many NVIDIA stuff on the end, is it normal?)

```


(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NVIDIA X Driver  1.0-7667  Fri Jun 17 07:03:12 PDT 2005
(II) NVIDIA Unified Driver for all NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[6] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[7] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[8] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[17] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[18] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[19] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[6] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[7] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[8] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[9] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[10] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[20] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[21] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[22] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xC0000000
(--) NVIDIA(0): MMIO registers at 0xCE000000
(II) NVIDIA(0): NVIDIA GPU detected as: GeForce2 MX/MX 400
(--) NVIDIA(0): VideoBIOS: 03.11.01.37.00
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): CRT-0: maximum pixel clock: 350 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) NVIDIA(0): S/M 550v: Using default hsync range of 30.00-55.00 kHz
(II) NVIDIA(0): S/M 550v: Using default vrefresh range of 50.00-120.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(WW) (640x350,S/M 550v) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x175,S/M 550v) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x400,S/M 550v) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x200,S/M 550v) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (720x400,S/M 550v) mode clock 35.5MHz exceeds DDC maximum 0MHz
(WW) (360x200,S/M 550v) mode clock 17.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,S/M 550v) mode clock 25.2MHz exceeds DDC maximum 0MHz
(WW) (320x240,S/M 550v) mode clock 12.6MHz exceeds DDC maximum 0MHz
(WW) (640x480,S/M 550v) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x240,S/M 550v) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,S/M 550v) mode clock 31.5MHz exceeds DDC maximum 0MHz
(WW) (320x240,S/M 550v) mode clock 15.75MHz exceeds DDC maximum 0MHz
(WW) (640x480,S/M 550v) mode clock 36MHz exceeds DDC maximum 0MHz
(WW) (320x240,S/M 550v) mode clock 18MHz exceeds DDC maximum 0MHz
(WW) (800x600,S/M 550v) mode clock 36MHz exceeds DDC maximum 0MHz
(WW) (400x300,S/M 550v) mode clock 18MHz exceeds DDC maximum 0MHz
(WW) (800x600,S/M 550v) mode clock 40MHz exceeds DDC maximum 0MHz
(WW) (400x300,S/M 550v) mode clock 20MHz exceeds DDC maximum 0MHz
(WW) (800x600,S/M 550v) mode clock 50MHz exceeds DDC maximum 0MHz
(WW) (400x300,S/M 550v) mode clock 25MHz exceeds DDC maximum 0MHz
(WW) (800x600,S/M 550v) mode clock 49.5MHz exceeds DDC maximum 0MHz
(WW) (400x300,S/M 550v) mode clock 24.75MHz exceeds DDC maximum 0MHz
(WW) (800x600,S/M 550v) mode clock 56.3MHz exceeds DDC maximum 0MHz
(WW) (400x300,S/M 550v) mode clock 28.15MHz exceeds DDC maximum 0MHz
(II) NVIDIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(WW) (1024x768,S/M 550v) mode clock 65MHz exceeds DDC maximum 0MHz
(WW) (512x384,S/M 550v) mode clock 32.5MHz exceeds DDC maximum 0MHz
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
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(WW) (832x624,S/M 550v) mode clock 57.284MHz exceeds DDC maximum 0MHz
(WW) (416x312,S/M 550v) mode clock 28.642MHz exceeds DDC maximum 0MHz
(WW) (1280x768,S/M 550v) mode clock 80.14MHz exceeds DDC maximum 0MHz
(WW) (640x384,S/M 550v) mode clock 40.07MHz exceeds DDC maximum 0MHz
(WW) (1280x800,S/M 550v) mode clock 83.46MHz exceeds DDC maximum 0MHz
(WW) (640x400,S/M 550v) mode clock 41.73MHz exceeds DDC maximum 0MHz
(WW) (1152x768,S/M 550v) mode clock 64.995MHz exceeds DDC maximum 0MHz
(WW) (576x384,S/M 550v) mode clock 32.497MHz exceeds DDC maximum 0MHz
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
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "640x400" (height 800 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 768)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): Display dimensions: (280, 210) mm
(--) NVIDIA(0): DPI set to (92, 92)
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
	[0] 0	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B]
	[1] 0	0	0xce000000 - 0xceffffff (0x1000000) MX[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfffe000 - 0xcfffefff (0x1000) MX[B]
	[8] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[9] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[10] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[11] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[12] -1	0	0xcfef0000 - 0xcfefffff (0x10000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xce000000 - 0xceffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d47f (0x80) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[23] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[25] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[26] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "abnt2"
(**) Generic Keyboard: XkbModel: "abnt2"
(**) Option "XkbLayout" "br"
(**) Generic Keyboard: XkbLayout: "br"
(**) Option "XkbVariant" "abnt2"
(**) Generic Keyboard: XkbVariant: "abnt2"
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
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
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

```
I hope we can solve this problem!!!

---

### Post by jonesy on 2005-10-18
First, I would recommend editing the /etc/X11/xorg.conf file and commenting out the line:

Section "Module"
...
      Load    "dri"
...
EndSection

The Load "dri" line is not needed when using the binary NVIDIA drivers and the README for the drivers explicitly states to remove that line.  Otherwise, both of your log files indicate no other errors with the XWindows side of things.  Let me know if that changes anything.  You can also decrease the boot time by turning off the NVIDIA boot up logo by adding:

Option "NoLogo" "true"

to the Device section of the /etc/X11/xorg.conf file.

---

### Post by Biffy on 2005-10-18
[QUOTE=jonesy]First, I would recommend editing the /etc/X11/xorg.conf file and commenting out the line:

Section "Module"
...
      Load    "dri"
...
EndSection

The Load "dri" line is not needed when using the binary NVIDIA drivers and the README for the drivers explicitly states to remove that line.  Otherwise, both of your log files indicate no other errors with the XWindows side of things.  Let me know if that changes anything.  You can also decrease the boot time by turning off the NVIDIA boot up logo by adding:

Option "NoLogo" "true"

to the Device section of the /etc/X11/xorg.conf file.[/QUOTE]

Commenting out DRI didnt work, and disabling the NVIDIA-logo didnt work either.

Is this only happening to me and CastleKingside and not to all NVIDIA-users?

---

### Post by Hairy_Palms on 2005-10-18
not happening to me at all, i have a geforce 3, maybe you both have the same card? if so go back to an older driver version that you know worked for you

---

### Post by kabus on 2005-10-18
[QUOTE=Biffy]
Is this only happening to me and CastleKingside and not to all NVIDIA-users?[/QUOTE]

I had the same problem.
X startup got considerably faster after I switched off AGP support by adding

```
Option		"NvAGP" "0"
```

to the "Device" section of xorg.conf

---

### Post by Biffy on 2005-10-18
[QUOTE=kabus]I had the same problem.
X startup got considerably faster after I switched off AGP support by adding

```
Option		"NvAGP" "0"
```

to the "Device" section of xorg.conf[/QUOTE]

No, that didnt solve the problem. :(

---

### Post by moglenstar on 2005-10-18
this is going on a whim here, but i'm using a pci gf2 on my ubuntu server.. and this is my device section of my xorg.conf:

> Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Driver          "nvidia"
        BusID           "PCI:0:10:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        Option          "NoLogo"
EndSection


now, ignoring 

        > BusID           "PCI:0:10:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"

which are things specific to my setup, and compositing which ive enabled..

i notice that you have your videoram size set on your config, try removing this line from the device section

> 
VideoRam    64000


again, this is all on a whim, on account of i dont have that on my xorg.conf, and it boots nice and fast for me.

---

### Post by CastleKingSide on 2005-10-18
I have a Geforce2 MX/MX 400, well I was trying out the "Option		"NvAGP" "0" ", i not just did not work but it made my fps on glxgears go down a little bit (means a lot  to me and my old stuff here) the best fps was without Option		"NvAGP" at all (i tried "0" "1" "2" "3").
The strangest thing happened this morning, when I started my computer it booted really fast (to my parameters), but after a reboot to see if there was a miracle reality kick me again a long wait happened until the lovely nvidia logo...
Right now I am in the middle of another problem with my fstab so ubuntu is mad at me, but as soon as I can figure this out I will go a little bit deeper on this....By the way: am I missing any information about my system that could help??

---

### Post by Biffy on 2005-10-18
Castle: I have the same graphic card as you have. Maybe there is a issue with that card.    (Geforce 2 MX400)

Any info on this?

---

### Post by Biffy on 2005-10-19
Moglenstar: Commenting out the videoram didnt work either.

---

### Post by CastleKingSide on 2005-10-19
Well I don't believe there is a problem with the card because on another distro (debian based too) it worked just fine, the only difference I can remember is that I had did not used Xorg, maybe there is problem between xorg and our card... 
just a thing did you commented only "dri"? cause I got GLcore commented too.

---

### Post by Biffy on 2005-10-20
[QUOTE=CastleKingSide]Well I don't believe there is a problem with the card because on another distro (debian based too) it worked just fine, the only difference I can remember is that I had did not used Xorg, maybe there is problem between xorg and our card... 
just a thing did you commented only "dri"? cause I got GLcore commented too.[/QUOTE]

But this was not a problem in hoary, this problem accured to me when i had upgraded to Breezy.

---

### Post by Biffy on 2005-10-23
No solution to this yet?

---

### Post by tobiturbo on 2005-10-24
[QUOTE=kabus]I had the same problem.
X startup got considerably faster after I switched off AGP support by adding

```
Option		"NvAGP" "0"
```

to the "Device" section of xorg.conf[/QUOTE]


@kabus you made my day :razz:
even the windows in gnome respond faster now

---

### Post by CastleKingSide on 2005-10-24
Man, I am reading more about NVIDIA stuff than any other thing thease days, I just can't find any way to change this... shoud we create a bug log or something? Well right now I am reading the nvidia forum searching for an answer, if i find any thing I'll post here.
See Ya!

---

### Post by Biffy on 2005-10-29
[QUOTE=CastleKingSide]Man, I am reading more about NVIDIA stuff than any other thing thease days, I just can't find any way to change this... shoud we create a bug log or something? Well right now I am reading the nvidia forum searching for an answer, if i find any thing I'll post here.
See Ya![/QUOTE]

I havent solved it either.

Tobiturbo: You dont have a AGP card?

---

### Post by brj on 2005-10-31
[QUOTE=Biffy]Commenting out DRI didnt work, and disabling the NVIDIA-logo didnt work either.

Is this only happening to me and CastleKingside and not to all NVIDIA-users?[/QUOTE]
no, it happens to me as well :(
i have a GeForce2 MX/MX 400 with 64MB.

jakob

---

### Post by Biffy on 2005-11-08
This only happens to people with this very card. Geforce 4 MX 400.

Ubuntu team, help!

---

### Post by Biffy on 2005-12-08
Still no solution to this? I have not solved it yet.

---

### Post by monotux on 2005-12-19
I'm suffering from a high load when using nvidia and xorg - everything came back to normal once I started using nv instead of nvidia - but I want to be able to play once in a while, so I need nvidia working...

I have no idea why it doesn't work - I have a gf3 ti500, and I haven't done anything with my system the last week, but the problems started out last night... :(

---

### Post by Pat_Primate on 2006-01-04
I have also been having this problem, Im using the current ubuntu nvidia drivers V7667 and I have a Geforce 2 mx/mx 400 64meg of ram.  I tried the two suggestions in this thread, commenting out the load dri, and adding nvagp 0, and neither of them fixed the problem (though it might load slightly faster now??)

Anyways I was just joining the discussion in the hopes that a better fix has been found.

---

### Post by bluenova on 2006-04-28
I also have the same issue

Ubuntu 5.10
GeForce2 MX/MX 400

Ubuntu does it's loading, then a black screen with a dash in the top left corner for about 2-4min then I get the Nvidia splash screen and everything is fine from then on.

It worked fine on Fedora Core 4 the past year. I've just moved over to Ubuntu, hi! :D

---

