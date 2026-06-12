---
title: "GPU Hung Nexuiz"
date: 2010-06-11
forum: Gaming &amp; Leisure
---

### Post by duke.tim on 2010-06-11
Okay so I can start the game and it runs fine until about 14 minutes into the game it will crash...giving the error below

```
Jun 11 20:19:43 duke-laptop kernel: [ 2381.760076] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Jun 11 20:19:43 duke-laptop kernel: [ 2381.760085] render error detected, EIR: 0x00000000
```

Is this a bug in the game or is my system (aka driver) need to be updated/changed? Can I fix it?

---

### Post by duke.tim on 2010-06-13
Okay well it's not just Nexuiz...it's any game that uses graphics... I have already turned the settings for desktop effects to none, that seems to have helped reduce the frequency of the error. Still this shouldn't be happening when I play games that are graphics intensive on Vista my computer doesn't crash. What is the Problem?

Just so you know I have to restart the computer to get gnome running again. ```
e.g. startx --:1
``` fails.

---

### Post by duke.tim on 2010-08-06
bump bump bump bump bump

---

### Post by handy on 2010-08-06
What GPU are you running?

If you post your /var/log/Xorg.0.log it could give us a clue as to what is happening?

---

### Post by duke.tim on 2010-08-07
Microprocessor 2.00 GHz Intel Core2 Duo Processor T6400
Microprocessor 2MB L2 Cache
Cache
Memory
4096MB
Memory Max 8192MB
Video Graphics Intel Graphics Media Accelerator 4500MHD
Video Memory Up to 1759MB


