---
title: "Cannot display X in Ubuntu 10.10 using ATI Rage XL and Sony Bravia KDL-52VL150"
date: 2012-02-20
forum: Desktop Environments
---

### Post by nelsonmntz on 2012-02-20
Cannot get X to display on Ubuntu 10.10 (2.6.35-22-generic i686) using 
ATI Technologies Inc Rage XL vga card, connected to a Sony Bravia KDL-52VL150.  
It appeared to work fine for a while, and then suddenly stopped working.  
Can no longer switch to a working resolution using Ctl+minus or Ctl+plus after boot up.  Details of xorg.conf, Xorg.0.log, lshw, lspci, mentioned below...

Any ideas on what could be the problem or things to try?

Thanks,
chipzz1 at gmail dot com

-------------------------------------------------------------------------------------
/etc/X11/xorg.conf:

Section "ServerLayout"
	Identifier     "XFree86 Configured"
	Screen      0  "Screen0" 0 0
        Option         "AIGLX"     "true"
EndSection

Section "ServerFlags"
	Option "AllowMouseOpenFail"  "true"
	Option	"DPMS"	"true"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi:unscaled"
	FontPath     "/usr/share/fonts/X11/100dpi:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/Speedo"
	FontPath     "/usr/share/fonts/X11/PEX"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/usr/share/fonts/truetype"
	FontPath     "/usr/share/fonts/latex-ttf-fonts"
EndSection

Section "Module"
	Load  "dbe" 
	Load  "dri" 
	Load  "glx" 
	Load  "freetype" 
	Load  "type1"  
	Load  "record" 
	Load  "extmod" 
	SubSection      "extmod"
		Option          "omit xfree86-dga"
	EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection


Section "Monitor"
	Identifier   "Monitor0"
	ModelName    "Generic Monitor"
        HorizSync 30-68
        VertRefresh 50-120
EndSection


Section "Device"
	Identifier  "Card0"
	VendorName  "All"
	BoardName   "All"

	Option "XAANoOffscreenPixmaps"
	Option "AllowGLXWithComposite" "true"
	Option "EnablePageFlip" "true"
	Option "TripleBuffer" "true"
	Option "Legacy3D" "false"
        Option  "XaaNoScanlineImageWriteRect" "true"
        Option  "XaaNoScanlineCPUToScreenColorExpandFill" "true"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	
	Option "AddARGBGLXVisuals" "true"
	Option "DisableGLXRootClipping" "true"
	SubSection "Display"
		Depth     1
		
	EndSubSection
	SubSection "Display"
		Depth     4
		
	EndSubSection
	SubSection "Display"
		Depth     8
		
	EndSubSection
	SubSection "Display"
		Depth     15
		
	EndSubSection
	SubSection "Display"
		Depth     16
		
	EndSubSection
	SubSection "Display"
		Depth     24
		
	EndSubSection
	SubSection "Display"
		Depth     32
		
	EndSubSection
EndSection

Section "DRI"
	Mode 0666
EndSection
-------------------------------------------------------------------------------------

/var/log/Xorg.0.log:

[    18.313] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    18.313] X Protocol Version 11, Revision 0
[    18.313] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    18.313] Current Operating System: Linux machine1 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    18.313] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=b1b9ee0c-3fc9-43bf-b223-c15c34f3de13 ro quiet splash
[    18.313] Build Date: 16 September 2010  05:39:22PM
[    18.313] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    18.313] Current version of pixman: 0.18.4
[    18.313] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    18.313] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.313] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Feb 19 20:44:34 2012
[    18.314] (==) Using config file: "/etc/X11/xorg.conf"
[    18.314] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.314] (==) ServerLayout "XFree86 Configured"
[    18.314] (**) |-->Screen "Screen0" (0)
[    18.314] (**) |   |-->Monitor "Monitor0"
[    18.315] (**) |   |-->Device "Card0"
[    18.315] (**) Option "AllowMouseOpenFail" "true"
[    18.315] (**) Option "AIGLX" "true"
[    18.315] (==) Automatically adding devices
[    18.315] (==) Automatically enabling devices
[    18.315] (WW) The directory "/usr/share/fonts/X11/Speedo" does not exist.
[    18.315] 	Entry deleted from font path.
[    18.315] (WW) The directory "/usr/share/fonts/X11/PEX" does not exist.
[    18.315] 	Entry deleted from font path.
[    18.315] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.315] 	Entry deleted from font path.
[    18.315] (WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype".
[    18.315] 	Entry deleted from font path.
[    18.315] 	(Run 'mkfontdir' on "/usr/share/fonts/truetype").
[    18.315] (WW) The directory "/usr/share/fonts/latex-ttf-fonts" does not exist.
[    18.320] 	Entry deleted from font path.
[    18.320] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.320] 	Entry deleted from font path.
[    18.320] (**) FontPath set to:
	/usr/share/fonts/X11/misc:unscaled,
	/usr/share/fonts/X11/75dpi:unscaled,
	/usr/share/fonts/X11/100dpi:unscaled,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.320] (**) ModulePath set to "/usr/lib/xorg/modules"
