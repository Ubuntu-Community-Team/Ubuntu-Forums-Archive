---
title: "DVI video output"
date: 2008-12-18
forum: Desktop Environments
---

### Post by webtent on 2008-12-18
Can someone help me determine if my Matrox G550 card and new ASUS VK222H
widescreen monitor will support DVI output on the card. It is dual head
with one vga I have a second LCD connected and one DVI with the new
monitor. I made what I thought were the appropriate changes to my
xorg.conf and the monitor came up blank. I disconnected the DVI and put
in a VGA adapter and it switched automatically to VGA input and came up.

Below is my xorg.conf and log output. I did notice 'Setting vga for
screen' and it does not look like I am running the Matrox driver? I
downloaded the latest driver, which has an install.sh script, but it
says 'The X server drivers included in this installation package do not
support the current version of your X server'. I did come across some
reading on the web that my card DVI output only supports up to 1280x1024
resolution, so I will want to get a new card to support 1440x900. Can
someone recommend a card that can work well with the latest Ubuntu? However, I do see some information in the log below about the 1440x900 resolution, does this mean it may be possible?

```
<snip>
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"vbe"
   Load  "mga"
   Load  "glx"
   Load  "dri"
EndSection
<snip>
Section "Device"
	Identifier	"G550_0"
	Driver		"mga"
	BusID		"PCI:1:0:0"
   Screen 0
EndSection
Section "Device"
	Identifier	"G550_1"
	Driver		"mga"
	BusID		"PCI:1:0:0"
   Screen 1
EndSection
Section "Monitor"
        Identifier      "AOC LM-700"
        Option          "DPMS"
	HorizSync	30-70
	VertRefresh	43-75
EndSection
Section "Monitor"
        Identifier      "ASUS VK222H"
        Option          "DPMS"
	HorizSync	30-70
	VertRefresh	60-80
EndSection
Section "Screen"
	Identifier	"Screen_0"
	Device		"G550_0"
	Monitor		"ASUS VK222H"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "Screen"
	Identifier	"Screen_1"
	Device		"G550_1"
	Monitor		"AOC LM-700"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
        Screen          "Screen_0" LeftOf "Screen_1"
   Screen      "Screen_1"
   Option "Xinerama"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
```