```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux duke-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=11dff1c6-e1a3-479d-9b57-86a0b52fe9ad ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug  6 20:35:12 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:2a42:103c:3627 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00007110/8
(--) PCI: (0:0:2:1) 8086:2a43:103c:3627 Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller rev 7, Mem @ 0xd5400000/1048576
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
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
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) GM45
(--) intel(0): Chipset: "GM45"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): Output LVDS1 has no monitor section
(II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
(II) intel(0): Output HDMI1 has no monitor section
(II) intel(0): Output DP1 has no monitor section
(II) intel(0): Output DP2 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): EDID for output LVDS1
(II) intel(0): Manufacturer: SEC  Model: 354c  Serial#: 0
(II) intel(0): Year: 2008  Week: 0
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified
(II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported detailed timing:
(II) intel(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) intel(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) intel(0): Unknown vendor-specific block f
(II) intel(0):  SAMSUNG
(II) intel(0):  160AT02-H02
(II) intel(0): EDID (in hex):
(II) intel(0): 	00ffffffffffff004ca34c3500000000
(II) intel(0): 	00120103802314780a87f594574f8c27
(II) intel(0): 	27505400000001010101010101010101
(II) intel(0): 	010101010101411c56a0500016303020
(II) intel(0): 	250061c6100000190000000f00000000
(II) intel(0): 	00000000001eb4027400000000fe0053
(II) intel(0): 	414d53554e470a2020202020000000fe
(II) intel(0): 	00313630415430322d4830320a2000ab
(II) intel(0): Not using default mode "320x175" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "360x200" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
(II) intel(0): Not using default mode "1024x768" (interlace mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "416x312" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
(II) intel(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1200" (monitor doesn't support reduced blanking)
(II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
(II) intel(0): Printing probed modes for output LVDS1
(II) intel(0): Modeline "1366x768"x60.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
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
(II) intel(0): EDID for output HDMI1
(II) intel(0): EDID for output DP1
(II) intel(0): EDID for output DP2
(II) intel(0): Output VGA1 disconnected
(II) intel(0): Output LVDS1 connected
(II) intel(0): Output HDMI1 disconnected
(II) intel(0): Output DP1 disconnected
(II) intel(0): Output DP2 disconnected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output LVDS1 using initial mode 1366x768
(II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(==) Depth 24 pixmap format is 32 bpp
(II) intel(0): [DRI2] Setup complete
(**) intel(0): Kernel mode setting active, disabling FBC.
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(**) intel(0): SwapBuffers wait enabled
(==) intel(0): VideoRam: 262144 KB
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
(==) intel(0): DPMS enabled
(==) intel(0): Intel XvMC decoder disabled
(II) intel(0): Set up textured video
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
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI2 GL provider for screen 0
(II) intel(0): Setting screen physical size to 361 x 203
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event3)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event3"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event8)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event8"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (/dev/input/event2)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Mic at Ext Front Jack (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Intel Line Out at Ext Front Jack (/dev/input/event11)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HP Webcam (/dev/input/event6)
(**) HP Webcam: Applying InputClass "evdev keyboard catchall"
(**) HP Webcam: always reports core events
(**) HP Webcam: Device: "/dev/input/event6"
(II) HP Webcam: Found keys
(II) HP Webcam: Configuring as keyboard
(II) XINPUT: Adding extended input device "HP Webcam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event5)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event5"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event12)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event12"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event7)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event4)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event4"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/event13)
(**) Targus BT Laser Notebook Mouse: Applying InputClass "evdev pointer catchall"
(**) Targus BT Laser Notebook Mouse: always reports core events
(**) Targus BT Laser Notebook Mouse: Device: "/dev/input/event13"
(II) Targus BT Laser Notebook Mouse: Found 3 mouse buttons
(II) Targus BT Laser Notebook Mouse: Found scroll wheel(s)
(II) Targus BT Laser Notebook Mouse: Found relative axes
(II) Targus BT Laser Notebook Mouse: Found x and y relative axes
(II) Targus BT Laser Notebook Mouse: Found absolute axes
(II) Targus BT Laser Notebook Mouse: Configuring as mouse
(**) Targus BT Laser Notebook Mouse: YAxisMapping: buttons 4 and 5
(**) Targus BT Laser Notebook Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Targus BT Laser Notebook Mouse" (type: MOUSE)
(II) Targus BT Laser Notebook Mouse: initialized for relative axes.
(WW) Targus BT Laser Notebook Mouse: ignoring absolute axes.
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) config/udev: removing device Targus BT Laser Notebook Mouse
(II) Targus BT Laser Notebook Mouse: Close
(II) UnloadModule: "evdev"
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/event13)
(**) Targus BT Laser Notebook Mouse: Applying InputClass "evdev pointer catchall"
(**) Targus BT Laser Notebook Mouse: always reports core events
(**) Targus BT Laser Notebook Mouse: Device: "/dev/input/event13"
(II) Targus BT Laser Notebook Mouse: Found 3 mouse buttons
(II) Targus BT Laser Notebook Mouse: Found scroll wheel(s)
(II) Targus BT Laser Notebook Mouse: Found relative axes
(II) Targus BT Laser Notebook Mouse: Found x and y relative axes
(II) Targus BT Laser Notebook Mouse: Found absolute axes
(II) Targus BT Laser Notebook Mouse: Configuring as mouse
(**) Targus BT Laser Notebook Mouse: YAxisMapping: buttons 4 and 5
(**) Targus BT Laser Notebook Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Targus BT Laser Notebook Mouse" (type: MOUSE)
(II) Targus BT Laser Notebook Mouse: initialized for relative axes.
(WW) Targus BT Laser Notebook Mouse: ignoring absolute axes.
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) XKB: reuse xkmfile /var/lib/xkb/server-C2602025D36F4EED7C5DCC7D374EA12453602E56.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-C2602025D36F4EED7C5DCC7D374EA12453602E56.xkm
(II) config/udev: removing device Targus BT Laser Notebook Mouse
(II) Targus BT Laser Notebook Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/event13)
(**) Targus BT Laser Notebook Mouse: Applying InputClass "evdev pointer catchall"
(**) Targus BT Laser Notebook Mouse: always reports core events
(**) Targus BT Laser Notebook Mouse: Device: "/dev/input/event13"
(II) Targus BT Laser Notebook Mouse: Found 3 mouse buttons
(II) Targus BT Laser Notebook Mouse: Found scroll wheel(s)
(II) Targus BT Laser Notebook Mouse: Found relative axes
(II) Targus BT Laser Notebook Mouse: Found x and y relative axes
(II) Targus BT Laser Notebook Mouse: Found absolute axes
(II) Targus BT Laser Notebook Mouse: Configuring as mouse
(**) Targus BT Laser Notebook Mouse: YAxisMapping: buttons 4 and 5
(**) Targus BT Laser Notebook Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Targus BT Laser Notebook Mouse" (type: MOUSE)
(II) Targus BT Laser Notebook Mouse: initialized for relative axes.
(WW) Targus BT Laser Notebook Mouse: ignoring absolute axes.
(II) config/udev: removing device Targus BT Laser Notebook Mouse
(II) Targus BT Laser Notebook Mouse: Close
(II) UnloadModule: "evdev"
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) intel(0): EDID vendor "SEC", prod id 13644
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/event13)
(**) Targus BT Laser Notebook Mouse: Applying InputClass "evdev pointer catchall"
(**) Targus BT Laser Notebook Mouse: always reports core events
(**) Targus BT Laser Notebook Mouse: Device: "/dev/input/event13"
(II) Targus BT Laser Notebook Mouse: Found 3 mouse buttons
(II) Targus BT Laser Notebook Mouse: Found scroll wheel(s)
(II) Targus BT Laser Notebook Mouse: Found relative axes
(II) Targus BT Laser Notebook Mouse: Found x and y relative axes
(II) Targus BT Laser Notebook Mouse: Found absolute axes
(II) Targus BT Laser Notebook Mouse: Configuring as mouse
(**) Targus BT Laser Notebook Mouse: YAxisMapping: buttons 4 and 5
(**) Targus BT Laser Notebook Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Targus BT Laser Notebook Mouse" (type: MOUSE)
(II) Targus BT Laser Notebook Mouse: initialized for relative axes.
(WW) Targus BT Laser Notebook Mouse: ignoring absolute axes.
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: removing device Targus BT Laser Notebook Mouse
(II) Targus BT Laser Notebook Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/event13)
(**) Targus BT Laser Notebook Mouse: Applying InputClass "evdev pointer catchall"
(**) Targus BT Laser Notebook Mouse: always reports core events
(**) Targus BT Laser Notebook Mouse: Device: "/dev/input/event13"
(II) Targus BT Laser Notebook Mouse: Found 3 mouse buttons
(II) Targus BT Laser Notebook Mouse: Found scroll wheel(s)
(II) Targus BT Laser Notebook Mouse: Found relative axes
(II) Targus BT Laser Notebook Mouse: Found x and y relative axes
(II) Targus BT Laser Notebook Mouse: Found absolute axes
(II) Targus BT Laser Notebook Mouse: Configuring as mouse
(**) Targus BT Laser Notebook Mouse: YAxisMapping: buttons 4 and 5
(**) Targus BT Laser Notebook Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Targus BT Laser Notebook Mouse" (type: MOUSE)
(II) Targus BT Laser Notebook Mouse: initialized for relative axes.
(WW) Targus BT Laser Notebook Mouse: ignoring absolute axes.
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: removing device Targus BT Laser Notebook Mouse
(II) Targus BT Laser Notebook Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/event13)
(**) Targus BT Laser Notebook Mouse: Applying InputClass "evdev pointer catchall"
(**) Targus BT Laser Notebook Mouse: always reports core events
(**) Targus BT Laser Notebook Mouse: Device: "/dev/input/event13"
(II) Targus BT Laser Notebook Mouse: Found 3 mouse buttons
(II) Targus BT Laser Notebook Mouse: Found scroll wheel(s)
(II) Targus BT Laser Notebook Mouse: Found relative axes
(II) Targus BT Laser Notebook Mouse: Found x and y relative axes
(II) Targus BT Laser Notebook Mouse: Found absolute axes
(II) Targus BT Laser Notebook Mouse: Configuring as mouse
(**) Targus BT Laser Notebook Mouse: YAxisMapping: buttons 4 and 5
(**) Targus BT Laser Notebook Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Targus BT Laser Notebook Mouse" (type: MOUSE)
(II) Targus BT Laser Notebook Mouse: initialized for relative axes.
(WW) Targus BT Laser Notebook Mouse: ignoring absolute axes.
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: removing device Targus BT Laser Notebook Mouse
(II) Targus BT Laser Notebook Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/event13)
(**) Targus BT Laser Notebook Mouse: Applying InputClass "evdev pointer catchall"
(**) Targus BT Laser Notebook Mouse: always reports core events
(**) Targus BT Laser Notebook Mouse: Device: "/dev/input/event13"
(II) Targus BT Laser Notebook Mouse: Found 3 mouse buttons
(II) Targus BT Laser Notebook Mouse: Found scroll wheel(s)
(II) Targus BT Laser Notebook Mouse: Found relative axes
(II) Targus BT Laser Notebook Mouse: Found x and y relative axes
(II) Targus BT Laser Notebook Mouse: Found absolute axes
(II) Targus BT Laser Notebook Mouse: Configuring as mouse
(**) Targus BT Laser Notebook Mouse: YAxisMapping: buttons 4 and 5
(**) Targus BT Laser Notebook Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Targus BT Laser Notebook Mouse" (type: MOUSE)
(II) Targus BT Laser Notebook Mouse: initialized for relative axes.
(WW) Targus BT Laser Notebook Mouse: ignoring absolute axes.
(II) XKB: reuse xkmfile /var/lib/xkb/server-C2602025D36F4EED7C5DCC7D374EA12453602E56.xkm
(II) config/udev: removing device Targus BT Laser Notebook Mouse
(II) Targus BT Laser Notebook Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Targus BT Laser Notebook Mouse (/dev/input/event13)
(**) Targus BT Laser Notebook Mouse: Applying InputClass "evdev pointer catchall"
(**) Targus BT Laser Notebook Mouse: always reports core events
(**) Targus BT Laser Notebook Mouse: Device: "/dev/input/event13"
(II) Targus BT Laser Notebook Mouse: Found 3 mouse buttons
(II) Targus BT Laser Notebook Mouse: Found scroll wheel(s)
(II) Targus BT Laser Notebook Mouse: Found relative axes
(II) Targus BT Laser Notebook Mouse: Found x and y relative axes
(II) Targus BT Laser Notebook Mouse: Found absolute axes
(II) Targus BT Laser Notebook Mouse: Configuring as mouse
(**) Targus BT Laser Notebook Mouse: YAxisMapping: buttons 4 and 5
(**) Targus BT Laser Notebook Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Targus BT Laser Notebook Mouse" (type: MOUSE)
(II) Targus BT Laser Notebook Mouse: initialized for relative axes.
(WW) Targus BT Laser Notebook Mouse: ignoring absolute axes.
(II) XKB: reuse xkmfile /var/lib/xkb/server-C2602025D36F4EED7C5DCC7D374EA12453602E56.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-C2602025D36F4EED7C5DCC7D374EA12453602E56.xkm

```

---

### Post by handy on 2010-08-08
It looks like everything is ok from your log file.

You could check & see if there is a later Linux driver available.

I know from my experience with the open ATi drivers, when I do the phoronix test suite test that Nexuiz is by far the hardest test on my OpenGL 3D, than any quake engined game flies by comparison.

You are in a tough situation. 

Perhaps your RAM has a problem? You could try the mem-test that is an option at boot on so many Live/install/CDs for distros. I expect that Ubuntu still has that on it. 

As far as testing the GPU I don't know of a specific (may exist?) you could download (big download) the phoronix test suite which will test your machine on a variety of games/resolutions & spit out the results. It could give you more info'. As I mentioned before it uses Nexuiz as part of the tests.

[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

Good luck with it, let us know how you go, in doing so you may attract someone's attention that knows more than I.

---