[    18.320] (**) Extension "Composite" is enabled
[    18.320] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.320] (II) Loader magic: 0x81f8e00
[    18.320] (II) Module ABI versions:
[    18.320] 	X.Org ANSI C Emulation: 0.4
[    18.320] 	X.Org Video Driver: 8.0
[    18.320] 	X.Org XInput driver : 11.0
[    18.320] 	X.Org Server Extension : 4.0
[    18.322] (--) PCI: (0:0:2:0) 8086:258a:1028:0180 rev 4, Mem @ 0xdff80000/524288, 0xf0000000/134217728, 0xdff40000/262144, I/O @ 0x0000ecd8/8
[    18.322] (--) PCI:*(0:4:0:0) 1002:4752:1002:8008 rev 39, Mem @ 0xde000000/16777216, 0xdfaff000/4096, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
[    18.322] (--) PCI: (0:4:2:0) 4444:0803:0070:4000 rev 1, Mem @ 0xd8000000/67108864
[    18.328] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.328] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[    18.328] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[    18.328] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    18.328] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[    18.328] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[    18.328] (II) "dri2" will be loaded by default.
[    18.328] (II) LoadModule: "dbe"
[    18.407] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.430] (II) Module dbe: vendor="X.Org Foundation"
[    18.430] 	compiled for 1.9.0, module version = 1.0.0
[    18.430] 	Module class: X.Org Server Extension
[    18.430] 	ABI class: X.Org Server Extension, version 4.0
[    18.430] (II) Loading extension DOUBLE-BUFFER
[    18.430] (II) LoadModule: "dri"
[    18.431] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.431] (II) Module dri: vendor="X.Org Foundation"
[    18.431] 	compiled for 1.9.0, module version = 1.0.0
[    18.431] 	ABI class: X.Org Server Extension, version 4.0
[    18.431] (II) Loading extension XFree86-DRI
[    18.431] (II) LoadModule: "glx"
[    18.432] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.432] (II) Module glx: vendor="X.Org Foundation"
[    18.432] 	compiled for 1.9.0, module version = 1.0.0
[    18.432] 	ABI class: X.Org Server Extension, version 4.0
[    18.432] (**) AIGLX enabled
[    18.432] (II) Loading extension GLX
[    18.432] (II) LoadModule: "record"
[    18.433] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.433] (II) Module record: vendor="X.Org Foundation"
[    18.433] 	compiled for 1.9.0, module version = 1.13.0
[    18.433] 	Module class: X.Org Server Extension
[    18.433] 	ABI class: X.Org Server Extension, version 4.0
[    18.433] (II) Loading extension RECORD
[    18.433] (II) LoadModule: "extmod"
[    18.434] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.434] (II) Module extmod: vendor="X.Org Foundation"
[    18.434] 	compiled for 1.9.0, module version = 1.0.0
[    18.434] 	Module class: X.Org Server Extension
[    18.434] 	ABI class: X.Org Server Extension, version 4.0
[    18.434] (II) Loading extension MIT-SCREEN-SAVER
[    18.434] (II) Loading extension XFree86-VidModeExtension
[    18.434] (II) Loading extension XFree86-DGA
[    18.434] (II) Loading extension DPMS
[    18.434] (II) Loading extension XVideo
[    18.434] (II) Loading extension XVideo-MotionCompensation
[    18.434] (II) Loading extension X-Resource
[    18.434] (II) LoadModule: "extmod"
[    18.435] (II) Reloading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.435] (II) Loading extension MIT-SCREEN-SAVER
[    18.435] (II) Loading extension XFree86-VidModeExtension
[    18.435] (II) Loading extension DPMS
[    18.435] (II) Loading extension XVideo
[    18.435] (II) Loading extension XVideo-MotionCompensation
[    18.435] (II) Loading extension X-Resource
[    18.435] (II) LoadModule: "dri2"
[    18.435] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.436] (II) Module dri2: vendor="X.Org Foundation"
[    18.436] 	compiled for 1.9.0, module version = 1.2.0
[    18.436] 	ABI class: X.Org Server Extension, version 4.0
[    18.436] (II) Loading extension DRI2
[    18.436] (==) Matched ati as autoconfigured driver 0
[    18.436] (==) Matched vesa as autoconfigured driver 1
[    18.436] (==) Matched fbdev as autoconfigured driver 2
[    18.436] (==) Assigned the driver to the xf86ConfigLayout
[    18.436] (II) LoadModule: "ati"
[    18.436] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    18.436] (II) Module ati: vendor="X.Org Foundation"
[    18.437] 	compiled for 1.9.0, module version = 6.13.1
[    18.437] 	Module class: X.Org Video Driver
[    18.437] 	ABI class: X.Org Video Driver, version 8.0
[    18.437] (II) LoadModule: "mach64"
[    18.437] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[    18.437] (II) Module mach64: vendor="X.Org Foundation"
[    18.437] 	compiled for 1.8.99.905, module version = 6.8.2
[    18.437] 	Module class: X.Org Video Driver
[    18.437] 	ABI class: X.Org Video Driver, version 8.0
[    18.437] (II) LoadModule: "vesa"
[    18.438] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.438] (II) Module vesa: vendor="X.Org Foundation"
[    18.438] 	compiled for 1.8.99.905, module version = 2.3.0
[    18.438] 	Module class: X.Org Video Driver
[    18.438] 	ABI class: X.Org Video Driver, version 8.0
[    18.438] (II) LoadModule: "fbdev"
[    18.438] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.438] (II) Module fbdev: vendor="X.Org Foundation"
[    18.439] 	compiled for 1.8.99.905, module version = 0.4.2
[    18.439] 	ABI class: X.Org Video Driver, version 8.0
[    18.439] (II) MACH64: Driver for ATI Mach64 chipsets
[    18.439] (II) VESA: driver for VESA chipsets: vesa
[    18.439] (II) FBDEV: driver for framebuffer: fbdev
[    18.439] (++) using VT number 7

