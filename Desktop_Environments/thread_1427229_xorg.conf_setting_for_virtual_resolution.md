---
title: "xorg.conf setting for virtual resolution"
date: 2010-03-11
forum: Desktop Environments
---

### Post by YaacovI on 2010-03-11
I'm trying to add an external monitor beside my laptop screen. I've just upgraded to 9.10 from the LTS, where the external monitor worked fine.

Using compiz, I ran into the 2048x2048 virtual resolution limit, since my two monitors are 1280x800 and 1400x1050. When I tried to put the monitors side by side, I got a message saying that the virtual screen resolution needed to be recalculated, clicked OK and then was told to logout. Upon logout the screen got messed up, it looked like five screens across with lines from one screen pushing into the other so that it wasn't readable. I rebooted and ubuntu hung before getting to the login screen. I deleted the xorg.conf file and was able to reboot fine, but the monitors were mirrored again.

After checking forums, I turned off compiz and am using metacity, since people report that they have solved similar problems by using metacity. However, I'm still hitting the 2048x2048 virtual resolution limit.

Here's what I've done. With the monitors set to mirror, I run the following commands:

```

xrandr --output LVDS1 --mode 1280x800
xrandr --newmode "1400x1050_60.00"  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync
xrandr --addmode VGA1 1400x1050_60.00
xrandr --output VGA1 --mode 1400x1050_60.00

```

This works, and now the two monitors are running at the correct resolution, but they are still mirroring rather than side by side. Next, I try:
```
xrandr --fb 2680x1050
```
and the output is:
```
xrandr: screen cannot be larger than 2048x2048 (desired size 2680x1050)
```
I get the same output if I try:
```
xrandr --output VGA1 --right-of LVDS
```

I read [here]("https://wiki.ubuntu.com/X/Config/Resolution") and [here]("http://en.opensuse.org/Multiple_Screens_Using_XRandR") that I need to use xorg.conf to set my virtual resolution. However, when I create an xorg.conf, I get the same problem with the messed up screen that I got originally. I've tried my old xorg.conf from 8.04, an edited version of it that only contained display related info and a clean xorg.conf with the virtual resolution set as I need it (see below). All of them give the same problem I got initially.

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2680 1050
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection 