```
X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux columbus 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 17 22:55:06 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen_0" (0)
(**) |   |-->Monitor "ASUS VK222H"
(**) |   |-->Device "G550_0"
(**) |-->Screen "Screen_1" (1)
(**) |   |-->Monitor "AOC LM-700"
(**) |   |-->Device "G550_1"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "Xinerama"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
<snip>
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
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

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1458,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2571 card 0000,0000 rev 02 class 06,04,00 hdr 01
<snip>
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
<snip>
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
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
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mga"
(II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) Module mga: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.4.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "mga"
(II) Reloading /usr/lib/xorg/modules/drivers//mga_drv.so
(II) UnloadModule: "mga"
(II) Failed to load module "mga" (already loaded, 2)
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
(II) MGA: driver for Matrox chipsets: mga2064w, mga1064sg, mga2164w,
	mga2164w AGP, mgag100, mgag100 PCI, mgag200, mgag200 PCI,
	mgag200 SE A PCI, mgag200 SE B PCI, mgag400, mgag550
(II) Primary Device is: PCI 01:00:0
(--) Chipset mgag550 found
(--) Chipset mgag550 found
(II) resource ranges after xf86ClaimFixedResources() call:
<snip>
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(--) MGA(0): Chipset: "mgag550"
(**) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(==) MGA(0): Using AGP 1x mode
(==) MGA(0): Using XAA acceleration
(--) MGA(0): Linear framebuffer at 0xF0000000
(==) MGA(0): MMIO registers at 0xF2000000
(--) MGA(0): Pseudo-DMA transfer window at 0xF3000000
(==) MGA(0): BIOS at 0xC0000
(--) MGA(0): Video BIOS info block at offset 0x07CE0
(==) MGA(0): Write-combining range (0xf0000000,0x2000000)
(--) MGA(0): Crtc2 will use 8192K of VideoRam
(--) MGA(0): VideoRAM: 24576 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) MGA(0): Splitting WC range: base: 0xf0000000, size: 0x1800000
(==) MGA(0): Write-combining range (0xf1000000,0x800000)
(==) MGA(0): Write-combining range (0xf0000000,0x1800000)
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C device "DDC P1:ddc2" removed.
(II) MGA(0): I2C Monitor info: (nil)
(II) MGA(0): end of I2C Monitor info
(--) MGA(0): No DDC signal
(II) MGA(0): DDC Monitor info: (nil)
(II) MGA(0): end of DDC Monitor info
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) MGA(0): initializing int10
(II) MGA(0): Primary V_BIOS segment is: 0xc000
(II) MGA(0): VESA BIOS detected
(II) MGA(0): VESA VBE Version 3.0
(II) MGA(0): VESA VBE Total Mem: 32768 kB
(II) MGA(0): VESA VBE OEM: Matrox Graphics Inc.
(II) MGA(0): VESA VBE OEM Software Rev: 1.4
(II) MGA(0): VESA VBE OEM Vendor: Matrox
(II) MGA(0): VESA VBE OEM Product: Matrox G550
(II) MGA(0): VESA VBE OEM Product Rev: 00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) MGA(0): VESA VBE DDC supported
(II) MGA(0): VESA VBE DDC Level 2
(II) MGA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) MGA(0): VESA VBE DDC read successfully
(II) MGA(0): VBE DDC Monitor info: 0x824d140
(II) MGA(0): Manufacturer: ACI  Model: 22a6  Serial#: 47959
(II) MGA(0): Year: 2008  Week: 34
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MGA(0): Sync:  Separate
(II) MGA(0): Max H-Image Size [cm]: horiz.: 53  vert.: 30
(II) MGA(0): Gamma: 2.20
(II) MGA(0): DPMS capabilities: Off; RGB/Color Display
(II) MGA(0): First detailed timing is preferred mode
(II) MGA(0): redX: 0.644 redY: 0.332   greenX: 0.286 greenY: 0.601
(II) MGA(0): blueX: 0.152 blueY: 0.076   whiteX: 0.312 whiteY: 0.328
(II) MGA(0): Supported VESA Video Modes:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@67Hz
(II) MGA(0): 640x480@72Hz
(II) MGA(0): 640x480@75Hz
(II) MGA(0): 800x600@56Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@72Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 832x624@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@70Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): 1280x1024@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported Future Video Modes:
(II) MGA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) MGA(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) MGA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MGA(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) MGA(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) MGA(0): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) MGA(0): Supported additional Video Mode:
(II) MGA(0): clock: 146.0 MHz   Image Size:  473 x 296 mm
(II) MGA(0): h_active: 1680  h_sync: 1960  h_sync_end 2136 h_blank_end 2240 h_border: 0
(II) MGA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) MGA(0): Serial No: 88LMTF047959
(II) MGA(0): Ranges: V min: 55  V max: 75 Hz, H min: 30  H max: 85 kHz, PixClock max 160 MHz
(II) MGA(0): Monitor name: ASUS VK222H
(II) MGA(0): EDID (in hex):
(II) MGA(0): 	00ffffffffffff000469a62257bb0000
(II) MGA(0): 	2212010368351e782ac720a455499927
(II) MGA(0): 	135054bfef00714f814081809500b300
(II) MGA(0): 	81000101010108399030621a274018b0
(II) MGA(0): 	3640d9281100001c000000ff0038384c
(II) MGA(0): 	4d54463034373935390a000000fd0037
(II) MGA(0): 	4b1e5510000a202020202020000000fc
(II) MGA(0): 	004153555320564b323232480a200082
(II) MGA(0): end of VBE DDC Monitor info

(II) MGA(0): EDID vendor "ACI", prod id 8870
(II) MGA(0): Using hsync ranges from config file
(II) MGA(0): Using vrefresh ranges from config file
(II) MGA(0): Printing DDC gathered Modelines:
(II) MGA(0): Modeline "1680x1050"x0.0  146.00  1680 1960 2136 2240  1050 1053 1059 1089 -hsync +vsync (65.2 kHz)
(II) MGA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MGA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) MGA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) MGA(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) MGA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) MGA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) MGA(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) MGA(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) MGA(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) MGA(0): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) MGA(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) MGA(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 17 MHz
(--) MGA(0): Max pixel clock is 1200 MHz
(II) MGA(0): ASUS VK222H: Using hsync range of 30.00-70.00 kHz
(II) MGA(0): ASUS VK222H: Using vrefresh range of 60.00-80.00 Hz
(II) MGA(0): ASUS VK222H: Using maximum pixel clock of 160.00 MHz
(II) MGA(0): Clock range:  17.75 to 1200.00 MHz
(II) MGA(0): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "360x200" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (vrefresh out of range)
(II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(0): Not using default mode "400x300" (vrefresh out of range)
(II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(0): Not using default mode "400x300" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1280x960" (hsync out of range)
(II) MGA(0): Not using default mode "640x480" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (hsync out of range)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1792x1344" (hsync out of range)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (hsync out of range)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1856x1392" (hsync out of range)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (hsync out of range)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (hsync out of range)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1152x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "576x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1152x864" (hsync out of range)
(II) MGA(0): Not using default mode "576x432" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1200" (hsync out of range)
(II) MGA(0): Not using default mode "960x600" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1200" (hsync out of range)
(II) MGA(0): Not using default mode "960x600" (hsync out of range)
(II) MGA(0): Not using default mode "1920x1440" (hsync out of range)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (hsync out of range)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (hsync out of range)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using default mode "2048x1536" (hsync out of range)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using driver mode "800x600" (vrefresh out of range)
(II) MGA(0): Not using driver mode "1280x1024" (hsync out of range)
(--) MGA(0): Has SDRAM
(--) MGA(0): Virtual size is 1280x1024 (pitch 1280)
(**) MGA(0): *Driver mode "1280x1024": 109.0 MHz, 63.7 kHz, 59.9 Hz
(II) MGA(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) MGA(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) MGA(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) MGA(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) MGA(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) MGA(0): Display dimensions: (530, 300) mm
(**) MGA(0): DPI set to (61, 86)
(II) MGA(0): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(--) MGA(1): Chipset: "mgag550"
(**) MGA(1): Depth 24, (--) framebuffer bpp 32
(==) MGA(1): RGB weight 888
(==) MGA(1): Using AGP 1x mode
(==) MGA(1): Using XAA acceleration
(--) MGA(1): Linear framebuffer at 0xF0000000
(==) MGA(1): MMIO registers at 0xF2000000
(--) MGA(1): Pseudo-DMA transfer window at 0xF3000000
(==) MGA(1): BIOS at 0xC0000
(--) MGA(1): Video BIOS info block at offset 0x07CE0
(==) MGA(1): Write-combining range (0xf0000000,0x2000000)
(--) MGA(1): VideoRAM: 8192 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(==) MGA(1): Write-combining range (0xf1800000,0x800000)
(II) MGA(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(1): I2C bus "DDC P2" initialized.
(II) MGA(1): I2C bus "MAVEN" initialized.
(II) MGA(1): Failed to register MGA-TVO I2C device!
(II) MGA(1): I2C device "DDC P2:ddc2" registered at address 0xA0.
(II) MGA(1): I2C Monitor info: 0x824f230
(II) MGA(1): Manufacturer: ACI  Model: 22a6  Serial#: 47959
(II) MGA(1): Year: 2008  Week: 34
(II) MGA(1): EDID Version: 1.3
(II) MGA(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MGA(1): Sync:  Separate
(II) MGA(1): Max H-Image Size [cm]: horiz.: 53  vert.: 30
(II) MGA(1): Gamma: 2.20
(II) MGA(1): DPMS capabilities: Off; RGB/Color Display
(II) MGA(1): First detailed timing is preferred mode
(II) MGA(1): redX: 0.644 redY: 0.332   greenX: 0.286 greenY: 0.601
(II) MGA(1): blueX: 0.152 blueY: 0.076   whiteX: 0.312 whiteY: 0.328
(II) MGA(1): Supported VESA Video Modes:
(II) MGA(1): 720x400@70Hz
(II) MGA(1): 640x480@60Hz
(II) MGA(1): 640x480@67Hz
(II) MGA(1): 640x480@72Hz
(II) MGA(1): 640x480@75Hz
(II) MGA(1): 800x600@56Hz
(II) MGA(1): 800x600@60Hz
(II) MGA(1): 800x600@72Hz
(II) MGA(1): 800x600@75Hz
(II) MGA(1): 832x624@75Hz
(II) MGA(1): 1024x768@60Hz
(II) MGA(1): 1024x768@70Hz
(II) MGA(1): 1024x768@75Hz
(II) MGA(1): 1280x1024@75Hz
(II) MGA(1): Manufacturer's mask: 0
(II) MGA(1): Supported Future Video Modes:
(II) MGA(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) MGA(1): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) MGA(1): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MGA(1): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) MGA(1): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) MGA(1): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
(II) MGA(1): Supported additional Video Mode:
(II) MGA(1): clock: 146.0 MHz   Image Size:  473 x 296 mm
(II) MGA(1): h_active: 1680  h_sync: 1960  h_sync_end 2136 h_blank_end 2240 h_border: 0
(II) MGA(1): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) MGA(1): Serial No: 88LMTF047959
(II) MGA(1): Ranges: V min: 55  V max: 75 Hz, H min: 30  H max: 85 kHz, PixClock max 160 MHz
(II) MGA(1): Monitor name: ASUS VK222H
(II) MGA(1): EDID (in hex):
(II) MGA(1): 	00ffffffffffff000469a62257bb0000
(II) MGA(1): 	2212010368351e782ac720a455499927
(II) MGA(1): 	135054bfef00714f814081809500b300
(II) MGA(1): 	81000101010108399030621a274018b0
(II) MGA(1): 	3640d9281100001c000000ff0038384c
(II) MGA(1): 	4d54463034373935390a000000fd0037
(II) MGA(1): 	4b1e5510000a202020202020000000fc
(II) MGA(1): 	004153555320564b323232480a200082
(II) MGA(1): end of I2C Monitor info
(II) MGA(1): EDID vendor "ACI", prod id 8870
(II) MGA(1): Using hsync ranges from config file
(II) MGA(1): Using vrefresh ranges from config file
(II) MGA(1): Printing DDC gathered Modelines:
(II) MGA(1): Modeline "1680x1050"x0.0  146.00  1680 1960 2136 2240  1050 1053 1059 1089 -hsync +vsync (65.2 kHz)
(II) MGA(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) MGA(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) MGA(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) MGA(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) MGA(1): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) MGA(1): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) MGA(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) MGA(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) MGA(1): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) MGA(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) MGA(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) MGA(1): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) MGA(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) MGA(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) MGA(1): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) MGA(1): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) MGA(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) MGA(1): Modeline "1440x900"x59.9  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) MGA(1): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(II) MGA(1): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
(==) MGA(1): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(1): Min pixel clock is 17 MHz
(--) MGA(1): Max pixel clock is 234 MHz
(II) MGA(1): AOC LM-700: Using hsync range of 30.00-70.00 kHz
(II) MGA(1): AOC LM-700: Using vrefresh range of 43.00-75.00 Hz
(II) MGA(1): AOC LM-700: Using maximum pixel clock of 160.00 MHz
(II) MGA(1): Clock range:  17.75 to 234.00 MHz
(II) MGA(1): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(1): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(1): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(1): Not using default mode "360x200" (vrefresh out of range)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(1): Not using default mode "320x240" (vrefresh out of range)
(II) MGA(1): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(1): Not using default mode "400x300" (vrefresh out of range)
(II) MGA(1): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) MGA(1): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(1): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(1): Not using default mode "1280x960" (hsync out of range)
(II) MGA(1): Not using default mode "640x480" (hsync out of range)
(II) MGA(1): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(1): Not using default mode "640x512" (hsync out of range)
(II) MGA(1): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(1): Not using default mode "640x512" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(1): Not using default mode "800x600" (hsync out of range)
(II) MGA(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(1): Not using default mode "896x672" (hsync out of range)
(II) MGA(1): Not using default mode "1792x1344" (insufficient memory for mode)
(II) MGA(1): Not using default mode "896x672" (hsync out of range)
(II) MGA(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(1): Not using default mode "928x696" (hsync out of range)
(II) MGA(1): Not using default mode "1856x1392" (insufficient memory for mode)
(II) MGA(1): Not using default mode "928x696" (hsync out of range)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (hsync out of range)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (hsync out of range)
(II) MGA(1): Not using default mode "1152x864" (hsync out of range)
(II) MGA(1): Not using default mode "576x432" (hsync out of range)
(II) MGA(1): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(1): Not using default mode "700x525" (hsync out of range)
(II) MGA(1): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(1): Not using default mode "700x525" (hsync out of range)
(II) MGA(1): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(1): Not using default mode "700x525" (hsync out of range)
(II) MGA(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x600" (hsync out of range)
(II) MGA(1): Not using default mode "1920x1200" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x600" (hsync out of range)
(II) MGA(1): Not using default mode "1920x1440" (insufficient memory for mode)
(II) MGA(1): Not using default mode "960x720" (hsync out of range)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (hsync out of range)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (hsync out of range)
(II) MGA(1): Not using default mode "2048x1536" (insufficient memory for mode)
(II) MGA(1): Not using default mode "1024x768" (hsync out of range)
(II) MGA(1): Not using driver mode "1280x1024" (hsync out of range)
(II) MGA(1): Not using driver mode "1024x768" (all modes must have the same width)
(II) MGA(1): Not using driver mode "1024x768" (all modes must have the same width)
(II) MGA(1): Not using driver mode "1024x768" (all modes must have the same width)
(II) MGA(1): Not using default mode "1024x768" (all modes must have the same width)
(II) MGA(1): Not using default mode "1024x768" (all modes must have the same width)
(II) MGA(1): Not using default mode "1024x768" (all modes must have the same width)
(II) MGA(1): Not using driver mode "800x600" (all modes must have the same width)
(II) MGA(1): Not using driver mode "800x600" (all modes must have the same width)
(II) MGA(1): Not using driver mode "800x600" (all modes must have the same width)
(II) MGA(1): Not using driver mode "800x600" (all modes must have the same width)
(II) MGA(1): Not using default mode "800x600" (all modes must have the same width)
(II) MGA(1): Not using default mode "800x600" (all modes must have the same width)
(II) MGA(1): Not using default mode "800x600" (all modes must have the same width)
(II) MGA(1): Not using default mode "800x600" (all modes must have the same width)
(II) MGA(1): Not using driver mode "640x480" (all modes must have the same width)
(II) MGA(1): Not using driver mode "640x480" (all modes must have the same width)
(II) MGA(1): Not using driver mode "640x480" (all modes must have the same width)
(II) MGA(1): Not using driver mode "640x480" (all modes must have the same width)
(II) MGA(1): Not using default mode "640x480" (all modes must have the same width)
(II) MGA(1): Not using default mode "640x480" (all modes must have the same width)
(II) MGA(1): Not using default mode "640x480" (all modes must have the same width)
(II) MGA(1): Not using default mode "640x480" (all modes must have the same width)
(--) MGA(1): Has SDRAM
(--) MGA(1): Virtual size is 1280x1024 (pitch 1280)
(**) MGA(1): *Driver mode "1280x1024": 109.0 MHz, 63.7 kHz, 59.9 Hz
(II) MGA(1): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(**) MGA(1): Display dimensions: (530, 300) mm
(**) MGA(1): DPI set to (61, 86)
(II) MGA(1): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
<snip>
(II) MGA(0): Splitting WC range: base: 0xf0000000, size: 0x1800000
(==) MGA(0): Write-combining range (0xf1000000,0x800000)
(==) MGA(0): Write-combining range (0xf0000000,0x1800000)
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(0): 16 DWORD fifo
(==) MGA(0): Default visual is TrueColor
(II) MGA(0): [drm] bpp: 32 depth: 24
(II) MGA(0): [drm] Sarea 2200+664: 2864
(WW) MGA(0): Direct rendering is not supported when Xinerama is enabled
(EE) MGA(0): [drm] DRIScreenInit failed.  Disabling DRI.
(II) MGA(0): Using 2252 lines for offscreen memory.
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid filled trapezoids
	8x8 mono pattern filled rectangles
	8x8 mono pattern filled trapezoids
	Indirect CPU to Screen color expansion
	Screen to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		14 256x256 slots
		5 512x512 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(**) Option "dpms"
(**) MGA(0): DPMS enabled
(II) MGA(0): Using overlay video
(WW) MGA(0): Direct rendering disabled
(==) RandR enabled
(==) MGA(1): Write-combining range (0xf1800000,0x800000)
(II) MGA(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(1): 16 DWORD fifo
(EE) MGA(1): Not initializing the DRI on the second head
(II) MGA(1): Using 614 lines for offscreen memory.
(II) MGA(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid filled trapezoids
	8x8 mono pattern filled rectangles
	8x8 mono pattern filled trapezoids
	Indirect CPU to Screen color expansion
	Screen to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		20 128x128 slots
		5 256x256 slots
(==) MGA(1): Backing store disabled
(==) MGA(1): Silken mouse enabled
(**) Option "dpms"
(**) MGA(1): DPMS enabled
(WW) MGA(1): Direct rendering disabled
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) AIGLX: Screen 1 is not DRI capable
(II) GLX: Initialized MESA-PROXY GL provider for screen 1
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
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
SetGrabKeysState - disabled
SetGrabKeysState - enabled
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```

-- 
Robert

---