[    18.441] (WW) Falling back to old probe method for vesa
[    18.441] (WW) Falling back to old probe method for fbdev
[    18.441] (II) Loading sub module "fbdevhw"
[    18.441] (II) LoadModule: "fbdevhw"
[    18.441] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.441] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.441] 	compiled for 1.9.0, module version = 0.0.2
[    18.441] 	ABI class: X.Org Video Driver, version 8.0
[    18.442] (EE) open /dev/fb0: No such file or directory
[    18.442] (==) MACH64(0): Depth 24, (--) framebuffer bpp 32
[    18.442] (==) MACH64(0): Using XAA acceleration architecture
[    18.442] (II) MACH64: Mach64 in slot 4:0:0 detected.
[    18.442] (II) Loading sub module "int10"
[    18.442] (II) LoadModule: "int10"
[    18.442] (II) Loading /usr/lib/xorg/modules/libint10.so
[    18.442] (II) Module int10: vendor="X.Org Foundation"
[    18.442] 	compiled for 1.9.0, module version = 1.0.0
[    18.442] 	ABI class: X.Org Video Driver, version 8.0
[    18.443] (II) MACH64(0): Primary V_BIOS segment is: 0xc000
[    18.443] (II) Loading sub module "ddc"
[    18.443] (II) LoadModule: "ddc"
[    18.443] (II) Module "ddc" already built-in
[    18.443] (II) Loading sub module "vbe"
[    18.443] (II) LoadModule: "vbe"
[    18.444] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    18.444] (II) Module vbe: vendor="X.Org Foundation"
[    18.444] 	compiled for 1.9.0, module version = 1.1.0
[    18.444] 	ABI class: X.Org Video Driver, version 8.0
[    18.444] (II) MACH64(0): VESA BIOS detected
[    18.444] (II) MACH64(0): VESA VBE Version 2.0
[    18.444] (II) MACH64(0): VESA VBE Total Mem: 8128 kB
[    18.445] (II) MACH64(0): VESA VBE OEM: ATI MACH64
[    18.445] (II) MACH64(0): VESA VBE OEM Software Rev: 1.0
[    18.445] (II) MACH64(0): VESA VBE OEM Vendor: ATI Technologies Inc.
[    18.445] (II) MACH64(0): VESA VBE OEM Product: MACH64GM
[    18.445] (II) MACH64(0): VESA VBE OEM Product Rev: 01.00
[    18.445] (II) MACH64(0): VESA VBE DDC supported
[    18.445] (II) MACH64(0): VESA VBE DDC Level 2
[    18.445] (II) MACH64(0): VESA VBE DDC transfer in appr. 2 sec.
[    18.493] (II) MACH64(0): VESA VBE DDC read successfully
[    18.493] (II) MACH64(0): Manufacturer: SNY  Model: 9c01  Serial#: 16843009
[    18.493] (II) MACH64(0): Year: 2008  Week: 1
[    18.493] (II) MACH64(0): EDID Version: 1.3
[    18.493] (II) MACH64(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    18.493] (II) MACH64(0): Sync:  Separate
[    18.493] (II) MACH64(0): Max Image Size [cm]: horiz.: 160  vert.: 90
[    18.493] (II) MACH64(0): Gamma: 2.20
[    18.493] (II) MACH64(0): No DPMS capabilities specified; RGB/Color Display
[    18.493] (II) MACH64(0): First detailed timing is preferred mode
[    18.493] (II) MACH64(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
[    18.493] (II) MACH64(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
[    18.493] (II) MACH64(0): Supported established timings:
[    18.493] (II) MACH64(0): 640x480@60Hz
[    18.493] (II) MACH64(0): 800x600@60Hz
[    18.493] (II) MACH64(0): 1024x768@60Hz
[    18.493] (II) MACH64(0): Manufacturer's mask: 0
[    18.493] (II) MACH64(0): Supported standard timings:
[    18.493] (II) MACH64(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    18.493] (II) MACH64(0): Supported detailed timing:
[    18.493] (II) MACH64(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
[    18.493] (II) MACH64(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    18.493] (II) MACH64(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    18.493] (II) MACH64(0): Supported detailed timing:
[    18.493] (II) MACH64(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
[    18.493] (II) MACH64(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
[    18.493] (II) MACH64(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
[    18.493] (II) MACH64(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 155 MHz
[    18.493] (II) MACH64(0): Monitor name: SONY TV
[    18.494] (II) MACH64(0): EDID (in hex):
[    18.494] (II) MACH64(0): 	00ffffffffffff004dd9019c01010101
[    18.494] (II) MACH64(0): 	0112010308a05a780a0dc9a057479827
[    18.494] (II) MACH64(0): 	12484c21080081800101010101010101
[    18.494] (II) MACH64(0): 	010101010101023a801871382d40582c
[    18.494] (II) MACH64(0): 	450040846300001e662150b051001b30
[    18.494] (II) MACH64(0): 	4070360040846300001e000000fd0039
[    18.494] (II) MACH64(0): 	3f1e500f000a202020202020000000fc
[    18.494] (II) MACH64(0): 	00534f4e592054560a20202020200038
[    18.494] (II) MACH64(0): EDID vendor "SNY", prod id 39937
[    18.494] (II) MACH64(0): Using hsync ranges from config file
[    18.494] (II) MACH64(0): Using vrefresh ranges from config file
[    18.494] (II) MACH64(0): Printing DDC gathered Modelines:
[    18.494] (II) MACH64(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    18.494] (II) MACH64(0): Modeline "1360x768"x0.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    18.494] (II) MACH64(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.494] (II) MACH64(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.494] (II) MACH64(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.494] (II) MACH64(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.494] (II) MACH64(0): BIOS Data:  BIOSSize=0x8000, ROMTable=0x010E.
[    18.494] (II) MACH64(0): BIOS Data:  ClockTable=0x097C, FrequencyTable=0x0000.
[    18.494] (II) MACH64(0): BIOS Data:  LCDTable=0x0000.
[    18.494] (II) MACH64(0): BIOS Data:  VideoTable=0x0000, HardwareTable=0x0158.
[    18.494] (II) MACH64(0): BIOS Data:  I2CType=0x0F, Tuner=0x00, Decoder=0x00, Audio=0x0F.
[    18.495] (--) MACH64(0): ATI 3D Rage XL or XC graphics controller detected.
[    18.495] (--) MACH64(0): Chip type 4752 "GR", version 7, foundry TSMC, class 0, revision 0x00.
[    18.495] (--) MACH64(0): PCI bus interface detected;  block I/O base is 0xD800.
[    18.495] (--) MACH64(0): ATI Mach64 adapter detected.
[    18.495] (!!) MACH64(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
[    18.495] (--) MACH64(0): Internal RAMDAC (subtype 1) detected.
[    18.495] (==) MACH64(0): RGB weight 888
[    18.495] (==) MACH64(0): Default visual is TrueColor
[    18.495] (==) MACH64(0): Using gamma correction (1.0, 1.0, 1.0)
[    18.495] (II) MACH64(0): Using Mach64 accelerator CRTC.
[    18.495] (II) MACH64(0): Storing hardware cursor image at 0xDE7FFC00.
[    18.495] (II) MACH64(0): Using 8 MB linear aperture at 0xDE000000.
[    18.495] (!!) MACH64(0): Virtual resolutions will be limited to 8191 kB
 due to linear aperture size and/or placement of hardware cursor image area.
[    18.495] (II) MACH64(0): Using Block 0 MMIO aperture at 0xDFAFF400.
[    18.495] (II) MACH64(0): Using Block 1 MMIO aperture at 0xDFAFF000.
[    18.498] (II) MACH64(0): MMIO write caching enabled.
[    18.498] (--) MACH64(0): 8192 kB of SGRAM (2:1) 32-bit detected (using 8191 kB).
[    18.498] (WW) MACH64(0): Cannot shadow an accelerated frame buffer.
[    18.498] (II) MACH64(0): Engine XCLK 62.815 MHz;  Refresh rate code 1.
[    18.498] (--) MACH64(0): Internal programmable clock generator detected.
[    18.498] (--) MACH64(0): Reference clock 157.5/11 (14.318) MHz.
[    18.498] (II) MACH64(0): Monitor0: Using hsync range of 30.00-68.00 kHz
[    18.498] (II) MACH64(0): Monitor0: Using vrefresh range of 50.00-120.00 Hz
[    18.498] (II) MACH64(0): Monitor0: Using maximum pixel clock of 155.00 MHz
[    18.498] (II) MACH64(0): Estimated virtual size for aspect ratio 1.7778 is 1920x1080
[    18.498] (II) MACH64(0): Maximum clock: 125.00 MHz
[    18.498] (II) MACH64(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
[    18.498] (II) MACH64(0): Not using default mode "640x480" (hsync out of range)
[    18.498] (II) MACH64(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "640x512" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "640x512" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
[    18.499] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
[    18.499] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
[    18.499] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
[    18.499] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1600x1200" (height too large for virtual size)
[    18.499] (II) MACH64(0): Not using default mode "800x600" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    18.499] (II) MACH64(0): Not using default mode "896x672" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1792x1344" (insufficient memory for mode)
[    18.499] (II) MACH64(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    18.499] (II) MACH64(0): Not using default mode "928x696" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1856x1392" (insufficient memory for mode)
[    18.499] (II) MACH64(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    18.499] (II) MACH64(0): Not using default mode "960x720" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    18.499] (II) MACH64(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1152x864" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "576x432" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    18.499] (II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
[    18.499] (II) MACH64(0): Not using default mode "700x525" (hsync out of range)
[    18.499] (II) MACH64(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
[    18.499] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    18.500] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    18.500] (II) MACH64(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using default mode "840x525" (hsync out of range)
[    18.500] (II) MACH64(0): Not using default mode "1920x1080" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using default mode "1920x1200" (insufficient memory for mode)
[    18.500] (II) MACH64(0): Not using default mode "960x600" (hsync out of range)
[    18.500] (II) MACH64(0): Not using default mode "1920x1440" (insufficient memory for mode)
[    18.500] (II) MACH64(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    18.500] (II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    18.500] (II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using default mode "2048x1536" (insufficient memory for mode)
[    18.500] (II) MACH64(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[    18.500] (II) MACH64(0): Not using driver mode "1920x1080" (bad mode clock/interlace/doublescan)
[    18.500] (WW) MACH64(0): Shrinking virtual size estimate from 1920x1080 to 1400x1050
[    18.500] (--) MACH64(0): Virtual size is 1400x1050 (pitch 1408)
[    18.500] (**) MACH64(0): *Default mode "1400x1050": 122.0 MHz, 64.9 kHz, 60.0 Hz
[    18.500] (II) MACH64(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
[    18.501] (**) MACH64(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
[    18.501] (II) MACH64(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.501] (**) MACH64(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
[    18.501] (II) MACH64(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.501] (**) MACH64(0): *Default mode "1440x900": 106.5 MHz, 55.9 kHz, 59.9 Hz
[    18.501] (II) MACH64(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.501] (**) MACH64(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
[    18.501] (II) MACH64(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    18.501] (**) MACH64(0): *Driver mode "1360x768": 85.5 MHz, 47.7 kHz, 60.0 Hz
[    18.501] (II) MACH64(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    18.501] (**) MACH64(0): *Default mode "1360x768": 84.8 MHz, 47.7 kHz, 59.8 Hz
[    18.501] (II) MACH64(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    18.501] (**) MACH64(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
[    18.501] (II) MACH64(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.501] (**) MACH64(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
[    18.501] (II) MACH64(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
[    18.501] (**) MACH64(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
[    18.501] (II) MACH64(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
[    18.501] (**) MACH64(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
[    18.501] (II) MACH64(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    18.501] (**) MACH64(0): *Default mode "1024x768i": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
[    18.501] (II) MACH64(0): Modeline "1024x768i"x86.9   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
[    18.501] (**) MACH64(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    18.501] (II) MACH64(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.501] (**) MACH64(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
[    18.501] (II) MACH64(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[    18.501] (**) MACH64(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
[    18.501] (II) MACH64(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.501] (**) MACH64(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
[    18.501] (II) MACH64(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.501] (**) MACH64(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
[    18.502] (II) MACH64(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.502] (**) MACH64(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
[    18.502] (II) MACH64(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.502] (**) MACH64(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    18.502] (II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.502] (**) MACH64(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
[    18.502] (II) MACH64(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[    18.502] (**) MACH64(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
[    18.502] (II) MACH64(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.502] (**) MACH64(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
[    18.502] (II) MACH64(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.502] (**) MACH64(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
[    18.502] (II) MACH64(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.502] (**) MACH64(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
[    18.502] (II) MACH64(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.502] (**) MACH64(0): *Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
[    18.502] (II) MACH64(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
[    18.502] (**) MACH64(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
[    18.502] (II) MACH64(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
[    18.502] (**) MACH64(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
[    18.502] (II) MACH64(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
[    18.502] (**) MACH64(0): *Default mode "720x450": 53.2 MHz, 55.9 kHz, 59.9 Hz (D)
[    18.502] (II) MACH64(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
[    18.502] (**) MACH64(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    18.502] (II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.502] (**) MACH64(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
[    18.502] (II) MACH64(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[    18.502] (**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
[    18.502] (II) MACH64(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.502] (**) MACH64(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
[    18.502] (II) MACH64(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    18.503] (**) MACH64(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
[    18.503] (II) MACH64(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
[    18.503] (**) MACH64(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
[    18.503] (II) MACH64(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.503] (**) MACH64(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
[    18.503] (II) MACH64(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
[    18.503] (**) MACH64(0): *Default mode "680x384": 36.0 MHz, 47.4 kHz, 60.0 Hz (D)
[    18.503] (II) MACH64(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
[    18.503] (**) MACH64(0): *Default mode "680x384": 42.4 MHz, 47.7 kHz, 59.8 Hz (D)
[    18.503] (II) MACH64(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
[    18.503] (**) MACH64(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
[    18.503] (II) MACH64(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
[    18.503] (**) MACH64(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
[    18.503] (II) MACH64(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
[    18.503] (**) MACH64(0): *Default mode "576x432": 52.5 MHz, 67.6 kHz, 75.0 Hz (D)
[    18.503] (II) MACH64(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
[    18.503] (**) MACH64(0): *Default mode "576x432": 48.4 MHz, 63.0 kHz, 70.0 Hz (D)
[    18.503] (II) MACH64(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
[    18.503] (**) MACH64(0): *Default mode "576x432": 40.8 MHz, 53.7 kHz, 60.1 Hz (D)
[    18.503] (II) MACH64(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
[    18.503] (**) MACH64(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
[    18.503] (II) MACH64(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
[    18.503] (**) MACH64(0): *Default mode "512x384i": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
[    18.503] (II) MACH64(0): Modeline "512x384i"x86.6   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync (35.5 kHz)
[    18.503] (**) MACH64(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
[    18.503] (II) MACH64(0): Modeline "512x384"x85.0   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync (68.7 kHz)
[    18.503] (**) MACH64(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
[    18.503] (II) MACH64(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
[    18.503] (**) MACH64(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
[    18.503] (II) MACH64(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
[    18.504] (**) MACH64(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
[    18.504] (II) MACH64(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
[    18.504] (**) MACH64(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
[    18.504] (II) MACH64(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
[    18.504] (**) MACH64(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
[    18.504] (II) MACH64(0): Modeline "400x300"x85.3   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync (53.7 kHz)
[    18.504] (**) MACH64(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
[    18.504] (II) MACH64(0): Modeline "400x300"x75.1   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync (46.9 kHz)
[    18.504] (**) MACH64(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
[    18.504] (II) MACH64(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
[    18.504] (**) MACH64(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
[    18.504] (II) MACH64(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
[    18.504] (**) MACH64(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
[    18.504] (II) MACH64(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
[    18.504] (**) MACH64(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
[    18.504] (II) MACH64(0): Modeline "320x240"x85.2   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync (43.3 kHz)
[    18.504] (**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
[    18.504] (II) MACH64(0): Modeline "320x240"x75.0   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync (37.5 kHz)
[    18.504] (**) MACH64(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
[    18.504] (II) MACH64(0): Modeline "320x240"x72.8   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync (37.9 kHz)
[    18.504] (**) MACH64(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
[    18.504] (II) MACH64(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
[    18.504] (**) MACH64(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
[    18.504] (II) MACH64(0): Modeline "360x200"x85.0   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync (37.9 kHz)
[    18.504] (**) MACH64(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
[    18.504] (II) MACH64(0): Modeline "320x200"x85.3   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync (37.9 kHz)
[    18.504] (**) MACH64(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
[    18.504] (II) MACH64(0): Modeline "320x175"x85.3   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync (37.9 kHz)
[    18.505] (**) MACH64(0): Display dimensions: (1600, 900) mm
[    18.505] (**) MACH64(0): DPI set to (22, 29)
[    18.505] (II) Loading sub module "fb"
[    18.505] (II) LoadModule: "fb"
[    18.505] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.505] (II) Module fb: vendor="X.Org Foundation"
[    18.505] 	compiled for 1.9.0, module version = 1.0.0
[    18.505] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.505] (II) Loading sub module "ramdac"
[    18.505] (II) LoadModule: "ramdac"
[    18.505] (II) Module "ramdac" already built-in
[    18.505] (II) Loading sub module "xaa"
[    18.505] (II) LoadModule: "xaa"
[    18.506] (II) Loading /usr/lib/xorg/modules/libxaa.so
[    18.506] (II) Module xaa: vendor="X.Org Foundation"
[    18.506] 	compiled for 1.9.0, module version = 1.2.1
[    18.506] 	ABI class: X.Org Video Driver, version 8.0
[    18.507] (II) Loading sub module "i2c"
[    18.507] (II) LoadModule: "i2c"
[    18.507] (II) Module "i2c" already built-in
[    18.507] (II) MACH64(0): I2C bus "Mach64" initialized.
[    18.509] (II) UnloadModule: "vesa"
[    18.509] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.509] (II) UnloadModule: "fbdev"
[    18.509] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.509] (II) UnloadModule: "fbdevhw"
[    18.509] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    18.509] (--) Depth 24 pixmap format is 32 bpp
[    18.603] (WW) MACH64(0): DRI static buffer allocation failed -- need at least 14437 kB video memory
[    18.603] (II) MACH64(0): Largest offscreen areas (with overlaps):
[    18.603] (II) MACH64(0): 	8 x 1489 rectangle at 1400,0
[    18.603] (II) MACH64(0): 	1408 x 439 rectangle at 0,1050
[    18.603] (II) MACH64(0): 	384 x 440 rectangle at 0,1050
[    18.603] (**) MACH64(0): Option "XaaNoScanlineCPUToScreenColorExpandFill" "true"
[    18.603] (**) MACH64(0): Option "XaaNoScanlineImageWriteRect" "true"
[    18.603] (**) MACH64(0): Option "XaaNoOffscreenPixmaps"
[    18.604] (II) MACH64(0): Using XFree86 Acceleration Architecture (XAA)
[    18.604] 	Screen to screen bit blits
[    18.604] 	Solid filled rectangles
[    18.604] 	8x8 mono pattern filled rectangles
[    18.604] 	Solid Lines
[    18.604] 	Setting up tile and stipple cache:
[    18.604] 		17 128x128 slots
[    18.604] 		4 256x256 slots
[    18.604] (==) MACH64(0): Backing store disabled
[    18.604] (==) MACH64(0): Silken mouse enabled
[    18.608] (==) MACH64(0): DPMS enabled
[    18.608] (WW) MACH64(0): Option "AllowGLXWithComposite" is not used
[    18.608] (WW) MACH64(0): Option "EnablePageFlip" is not used
[    18.608] (WW) MACH64(0): Option "TripleBuffer" is not used
[    18.608] (WW) MACH64(0): Option "Legacy3D" is not used
[    18.608] (WW) MACH64(0): Option "AddARGBGLXVisuals" is not used
[    18.608] (WW) MACH64(0): Option "DisableGLXRootClipping" is not used
[    18.608] (II) MACH64(0): Direct rendering disabled
[    18.608] (==) RandR enabled
[    18.608] (II) Initializing built-in extension Generic Event Extension
[    18.608] (II) Initializing built-in extension SHAPE
[    18.608] (II) Initializing built-in extension MIT-SHM
[    18.608] (II) Initializing built-in extension XInputExtension
[    18.608] (II) Initializing built-in extension XTEST
[    18.608] (II) Initializing built-in extension BIG-REQUESTS
[    18.608] (II) Initializing built-in extension SYNC
[    18.608] (II) Initializing built-in extension XKEYBOARD
[    18.608] (II) Initializing built-in extension XC-MISC
[    18.608] (II) Initializing built-in extension SECURITY
[    18.608] (II) Initializing built-in extension XINERAMA
[    18.608] (II) Initializing built-in extension XFIXES
[    18.608] (II) Initializing built-in extension RENDER
[    18.608] (II) Initializing built-in extension RANDR
[    18.608] (II) Initializing built-in extension COMPOSITE
[    18.608] (II) Initializing built-in extension DAMAGE
[    18.608] (II) Initializing built-in extension GESTURE
[    18.625] (II) AIGLX: Screen 0 is not DRI2 capable
[    18.625] (II) AIGLX: Screen 0 is not DRI capable
[    18.631] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    18.631] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    18.669] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.683] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    18.683] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.683] (II) LoadModule: "evdev"
[    18.683] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.684] (II) Module evdev: vendor="X.Org Foundation"
[    18.684] 	compiled for 1.9.0, module version = 2.3.2
[    18.684] 	Module class: X.Org XInput Driver
[    18.684] 	ABI class: X.Org XInput driver, version 11.0
[    18.684] (**) Power Button: always reports core events
[    18.684] (**) Power Button: Device: "/dev/input/event1"
[    18.684] (II) Power Button: Found keys
[    18.684] (II) Power Button: Configuring as keyboard
[    18.684] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.684] (**) Option "xkb_rules" "evdev"
[    18.684] (**) Option "xkb_model" "pc105"
[    18.684] (**) Option "xkb_layout" "us"
[    18.686] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.686] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.686] (**) Power Button: always reports core events
[    18.686] (**) Power Button: Device: "/dev/input/event0"
[    18.686] (II) Power Button: Found keys
[    18.686] (II) Power Button: Configuring as keyboard
[    18.687] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.687] (**) Option "xkb_rules" "evdev"
[    18.687] (**) Option "xkb_model" "pc105"
[    18.687] (**) Option "xkb_layout" "us"
[    18.690] (II) config/udev: Adding input device BTC USB Multimedia Cordless Kit   (/dev/input/event3)
[    18.691] (**) BTC USB Multimedia Cordless Kit  : Applying InputClass "evdev keyboard catchall"
[    18.691] (**) BTC USB Multimedia Cordless Kit  : always reports core events
[    18.691] (**) BTC USB Multimedia Cordless Kit  : Device: "/dev/input/event3"
[    18.691] (II) BTC USB Multimedia Cordless Kit  : Found keys
[    18.691] (II) BTC USB Multimedia Cordless Kit  : Configuring as keyboard
[    18.691] (II) XINPUT: Adding extended input device "BTC USB Multimedia Cordless Kit  " (type: KEYBOARD)
[    18.691] (**) Option "xkb_rules" "evdev"
[    18.691] (**) Option "xkb_model" "pc105"
[    18.691] (**) Option "xkb_layout" "us"
[    18.692] (II) config/udev: Adding input device BTC USB Multimedia Cordless Kit   (/dev/input/event4)
[    18.692] (**) BTC USB Multimedia Cordless Kit  : Applying InputClass "evdev pointer catchall"
[    18.692] (**) BTC USB Multimedia Cordless Kit  : Applying InputClass "evdev keyboard catchall"
[    18.692] (**) BTC USB Multimedia Cordless Kit  : always reports core events
[    18.692] (**) BTC USB Multimedia Cordless Kit  : Device: "/dev/input/event4"
[    18.692] (II) BTC USB Multimedia Cordless Kit  : Found 3 mouse buttons
[    18.692] (II) BTC USB Multimedia Cordless Kit  : Found scroll wheel(s)
[    18.693] (II) BTC USB Multimedia Cordless Kit  : Found relative axes
[    18.693] (II) BTC USB Multimedia Cordless Kit  : Found x and y relative axes
[    18.693] (II) BTC USB Multimedia Cordless Kit  : Found absolute axes
[    18.693] (II) evdev-grail: failed to open grail, no gesture support
[    18.693] (II) BTC USB Multimedia Cordless Kit  : Found x and y absolute axes
[    18.693] (II) BTC USB Multimedia Cordless Kit  : Found keys
[    18.693] (II) BTC USB Multimedia Cordless Kit  : Configuring as mouse
[    18.693] (II) BTC USB Multimedia Cordless Kit  : Configuring as keyboard
[    18.693] (**) BTC USB Multimedia Cordless Kit  : YAxisMapping: buttons 4 and 5
[    18.693] (**) BTC USB Multimedia Cordless Kit  : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.693] (II) XINPUT: Adding extended input device "BTC USB Multimedia Cordless Kit  " (type: KEYBOARD)
[    18.693] (**) Option "xkb_rules" "evdev"
[    18.693] (**) Option "xkb_model" "pc105"
[    18.693] (**) Option "xkb_layout" "us"
[    18.693] (II) BTC USB Multimedia Cordless Kit  : initialized for relative axes.
[    18.693] (WW) BTC USB Multimedia Cordless Kit  : ignoring absolute axes.
[    18.694] (II) config/udev: Adding input device BTC USB Multimedia Cordless Kit   (/dev/input/js0)
[    18.694] (II) No input driver/identifier specified (ignoring)
[    18.695] (II) config/udev: Adding input device BTC USB Multimedia Cordless Kit   (/dev/input/mouse0)
[    18.695] (II) No input driver/identifier specified (ignoring)
[    18.703] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    18.703] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.703] (**) AT Translated Set 2 keyboard: always reports core events
[    18.703] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    18.703] (II) AT Translated Set 2 keyboard: Found keys
[    18.703] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    18.703] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    18.703] (**) Option "xkb_rules" "evdev"
[    18.703] (**) Option "xkb_model" "pc105"
[    18.703] (**) Option "xkb_layout" "us"
[    18.704] (II) config/udev: Adding input device PS/2 Logitech Mouse (/dev/input/event5)
[    18.704] (**) PS/2 Logitech Mouse: Applying InputClass "evdev pointer catchall"
[    18.704] (**) PS/2 Logitech Mouse: always reports core events
[    18.704] (**) PS/2 Logitech Mouse: Device: "/dev/input/event5"
[    18.704] (II) PS/2 Logitech Mouse: Found 3 mouse buttons
[    18.704] (II) PS/2 Logitech Mouse: Found relative axes
[    18.704] (II) PS/2 Logitech Mouse: Found x and y relative axes
[    18.704] (II) PS/2 Logitech Mouse: Configuring as mouse
[    18.704] (**) PS/2 Logitech Mouse: YAxisMapping: buttons 4 and 5
[    18.704] (**) PS/2 Logitech Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.705] (II) XINPUT: Adding extended input device "PS/2 Logitech Mouse" (type: MOUSE)
[    18.705] (II) PS/2 Logitech Mouse: initialized for relative axes.
[    18.705] (II) config/udev: Adding input device PS/2 Logitech Mouse (/dev/input/mouse1)
[    18.705] (II) No input driver/identifier specified (ignoring)
[    48.576] (II) Open ACPI successful (/var/run/acpid.socket)
[    49.223] (II) Power Button: Device reopened after 1 attempts.
[    49.223] (II) Power Button: Device reopened after 1 attempts.
[    49.224] (II) BTC USB Multimedia Cordless Kit  : Device reopened after 1 attempts.
[    49.224] (II) BTC USB Multimedia Cordless Kit  : Device reopened after 1 attempts.
[    49.224] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[    49.224] (II) PS/2 Logitech Mouse: Device reopened after 1 attempts.
-------------------------------------------------------------------------------------
user1@machine1:~$ sudo lshw -c video
[sudo] password for user1: 
  *-display UNCLAIMED     
       description: Display controller
       product: E7221 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:dff80000-dfffffff ioport:ecd8(size=8) memory:f0000000-f7ffffff memory:dff40000-dff7ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Rage XL
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 27
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:de000000-deffffff ioport:d800(size=256) memory:dfaff000-dfafffff memory:dfb00000-dfb1ffff
-------------------------------------------------------------------------------------
user1@machine1:/etc/X11$ lspci -t
-[0000:00]-+-00.0
           +-01.0-[01]--
           +-02.0
           +-1c.0-[02]----00.0
           +-1c.1-[03]--
           +-1d.0
           +-1d.1
           +-1d.2
           +-1d.3
           +-1d.7
           +-1e.0-[04]--+-00.0
           |            +-01.0
           |            \-02.0
           +-1f.0
           +-1f.1
           +-1f.2
           \-1f.3
-------------------------------------------------------------------------------------
user1@machine1:/etc/X11$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation E7220/E7221 Memory Controller Hub [8086:2588] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation E7220/E7221 PCI Express Root Port [8086:2589] (rev 04)
00:02.0 Display controller [0380]: Intel Corporation E7221 Integrated Graphics Controller [8086:258a] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller [8086:2652] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
04:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage XL [1002:4752] (rev 27)
04:01.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10)
04:02.0 Multimedia video controller [0400]: Internext Compression Inc iTVC15 MPEG-2 Encoder [4444:0803] (rev 01)
user1@machine1:/etc/X11$ 
-------------------------------------------------------------------------------------

---