```

Any suggestions as to how I can get the virtual resolution up to 2680x1050 would be appreciated!

---

### Post by gamersblood on 2010-03-11
Can you give your system information? Special about the GPU

---

### Post by YaacovI on 2010-03-11
Thanks gamersblood, the system is an Inspiron 700m. The GPU is the Intel Corporation 82852/855GM Integrated Graphics Device.

Here's the Xorg.0.log file in case it helps.

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux littleglowingfriend 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=10396ff1-5fe0-4893-8090-bf35a20fb707 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 11 13:47:42 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:3582:1028:018d Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe8000000/134217728, 0xe0000000/524288, I/O @ 0x00001800/8
(==) Using default built-in configuration (39 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default intel Device 0"
		Driver	"intel"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default intel Screen 0"
		Device	"Builtin Default intel Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default i810 Device 0"
		Driver	"i810"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default i810 Screen 0"
		Device	"Builtin Default i810 Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default intel Screen 0"
		Screen	"Builtin Default i810 Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default intel Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default intel Device 0"
(==) No monitor specified for screen "Builtin Default intel Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default i810 Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default i810 Device 0"
(==) No monitor specified for screen "Builtin Default i810 Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (3)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "i810"
(WW) Warning, couldn't open module i810
(II) UnloadModule: "i810"
(EE) Failed to load module "i810" (module does not exist, 0)
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Builtin Default intel Screen 0" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 855GME
(--) intel(0): Chipset: "852GM/855GM"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output DVI1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 3157  Serial#: 0
(II) intel(0): Year: 2004  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 18
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.0 MHz   Image Size:  261 x 163 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1472 h_border: 0
(II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 849 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  Y4396121W1
(II) intel(0):  ÿúñã±{@
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca3573100000000
(II) intel(0): 	000e0103801c12780a87f594574f8c27
(II) intel(0): 	27505400080001010101010101010101
(II) intel(0): 	0101010101014a1d00c0502031301030
(II) intel(0): 	130005a3100000190000000f00000000
(II) intel(0): 	000000000032d2023200000000fe0059
(II) intel(0): 	343339360131323157310a20000000fe
(II) intel(0): 	00fffaf1e3b17b400001010a202000a7
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output DVI1 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1280x800
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(II) intel(0): Tiled allocation successful.
(II) UXA(0): Driver registered support for the following operations:
(II)         solid
(II)         copy
(II)         composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): No memory allocations
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(WW) intel(0): Disabling Xv because no adaptors could be initialized.
(II) intel(0): direct rendering: DRI2 Enabled
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 261 x 163
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event6"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 3157  Serial#: 0
(II) intel(0): Year: 2004  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 18
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.0 MHz   Image Size:  261 x 163 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1472 h_border: 0
(II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 849 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  Y4396121W1
(II) intel(0):  ÿúñã±{@
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca3573100000000
(II) intel(0): 	000e0103801c12780a87f594574f8c27
(II) intel(0): 	27505400080001010101010101010101
(II) intel(0): 	0101010101014a1d00c0502031301030
(II) intel(0): 	130005a3100000190000000f00000000
(II) intel(0): 	000000000032d2023200000000fe0059
(II) intel(0): 	343339360131323157310a20000000fe
(II) intel(0): 	00fffaf1e3b17b400001010a202000a7
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 3157  Serial#: 0
(II) intel(0): Year: 2004  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 18
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.0 MHz   Image Size:  261 x 163 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1472 h_border: 0
(II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 849 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  Y4396121W1
(II) intel(0):  ÿúñã±{@
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca3573100000000
(II) intel(0): 	000e0103801c12780a87f594574f8c27
(II) intel(0): 	27505400080001010101010101010101
(II) intel(0): 	0101010101014a1d00c0502031301030
(II) intel(0): 	130005a3100000190000000f00000000
(II) intel(0): 	000000000032d2023200000000fe0059
(II) intel(0): 	343339360131323157310a20000000fe
(II) intel(0): 	00fffaf1e3b17b400001010a202000a7
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 3157  Serial#: 0
(II) intel(0): Year: 2004  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 18
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.0 MHz   Image Size:  261 x 163 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1472 h_border: 0
(II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 849 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  Y4396121W1
(II) intel(0):  ÿúñã±{@
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca3573100000000
(II) intel(0): 	000e0103801c12780a87f594574f8c27
(II) intel(0): 	27505400080001010101010101010101
(II) intel(0): 	0101010101014a1d00c0502031301030
(II) intel(0): 	130005a3100000190000000f00000000
(II) intel(0): 	000000000032d2023200000000fe0059
(II) intel(0): 	343339360131323157310a20000000fe
(II) intel(0): 	00fffaf1e3b17b400001010a202000a7
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 3157  Serial#: 0
(II) intel(0): Year: 2004  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 18
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.0 MHz   Image Size:  261 x 163 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1472 h_border: 0
(II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 849 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  Y4396121W1
(II) intel(0):  ÿúñã±{@
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca3573100000000
(II) intel(0): 	000e0103801c12780a87f594574f8c27
(II) intel(0): 	27505400080001010101010101010101
(II) intel(0): 	0101010101014a1d00c0502031301030
(II) intel(0): 	130005a3100000190000000f00000000
(II) intel(0): 	000000000032d2023200000000fe0059
(II) intel(0): 	343339360131323157310a20000000fe
(II) intel(0): 	00fffaf1e3b17b400001010a202000a7
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 3157  Serial#: 0
(II) intel(0): Year: 2004  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 18
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.0 MHz   Image Size:  261 x 163 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1472 h_border: 0
(II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 849 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  Y4396121W1
(II) intel(0):  ÿúñã±{@
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca3573100000000
(II) intel(0): 	000e0103801c12780a87f594574f8c27
(II) intel(0): 	27505400080001010101010101010101
(II) intel(0): 	0101010101014a1d00c0502031301030
(II) intel(0): 	130005a3100000190000000f00000000
(II) intel(0): 	000000000032d2023200000000fe0059
(II) intel(0): 	343339360131323157310a20000000fe
(II) intel(0): 	00fffaf1e3b17b400001010a202000a7
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DVI1
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 3157  Serial#: 0
(II) intel(0): Year: 2004  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 28  vert.: 18
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Supported established timings:
(II) intel(0): 1024x768@60Hz
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 75.0 MHz   Image Size:  261 x 163 mm
(II) intel(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1472 h_border: 0
(II) intel(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 849 v_border: 0
(WW) intel(0): Unknown vendor-specific block f
(II) intel(0):  Y4396121W1
(II) intel(0):  ÿúñã±{@
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca3573100000000
(II) intel(0): 	000e0103801c12780a87f594574f8c27
(II) intel(0): 	27505400080001010101010101010101
(II) intel(0): 	0101010101014a1d00c0502031301030
(II) intel(0): 	130005a3100000190000000f00000000
(II) intel(0): 	000000000032d2023200000000fe0059
(II) intel(0): 	343339360131323157310a20000000fe
(II) intel(0): 	00fffaf1e3b17b400001010a202000a7
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1280x800"x60.0   74.98  1280 1296 1344 1472  800 801 804 849 -hsync -vsync (50.9 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): EDID for output DVI1
```

---

