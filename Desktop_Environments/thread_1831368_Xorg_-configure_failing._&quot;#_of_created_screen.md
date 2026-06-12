---
title: "Xorg -configure failing. &quot;# of created screens does not match ...&quot;"
date: 2011-08-23
forum: Desktop Environments
---

### Post by DiagonalArg on 2011-08-23
I hope someone can help with this!  I've got old CRT monitor that is not being properly recognized by ubuntu 11.04.  I get some kind of refresh rate chaos on the login screen, which can only be corrected by logging in and setting the resolution fairly low. The display setting configuration does not have any choices for refresh rate.

I tried to create an xorg.conf via ctl-alt-F1, login, sudo service gdm stop, sudo Xorg -configure.  The process fails with "Number of created screens does not match number of detected devices".  My setup is very simple, I only have one screen.

My log file is below, and the xorg.conf below that.

Thanks for your input! 

> [   522.460] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   522.460] X Protocol Version 11, Revision 0
[   522.460] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   522.460] Current Operating System: Linux Tyan-S3970 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64
[   522.461] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=088a1cbf-5ade-46c2-821f-e0c7753e84d5 ro quiet splash vt.handoff=7
[   522.461] Build Date: 21 May 2011  11:48:41AM
[   522.461] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   522.461] Current version of pixman: 0.20.2
[   522.461] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   522.461] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   522.461] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 23 05:39:18 2011
[   522.461] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   522.462] (==) No Layout section.  Using the first Screen section.
[   522.462] (==) No screen section available. Using defaults.
[   522.462] (**) |-->Screen "Default Screen Section" (0)
[   522.462] (**) |   |-->Monitor "<default monitor>"
[   522.462] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   522.462] (==) Automatically adding devices
[   522.462] (==) Automatically enabling devices
[   522.462] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   522.462] 	Entry deleted from font path.
[   522.462] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   522.462] 	Entry deleted from font path.
[   522.462] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   522.462] 	Entry deleted from font path.
[   522.462] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   522.462] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   522.463] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   522.463] (II) Loader magic: 0x7e0280
[   522.463] (II) Module ABI versions:
[   522.463] 	X.Org ANSI C Emulation: 0.4
[   522.463] 	X.Org Video Driver: 10.0
[   522.463] 	X.Org XInput driver : 12.3
[   522.463] 	X.Org Server Extension : 5.0
[   522.464] (--) PCI:*(0:0:6:0) 18ca:0020:18ca:0020 rev 0, Mem @ 0xf8000000/67108864, 0xfebc0000/262144, I/O @ 0x0000ec00/128
[   522.464] (II) Open ACPI successful (/var/run/acpid.socket)
[   522.464] (II) LoadModule: "extmod"
[   522.465] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   522.465] (II) Module extmod: vendor="X.Org Foundation"
[   522.465] 	compiled for 1.10.1, module version = 1.0.0
[   522.465] 	Module class: X.Org Server Extension
[   522.465] 	ABI class: X.Org Server Extension, version 5.0
[   522.465] (II) Loading extension MIT-SCREEN-SAVER
[   522.465] (II) Loading extension XFree86-VidModeExtension
[   522.465] (II) Loading extension XFree86-DGA
[   522.465] (II) Loading extension DPMS
[   522.465] (II) Loading extension XVideo
[   522.465] (II) Loading extension XVideo-MotionCompensation
[   522.465] (II) Loading extension X-Resource
[   522.465] (II) LoadModule: "dbe"
[   522.466] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   522.466] (II) Module dbe: vendor="X.Org Foundation"
[   522.466] 	compiled for 1.10.1, module version = 1.0.0
[   522.466] 	Module class: X.Org Server Extension
[   522.466] 	ABI class: X.Org Server Extension, version 5.0
[   522.466] (II) Loading extension DOUBLE-BUFFER
[   522.466] (II) LoadModule: "glx"
[   522.467] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   522.467] (II) Module glx: vendor="X.Org Foundation"
[   522.467] 	compiled for 1.10.1, module version = 1.0.0
[   522.467] 	ABI class: X.Org Server Extension, version 5.0
[   522.467] (==) AIGLX enabled
[   522.467] (II) Loading extension GLX
[   522.467] (II) LoadModule: "record"
[   522.468] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   522.468] (II) Module record: vendor="X.Org Foundation"
[   522.468] 	compiled for 1.10.1, module version = 1.13.0
[   522.468] 	Module class: X.Org Server Extension
[   522.468] 	ABI class: X.Org Server Extension, version 5.0
[   522.468] (II) Loading extension RECORD
[   522.468] (II) LoadModule: "dri"
[   522.469] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   522.469] (II) Module dri: vendor="X.Org Foundation"
[   522.469] 	compiled for 1.10.1, module version = 1.0.0
[   522.469] 	ABI class: X.Org Server Extension, version 5.0
[   522.469] (II) Loading extension XFree86-DRI
[   522.469] (II) LoadModule: "dri2"
[   522.470] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   522.470] (II) Module dri2: vendor="X.Org Foundation"
[   522.470] 	compiled for 1.10.1, module version = 1.2.0
[   522.470] 	ABI class: X.Org Server Extension, version 5.0
[   522.470] (II) Loading extension DRI2
[   522.470] (==) Matched xgi as autoconfigured driver 0
[   522.470] (==) Matched vesa as autoconfigured driver 1
[   522.470] (==) Matched fbdev as autoconfigured driver 2
[   522.470] (==) Assigned the driver to the xf86ConfigLayout
[   522.470] (II) LoadModule: "xgi"
[   522.471] (WW) Warning, couldn't open module xgi
[   522.471] (II) UnloadModule: "xgi"
[   522.471] (II) Unloading xgi
[   522.471] (EE) Failed to load module "xgi" (module does not exist, 0)
[   522.471] (II) LoadModule: "vesa"
[   522.472] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   522.472] (II) Module vesa: vendor="X.Org Foundation"
[   522.472] 	compiled for 1.10.0, module version = 2.3.0
[   522.472] 	Module class: X.Org Video Driver
[   522.472] 	ABI class: X.Org Video Driver, version 10.0
[   522.472] (II) LoadModule: "fbdev"
[   522.473] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   522.473] (II) Module fbdev: vendor="X.Org Foundation"
[   522.473] 	compiled for 1.10.0, module version = 0.4.2
[   522.473] 	ABI class: X.Org Video Driver, version 10.0
[   522.473] (II) VESA: driver for VESA chipsets: vesa
[   522.473] (II) FBDEV: driver for framebuffer: fbdev
[   522.473] (--) using VT number 8

[   522.484] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   522.484] (WW) Falling back to old probe method for fbdev
[   522.484] (II) Loading sub module "fbdevhw"
[   522.484] (II) LoadModule: "fbdevhw"
[   522.484] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   522.484] (II) Module fbdevhw: vendor="X.Org Foundation"
[   522.485] 	compiled for 1.10.1, module version = 0.0.2
[   522.485] 	ABI class: X.Org Video Driver, version 10.0
[   522.485] (II) Loading sub module "vbe"
[   522.485] (II) LoadModule: "vbe"
[   522.485] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   522.485] (II) Module vbe: vendor="X.Org Foundation"
[   522.485] 	compiled for 1.10.1, module version = 1.1.0
[   522.485] 	ABI class: X.Org Video Driver, version 10.0
[   522.485] (II) Loading sub module "int10"
[   522.485] (II) LoadModule: "int10"
[   522.485] (II) Loading /usr/lib/xorg/modules/libint10.so
[   522.486] (II) Module int10: vendor="X.Org Foundation"
[   522.486] 	compiled for 1.10.1, module version = 1.0.0
[   522.486] 	ABI class: X.Org Video Driver, version 10.0
[   522.486] (II) VESA(0): initializing int10
[   522.490] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   522.491] (II) VESA(0): VESA BIOS detected
[   522.491] (II) VESA(0): VESA VBE Version 3.0
[   522.491] (II) VESA(0): VESA VBE Total Mem: 8192 kB
[   522.491] (II) VESA(0): VESA VBE OEM: XGI
[   522.491] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[   522.491] (II) VESA(0): VESA VBE OEM Vendor: XGI Technology, Inc.
[   522.491] (II) VESA(0): VESA VBE OEM Product: Volari Z7
[   522.491] (II) VESA(0): VESA VBE OEM Product Rev: 1.07.08
[   522.508] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   522.508] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[   522.508] (==) VESA(0): RGB weight 888
[   522.508] (==) VESA(0): Default visual is TrueColor
[   522.508] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[   522.508] (II) Loading sub module "ddc"
[   522.508] (II) LoadModule: "ddc"
[   522.508] (II) Module "ddc" already built-in
[   522.787] (II) VESA(0): VESA VBE DDC supported
[   522.787] (II) VESA(0): VESA VBE DDC Level 2
[   522.787] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[   525.595] (II) VESA(0): VESA VBE DDC read successfully
[   525.595] (II) VESA(0): Manufacturer: NEC  Model: 61da  Serial#: 28883
[   525.595] (II) VESA(0): Year: 2003  Week: 20
[   525.595] (II) VESA(0): EDID Version: 1.3
[   525.595] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   525.595] (II) VESA(0): Sync:  Separate  Composite
[   525.595] (II) VESA(0): Max Image Size [cm]: horiz.: 40  vert.: 30
[   525.595] (II) VESA(0): Gamma: 2.20
[   525.595] (II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[   525.595] (II) VESA(0): First detailed timing is preferred mode
[   525.595] (II) VESA(0): GTF timings supported
[   525.595] (II) VESA(0): redX: 0.627 redY: 0.341   greenX: 0.292 greenY: 0.605
[   525.595] (II) VESA(0): blueX: 0.149 blueY: 0.072   whiteX: 0.283 whiteY: 0.297
[   525.595] (II) VESA(0): Supported established timings:
[   525.595] (II) VESA(0): 720x400@70Hz
[   525.595] (II) VESA(0): 720x400@88Hz
[   525.595] (II) VESA(0): 640x480@60Hz
[   525.595] (II) VESA(0): 640x480@67Hz
[   525.595] (II) VESA(0): 640x480@72Hz
[   525.595] (II) VESA(0): 640x480@75Hz
[   525.595] (II) VESA(0): 800x600@56Hz
[   525.595] (II) VESA(0): 800x600@60Hz
[   525.595] (II) VESA(0): 800x600@72Hz
[   525.595] (II) VESA(0): 800x600@75Hz
[   525.595] (II) VESA(0): 832x624@75Hz
[   525.595] (II) VESA(0): 1024x768@60Hz
[   525.595] (II) VESA(0): 1024x768@70Hz
[   525.595] (II) VESA(0): 1024x768@75Hz
[   525.595] (II) VESA(0): 1280x1024@75Hz
[   525.595] (II) VESA(0): 1152x864@75Hz
[   525.595] (II) VESA(0): Manufacturer's mask: 0
[   525.595] (II) VESA(0): Supported standard timings:
[   525.595] (II) VESA(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
[   525.595] (II) VESA(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[   525.595] (II) VESA(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[   525.595] (II) VESA(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   525.595] (II) VESA(0): #4: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
[   525.595] (II) VESA(0): #5: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
[   525.595] (II) VESA(0): #6: hsize: 1792  vsize 1344  refresh: 75  vid: 20417
[   525.595] (II) VESA(0): #7: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
[   525.595] (II) VESA(0): Supported detailed timing:
[   525.595] (II) VESA(0): clock: 229.5 MHz   Image Size:  396 x 297 mm
[   525.595] (II) VESA(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
[   525.595] (II) VESA(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
[   525.595] (II) VESA(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 115 kHz, PixClock max 335 MHz
[   525.595] (II) VESA(0): Monitor name: NEC FE2111SB
[   525.595] (II) VESA(0): Serial No: 305428883
[   525.595] (II) VESA(0): EDID (in hex):
[   525.595] (II) VESA(0): 	00ffffffffffff0038a3da61d3700000
[   525.595] (II) VESA(0): 	140d01030c281e78eb9c68a0574a9b26
[   525.595] (II) VESA(0): 	12484cffef80315945596159714f8199
[   525.595] (II) VESA(0): 	a94fc14fd14fa659403062b0324040c0
[   525.595] (II) VESA(0): 	13008c291100001e000000fd0032a01e
[   525.595] (II) VESA(0): 	7321000a202020202020000000fc004e
[   525.595] (II) VESA(0): 	45432046453231313153420a000000ff
[   525.595] (II) VESA(0): 	003330353432383838330a202020007d
[   525.595] (II) VESA(0): EDID vendor "NEC", prod id 25050
[   525.595] (II) VESA(0): Using EDID range info for horizontal sync
[   525.595] (II) VESA(0): Using EDID range info for vertical refresh
[   525.595] (II) VESA(0): Printing DDC gathered Modelines:
[   525.595] (II) VESA(0): Modeline "1600x1200"x0.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (106.2 kHz)
[   525.595] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   525.596] (II) VESA(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   525.596] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[   525.596] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[   525.596] (II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[   525.596] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   525.596] (II) VESA(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
[   525.596] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   525.596] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[   525.596] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[   525.596] (II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[   525.596] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   525.596] (II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[   525.596] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[   525.596] (II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[   525.596] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[   525.596] (II) VESA(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[   525.596] (II) VESA(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[   525.596] (II) VESA(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[   525.596] (II) VESA(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
[   525.596] (II) VESA(0): Modeline "1600x1200"x0.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
[   525.596] (II) VESA(0): Modeline "1792x1344"x0.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 -hsync +vsync (106.3 kHz)
[   525.596] (II) VESA(0): Modeline "1920x1440"x0.0  297.00  1920 2064 2288 2640  1440 1441 1444 1500 -hsync +vsync (112.5 kHz)
[   525.596] (II) VESA(0): Searching for matching VESA mode(s):
[   525.596] Mode: 102 (800x600)
[   525.596] 	ModeAttributes: 0x1f
[   525.596] 	WinAAttributes: 0x7
[   525.596] 	WinBAttributes: 0x0
[   525.596] 	WinGranularity: 64
[   525.596] 	WinSize: 64
[   525.596] 	WinASegment: 0xa000
[   525.596] 	WinBSegment: 0xa000
[   525.596] 	WinFuncPtr: 0xc00038bf
[   525.596] 	BytesPerScanline: 100
[   525.596] 	XResolution: 800
[   525.596] 	YResolution: 600
[   525.596] 	XCharSize: 8
[   525.596] 	YCharSize: 16
[   525.596] 	NumberOfPlanes: 4
[   525.596] 	BitsPerPixel: 4
[   525.596] 	NumberOfBanks: 1
[   525.596] 	MemoryModel: 3
[   525.596] 	BankSize: 0
[   525.596] 	NumberOfImages: 31
[   525.596] 	RedMaskSize: 0
[   525.596] 	RedFieldPosition: 0
[   525.596] 	GreenMaskSize: 0
[   525.596] 	GreenFieldPosition: 0
[   525.596] 	BlueMaskSize: 0
[   525.596] 	BlueFieldPosition: 0
[   525.596] 	RsvdMaskSize: 0
[   525.596] 	RsvdFieldPosition: 0
[   525.596] 	DirectColorModeInfo: 0
[   525.596] 	PhysBasePtr: 0xf8000000
[   525.596] 	LinBytesPerScanLine: 100
[   525.596] 	BnkNumberOfImagePages: 31
[   525.596] 	LinNumberOfImagePages: 31
[   525.596] 	LinRedMaskSize: 0
[   525.596] 	LinRedFieldPosition: 0
[   525.596] 	LinGreenMaskSize: 0
[   525.596] 	LinGreenFieldPosition: 0
[   525.596] 	LinBlueMaskSize: 0
[   525.597] 	LinBlueFieldPosition: 0
[   525.597] 	LinRsvdMaskSize: 0
[   525.597] 	LinRsvdFieldPosition: 0
[   525.597] 	MaxPixelClock: 300000000
[   525.597] Mode: 101 (640x480)
[   525.597] 	ModeAttributes: 0x9f
[   525.597] 	WinAAttributes: 0x7
[   525.597] 	WinBAttributes: 0x0
[   525.597] 	WinGranularity: 64
[   525.597] 	WinSize: 64
[   525.597] 	WinASegment: 0xa000
[   525.597] 	WinBSegment: 0xa000
[   525.597] 	WinFuncPtr: 0xc00038bf
[   525.597] 	BytesPerScanline: 640
[   525.597] 	XResolution: 640
[   525.597] 	YResolution: 480
[   525.597] 	XCharSize: 8
[   525.597] 	YCharSize: 16
[   525.597] 	NumberOfPlanes: 1
[   525.597] 	BitsPerPixel: 8
[   525.597] 	NumberOfBanks: 1
[   525.597] 	MemoryModel: 4
[   525.597] 	BankSize: 0
[   525.597] 	NumberOfImages: 24
[   525.597] 	RedMaskSize: 0
[   525.597] 	RedFieldPosition: 0
[   525.597] 	GreenMaskSize: 0
[   525.597] 	GreenFieldPosition: 0
[   525.597] 	BlueMaskSize: 0
[   525.597] 	BlueFieldPosition: 0
[   525.597] 	RsvdMaskSize: 0
[   525.597] 	RsvdFieldPosition: 0
[   525.597] 	DirectColorModeInfo: 0
[   525.597] 	PhysBasePtr: 0xf8000000
[   525.597] 	LinBytesPerScanLine: 640
[   525.597] 	BnkNumberOfImagePages: 24
[   525.597] 	LinNumberOfImagePages: 24
[   525.597] 	LinRedMaskSize: 0
[   525.597] 	LinRedFieldPosition: 0
[   525.597] 	LinGreenMaskSize: 0
[   525.597] 	LinGreenFieldPosition: 0
[   525.597] 	LinBlueMaskSize: 0
[   525.597] 	LinBlueFieldPosition: 0
[   525.597] 	LinRsvdMaskSize: 0
[   525.597] 	LinRsvdFieldPosition: 0
[   525.597] 	MaxPixelClock: 300000000
[   525.597] Mode: 100 (640x400)
[   525.597] 	ModeAttributes: 0x9f
[   525.597] 	WinAAttributes: 0x7
[   525.597] 	WinBAttributes: 0x0
[   525.597] 	WinGranularity: 64
[   525.597] 	WinSize: 64
[   525.597] 	WinASegment: 0xa000
[   525.597] 	WinBSegment: 0xa000
[   525.597] 	WinFuncPtr: 0xc00038bf
[   525.597] 	BytesPerScanline: 640
[   525.597] 	XResolution: 640
[   525.598] 	YResolution: 400
[   525.598] 	XCharSize: 8
[   525.598] 	YCharSize: 16
[   525.598] 	NumberOfPlanes: 1
[   525.598] 	BitsPerPixel: 8
[   525.598] 	NumberOfBanks: 1
[   525.598] 	MemoryModel: 4
[   525.598] 	BankSize: 0
[   525.598] 	NumberOfImages: 31
[   525.598] 	RedMaskSize: 0
[   525.598] 	RedFieldPosition: 0
[   525.598] 	GreenMaskSize: 0
[   525.598] 	GreenFieldPosition: 0
[   525.598] 	BlueMaskSize: 0
[   525.598] 	BlueFieldPosition: 0
[   525.598] 	RsvdMaskSize: 0
[   525.598] 	RsvdFieldPosition: 0
[   525.598] 	DirectColorModeInfo: 0
[   525.598] 	PhysBasePtr: 0xf8000000
[   525.598] 	LinBytesPerScanLine: 640
[   525.598] 	BnkNumberOfImagePages: 31
[   525.598] 	LinNumberOfImagePages: 31
[   525.598] 	LinRedMaskSize: 0
[   525.598] 	LinRedFieldPosition: 0
[   525.598] 	LinGreenMaskSize: 0
[   525.598] 	LinGreenFieldPosition: 0
[   525.598] 	LinBlueMaskSize: 0
[   525.598] 	LinBlueFieldPosition: 0
[   525.598] 	LinRsvdMaskSize: 0
[   525.598] 	LinRsvdFieldPosition: 0
[   525.598] 	MaxPixelClock: 1000000
[   525.598] Mode: 103 (800x600)
[   525.598] 	ModeAttributes: 0x9f
[   525.598] 	WinAAttributes: 0x7
[   525.598] 	WinBAttributes: 0x0
[   525.598] 	WinGranularity: 64
[   525.598] 	WinSize: 64
[   525.598] 	WinASegment: 0xa000
[   525.598] 	WinBSegment: 0xa000
[   525.598] 	WinFuncPtr: 0xc00038bf
[   525.598] 	BytesPerScanline: 800
[   525.598] 	XResolution: 800
[   525.598] 	YResolution: 600
[   525.598] 	XCharSize: 8
[   525.598] 	YCharSize: 16
[   525.598] 	NumberOfPlanes: 1
[   525.598] 	BitsPerPixel: 8
[   525.598] 	NumberOfBanks: 1
[   525.598] 	MemoryModel: 4
[   525.598] 	BankSize: 0
[   525.598] 	NumberOfImages: 15
[   525.598] 	RedMaskSize: 0
[   525.598] 	RedFieldPosition: 0
[   525.598] 	GreenMaskSize: 0
[   525.598] 	GreenFieldPosition: 0
[   525.598] 	BlueMaskSize: 0
[   525.598] 	BlueFieldPosition: 0
[   525.598] 	RsvdMaskSize: 0
[   525.598] 	RsvdFieldPosition: 0
[   525.598] 	DirectColorModeInfo: 0
[   525.598] 	PhysBasePtr: 0xf8000000
[   525.598] 	LinBytesPerScanLine: 800
[   525.598] 	BnkNumberOfImagePages: 15
[   525.598] 	LinNumberOfImagePages: 15
[   525.598] 	LinRedMaskSize: 0
[   525.598] 	LinRedFieldPosition: 0
[   525.598] 	LinGreenMaskSize: 0
[   525.598] 	LinGreenFieldPosition: 0
[   525.598] 	LinBlueMaskSize: 0
[   525.598] 	LinBlueFieldPosition: 0
[   525.598] 	LinRsvdMaskSize: 0
[   525.598] 	LinRsvdFieldPosition: 0
[   525.598] 	MaxPixelClock: 300000000
[   525.599] Mode: 104 (1024x768)
[   525.599] 	ModeAttributes: 0x1f
[   525.599] 	WinAAttributes: 0x7
[   525.599] 	WinBAttributes: 0x0
[   525.599] 	WinGranularity: 64
[   525.599] 	WinSize: 64
[   525.599] 	WinASegment: 0xa000
[   525.599] 	WinBSegment: 0xa000
[   525.599] 	WinFuncPtr: 0xc00038bf
[   525.599] 	BytesPerScanline: 128
[   525.599] 	XResolution: 1024
[   525.599] 	YResolution: 768
[   525.599] 	XCharSize: 8
[   525.599] 	YCharSize: 16
[   525.599] 	NumberOfPlanes: 4
[   525.599] 	BitsPerPixel: 4
[   525.599] 	NumberOfBanks: 1
[   525.599] 	MemoryModel: 3
[   525.599] 	BankSize: 0
[   525.599] 	NumberOfImages: 15
[   525.599] 	RedMaskSize: 0
[   525.599] 	RedFieldPosition: 0
[   525.599] 	GreenMaskSize: 0
[   525.599] 	GreenFieldPosition: 0
[   525.599] 	BlueMaskSize: 0
[   525.599] 	BlueFieldPosition: 0
[   525.599] 	RsvdMaskSize: 0
[   525.599] 	RsvdFieldPosition: 0
[   525.599] 	DirectColorModeInfo: 0
[   525.599] 	PhysBasePtr: 0xf8000000
[   525.599] 	LinBytesPerScanLine: 128
[   525.599] 	BnkNumberOfImagePages: 15
[   525.599] 	LinNumberOfImagePages: 15
[   525.599] 	LinRedMaskSize: 0
[   525.599] 	LinRedFieldPosition: 0
[   525.599] 	LinGreenMaskSize: 0
[   525.599] 	LinGreenFieldPosition: 0
[   525.599] 	LinBlueMaskSize: 0
[   525.599] 	LinBlueFieldPosition: 0
[   525.599] 	LinRsvdMaskSize: 0
[   525.599] 	LinRsvdFieldPosition: 0
[   525.599] 	MaxPixelClock: 300000000
[   525.599] Mode: 105 (1024x768)
[   525.599] 	ModeAttributes: 0x9f
[   525.599] 	WinAAttributes: 0x7
[   525.599] 	WinBAttributes: 0x0
[   525.599] 	WinGranularity: 64
[   525.599] 	WinSize: 64
[   525.599] 	WinASegment: 0xa000
[   525.599] 	WinBSegment: 0xa000
[   525.599] 	WinFuncPtr: 0xc00038bf
[   525.599] 	BytesPerScanline: 1024
[   525.599] 	XResolution: 1024
[   525.599] 	YResolution: 768
[   525.599] 	XCharSize: 8
[   525.599] 	YCharSize: 16
[   525.599] 	NumberOfPlanes: 1
[   525.599] 	BitsPerPixel: 8
[   525.599] 	NumberOfBanks: 1
[   525.599] 	MemoryModel: 4
[   525.599] 	BankSize: 0
[   525.599] 	NumberOfImages: 9
[   525.599] 	RedMaskSize: 0
[   525.599] 	RedFieldPosition: 0
[   525.599] 	GreenMaskSize: 0
[   525.599] 	GreenFieldPosition: 0
[   525.599] 	BlueMaskSize: 0
[   525.599] 	BlueFieldPosition: 0
[   525.599] 	RsvdMaskSize: 0
[   525.599] 	RsvdFieldPosition: 0
[   525.599] 	DirectColorModeInfo: 0
[   525.599] 	PhysBasePtr: 0xf8000000
[   525.599] 	LinBytesPerScanLine: 1024
[   525.599] 	BnkNumberOfImagePages: 9
[   525.599] 	LinNumberOfImagePages: 9
[   525.599] 	LinRedMaskSize: 0
[   525.599] 	LinRedFieldPosition: 0
[   525.599] 	LinGreenMaskSize: 0
[   525.599] 	LinGreenFieldPosition: 0
[   525.599] 	LinBlueMaskSize: 0
[   525.599] 	LinBlueFieldPosition: 0
[   525.599] 	LinRsvdMaskSize: 0
[   525.599] 	LinRsvdFieldPosition: 0
[   525.599] 	MaxPixelClock: 300000000
[   525.600] Mode: 107 (1280x1024)
[   525.600] 	ModeAttributes: 0x9f
[   525.600] 	WinAAttributes: 0x7
[   525.600] 	WinBAttributes: 0x0
[   525.600] 	WinGranularity: 64
[   525.600] 	WinSize: 64
[   525.600] 	WinASegment: 0xa000
[   525.600] 	WinBSegment: 0xa000
[   525.600] 	WinFuncPtr: 0xc00038bf
[   525.600] 	BytesPerScanline: 1280
[   525.600] 	XResolution: 1280
[   525.600] 	YResolution: 1024
[   525.600] 	XCharSize: 8
[   525.600] 	YCharSize: 16
[   525.600] 	NumberOfPlanes: 1
[   525.600] 	BitsPerPixel: 8
[   525.600] 	NumberOfBanks: 1
[   525.600] 	MemoryModel: 4
[   525.600] 	BankSize: 0
[   525.600] 	NumberOfImages: 5
[   525.600] 	RedMaskSize: 0
[   525.600] 	RedFieldPosition: 0
[   525.600] 	GreenMaskSize: 0
[   525.600] 	GreenFieldPosition: 0
[   525.600] 	BlueMaskSize: 0
[   525.600] 	BlueFieldPosition: 0
[   525.600] 	RsvdMaskSize: 0
[   525.600] 	RsvdFieldPosition: 0
[   525.600] 	DirectColorModeInfo: 0
[   525.600] 	PhysBasePtr: 0xf8000000
[   525.600] 	LinBytesPerScanLine: 1280
[   525.600] 	BnkNumberOfImagePages: 5
[   525.600] 	LinNumberOfImagePages: 5
[   525.600] 	LinRedMaskSize: 0
[   525.600] 	LinRedFieldPosition: 0
[   525.600] 	LinGreenMaskSize: 0
[   525.600] 	LinGreenFieldPosition: 0
[   525.600] 	LinBlueMaskSize: 0
[   525.600] 	LinBlueFieldPosition: 0
[   525.600] 	LinRsvdMaskSize: 0
[   525.600] 	LinRsvdFieldPosition: 0
[   525.600] 	MaxPixelClock: 300000000
[   525.600] Mode: 130 (1600x1200)
[   525.600] 	ModeAttributes: 0x9f
[   525.600] 	WinAAttributes: 0x7
[   525.600] 	WinBAttributes: 0x0
[   525.600] 	WinGranularity: 64
[   525.600] 	WinSize: 64
[   525.600] 	WinASegment: 0xa000
[   525.600] 	WinBSegment: 0xa000
[   525.600] 	WinFuncPtr: 0xc00038bf
[   525.600] 	BytesPerScanline: 1600
[   525.600] 	XResolution: 1600
[   525.600] 	YResolution: 1200
[   525.600] 	XCharSize: 8
[   525.600] 	YCharSize: 16
[   525.600] 	NumberOfPlanes: 1
[   525.600] 	BitsPerPixel: 8
[   525.600] 	NumberOfBanks: 1
[   525.600] 	MemoryModel: 4
[   525.600] 	BankSize: 0
[   525.600] 	NumberOfImages: 3
[   525.600] 	RedMaskSize: 0
[   525.600] 	RedFieldPosition: 0
[   525.600] 	GreenMaskSize: 0
[   525.600] 	GreenFieldPosition: 0
[   525.600] 	BlueMaskSize: 0
[   525.600] 	BlueFieldPosition: 0
[   525.600] 	RsvdMaskSize: 0
[   525.600] 	RsvdFieldPosition: 0
[   525.600] 	DirectColorModeInfo: 0
[   525.600] 	PhysBasePtr: 0xf8000000
[   525.600] 	LinBytesPerScanLine: 1600
[   525.600] 	BnkNumberOfImagePages: 3
[   525.601] 	LinNumberOfImagePages: 3
[   525.601] 	LinRedMaskSize: 0
[   525.601] 	LinRedFieldPosition: 0
[   525.601] 	LinGreenMaskSize: 0
[   525.601] 	LinGreenFieldPosition: 0
[   525.601] 	LinBlueMaskSize: 0
[   525.601] 	LinBlueFieldPosition: 0
[   525.601] 	LinRsvdMaskSize: 0
[   525.601] 	LinRsvdFieldPosition: 0
[   525.601] 	MaxPixelClock: 300000000
[   525.601] Mode: 131 (1600x1200)
[   525.601] 	ModeAttributes: 0x9b
[   525.601] 	WinAAttributes: 0x7
[   525.601] 	WinBAttributes: 0x0
[   525.601] 	WinGranularity: 64
[   525.601] 	WinSize: 64
[   525.601] 	WinASegment: 0xa000
[   525.601] 	WinBSegment: 0xa000
[   525.601] 	WinFuncPtr: 0xc00038bf
[   525.601] 	BytesPerScanline: 3200
[   525.601] 	XResolution: 1600
[   525.601] 	YResolution: 1200
[   525.601] 	XCharSize: 8
[   525.601] 	YCharSize: 16
[   525.601] 	NumberOfPlanes: 1
[   525.601] 	BitsPerPixel: 16
[   525.601] 	NumberOfBanks: 1
[   525.601] 	MemoryModel: 6
[   525.601] 	BankSize: 0
[   525.601] 	NumberOfImages: 1
[   525.601] 	RedMaskSize: 5
[   525.601] 	RedFieldPosition: 11
[   525.601] 	GreenMaskSize: 6
[   525.601] 	GreenFieldPosition: 5
[   525.601] 	BlueMaskSize: 5
[   525.601] 	BlueFieldPosition: 0
[   525.601] 	RsvdMaskSize: 0
[   525.601] 	RsvdFieldPosition: 0
[   525.601] 	DirectColorModeInfo: 0
[   525.601] 	PhysBasePtr: 0xf8000000
[   525.601] 	LinBytesPerScanLine: 3200
[   525.601] 	BnkNumberOfImagePages: 1
[   525.601] 	LinNumberOfImagePages: 1
[   525.601] 	LinRedMaskSize: 5
[   525.601] 	LinRedFieldPosition: 11
[   525.601] 	LinGreenMaskSize: 6
[   525.601] 	LinGreenFieldPosition: 5
[   525.601] 	LinBlueMaskSize: 5
[   525.601] 	LinBlueFieldPosition: 0
[   525.601] 	LinRsvdMaskSize: 0
[   525.601] 	LinRsvdFieldPosition: 0
[   525.601] 	MaxPixelClock: 300000000
[   525.601] Mode: 10d (320x200)
[   525.601] 	ModeAttributes: 0x9b
[   525.601] 	WinAAttributes: 0x7
[   525.602] 	WinBAttributes: 0x0
[   525.602] 	WinGranularity: 64
[   525.602] 	WinSize: 64
[   525.602] 	WinASegment: 0xa000
[   525.602] 	WinBSegment: 0xa000
[   525.602] 	WinFuncPtr: 0xc00038bf
[   525.602] 	BytesPerScanline: 640
[   525.602] 	XResolution: 320
[   525.602] 	YResolution: 200
[   525.602] 	XCharSize: 8
[   525.602] 	YCharSize: 8
[   525.602] 	NumberOfPlanes: 1
[   525.602] 	BitsPerPixel: 15
[   525.602] 	NumberOfBanks: 1
[   525.602] 	MemoryModel: 6
[   525.602] 	BankSize: 0
[   525.602] 	NumberOfImages: 63
[   525.602] 	RedMaskSize: 5
[   525.602] 	RedFieldPosition: 10
[   525.602] 	GreenMaskSize: 5
[   525.602] 	GreenFieldPosition: 5
[   525.602] 	BlueMaskSize: 5
[   525.602] 	BlueFieldPosition: 0
[   525.602] 	RsvdMaskSize: 0
[   525.602] 	RsvdFieldPosition: 0
[   525.602] 	DirectColorModeInfo: 0
[   525.602] 	PhysBasePtr: 0xf8000000
[   525.602] 	LinBytesPerScanLine: 640
[   525.602] 	BnkNumberOfImagePages: 63
[   525.602] 	LinNumberOfImagePages: 63
[   525.602] 	LinRedMaskSize: 5
[   525.602] 	LinRedFieldPosition: 10
[   525.602] 	LinGreenMaskSize: 5
[   525.602] 	LinGreenFieldPosition: 5
[   525.602] 	LinBlueMaskSize: 5
[   525.602] 	LinBlueFieldPosition: 0
[   525.602] 	LinRsvdMaskSize: 0
[   525.602] 	LinRsvdFieldPosition: 0
[   525.602] 	MaxPixelClock: 1000000
[   525.602] Mode: 10e (320x200)
[   525.602] 	ModeAttributes: 0x9b
[   525.602] 	WinAAttributes: 0x7
[   525.602] 	WinBAttributes: 0x0
[   525.602] 	WinGranularity: 64
[   525.602] 	WinSize: 64
[   525.602] 	WinASegment: 0xa000
[   525.602] 	WinBSegment: 0xa000
[   525.602] 	WinFuncPtr: 0xc00038bf
[   525.602] 	BytesPerScanline: 640
[   525.602] 	XResolution: 320
[   525.602] 	YResolution: 200
[   525.602] 	XCharSize: 8
[   525.602] 	YCharSize: 8
[   525.602] 	NumberOfPlanes: 1
[   525.602] 	BitsPerPixel: 16
[   525.602] 	NumberOfBanks: 1
[   525.602] 	MemoryModel: 6
[   525.602] 	BankSize: 0
[   525.602] 	NumberOfImages: 63
[   525.602] 	RedMaskSize: 5
[   525.602] 	RedFieldPosition: 11
[   525.602] 	GreenMaskSize: 6
[   525.602] 	GreenFieldPosition: 5
[   525.602] 	BlueMaskSize: 5
[   525.602] 	BlueFieldPosition: 0
[   525.602] 	RsvdMaskSize: 0
[   525.602] 	RsvdFieldPosition: 0
[   525.602] 	DirectColorModeInfo: 0
[   525.602] 	PhysBasePtr: 0xf8000000
[   525.602] 	LinBytesPerScanLine: 640
[   525.602] 	BnkNumberOfImagePages: 63
[   525.602] 	LinNumberOfImagePages: 63
[   525.602] 	LinRedMaskSize: 5
[   525.602] 	LinRedFieldPosition: 11
[   525.602] 	LinGreenMaskSize: 6
[   525.602] 	LinGreenFieldPosition: 5
[   525.602] 	LinBlueMaskSize: 5
[   525.602] 	LinBlueFieldPosition: 0
[   525.602] 	LinRsvdMaskSize: 0
[   525.602] 	LinRsvdFieldPosition: 0
[   525.602] 	MaxPixelClock: 1000000
[   525.603] Mode: 110 (640x480)
[   525.603] 	ModeAttributes: 0x9b
[   525.603] 	WinAAttributes: 0x7
[   525.603] 	WinBAttributes: 0x0
[   525.603] 	WinGranularity: 64
[   525.603] 	WinSize: 64
[   525.603] 	WinASegment: 0xa000
[   525.603] 	WinBSegment: 0xa000
[   525.603] 	WinFuncPtr: 0xc00038bf
[   525.603] 	BytesPerScanline: 1280
[   525.603] 	XResolution: 640
[   525.603] 	YResolution: 480
[   525.603] 	XCharSize: 8
[   525.603] 	YCharSize: 16
[   525.603] 	NumberOfPlanes: 1
[   525.603] 	BitsPerPixel: 15
[   525.603] 	NumberOfBanks: 1
[   525.603] 	MemoryModel: 6
[   525.603] 	BankSize: 0
[   525.603] 	NumberOfImages: 11
[   525.603] 	RedMaskSize: 5
[   525.603] 	RedFieldPosition: 10
[   525.603] 	GreenMaskSize: 5
[   525.603] 	GreenFieldPosition: 5
[   525.603] 	BlueMaskSize: 5
[   525.603] 	BlueFieldPosition: 0
[   525.603] 	RsvdMaskSize: 0
[   525.603] 	RsvdFieldPosition: 0
[   525.603] 	DirectColorModeInfo: 0
[   525.603] 	PhysBasePtr: 0xf8000000
[   525.603] 	LinBytesPerScanLine: 1280
[   525.603] 	BnkNumberOfImagePages: 11
[   525.603] 	LinNumberOfImagePages: 11
[   525.603] 	LinRedMaskSize: 5
[   525.603] 	LinRedFieldPosition: 10
[   525.603] 	LinGreenMaskSize: 5
[   525.603] 	LinGreenFieldPosition: 5
[   525.603] 	LinBlueMaskSize: 5
[   525.603] 	LinBlueFieldPosition: 0
[   525.603] 	LinRsvdMaskSize: 0
[   525.603] 	LinRsvdFieldPosition: 0
[   525.603] 	MaxPixelClock: 300000000
[   525.603] Mode: 111 (640x480)
[   525.603] 	ModeAttributes: 0x9b
[   525.603] 	WinAAttributes: 0x7
[   525.603] 	WinBAttributes: 0x0
[   525.603] 	WinGranularity: 64
[   525.603] 	WinSize: 64
[   525.603] 	WinASegment: 0xa000
[   525.603] 	WinBSegment: 0xa000
[   525.603] 	WinFuncPtr: 0xc00038bf
[   525.603] 	BytesPerScanline: 1280
[   525.603] 	XResolution: 640
[   525.603] 	YResolution: 480
[   525.603] 	XCharSize: 8
[   525.603] 	YCharSize: 16
[   525.603] 	NumberOfPlanes: 1
[   525.603] 	BitsPerPixel: 16
[   525.603] 	NumberOfBanks: 1
[   525.603] 	MemoryModel: 6
[   525.603] 	BankSize: 0
[   525.603] 	NumberOfImages: 11
[   525.603] 	RedMaskSize: 5
[   525.603] 	RedFieldPosition: 11
[   525.603] 	GreenMaskSize: 6
[   525.603] 	GreenFieldPosition: 5
[   525.603] 	BlueMaskSize: 5
[   525.603] 	BlueFieldPosition: 0
[   525.603] 	RsvdMaskSize: 0
[   525.603] 	RsvdFieldPosition: 0
[   525.603] 	DirectColorModeInfo: 0
[   525.603] 	PhysBasePtr: 0xf8000000
[   525.603] 	LinBytesPerScanLine: 1280
[   525.603] 	BnkNumberOfImagePages: 11
[   525.603] 	LinNumberOfImagePages: 11
[   525.603] 	LinRedMaskSize: 5
[   525.603] 	LinRedFieldPosition: 11
[   525.603] 	LinGreenMaskSize: 6
[   525.603] 	LinGreenFieldPosition: 5
[   525.603] 	LinBlueMaskSize: 5
[   525.603] 	LinBlueFieldPosition: 0
[   525.603] 	LinRsvdMaskSize: 0
[   525.603] 	LinRsvdFieldPosition: 0
[   525.603] 	MaxPixelClock: 300000000
[   525.604] Mode: 113 (800x600)
[   525.604] 	ModeAttributes: 0x9b
[   525.604] 	WinAAttributes: 0x7
[   525.604] 	WinBAttributes: 0x0
[   525.604] 	WinGranularity: 64
[   525.604] 	WinSize: 64
[   525.604] 	WinASegment: 0xa000
[   525.604] 	WinBSegment: 0xa000
[   525.604] 	WinFuncPtr: 0xc00038bf
[   525.604] 	BytesPerScanline: 1600
[   525.604] 	XResolution: 800
[   525.604] 	YResolution: 600
[   525.604] 	XCharSize: 8
[   525.604] 	YCharSize: 16
[   525.604] 	NumberOfPlanes: 1
[   525.604] 	BitsPerPixel: 15
[   525.604] 	NumberOfBanks: 1
[   525.604] 	MemoryModel: 6
[   525.604] 	BankSize: 0
[   525.604] 	NumberOfImages: 7
[   525.604] 	RedMaskSize: 5
[   525.604] 	RedFieldPosition: 10
[   525.604] 	GreenMaskSize: 5
[   525.604] 	GreenFieldPosition: 5
[   525.604] 	BlueMaskSize: 5
[   525.604] 	BlueFieldPosition: 0
[   525.604] 	RsvdMaskSize: 0
[   525.604] 	RsvdFieldPosition: 0
[   525.604] 	DirectColorModeInfo: 0
[   525.604] 	PhysBasePtr: 0xf8000000
[   525.604] 	LinBytesPerScanLine: 1600
[   525.604] 	BnkNumberOfImagePages: 7
[   525.604] 	LinNumberOfImagePages: 7
[   525.604] 	LinRedMaskSize: 5
[   525.604] 	LinRedFieldPosition: 10
[   525.604] 	LinGreenMaskSize: 5
[   525.604] 	LinGreenFieldPosition: 5
[   525.604] 	LinBlueMaskSize: 5
[   525.604] 	LinBlueFieldPosition: 0
[   525.604] 	LinRsvdMaskSize: 0
[   525.604] 	LinRsvdFieldPosition: 0
[   525.604] 	MaxPixelClock: 300000000
[   525.604] Mode: 114 (800x600)
[   525.604] 	ModeAttributes: 0x9b
[   525.604] 	WinAAttributes: 0x7
[   525.604] 	WinBAttributes: 0x0
[   525.604] 	WinGranularity: 64
[   525.604] 	WinSize: 64
[   525.604] 	WinASegment: 0xa000
[   525.604] 	WinBSegment: 0xa000
[   525.605] 	WinFuncPtr: 0xc00038bf
[   525.605] 	BytesPerScanline: 1600
[   525.605] 	XResolution: 800
[   525.605] 	YResolution: 600
[   525.605] 	XCharSize: 8
[   525.605] 	YCharSize: 16
[   525.605] 	NumberOfPlanes: 1
[   525.605] 	BitsPerPixel: 16
[   525.605] 	NumberOfBanks: 1
[   525.605] 	MemoryModel: 6
[   525.605] 	BankSize: 0
[   525.605] 	NumberOfImages: 7
[   525.605] 	RedMaskSize: 5
[   525.605] 	RedFieldPosition: 11
[   525.605] 	GreenMaskSize: 6
[   525.605] 	GreenFieldPosition: 5
[   525.605] 	BlueMaskSize: 5
[   525.605] 	BlueFieldPosition: 0
[   525.605] 	RsvdMaskSize: 0
[   525.605] 	RsvdFieldPosition: 0
[   525.605] 	DirectColorModeInfo: 0
[   525.605] 	PhysBasePtr: 0xf8000000
[   525.605] 	LinBytesPerScanLine: 1600
[   525.605] 	BnkNumberOfImagePages: 7
[   525.605] 	LinNumberOfImagePages: 7
[   525.605] 	LinRedMaskSize: 5
[   525.605] 	LinRedFieldPosition: 11
[   525.605] 	LinGreenMaskSize: 6
[   525.605] 	LinGreenFieldPosition: 5
[   525.605] 	LinBlueMaskSize: 5
[   525.605] 	LinBlueFieldPosition: 0
[   525.605] 	LinRsvdMaskSize: 0
[   525.605] 	LinRsvdFieldPosition: 0
[   525.605] 	MaxPixelClock: 300000000
[   525.605] Mode: 116 (1024x768)
[   525.605] 	ModeAttributes: 0x9b
[   525.605] 	WinAAttributes: 0x7
[   525.605] 	WinBAttributes: 0x0
[   525.605] 	WinGranularity: 64
[   525.605] 	WinSize: 64
[   525.605] 	WinASegment: 0xa000
[   525.605] 	WinBSegment: 0xa000
[   525.605] 	WinFuncPtr: 0xc00038bf
[   525.605] 	BytesPerScanline: 2048
[   525.605] 	XResolution: 1024
[   525.605] 	YResolution: 768
[   525.605] 	XCharSize: 8
[   525.605] 	YCharSize: 16
[   525.605] 	NumberOfPlanes: 1
[   525.605] 	BitsPerPixel: 15
[   525.605] 	NumberOfBanks: 1
[   525.605] 	MemoryModel: 6
[   525.605] 	BankSize: 0
[   525.605] 	NumberOfImages: 4
[   525.605] 	RedMaskSize: 5
[   525.605] 	RedFieldPosition: 10
[   525.605] 	GreenMaskSize: 5
[   525.605] 	GreenFieldPosition: 5
[   525.605] 	BlueMaskSize: 5
[   525.605] 	BlueFieldPosition: 0
[   525.605] 	RsvdMaskSize: 0
[   525.605] 	RsvdFieldPosition: 0
[   525.605] 	DirectColorModeInfo: 0
[   525.605] 	PhysBasePtr: 0xf8000000
[   525.605] 	LinBytesPerScanLine: 2048
[   525.605] 	BnkNumberOfImagePages: 4
[   525.605] 	LinNumberOfImagePages: 4
[   525.605] 	LinRedMaskSize: 5
[   525.605] 	LinRedFieldPosition: 10
[   525.605] 	LinGreenMaskSize: 5
[   525.605] 	LinGreenFieldPosition: 5
[   525.605] 	LinBlueMaskSize: 5
[   525.605] 	LinBlueFieldPosition: 0
[   525.605] 	LinRsvdMaskSize: 0
[   525.605] 	LinRsvdFieldPosition: 0
[   525.605] 	MaxPixelClock: 300000000
[   525.606] Mode: 117 (1024x768)
[   525.606] 	ModeAttributes: 0x9b
[   525.606] 	WinAAttributes: 0x7
[   525.606] 	WinBAttributes: 0x0
[   525.606] 	WinGranularity: 64
[   525.606] 	WinSize: 64
[   525.606] 	WinASegment: 0xa000
[   525.606] 	WinBSegment: 0xa000
[   525.606] 	WinFuncPtr: 0xc00038bf
[   525.606] 	BytesPerScanline: 2048
[   525.606] 	XResolution: 1024
[   525.606] 	YResolution: 768
[   525.606] 	XCharSize: 8
[   525.606] 	YCharSize: 16
[   525.606] 	NumberOfPlanes: 1
[   525.606] 	BitsPerPixel: 16
[   525.606] 	NumberOfBanks: 1
[   525.606] 	MemoryModel: 6
[   525.606] 	BankSize: 0
[   525.606] 	NumberOfImages: 4
[   525.606] 	RedMaskSize: 5
[   525.606] 	RedFieldPosition: 11
[   525.606] 	GreenMaskSize: 6
[   525.606] 	GreenFieldPosition: 5
[   525.606] 	BlueMaskSize: 5
[   525.606] 	BlueFieldPosition: 0
[   525.606] 	RsvdMaskSize: 0
[   525.606] 	RsvdFieldPosition: 0
[   525.606] 	DirectColorModeInfo: 0
[   525.606] 	PhysBasePtr: 0xf8000000
[   525.606] 	LinBytesPerScanLine: 2048
[   525.606] 	BnkNumberOfImagePages: 4
[   525.606] 	LinNumberOfImagePages: 4
[   525.606] 	LinRedMaskSize: 5
[   525.606] 	LinRedFieldPosition: 11
[   525.606] 	LinGreenMaskSize: 6
[   525.606] 	LinGreenFieldPosition: 5
[   525.606] 	LinBlueMaskSize: 5
[   525.606] 	LinBlueFieldPosition: 0
[   525.606] 	LinRsvdMaskSize: 0
[   525.606] 	LinRsvdFieldPosition: 0
[   525.606] 	MaxPixelClock: 300000000
[   525.606] Mode: 119 (1280x1024)
[   525.606] 	ModeAttributes: 0x9b
[   525.606] 	WinAAttributes: 0x7
[   525.606] 	WinBAttributes: 0x0
[   525.606] 	WinGranularity: 64
[   525.606] 	WinSize: 64
[   525.606] 	WinASegment: 0xa000
[   525.606] 	WinBSegment: 0xa000
[   525.606] 	WinFuncPtr: 0xc00038bf
[   525.606] 	BytesPerScanline: 2560
[   525.606] 	XResolution: 1280
[   525.606] 	YResolution: 1024
[   525.606] 	XCharSize: 8
[   525.606] 	YCharSize: 16
[   525.606] 	NumberOfPlanes: 1
[   525.606] 	BitsPerPixel: 15
[   525.606] 	NumberOfBanks: 1
[   525.606] 	MemoryModel: 6
[   525.606] 	BankSize: 0
[   525.606] 	NumberOfImages: 2
[   525.606] 	RedMaskSize: 5
[   525.606] 	RedFieldPosition: 10
[   525.606] 	GreenMaskSize: 5
[   525.606] 	GreenFieldPosition: 5
[   525.606] 	BlueMaskSize: 5
[   525.606] 	BlueFieldPosition: 0
[   525.606] 	RsvdMaskSize: 0
[   525.606] 	RsvdFieldPosition: 0
[   525.606] 	DirectColorModeInfo: 0
[   525.606] 	PhysBasePtr: 0xf8000000
[   525.606] 	LinBytesPerScanLine: 2560
[   525.606] 	BnkNumberOfImagePages: 2
[   525.606] 	LinNumberOfImagePages: 2
[   525.606] 	LinRedMaskSize: 5
[   525.606] 	LinRedFieldPosition: 10
[   525.606] 	LinGreenMaskSize: 5
[   525.606] 	LinGreenFieldPosition: 5
[   525.606] 	LinBlueMaskSize: 5
[   525.606] 	LinBlueFieldPosition: 0
[   525.606] 	LinRsvdMaskSize: 0
[   525.606] 	LinRsvdFieldPosition: 0
[   525.606] 	MaxPixelClock: 300000000
[   525.607] Mode: 11a (1280x1024)
[   525.607] 	ModeAttributes: 0x9b
[   525.607] 	WinAAttributes: 0x7
[   525.607] 	WinBAttributes: 0x0
[   525.607] 	WinGranularity: 64
[   525.607] 	WinSize: 64
[   525.607] 	WinASegment: 0xa000
[   525.607] 	WinBSegment: 0xa000
[   525.607] 	WinFuncPtr: 0xc00038bf
[   525.607] 	BytesPerScanline: 2560
[   525.607] 	XResolution: 1280
[   525.607] 	YResolution: 1024
[   525.607] 	XCharSize: 8
[   525.607] 	YCharSize: 16
[   525.607] 	NumberOfPlanes: 1
[   525.607] 	BitsPerPixel: 16
[   525.607] 	NumberOfBanks: 1
[   525.607] 	MemoryModel: 6
[   525.607] 	BankSize: 0
[   525.607] 	NumberOfImages: 2
[   525.607] 	RedMaskSize: 5
[   525.607] 	RedFieldPosition: 11
[   525.607] 	GreenMaskSize: 6
[   525.607] 	GreenFieldPosition: 5
[   525.607] 	BlueMaskSize: 5
[   525.607] 	BlueFieldPosition: 0
[   525.607] 	RsvdMaskSize: 0
[   525.607] 	RsvdFieldPosition: 0
[   525.607] 	DirectColorModeInfo: 0
[   525.607] 	PhysBasePtr: 0xf8000000
[   525.607] 	LinBytesPerScanLine: 2560
[   525.607] 	BnkNumberOfImagePages: 2
[   525.607] 	LinNumberOfImagePages: 2
[   525.607] 	LinRedMaskSize: 5
[   525.607] 	LinRedFieldPosition: 11
[   525.607] 	LinGreenMaskSize: 6
[   525.607] 	LinGreenFieldPosition: 5
[   525.607] 	LinBlueMaskSize: 5
[   525.607] 	LinBlueFieldPosition: 0
[   525.607] 	LinRsvdMaskSize: 0
[   525.607] 	LinRsvdFieldPosition: 0
[   525.607] 	MaxPixelClock: 300000000
[   525.607] Mode: 132 (320x240)
[   525.608] 	ModeAttributes: 0x9f
[   525.608] 	WinAAttributes: 0x7
[   525.608] 	WinBAttributes: 0x0
[   525.608] 	WinGranularity: 64
[   525.608] 	WinSize: 64
[   525.608] 	WinASegment: 0xa000
[   525.608] 	WinBSegment: 0xa000
[   525.608] 	WinFuncPtr: 0xc00038bf
[   525.608] 	BytesPerScanline: 320
[   525.608] 	XResolution: 320
[   525.608] 	YResolution: 240
[   525.608] 	XCharSize: 8
[   525.608] 	YCharSize: 8
[   525.608] 	NumberOfPlanes: 1
[   525.608] 	BitsPerPixel: 8
[   525.608] 	NumberOfBanks: 1
[   525.608] 	MemoryModel: 4
[   525.608] 	BankSize: 0
[   525.608] 	NumberOfImages: 63
[   525.608] 	RedMaskSize: 0
[   525.608] 	RedFieldPosition: 0
[   525.608] 	GreenMaskSize: 0
[   525.608] 	GreenFieldPosition: 0
[   525.608] 	BlueMaskSize: 0
[   525.608] 	BlueFieldPosition: 0
[   525.608] 	RsvdMaskSize: 0
[   525.608] 	RsvdFieldPosition: 0
[   525.608] 	DirectColorModeInfo: 0
[   525.608] 	PhysBasePtr: 0xf8000000
[   525.608] 	LinBytesPerScanLine: 320
[   525.608] 	BnkNumberOfImagePages: 63
[   525.608] 	LinNumberOfImagePages: 63
[   525.608] 	LinRedMaskSize: 0
[   525.608] 	LinRedFieldPosition: 0
[   525.608] 	LinGreenMaskSize: 0
[   525.608] 	LinGreenFieldPosition: 0
[   525.608] 	LinBlueMaskSize: 0
[   525.608] 	LinBlueFieldPosition: 0
[   525.608] 	LinRsvdMaskSize: 0
[   525.608] 	LinRsvdFieldPosition: 0
[   525.608] 	MaxPixelClock: 1000000
[   525.608] Mode: 133 (400x300)
[   525.608] 	ModeAttributes: 0x9f
[   525.608] 	WinAAttributes: 0x7
[   525.608] 	WinBAttributes: 0x0
[   525.608] 	WinGranularity: 64
[   525.608] 	WinSize: 64
[   525.608] 	WinASegment: 0xa000
[   525.608] 	WinBSegment: 0xa000
[   525.608] 	WinFuncPtr: 0xc00038bf
[   525.608] 	BytesPerScanline: 400
[   525.608] 	XResolution: 400
[   525.608] 	YResolution: 300
[   525.608] 	XCharSize: 8
[   525.608] 	YCharSize: 8
[   525.608] 	NumberOfPlanes: 1
[   525.608] 	BitsPerPixel: 8
[   525.608] 	NumberOfBanks: 1
[   525.608] 	MemoryModel: 4
[   525.608] 	BankSize: 0
[   525.608] 	NumberOfImages: 63
[   525.608] 	RedMaskSize: 0
[   525.608] 	RedFieldPosition: 0
[   525.608] 	GreenMaskSize: 0
[   525.608] 	GreenFieldPosition: 0
[   525.608] 	BlueMaskSize: 0
[   525.608] 	BlueFieldPosition: 0
[   525.608] 	RsvdMaskSize: 0
[   525.608] 	RsvdFieldPosition: 0
[   525.608] 	DirectColorModeInfo: 0
[   525.608] 	PhysBasePtr: 0xf8000000
[   525.608] 	LinBytesPerScanLine: 400
[   525.608] 	BnkNumberOfImagePages: 63
[   525.608] 	LinNumberOfImagePages: 63
[   525.608] 	LinRedMaskSize: 0
[   525.608] 	LinRedFieldPosition: 0
[   525.608] 	LinGreenMaskSize: 0
[   525.608] 	LinGreenFieldPosition: 0
[   525.608] 	LinBlueMaskSize: 0
[   525.608] 	LinBlueFieldPosition: 0
[   525.608] 	LinRsvdMaskSize: 0
[   525.608] 	LinRsvdFieldPosition: 0
[   525.608] 	MaxPixelClock: 1000000
[   525.609] Mode: 134 (512x384)
[   525.609] 	ModeAttributes: 0x9f
[   525.609] 	WinAAttributes: 0x7
[   525.609] 	WinBAttributes: 0x0
[   525.609] 	WinGranularity: 64
[   525.609] 	WinSize: 64
[   525.609] 	WinASegment: 0xa000
[   525.609] 	WinBSegment: 0xa000
[   525.609] 	WinFuncPtr: 0xc00038bf
[   525.609] 	BytesPerScanline: 512
[   525.609] 	XResolution: 512
[   525.609] 	YResolution: 384
[   525.609] 	XCharSize: 8
[   525.609] 	YCharSize: 8
[   525.609] 	NumberOfPlanes: 1
[   525.609] 	BitsPerPixel: 8
[   525.609] 	NumberOfBanks: 1
[   525.609] 	MemoryModel: 4
[   525.609] 	BankSize: 0
[   525.609] 	NumberOfImages: 41
[   525.609] 	RedMaskSize: 0
[   525.609] 	RedFieldPosition: 0
[   525.609] 	GreenMaskSize: 0
[   525.609] 	GreenFieldPosition: 0
[   525.609] 	BlueMaskSize: 0
[   525.609] 	BlueFieldPosition: 0
[   525.609] 	RsvdMaskSize: 0
[   525.609] 	RsvdFieldPosition: 0
[   525.609] 	DirectColorModeInfo: 0
[   525.609] 	PhysBasePtr: 0xf8000000
[   525.609] 	LinBytesPerScanLine: 512
[   525.609] 	BnkNumberOfImagePages: 41
[   525.609] 	LinNumberOfImagePages: 41
[   525.609] 	LinRedMaskSize: 0
[   525.609] 	LinRedFieldPosition: 0
[   525.609] 	LinGreenMaskSize: 0
[   525.609] 	LinGreenFieldPosition: 0
[   525.609] 	LinBlueMaskSize: 0
[   525.609] 	LinBlueFieldPosition: 0
[   525.609] 	LinRsvdMaskSize: 0
[   525.609] 	LinRsvdFieldPosition: 0
[   525.609] 	MaxPixelClock: 1000000
[   525.609] Mode: 135 (320x240)
[   525.609] 	ModeAttributes: 0x9b
[   525.609] 	WinAAttributes: 0x7
[   525.609] 	WinBAttributes: 0x0
[   525.609] 	WinGranularity: 64
[   525.609] 	WinSize: 64
[   525.609] 	WinASegment: 0xa000
[   525.609] 	WinBSegment: 0xa000
[   525.609] 	WinFuncPtr: 0xc00038bf
[   525.609] 	BytesPerScanline: 640
[   525.609] 	XResolution: 320
[   525.609] 	YResolution: 240
[   525.609] 	XCharSize: 8
[   525.609] 	YCharSize: 8
[   525.609] 	NumberOfPlanes: 1
[   525.609] 	BitsPerPixel: 16
[   525.609] 	NumberOfBanks: 1
[   525.609] 	MemoryModel: 6
[   525.609] 	BankSize: 0
[   525.609] 	NumberOfImages: 41
[   525.609] 	RedMaskSize: 5
[   525.609] 	RedFieldPosition: 11
[   525.609] 	GreenMaskSize: 6
[   525.609] 	GreenFieldPosition: 5
[   525.609] 	BlueMaskSize: 5
[   525.609] 	BlueFieldPosition: 0
[   525.609] 	RsvdMaskSize: 0
[   525.609] 	RsvdFieldPosition: 0
[   525.609] 	DirectColorModeInfo: 0
[   525.609] 	PhysBasePtr: 0xf8000000
[   525.610] 	LinBytesPerScanLine: 640
[   525.610] 	BnkNumberOfImagePages: 41
[   525.610] 	LinNumberOfImagePages: 41
[   525.610] 	LinRedMaskSize: 5
[   525.610] 	LinRedFieldPosition: 11
[   525.610] 	LinGreenMaskSize: 6
[   525.610] 	LinGreenFieldPosition: 5
[   525.610] 	LinBlueMaskSize: 5
[   525.610] 	LinBlueFieldPosition: 0
[   525.610] 	LinRsvdMaskSize: 0
[   525.610] 	LinRsvdFieldPosition: 0
[   525.610] 	MaxPixelClock: 1000000
[   525.610] Mode: 136 (400x300)
[   525.610] 	ModeAttributes: 0x9b
[   525.610] 	WinAAttributes: 0x7
[   525.610] 	WinBAttributes: 0x0
[   525.610] 	WinGranularity: 64
[   525.610] 	WinSize: 64
[   525.610] 	WinASegment: 0xa000
[   525.610] 	WinBSegment: 0xa000
[   525.610] 	WinFuncPtr: 0xc00038bf
[   525.610] 	BytesPerScanline: 800
[   525.610] 	XResolution: 400
[   525.610] 	YResolution: 300
[   525.610] 	XCharSize: 8
[   525.610] 	YCharSize: 8
[   525.610] 	NumberOfPlanes: 1
[   525.610] 	BitsPerPixel: 16
[   525.610] 	NumberOfBanks: 1
[   525.610] 	MemoryModel: 6
[   525.610] 	BankSize: 0
[   525.610] 	NumberOfImages: 31
[   525.610] 	RedMaskSize: 5
[   525.610] 	RedFieldPosition: 11
[   525.610] 	GreenMaskSize: 6
[   525.610] 	GreenFieldPosition: 5
[   525.610] 	BlueMaskSize: 5
[   525.610] 	BlueFieldPosition: 0
[   525.610] 	RsvdMaskSize: 0
[   525.610] 	RsvdFieldPosition: 0
[   525.610] 	DirectColorModeInfo: 0
[   525.610] 	PhysBasePtr: 0xf8000000
[   525.610] 	LinBytesPerScanLine: 800
[   525.610] 	BnkNumberOfImagePages: 31
[   525.610] 	LinNumberOfImagePages: 31
[   525.610] 	LinRedMaskSize: 5
[   525.610] 	LinRedFieldPosition: 11
[   525.610] 	LinGreenMaskSize: 6
[   525.610] 	LinGreenFieldPosition: 5
[   525.610] 	LinBlueMaskSize: 5
[   525.610] 	LinBlueFieldPosition: 0
[   525.610] 	LinRsvdMaskSize: 0
[   525.610] 	LinRsvdFieldPosition: 0
[   525.610] 	MaxPixelClock: 1000000
[   525.611] Mode: 137 (512x384)
[   525.611] 	ModeAttributes: 0x9b
[   525.611] 	WinAAttributes: 0x7
[   525.611] 	WinBAttributes: 0x0
[   525.611] 	WinGranularity: 64
[   525.611] 	WinSize: 64
[   525.611] 	WinASegment: 0xa000
[   525.611] 	WinBSegment: 0xa000
[   525.611] 	WinFuncPtr: 0xc00038bf
[   525.611] 	BytesPerScanline: 1024
[   525.611] 	XResolution: 512
[   525.611] 	YResolution: 384
[   525.611] 	XCharSize: 8
[   525.611] 	YCharSize: 8
[   525.611] 	NumberOfPlanes: 1
[   525.611] 	BitsPerPixel: 16
[   525.611] 	NumberOfBanks: 1
[   525.611] 	MemoryModel: 6
[   525.611] 	BankSize: 0
[   525.611] 	NumberOfImages: 20
[   525.611] 	RedMaskSize: 5
[   525.611] 	RedFieldPosition: 11
[   525.611] 	GreenMaskSize: 6
[   525.611] 	GreenFieldPosition: 5
[   525.611] 	BlueMaskSize: 5
[   525.611] 	BlueFieldPosition: 0
[   525.611] 	RsvdMaskSize: 0
[   525.611] 	RsvdFieldPosition: 0
[   525.611] 	DirectColorModeInfo: 0
[   525.611] 	PhysBasePtr: 0xf8000000
[   525.611] 	LinBytesPerScanLine: 1024
[   525.611] 	BnkNumberOfImagePages: 20
[   525.611] 	LinNumberOfImagePages: 20
[   525.611] 	LinRedMaskSize: 5
[   525.611] 	LinRedFieldPosition: 11
[   525.611] 	LinGreenMaskSize: 6
[   525.611] 	LinGreenFieldPosition: 5
[   525.611] 	LinBlueMaskSize: 5
[   525.611] 	LinBlueFieldPosition: 0
[   525.611] 	LinRsvdMaskSize: 0
[   525.611] 	LinRsvdFieldPosition: 0
[   525.611] 	MaxPixelClock: 1000000
[   525.611] Mode: 138 (320x200)
[   525.611] 	ModeAttributes: 0x9f
[   525.611] 	WinAAttributes: 0x7
[   525.611] 	WinBAttributes: 0x0
[   525.611] 	WinGranularity: 64
[   525.611] 	WinSize: 64
[   525.611] 	WinASegment: 0xa000
[   525.611] 	WinBSegment: 0xa000
[   525.611] 	WinFuncPtr: 0xc00038bf
[   525.611] 	BytesPerScanline: 320
[   525.611] 	XResolution: 320
[   525.611] 	YResolution: 200
[   525.611] 	XCharSize: 8
[   525.611] 	YCharSize: 8
[   525.611] 	NumberOfPlanes: 1
[   525.611] 	BitsPerPixel: 8
[   525.611] 	NumberOfBanks: 1
[   525.611] 	MemoryModel: 4
[   525.611] 	BankSize: 0
[   525.611] 	NumberOfImages: 127
[   525.611] 	RedMaskSize: 0
[   525.611] 	RedFieldPosition: 0
[   525.611] 	GreenMaskSize: 0
[   525.611] 	GreenFieldPosition: 0
[   525.611] 	BlueMaskSize: 0
[   525.611] 	BlueFieldPosition: 0
[   525.611] 	RsvdMaskSize: 0
[   525.611] 	RsvdFieldPosition: 0
[   525.611] 	DirectColorModeInfo: 0
[   525.611] 	PhysBasePtr: 0xf8000000
[   525.611] 	LinBytesPerScanLine: 320
[   525.611] 	BnkNumberOfImagePages: 127
[   525.611] 	LinNumberOfImagePages: 127
[   525.611] 	LinRedMaskSize: 0
[   525.611] 	LinRedFieldPosition: 0
[   525.611] 	LinGreenMaskSize: 0
[   525.611] 	LinGreenFieldPosition: 0
[   525.611] 	LinBlueMaskSize: 0
[   525.611] 	LinBlueFieldPosition: 0
[   525.611] 	LinRsvdMaskSize: 0
[   525.611] 	LinRsvdFieldPosition: 0
[   525.611] 	MaxPixelClock: 1000000
[   525.612] Mode: 139 (640x400)
[   525.612] 	ModeAttributes: 0x9b
[   525.612] 	WinAAttributes: 0x7
[   525.612] 	WinBAttributes: 0x0
[   525.612] 	WinGranularity: 64
[   525.612] 	WinSize: 64
[   525.612] 	WinASegment: 0xa000
[   525.612] 	WinBSegment: 0xa000
[   525.612] 	WinFuncPtr: 0xc00038bf
[   525.612] 	BytesPerScanline: 1280
[   525.612] 	XResolution: 640
[   525.612] 	YResolution: 400
[   525.612] 	XCharSize: 8
[   525.612] 	YCharSize: 16
[   525.612] 	NumberOfPlanes: 1
[   525.612] 	BitsPerPixel: 16
[   525.612] 	NumberOfBanks: 1
[   525.612] 	MemoryModel: 6
[   525.612] 	BankSize: 0
[   525.612] 	NumberOfImages: 15
[   525.612] 	RedMaskSize: 5
[   525.612] 	RedFieldPosition: 11
[   525.612] 	GreenMaskSize: 6
[   525.612] 	GreenFieldPosition: 5
[   525.612] 	BlueMaskSize: 5
[   525.612] 	BlueFieldPosition: 0
[   525.612] 	RsvdMaskSize: 0
[   525.612] 	RsvdFieldPosition: 0
[   525.612] 	DirectColorModeInfo: 0
[   525.612] 	PhysBasePtr: 0xf8000000
[   525.612] 	LinBytesPerScanLine: 1280
[   525.612] 	BnkNumberOfImagePages: 15
[   525.612] 	LinNumberOfImagePages: 15
[   525.612] 	LinRedMaskSize: 5
[   525.612] 	LinRedFieldPosition: 11
[   525.612] 	LinGreenMaskSize: 6
[   525.612] 	LinGreenFieldPosition: 5
[   525.612] 	LinBlueMaskSize: 5
[   525.612] 	LinBlueFieldPosition: 0
[   525.612] 	LinRsvdMaskSize: 0
[   525.612] 	LinRsvdFieldPosition: 0
[   525.612] 	MaxPixelClock: 1000000
[   525.612] *Mode: 112 (640x480)
[   525.613] 	ModeAttributes: 0x9b
[   525.613] 	WinAAttributes: 0x7
[   525.613] 	WinBAttributes: 0x0
[   525.613] 	WinGranularity: 64
[   525.613] 	WinSize: 64
[   525.613] 	WinASegment: 0xa000
[   525.613] 	WinBSegment: 0xa000
[   525.613] 	WinFuncPtr: 0xc00038bf
[   525.613] 	BytesPerScanline: 2560
[   525.613] 	XResolution: 640
[   525.613] 	YResolution: 480
[   525.613] 	XCharSize: 8
[   525.613] 	YCharSize: 16
[   525.613] 	NumberOfPlanes: 1
[   525.613] 	BitsPerPixel: 32
[   525.613] 	NumberOfBanks: 1
[   525.613] 	MemoryModel: 6
[   525.613] 	BankSize: 0
[   525.613] 	NumberOfImages: 5
[   525.613] 	RedMaskSize: 8
[   525.613] 	RedFieldPosition: 16
[   525.613] 	GreenMaskSize: 8
[   525.613] 	GreenFieldPosition: 8
[   525.613] 	BlueMaskSize: 8
[   525.613] 	BlueFieldPosition: 0
[   525.613] 	RsvdMaskSize: 8
[   525.613] 	RsvdFieldPosition: 24
[   525.613] 	DirectColorModeInfo: 0
[   525.613] 	PhysBasePtr: 0xf8000000
[   525.613] 	LinBytesPerScanLine: 2560
[   525.613] 	BnkNumberOfImagePages: 5
[   525.613] 	LinNumberOfImagePages: 5
[   525.613] 	LinRedMaskSize: 8
[   525.613] 	LinRedFieldPosition: 16
[   525.613] 	LinGreenMaskSize: 8
[   525.613] 	LinGreenFieldPosition: 8
[   525.613] 	LinBlueMaskSize: 8
[   525.613] 	LinBlueFieldPosition: 0
[   525.613] 	LinRsvdMaskSize: 8
[   525.613] 	LinRsvdFieldPosition: 24
[   525.613] 	MaxPixelClock: 300000000
[   525.613] *Mode: 115 (800x600)
[   525.613] 	ModeAttributes: 0x9b
[   525.613] 	WinAAttributes: 0x7
[   525.613] 	WinBAttributes: 0x0
[   525.613] 	WinGranularity: 64
[   525.613] 	WinSize: 64
[   525.613] 	WinASegment: 0xa000
[   525.613] 	WinBSegment: 0xa000
[   525.613] 	WinFuncPtr: 0xc00038bf
[   525.613] 	BytesPerScanline: 3200
[   525.613] 	XResolution: 800
[   525.613] 	YResolution: 600
[   525.613] 	XCharSize: 8
[   525.613] 	YCharSize: 16
[   525.613] 	NumberOfPlanes: 1
[   525.613] 	BitsPerPixel: 32
[   525.613] 	NumberOfBanks: 1
[   525.613] 	MemoryModel: 6
[   525.613] 	BankSize: 0
[   525.613] 	NumberOfImages: 3
[   525.613] 	RedMaskSize: 8
[   525.613] 	RedFieldPosition: 16
[   525.613] 	GreenMaskSize: 8
[   525.613] 	GreenFieldPosition: 8
[   525.613] 	BlueMaskSize: 8
[   525.613] 	BlueFieldPosition: 0
[   525.613] 	RsvdMaskSize: 8
[   525.613] 	RsvdFieldPosition: 24
[   525.613] 	DirectColorModeInfo: 0
[   525.613] 	PhysBasePtr: 0xf8000000
[   525.613] 	LinBytesPerScanLine: 3200
[   525.613] 	BnkNumberOfImagePages: 3
[   525.613] 	LinNumberOfImagePages: 3
[   525.613] 	LinRedMaskSize: 8
[   525.613] 	LinRedFieldPosition: 16
[   525.613] 	LinGreenMaskSize: 8
[   525.613] 	LinGreenFieldPosition: 8
[   525.613] 	LinBlueMaskSize: 8
[   525.613] 	LinBlueFieldPosition: 0
[   525.613] 	LinRsvdMaskSize: 8
[   525.613] 	LinRsvdFieldPosition: 24
[   525.613] 	MaxPixelClock: 300000000
[   525.614] *Mode: 118 (1024x768)
[   525.614] 	ModeAttributes: 0x9b
[   525.614] 	WinAAttributes: 0x7
[   525.614] 	WinBAttributes: 0x0
[   525.614] 	WinGranularity: 64
[   525.614] 	WinSize: 64
[   525.614] 	WinASegment: 0xa000
[   525.614] 	WinBSegment: 0xa000
[   525.614] 	WinFuncPtr: 0xc00038bf
[   525.614] 	BytesPerScanline: 4096
[   525.614] 	XResolution: 1024
[   525.614] 	YResolution: 768
[   525.614] 	XCharSize: 8
[   525.614] 	YCharSize: 16
[   525.614] 	NumberOfPlanes: 1
[   525.614] 	BitsPerPixel: 32
[   525.614] 	NumberOfBanks: 1
[   525.614] 	MemoryModel: 6
[   525.614] 	BankSize: 0
[   525.614] 	NumberOfImages: 1
[   525.614] 	RedMaskSize: 8
[   525.614] 	RedFieldPosition: 16
[   525.614] 	GreenMaskSize: 8
[   525.614] 	GreenFieldPosition: 8
[   525.614] 	BlueMaskSize: 8
[   525.614] 	BlueFieldPosition: 0
[   525.614] 	RsvdMaskSize: 8
[   525.614] 	RsvdFieldPosition: 24
[   525.614] 	DirectColorModeInfo: 0
[   525.614] 	PhysBasePtr: 0xf8000000
[   525.614] 	LinBytesPerScanLine: 4096
[   525.614] 	BnkNumberOfImagePages: 1
[   525.614] 	LinNumberOfImagePages: 1
[   525.614] 	LinRedMaskSize: 8
[   525.614] 	LinRedFieldPosition: 16
[   525.614] 	LinGreenMaskSize: 8
[   525.614] 	LinGreenFieldPosition: 8
[   525.614] 	LinBlueMaskSize: 8
[   525.614] 	LinBlueFieldPosition: 0
[   525.614] 	LinRsvdMaskSize: 8
[   525.614] 	LinRsvdFieldPosition: 24
[   525.614] 	MaxPixelClock: 300000000
[   525.614] *Mode: 11b (1280x1024)
[   525.614] 	ModeAttributes: 0x9b
[   525.614] 	WinAAttributes: 0x7
[   525.614] 	WinBAttributes: 0x0
[   525.614] 	WinGranularity: 64
[   525.614] 	WinSize: 64
[   525.614] 	WinASegment: 0xa000
[   525.614] 	WinBSegment: 0xa000
[   525.614] 	WinFuncPtr: 0xc00038bf
[   525.614] 	BytesPerScanline: 5120
[   525.614] 	XResolution: 1280
[   525.614] 	YResolution: 1024
[   525.614] 	XCharSize: 8
[   525.614] 	YCharSize: 16
[   525.615] 	NumberOfPlanes: 1
[   525.615] 	BitsPerPixel: 32
[   525.615] 	NumberOfBanks: 1
[   525.615] 	MemoryModel: 6
[   525.615] 	BankSize: 0
[   525.615] 	NumberOfImages: 0
[   525.615] 	RedMaskSize: 8
[   525.615] 	RedFieldPosition: 16
[   525.615] 	GreenMaskSize: 8
[   525.615] 	GreenFieldPosition: 8
[   525.615] 	BlueMaskSize: 8
[   525.615] 	BlueFieldPosition: 0
[   525.615] 	RsvdMaskSize: 8
[   525.615] 	RsvdFieldPosition: 24
[   525.615] 	DirectColorModeInfo: 0
[   525.615] 	PhysBasePtr: 0xf8000000
[   525.615] 	LinBytesPerScanLine: 5120
[   525.615] 	BnkNumberOfImagePages: 0
[   525.615] 	LinNumberOfImagePages: 0
[   525.615] 	LinRedMaskSize: 8
[   525.615] 	LinRedFieldPosition: 16
[   525.615] 	LinGreenMaskSize: 8
[   525.615] 	LinGreenFieldPosition: 8
[   525.615] 	LinBlueMaskSize: 8
[   525.615] 	LinBlueFieldPosition: 0
[   525.615] 	LinRsvdMaskSize: 8
[   525.615] 	LinRsvdFieldPosition: 24
[   525.615] 	MaxPixelClock: 300000000
[   525.615] *Mode: 13e (1600x1200)
[   525.615] 	ModeAttributes: 0x9b
[   525.615] 	WinAAttributes: 0x7
[   525.615] 	WinBAttributes: 0x0
[   525.615] 	WinGranularity: 64
[   525.615] 	WinSize: 64
[   525.615] 	WinASegment: 0xa000
[   525.615] 	WinBSegment: 0xa000
[   525.615] 	WinFuncPtr: 0xc00038bf
[   525.615] 	BytesPerScanline: 6400
[   525.615] 	XResolution: 1600
[   525.615] 	YResolution: 1200
[   525.615] 	XCharSize: 8
[   525.615] 	YCharSize: 16
[   525.615] 	NumberOfPlanes: 1
[   525.615] 	BitsPerPixel: 32
[   525.615] 	NumberOfBanks: 1
[   525.615] 	MemoryModel: 6
[   525.615] 	BankSize: 0
[   525.615] 	NumberOfImages: 0
[   525.615] 	RedMaskSize: 8
[   525.615] 	RedFieldPosition: 16
[   525.615] 	GreenMaskSize: 8
[   525.615] 	GreenFieldPosition: 8
[   525.615] 	BlueMaskSize: 8
[   525.615] 	BlueFieldPosition: 0
[   525.615] 	RsvdMaskSize: 8
[   525.615] 	RsvdFieldPosition: 24
[   525.615] 	DirectColorModeInfo: 0
[   525.615] 	PhysBasePtr: 0xf8000000
[   525.615] 	LinBytesPerScanLine: 6400
[   525.615] 	BnkNumberOfImagePages: 0
[   525.615] 	LinNumberOfImagePages: 0
[   525.615] 	LinRedMaskSize: 8
[   525.615] 	LinRedFieldPosition: 16
[   525.615] 	LinGreenMaskSize: 8
[   525.615] 	LinGreenFieldPosition: 8
[   525.615] 	LinBlueMaskSize: 8
[   525.615] 	LinBlueFieldPosition: 0
[   525.615] 	LinRsvdMaskSize: 8
[   525.615] 	LinRsvdFieldPosition: 24
[   525.615] 	MaxPixelClock: 300000000
[   525.615] 
[   525.615] (II) VESA(0): Total Memory: 128 64KB banks (8192kB)
[   525.615] (II) VESA(0): <default monitor>: Using hsync range of 30.00-115.00 kHz
[   525.615] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-160.00 Hz
[   525.615] (II) VESA(0): <default monitor>: Using maximum pixel clock of 335.00 MHz
[   525.615] (WW) VESA(0): Unable to estimate virtual size
[   525.654] (--) VESA(0): Virtual size is 1600x1200 (pitch 1600)
[   525.654] (**) VESA(0): *Built-in mode "1600x1200"
[   525.654] (**) VESA(0): *Built-in mode "1280x1024"
[   525.654] (**) VESA(0): *Built-in mode "1024x768"
[   525.654] (**) VESA(0): *Built-in mode "800x600"
[   525.654] (**) VESA(0): *Built-in mode "640x480"
[   525.654] (**) VESA(0): Display dimensions: (400, 300) mm
[   525.654] (**) VESA(0): DPI set to (101, 101)
[   525.654] (**) VESA(0): Using "Shadow Framebuffer"
[   525.654] (II) Loading sub module "shadow"
[   525.654] (II) LoadModule: "shadow"
[   525.654] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   525.654] (II) Module shadow: vendor="X.Org Foundation"
[   525.654] 	compiled for 1.10.1, module version = 1.1.0
[   525.654] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   525.654] (II) Loading sub module "fb"
[   525.654] (II) LoadModule: "fb"
[   525.654] (II) Loading /usr/lib/xorg/modules/libfb.so
[   525.654] (II) Module fb: vendor="X.Org Foundation"
[   525.654] 	compiled for 1.10.1, module version = 1.0.0
[   525.654] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   525.655] (II) UnloadModule: "fbdev"
[   525.655] (II) Unloading fbdev
[   525.655] (II) UnloadModule: "fbdevhw"
[   525.655] (II) Unloading fbdevhw
[   525.655] (==) Depth 24 pixmap format is 32 bpp
[   525.655] (II) Loading sub module "int10"
[   525.655] (II) LoadModule: "int10"
[   525.655] (II) Loading /usr/lib/xorg/modules/libint10.so
[   525.655] (II) Module int10: vendor="X.Org Foundation"
[   525.655] 	compiled for 1.10.1, module version = 1.0.0
[   525.655] 	ABI class: X.Org Video Driver, version 10.0
[   525.655] (II) VESA(0): initializing int10
[   525.658] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[   525.659] (II) VESA(0): VESA BIOS detected
[   525.659] (II) VESA(0): VESA VBE Version 3.0
[   525.659] (II) VESA(0): VESA VBE Total Mem: 8192 kB
[   525.659] (II) VESA(0): VESA VBE OEM: XGI
[   525.659] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[   525.659] (II) VESA(0): VESA VBE OEM Vendor: XGI Technology, Inc.
[   525.659] (II) VESA(0): VESA VBE OEM Product: Volari Z7
[   525.659] (II) VESA(0): VESA VBE OEM Product Rev: 1.07.08
[   525.660] (II) VESA(0): virtual address = 0x7f9e06068000,
	physical address = 0xf8000000, size = 8388608
[   525.667] (II) VESA(0): Setting up VESA Mode 0x13E (1600x1200)
[   525.700] (==) VESA(0): Default visual is TrueColor
[   525.701] (==) VESA(0): Backing store disabled
[   525.701] (==) VESA(0): DPMS enabled
[   525.701] (==) RandR enabled
[   525.701] (II) Initializing built-in extension Generic Event Extension
[   525.701] (II) Initializing built-in extension SHAPE
[   525.701] (II) Initializing built-in extension MIT-SHM
[   525.701] (II) Initializing built-in extension XInputExtension
[   525.701] (II) Initializing built-in extension XTEST
[   525.701] (II) Initializing built-in extension BIG-REQUESTS
[   525.701] (II) Initializing built-in extension SYNC
[   525.701] (II) Initializing built-in extension XKEYBOARD
[   525.701] (II) Initializing built-in extension XC-MISC
[   525.701] (II) Initializing built-in extension SECURITY
[   525.701] (II) Initializing built-in extension XINERAMA
[   525.701] (II) Initializing built-in extension XFIXES
[   525.701] (II) Initializing built-in extension RENDER
[   525.701] (II) Initializing built-in extension RANDR
[   525.701] (II) Initializing built-in extension COMPOSITE
[   525.701] (II) Initializing built-in extension DAMAGE
[   525.701] (II) Initializing built-in extension GESTURE
[   525.708] (II) AIGLX: Screen 0 is not DRI2 capable
[   525.708] (II) AIGLX: Screen 0 is not DRI capable
[   525.708] (II) AIGLX: Trying DRI driver /usr/lib/dri/swrast_dri.so
[   525.711] (II) AIGLX: Loaded and initialized swrast
[   525.711] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   525.736] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   525.746] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   525.746] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   525.746] (II) LoadModule: "evdev"
[   525.746] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   525.746] (II) Module evdev: vendor="X.Org Foundation"
[   525.746] 	compiled for 1.10.0.902, module version = 2.6.0
[   525.746] 	Module class: X.Org XInput Driver
[   525.746] 	ABI class: X.Org XInput driver, version 12.3
[   525.746] (II) Using input driver 'evdev' for 'Power Button'
[   525.746] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   525.746] (**) Power Button: always reports core events
[   525.746] (**) Power Button: Device: "/dev/input/event1"
[   525.747] (--) Power Button: Found keys
[   525.747] (II) Power Button: Configuring as keyboard
[   525.747] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   525.747] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   525.747] (**) Option "xkb_rules" "evdev"
[   525.747] (**) Option "xkb_model" "pc105"
[   525.747] (**) Option "xkb_layout" "us"
[   525.748] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   525.748] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   525.748] (II) Using input driver 'evdev' for 'Sleep Button'
[   525.748] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   525.748] (**) Sleep Button: always reports core events
[   525.748] (**) Sleep Button: Device: "/dev/input/event2"
[   525.748] (--) Sleep Button: Found keys
[   525.748] (II) Sleep Button: Configuring as keyboard
[   525.748] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSLPBN:00/input/input2/event2"
[   525.748] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[   525.748] (**) Option "xkb_rules" "evdev"
[   525.748] (**) Option "xkb_model" "pc105"
[   525.748] (**) Option "xkb_layout" "us"
[   525.750] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   525.750] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   525.750] (II) Using input driver 'evdev' for 'Power Button'
[   525.750] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   525.750] (**) Power Button: always reports core events
[   525.750] (**) Power Button: Device: "/dev/input/event0"
[   525.750] (--) Power Button: Found keys
[   525.750] (II) Power Button: Configuring as keyboard
[   525.750] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   525.750] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[   525.751] (**) Option "xkb_rules" "evdev"
[   525.751] (**) Option "xkb_model" "pc105"
[   525.751] (**) Option "xkb_layout" "us"
[   525.767] (II) config/udev: Adding input device SSS USB Headphone Set (/dev/input/event4)
[   525.767] (**) SSS USB Headphone Set: Applying InputClass "evdev keyboard catchall"
[   525.767] (II) Using input driver 'evdev' for 'SSS USB Headphone Set'
[   525.767] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   525.767] (**) SSS USB Headphone Set: always reports core events
[   525.767] (**) SSS USB Headphone Set: Device: "/dev/input/event4"
[   525.767] (--) SSS USB Headphone Set: Found keys
[   525.767] (II) SSS USB Headphone Set: Configuring as keyboard
[   525.767] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:03.0/usb2/2-2/2-2:1.3/input/input4/event4"
[   525.767] (II) XINPUT: Adding extended input device "SSS USB Headphone Set" (type: KEYBOARD)
[   525.767] (**) Option "xkb_rules" "evdev"
[   525.767] (**) Option "xkb_model" "pc105"
[   525.767] (**) Option "xkb_layout" "us"
[   525.771] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   525.771] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   525.771] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   525.771] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   525.771] (**) AT Translated Set 2 keyboard: always reports core events
[   525.771] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   525.771] (--) AT Translated Set 2 keyboard: Found keys
[   525.771] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[   525.771] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   525.771] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[   525.771] (**) Option "xkb_rules" "evdev"
[   525.771] (**) Option "xkb_model" "pc105"
[   525.771] (**) Option "xkb_layout" "us"
[   525.772] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event5)
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "evdev pointer catchall"
[   525.773] (II) Using input driver 'evdev' for 'ImPS/2 Logitech Wheel Mouse'
[   525.773] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: always reports core events
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: Device: "/dev/input/event5"
[   525.773] (--) ImPS/2 Logitech Wheel Mouse: Found 3 mouse buttons
[   525.773] (--) ImPS/2 Logitech Wheel Mouse: Found scroll wheel(s)
[   525.773] (--) ImPS/2 Logitech Wheel Mouse: Found relative axes
[   525.773] (--) ImPS/2 Logitech Wheel Mouse: Found x and y relative axes
[   525.773] (II) ImPS/2 Logitech Wheel Mouse: Configuring as mouse
[   525.773] (II) ImPS/2 Logitech Wheel Mouse: Adding scrollwheel support
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: YAxisMapping: buttons 4 and 5
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   525.773] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[   525.773] (II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE)
[   525.773] (II) ImPS/2 Logitech Wheel Mouse: initialized for relative axes.
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: (accel) keeping acceleration scheme 1
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration profile 0
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000
[   525.773] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4
[   525.774] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse0)
[   525.774] (II) No input driver/identifier specified (ignoring)
[   538.871] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)

> 
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
	Load  "dbe"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card0"
	Driver      "vesa"
	BusID       "PCI:0:6:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:0:6:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


---

### Post by realzippy on 2011-08-23
Open /etc/default/grub
```
gksudo gedit /etc/default/grub
```
and delete the # in line: (so it is not ignored)
#GRUB_GFXMODE=640x480
save changes.
Run
```
sudo update-grub
```

That might fix your boot "chaos".
If you have resolution problems when ubuntu runs,post output from

```
xrandr -q
```

---

### Post by carlexpc on 2011-08-23
try to reconfigure your Xorg package like this:

$ sudo dpkg-reconfigure <xorg package for your video card>

for example:

$ sudo dpkg-reconfigure xserver-xorg-video-intel

---

### Post by DiagonalArg on 2011-08-26
RealZippy - Thanks.  Unfortunately, that approach is not working.  The "Chaos" I speak of is on the login screen.  The screen image "shimmers" and there is a double image (two mouse pointers, for example).  I had the same problem after login, until I changed the resolution from 1600x1200 to 1280x1024.  At first I thought it was an electrical issue, perhaps my power supply being too close to the CRT, but moving the computer far away did nothing.  Then I noticed that the only choice for refresh rate under system>>preferences>>monitors, is 0Hz, so I assumed I'd be needing an xorg.conf.

Here is my xrandr -q output, though it doesn't appear to tell us a lot ...

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1600 x 1200
default connected 1280x1024+0+0 0mm x 0mm
   1600x1200       0.0  
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0

---

### Post by DiagonalArg on 2011-08-26
> **carlexpc said:**
> try to reconfigure your Xorg package like this:

$ sudo dpkg-reconfigure <xorg package for your video card>

for example:

$ sudo dpkg-reconfigure xserver-xorg-video-intel

Ok, so I'm just running a Tyan server board here, with onboard video.  ([http://www.tyan.com/archive/products/html/tomcath1000e.html](http://www.tyan.com/archive/products/html/tomcath1000e.html))

This is what the spec sheet says:

Integrated 2D / 3D PCI Graphics
.XGI VolariTM Z7 graphic controller
.PCI interface
.16MB DDR video frame buffer memory

I see a whole long list of xserver-xorg-video-*.  Which should I pick??

In case it's relevant, the CRT is an NEC MultiSync FE2111SB.  What I had been doing was searching for an xorg.conf for that, but maybe that's the wrong approach?

Thanks for the help ... not sure where to go from here ...

---

### Post by realzippy on 2011-08-26
..we could test creating a modeline.Your monitor should do
1600x1200 @ 75 Hz  or sort of.

Otherwise I had to google,never heard about an issue with doubled cursor.
Also admit that I have no idea about volari known issues...
So you want a quick xrandr-add-modeline-test?

---

### Post by realzippy on 2011-08-26
If you want to test run those 3 commands:
```
xrandr --newmode "1600x1200_75.00"  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync
xrandr --addmode default 1600x1200_75.00
xrandr --output default --mode 1600x1200_75.00
```

---

### Post by DiagonalArg on 2011-08-26
> **realzippy said:**
> ..we could test creating a modeline.Your monitor should do
1600x1200 @ 75 Hz  or sort of.

Otherwise I had to google,never heard about an issue with doubled cursor.
Also admit that I have no idea about volari known issues...
So you want a quick xrandr-add-modeline-test?

Ok, so ... a bit Greek to me.  What are you suggesting I do with "xrandr-add-modeline-test"?  (I can't find a man page on it.)

And by the way, I can google around looking for xorg.conf files, but they are perhaps Spanish to me.  I mean, I get a basic idea, but ...

Thanks for your help ...

---

### Post by DiagonalArg on 2011-08-26
Ok.  I"ll try that.  What does this string of characters represent?

204.75  1600 1720 1888 2176  1200 1203 1207 1255

[Nevermind, I'm looking at the man page ... complicated~!]

---

### Post by realzippy on 2011-08-26
That is a modeline created by cvt:

```
cvt 1600 1200 75
```
Modeline syntax: pclk hdisp hsyncstart hsyncend htotal vdisp vsyncstart vsyncend vtotal

As you can see in your log,there are also modelines,with that faulty
0 Hz...  :
Modeline "1600x1200"x[COLOR="Red"]0.0 [/COLOR]202.50 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync 

..this might be due to a bad Edid file.

Don 't worry,the xrandr commands I suggested are per session only,
if anything should go wrong (can't ;-) ),just reboot or restart X.

---

### Post by DiagonalArg on 2011-08-26
Ok, I'm trying but this is what I get in response to the first command:

xrandr --newmode "1600x1200_75.00"  204.75  1600 1720 1888 2176  1200 1203 1207 1255 -hsync +vsync 

xrandr: Failed to get size of gamma for output default

:confused:

---

### Post by DiagonalArg on 2011-08-26
Ah, I'm feeling real stupid because I really should have added this before.  I'm also running through a KVM.  Specs are, maximum resolution:

1920x1440
Video Bandwidth 200Mhz.

---

### Post by realzippy on 2011-08-26
That is common,ignore it.
After you have run 1rst command,the resolution should appear
in the bottom of 
```
xrandr -q
```
Just go on with other both commands...

---

### Post by DiagonalArg on 2011-08-26
KVM is probably not the issue though, because I don't have this problem on a Dell with the same Ubuntu 11.04.

---

### Post by realzippy on 2011-08-26
> **DiagonalArg said:**
> Ah, I'm feeling real stupid because I really should have added this before.  I'm also running through a KVM.  Specs are, maximum resolution:

1920x1440
Video Bandwidth 200Mhz.

Indeed.
..our modeline uses 204.75 Mhz,but anyway,please go on.
If it fails,we can test another modeline..(with 72 Hz instead,resulting 196 Mhz)

---

### Post by DiagonalArg on 2011-08-26
Yup, fails as it did before.  I had to use system>>prefs monitors to go back to the 1280x1024 setting. 

There is shimmering on the screen.  Just off the center-line there are horizontal lines about 1.5" long moving up & down the screen.

---

### Post by realzippy on 2011-08-26
then test 72 Hz :

```
xrandr --newmode "1600x1200_72.00"  [COLOR="SeaGreen"]196.00[/COLOR]  1600 1720 1888 2176  1200 1203 1207 1253 -hsync +vsync
xrandr --addmode default 1600x1200_72.00
xrandr --output default --mode 1600x1200_72.00
```

---

### Post by DiagonalArg on 2011-08-26
Here's xranar -q from that Dell I mentioned:

Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 4096 x 4096            
VGA-1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 396mm   
x 297mm                                                                          
   1600x1200      85.0*+   75.0     70.0     65.0     60.0                       
   1920x1440      75.0     60.0                                                  
   1856x1392      75.0     60.0                                                  
   1792x1344      75.0     60.0                                                  
   1920x1200      84.9     74.9     59.9                                         
   1680x1050      84.9     74.9     60.0                                         
   1400x1050      85.0     74.9     60.0                                         
   1280x1024      85.0     75.0     60.0                                         
   1440x900       84.8     75.0     59.9                                         
   1280x960       85.0     60.0                                                  
   1360x768       60.0                                                           
   1280x800       84.9     74.9     59.8                                         
   1152x864       75.0                                                           
   1280x768       84.8     74.9     59.9                                         
   1024x768       85.0     75.1     75.0     70.1     60.0                       
   832x624        74.6                                                           
   800x600        85.1     72.2     75.0     60.3     56.2                       
   848x480        60.0                                                           
   640x480        85.0     75.0     72.8     72.8     66.7     60.0     59.9     
   720x400        85.0     87.8     70.1                                         
   640x400        85.1                                                           
   640x350        85.1                                                           
TV-1 disconnected (normal left inverted right x axis y axis)

---

### Post by DiagonalArg on 2011-08-26
Well, no go on 
xrandr --newmode "1600x1200_72.00" ...

Same problem as before.

How can I understand that string of digits & flags on the --newmode line?  I suppose the point is to just explore parameter space?

---

### Post by realzippy on 2011-08-26
That doesn't help,although it seems that the 200 Mhz limit of the switch seems to be no problem.(referring to post #18 )
Please test the 72 Hz version I suggested,if it also fails,
I would check if:

1.Monitor works fine without KVM
2.change the monitor cables between the 2 monitors,sometimes they corrupt
 signal handling.

---

### Post by realzippy on 2011-08-26
> **DiagonalArg said:**
> 
How can I understand that string of digits & flags on the --newmode line?  I suppose the point is to just explore parameter space?

[http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline)

---

### Post by DiagonalArg on 2011-08-26
Ya, that second mode doesn't work.  I'll try switching the monitor cables, now.  I'll let you know if that makes a difference.  If not.  I'll have to disassemble to try that monitor on it's own, with this computer.  (That would be later this afternoon.)

I really appreciate all your help, RealZippy!  Back at you in a bit ...

---

### Post by realzippy on 2011-08-26
Also playing with the modeline values might help,remember an old thread
where many modelines made problems,at last one worked,although nobody involved in that thread understood why...

Good luck!

---

### Post by DiagonalArg on 2011-08-26
Ok, well ... it's not the cable.  I just switched.  I did notice that on the Dell, System>>Prefs>>Monitors has identified the monitor correctly as a "NEC Coporation 20"".  On this Tyan, it just says that the monitor is unknown.  I guess that means we're closing in on that "XGI VolariTM Z7 graphic controller" being the one that is presenting the difficulty, yes?

In any case, I'll try without the KVM, later today ...  If it works, is there some way for me to save the identified settings, and then import them into this machine for use while it's on the KVM?

---

### Post by DiagonalArg on 2011-08-26
Ok, well this claims that the XGI Volari Z7 should work with the "sis" driver:

[http://manpages.ubuntu.com/manpages/hardy/man4/sis.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/sis.4.html)

>   sis  is  an  Xorg  driver  for SiS (Silicon Integrated Systems) and XGI video chips.  The  driver  is  accelerated  and  provides  support for colordepths  of  8,  16 and 24 bpp. XVideo, Render and other extensions are supported as well.

So ... how do I identify which driver I've got??

---

### Post by realzippy on 2011-08-26
deleted nonsense due to misunderstanding.

---

### Post by realzippy on 2011-08-26
> **DiagonalArg said:**
> 
So ... how do I identify which driver I've got??

usually
```
lshw -c video
```
shows.
Eg here  (2 graphic cards):

```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: [COLOR="Lime"]driver=nvidia[/COLOR] latency=0
       resources: irq:16 memory:d0000000-d0ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128) memory:d1000000-d107ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: [COLOR="Lime"]driver=i915[/COLOR] latency=0
       resources: irq:42 memory:d1400000-d17fffff memory:c0000000-cfffffff ioport:4050(size=8)
```


..guess you run vesa,since the sis driver refuses to work about 1024x768
(normally).Also the Xorg.0.log tells you.First you posted (with the nec)
runs vesa,so...

---

### Post by DiagonalArg on 2011-08-26
> **realzippy said:**
> Just realise that the Xorg.0.log you posted must be the one when started
with the NEC FE2111SB connected/switched to...
Monitor's edid seems fine,since the nec is working.
Maybe you get a hint when switching to the other monitor before booting,
and post resulting Xorg.0.log again..

Ok, I thought I was connecting the NEC directly to the Tyan and booting again, to see if it worked without the KVM.  Are you now saying I should (also?) boot with a different monitor and see what I get, posting the Xorg.0.log?

(I did install ubuntu on this machine using a different monitor connected directly, sans KVM.  Could switching monitor like this present a problem?)

---

### Post by DiagonalArg on 2011-08-26
> ..guess you run vesa,since the sis driver refuses to work about 1024x768
(normally).Also the Xorg.0.log tells you.First you posted (with the nec)
runs vesa,so..

Turns out, not.  It's "xgifb":

sudo lshw -c video
  *-display               
       description: VGA compatible controller
       product: Z7/Z9 (XG20 core)
       vendor: XGI Technology Inc. (eXtreme Graphics Innovation)
       physical id: 6
       bus info: pci@0000:00:06.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller cap_list rom
       configuration: driver=xgifb latency=0
       resources: irq:0 memory:f8000000-fbffffff memory:febc0000-febfffff ioport:ec00(size=128)

---

### Post by realzippy on 2011-08-26
No,wait...It seems that I got you totally wrong:
I thought you connected 1 computer to 2 monitors...
one monitor working fine,the other making trouble.
Sorry for that goof,now I need a breath and think about it.

---

### Post by DiagonalArg on 2011-08-26
Got it!  No, one monitor --> KVM --> multiple machines.  One machine is a Dell/ Ubuntu 11.04, which identifies "NEC Corporation 20"".  The other is a Tyan S3970/ Ubuntu 11.04, with the  XGI Volari Z7 and which fails to identify the monitor.

Dude, I really appreciate the help.  I've been up all night struggling with this thing.  I better get 3 hours of sleep before I have to go to a meeting!  :-/

Later -

---

### Post by realzippy on 2011-08-26
So you have a tyan server or whatever,and a dell.
When running the dell,the nec monitor runs fine,
when switching to tyan it is garbled.
Did I understand now?
Again,sorry.

Edit:
crossposting,but it seems as I understood now.
Well,thats a completely different story...

---

### Post by DiagonalArg on 2011-08-26
You got it.

Hey, no apologies necessary.  In fact, if I could deliver food, I'd do it!  :)

---

### Post by realzippy on 2011-08-26
You think I need food to get my brain up? :-)

back to topic:
*(I did install ubuntu on this machine using a different monitor connected directly, sans KVM. Could switching monitor like this present a problem?)*

...if a xorg.conf got created,yes.
Otherwise kernel/graphics driver should handle a different monitor.

But you should sleep now... ?

---

### Post by DiagonalArg on 2011-08-26
Ok, RealZippy!  So, to answer your question, no there was no xorg.conf created when the system was installed with the other monitor (and there's no xorg.conf now), nor is there on the Dell that is working fine.

I'm pretty sure it's not useful, but I have here the lshw -c video for the Dell:

>   *-display                                                                      
       description: VGA compatible controller                                    
       product: NV17 [GeForce4 MX 420]                                           
       vendor: nVidia Corporation                                                
       physical id: 0                                                            
       bus info: pci@0000:01:00.0                                                
       version: a3                                                               
       width: 32 bits                                                            
       clock: 66MHz                                                              
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom       
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5            
       resources: irq:16 memory:fc000000-fcffffff memory:f4000000-f7ffffff memor\
y:f3f80000-f3ffffff memory:f0000000-f001ffff 

If you have more thoughts, I'm all ears!

---

### Post by DiagonalArg on 2011-08-26
Well, I just tried booting from the live CD - It's got the same problem, exactly.  And, I guess no surprise, the same driver is being used for the video.

Hm...  Now that you're understanding that there's only one monitor, should I still be doing the experiment of connecting to the Tyan without the KVM?  What do you think?

---

### Post by DiagonalArg on 2011-08-26
Ok, besides the Dell, I've got an old thinkpad on which this monitor is working through the KVM.  That thinkpad does not identify the monitor ("Unknown"), but it does work:

> Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1200            
default connected 1600x1200+0+0 0mm x 0mm                                        
   1600x1200      85.0*    75.0     70.0     65.0     60.0                       
   1400x1050      85.0     75.0     70.0     60.0                                
   1280x1024      85.0     75.0     60.0                                         
   1024x768       87.0     85.0     75.0     70.0     60.0                       
   800x600        85.0     75.0     72.0     60.0     56.0     70.0     65.0     
   640x480        85.0     75.0     73.0     67.0     60.0                       
   640x400        85.0                                                           
   512x384        87.0     85.0     75.0     70.0     60.0                       
   400x300        85.0     75.0     72.0     60.0     56.0                       
   320x240        85.0     75.0     73.0     60.0                                
   320x200        85.0                                                           
  *-display UNCLAIMED                                                            
       description: VGA compatible controller                                    
       product: SuperSavage IX/C SDR                                             
       vendor: S3 Inc.                                                           
       physical id: 0                                                            
       bus info: pci@0000:01:00.0                                                
       version: 05                                                               
       width: 32 bits                                                            
       clock: 66MHz                                                              
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list           
       configuration: latency=64 maxlatency=255 mingnt=4                         
       resources: memory:c0100000-c017ffff memory:e8000000-ebffffff memory:e4000\
000-e7ffffff memory:e0000000-e1ffffff memory:e2000000-e200ffff

On the other hand, I tried another Dell using the live CD.  That Dell identified the monitor as a NEC 20" (as did the first Dell), and gives the following xrandr output, but (unlike thee first Dell) the display has problems with re-drawing the screen after a window is moved:

> Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 2048 x 2048            
VGA1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 396mm x \
297mm                                                                            
   1600x1200      85.0*+   75.0     70.0     65.0     60.0                       
   1920x1440      75.0     60.0                                                  
   1856x1392      75.0     60.0                                                  
   1792x1344      75.0     60.0                                                  
   1920x1200      84.9     74.9     59.9                                         
   1680x1050      84.9     74.9     60.0                                         
   1400x1050      85.0     74.9     60.0                                         
   1280x1024      85.0     75.0     60.0                                         
   1440x900       84.8     75.0     59.9                                         
   1280x960       85.0     60.0                                                  
   1360x768       60.0                                                           
   1280x800       84.9     74.9     59.8                                         
   1152x864       75.0                                                           
   1280x768       84.8     74.9     59.9                                         
   1024x768       85.0     75.1     75.0     70.1     60.0     43.5              
   832x624        74.6                                                           
   800x600        85.1     72.2     75.0     60.3     56.2                       
   848x480        60.0                                                           
   640x480        85.0     75.0     72.8     72.8     66.7     60.0     59.9     
   720x400        85.0     87.8     70.1                                         
   640x400        85.1                                                           
   640x350        85.1 

Ok, that's all the data I know how to gather right now!

---

### Post by DiagonalArg on 2011-08-27
Ok, I tried connecting the Tyan to the monitor directly, without the KVM.  Same problem appears.  I wonder if I could get a pic of this??  (I'll add it to this post, if I can.)  So we've got something kind of hit or miss.  Some machines work, some don't.

---

### Post by realzippy on 2011-08-27
> **DiagonalArg said:**
> 
If you have more thoughts, I'm all ears!

Sorry,all thoughts I had overnight about this where same as yours:
1.Testing tyan without KVM  => same issue
2.Running liveCD on tyan    => same issue
3.Running other machine with same monitor =>all good,so monitor is not the problem

It seems pretty driver related,eg the nouveau driver worked.
Desperate shot in the dark:
[http://www.x.org/archive/X11R7.5/doc/man/man4/xgi.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/xgi.4.html)
Maybe (as you suggested formerly) creating an xorg.conf is
the last chance,since there seem to be a few driver specific options.
Eg,there is Mode "XGI1600x1200-60" ,which only works with reduced color depth.
Also other kernels might give different results,since xgifb is kernel's XGI framebuffer driver ...

---

### Post by realzippy on 2011-08-27
BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=088a1cbf-5ade-46c2-821f-e0c7753e84d5 ro quiet splash **vt.handoff=7**

What happens when deleting/disabling vt.handoff=7 to the
*"refresh rate chaos on the login screen"*
.....................................................
*vt.handoff=7  causes the kernel to maintain the current contents of video memory on virtual terminal 7, which is a new "transparent" VT type.*

---

### Post by realzippy on 2011-08-27
Also found an [Xorg.0.log]("http://forums.opensuse.org/deutsch-german/hilfe-und-helfen/installation-administration/456281-screen-monitor-einstellung-11-4-a.html#post2310504") running a tyan board with same onboard graphics
on the german suse forum.The guy complains about not to be able to lower resolution to others than 1600x1200, but not mentioning any graphic glitches.
Comparing his log to yours,I see that (besides he runs 2.6.38 64bit):

His:
[109266.434] X.Org ANSI C Emulation: 0.4
[109266.434] X.Org Video Driver: 8.0
[109266.434] X.Org XInput driver : 11.0
[109266.434] X.Org Server Extension : 4.0

Yours:
[ 522.463] X.Org ANSI C Emulation: 0.4
[ 522.463] X.Org Video Driver: 10.0
[ 522.463] X.Org XInput driver : 12.3
[ 522.463] X.Org Server Extension : 5.0

If you srcoll down his log,you see that the fbdev driver takes over
the card setting colour depth to 16bit:

[109266.717] ABI class: X.Org Video Driver, version 8.0
[109266.718] (**) FBDEV(0): claimed PCI slot 17@0:3:0
[109266.718] (II) FBDEV(0): using default device
[109266.718] (WW) Falling back to old probe method for vesa
[109266.718] (II) FBDEV(0): Creating default Display subsection in Screen section
"Default Screen" for depth/fbbpp 16/16
[109266.718] (==) FBDEV(0): Depth 16, (==) framebuffer bpp 16

...on your machine the VESA driver kicks in:
[ 522.508] (II) VESA(0): Creating default Display subsection in Screen section "Default Screen Section" for depth/fbbpp 24/32
[ 522.508] (==) VESA(0): Depth 24, (--) framebuffer bpp 32

.........................................................

Whatever that means....downgrading X.org driver?.......maybe manually modeset colordepth to 16 is worth a try?

---

### Post by DiagonalArg on 2011-08-28
> It seems pretty driver related,eg the nouveau driver worked.

RealZippy - What do you mean by "nouveau" here?

Ok, I didn't get a lot of time today, so the only thing I tried, before reading your posts, was to put in an old PCI video card.  When I did, system>>prefs>>monitors reports the monitor as "unknown", but I do get a slightly better output from xrandr, though the 1600x1200 video is not identified.:

> xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      85.0*    75.0     60.0  
   1280x960       85.0     60.0  
   1152x864       75.0    100.0     85.0     70.0     60.0  
   1024x768       87.0     85.0     75.0     70.0     60.0  
   960x720        75.0     60.0  
   928x696        75.0     60.0  
   896x672        75.0     60.0  
   832x624        75.0  
   800x600        85.0     75.0     72.0     60.0     56.0     70.0     65.0  
   840x525        85.0     75.0     70.0     60.0  
   700x525        85.0     75.0     70.0     60.0  
   640x512        85.0     75.0     60.0  
   720x450        60.0  
   640x480        85.0     75.0     73.0     67.0     60.0  
   720x400        88.0     70.0     85.0  
   680x384        60.0  
   640x400        85.0  
   576x432       100.0     85.0     75.0     70.0     60.0  
   640x350        85.0  
   512x384        87.0     85.0     75.0     70.0     60.0  
   416x312        75.0  
   400x300        85.0     75.0     72.0     60.0     56.0  
   320x240        85.0     75.0     73.0     60.0  
   360x200        85.0  
   320x200        85.0  
   320x175        85.0

Also, for lshw:

> sudo lshw -c video 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 3D Rage Pro 215GP
       vendor: ATI Technologies Inc
       physical id: 7
       bus info: pci@0000:00:07.0
       version: 5c
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=64 mingnt=8
       resources: memory:fc000000-fcffffff ioport:e000(size=256) memory:febff000-febfffff memory:febc0000-febdffff

Long day tomorrow, so I'm not sure if I'll get to trying your suggestion to delete the "vt.handoff=7" before Monday.  If you give me an idea how to do this:

> Whatever that means....downgrading X.org driver?.......maybe manually modeset colordepth to 16 is worth a try?


then I'll try it, too.  (Sorry, don't know much about how to get into the blood and guts of linux, yet.  When looking here for example, [http://www.x.org/archive/X11R7.5/doc/man/man4/xgi.4.html]("http://www.x.org/archive/X11R7.5/doc/man/man4/xgi.4.html"), I'm not clear if there's a way for me to set configuration paramters/options.)

Ok, it's 3AM.  Can't stay up <<all>> night tonight!

Thanks for all your brain (and google!) work.

---

### Post by realzippy on 2011-08-28
> **DiagonalArg said:**
> RealZippy - What do you mean by "nouveau" here?
Meant your test with that dell machine/GeForce4 MX 420 running the free nvidia driver (called "nouveau"):
```
configuration: driver=nouveau
```
> **DiagonalArg said:**
> 
....was to put in an old PCI video card... though the 1600x1200 video is not identified.
For that card xrandr reported screen maximum 1280 x 1024,so no way for
adding 1600x1200...
> **DiagonalArg said:**
> 
 ..to delete the "vt.handoff=7" before Monday.  If you give me an idea how to do this
You had to edit /etc/default/grub
.........................................................................
But,the more I read about linux/xgi driver,the more I get the feeling we are beating a dead horse.
If there wasn't that guy from suse forum,(post #41),and his log file,
I would suggest to give up and search for another graphics card you could plug in.Downgrading to his Xorg version (X.Org X Server 1.9.3) from X.Org X Server 1.10.1 might be impossible or really hard work,so I suggest:

[Download]("http://linux.softpedia.com/progDownload/openSUSE-GNOME-Live-CD-Download-30750.html") the OpenSuse liveCD 11.4 to get exactly his configuration,where 1600x1200 seems to work.
Start it,and if it should be possible to set that configuration,we know it *is* possible.
Think that is the easiest way...

---

### Post by DiagonalArg on 2011-08-30
Ok, I tried the openSUSE live distro.  This is what I get...

The monitor configuration gui tool and xrandr present only a single option:

> Monitor: unknown                                                                 
1600x1200                                                                        
77Hz refresh

> xrandr -q                                                                        
xrandr: Failed to get size of gamma for output default                           
Screen 0: minimum 1600 x 1200, current 1600 x 1200, maximum 1600 x 1200          
default connected 1600x1200+0+0 0mm x 0mm                                        
   1600x1200      77.0*

Since there's no lshw in openSUSE, I looked around and found hwinfo, but wasn't able to identify the driver....

> hwinfo --monitor                                                                 
29: None 00.0: 10000 Monitor                                                     
  [Created at monitor.95]                                                        
  Unique ID: rdCR.Kj_d3dBURP9                                                    
  Hardware Class: monitor                                                        
  Model: "NEC FE2111SB"                                                          
  Vendor: NEC "NEC"                                                              
  Device: eisa 0x61da "NEC FE2111SB"                                             
  Serial ID: "305428883"                                                         
  Resolution: 720x400@70Hz                                                       
  Resolution: 720x400@88Hz                                                       
  Resolution: 640x480@60Hz                                                       
  Resolution: 640x480@67Hz                                                       
  Resolution: 640x480@72Hz                                                       
  Resolution: 640x480@75Hz                                                       
  Resolution: 800x600@56Hz                                                       
  Resolution: 800x600@60Hz                                                       
  Resolution: 800x600@72Hz                                                       
  Resolution: 800x600@75Hz                                                       
  Resolution: 832x624@75Hz                                                       
  Resolution: 1024x768@60Hz                                                      
  Resolution: 1024x768@70Hz                                                      
  Resolution: 1024x768@75Hz                                                      
  Resolution: 1280x1024@75Hz                                                     
  Resolution: 640x480@85Hz                                                       
  Resolution: 800x600@85Hz                                                       
  Resolution: 1024x768@85Hz                                                      
  Resolution: 1152x864@75Hz                                                      
  Resolution: 1600x1200@60Hz                                                     
  Size: 396x297 mm                                                               
  Detailed Timings #0:                                                           
     Resolution: 1600x1200                                                       
     Horizontal: 1600 1664 1856 2160 (+64 +256 +560) +hsync                      
       Vertical: 1200 1201 1204 1250 (+1 +4 +50) +vsync                          
    Frequencies: 229.50 MHz, 106.25 kHz, 85.00 Hz                                
  Driver Info #0:                                                                
    Max. Resolution: 1600x1200                                                   
    Vert. Sync Range: 50-160 Hz                                                  
    Hor. Sync Range: 30-115 kHz                                                  
    Bandwidth: 229 MHz                                                           
  Config Status: cfg=new, avail=yes, need=no, active=unknown

I must admit that the 1600x1200 resolution @77 hz does produce some "blur".  It's readable, but a bit of a strain.  Would that be worse or better at 60hz?  I don't know.

Ok, now I'll go try that grub config option....

---

### Post by realzippy on 2011-08-30
Don't know also.
You could test a modeline you create with
```
cvt 1600 1200 60
```
or any other Vrefresh...
(same procedure as in post #17)

---

### Post by DiagonalArg on 2011-08-30
> BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=088a1cbf-5ade-46c2-821f-e0c7753e84d5 ro quiet splash vt.handoff=7

What happens when deleting/disabling vt.handoff=7 to the
"refresh rate chaos on the login screen"
.................................................. ...
vt.handoff=7 causes the kernel to maintain the current contents of video memory on virtual terminal 7, which is a new "transparent" VT type.

Ok, that doesn't appear to have done anything ...

I had in mind to do just what you suggested, going back to openSUSE and setting the refresh to 60hz.  I'm going back to look at the procedure, now ...

(Boy, I really appreciate your sticking with this.  I feel like I've found a video driver/modeline guru. :)

---

### Post by DiagonalArg on 2011-08-30
Hm.  I'm remembering that the color depth is supposed to be set lower for that 60hz mode (16 bit, I think).  That, I'm not sure how to do.  I'll try it just using the cvt 1600 1200 60, but if there's something else I should do, let me know and I'll go back and do it.  Report in a minute...

---

### Post by realzippy on 2011-08-30
> **DiagonalArg said:**
> Hm.  I'm remembering that the color depth is supposed to be set lower for that 60hz mode (16 bit, I think).  That, I'm not sure how to do.

vga=798 
as boot option
would be 1600x1200 16bit.
Don't know how to set boot options to a suse liveCD...but should be possible.

---

### Post by DiagonalArg on 2011-08-30
Ok, so I tried both 72hz and 60hz under openSUSE. They both appear the same as the 77hz.  They work, but there is that slight blurriness that I mentioned.  

I've learned a hell of a lot, but unless there is something I was supposed to try with the reduced color depth, I am guessing that this is the end of the line!  That I should be trying to find some ancient PCI video card that might be a bit better than the even more ancient one I tried in there yesterday.

Well, no real food to offer, but ... have some popcorn on me!

:popcorn:

(Do they give gold stars on this forum?)

---

### Post by DiagonalArg on 2011-08-30
Ya, there's a way to set boot options on the live openSUSE disk.  I'll go try that, just to make sure we've thoroughly exhausted all possibilities!   (Where do we look up boot options?)

---

### Post by realzippy on 2011-08-30
..just threw in openSuSe live,they made it pretty simple:

just type desired boot option
**vga=798** 
 at "welcome" sceen...


btw,vga=796 would be 8bit

---

### Post by DiagonalArg on 2011-08-30
Ok, I tried vga=798, which complained, but it then popped up with a list of video option values.  It said 1600x1200x16 was "331", so I used that.   (x8 was "330" and x32 was "33E")

Unfortunately, everything looked just the same - it works, but with a tinge of eye-strain-causing blurriness.

Maybe I should just VNC into the Tyan from the Dell?  :P

Ok, well, with a great bow to my guru, I'll say ... Have a good day!  (But in case further spiritual inspiration may strike you, I will continue to monitor this thread.)

---

### Post by realzippy on 2011-08-30
331?
I would understand if it was 286,since those are the vesa modes.
Linux kernel do not accept those,so Linux video mode number is simply the VESA number plus 512..
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

---

### Post by DiagonalArg on 2011-08-30
> **realzippy said:**
> 331?
I would understand if it was 286,since those are the vesa modes.
Linux kernel do not accept those,so Linux video mode number is simply the VESA number plus 512..
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

Ok, I tried again.  The first issue is that I'm putting in vga=798, and after loading the kernel, it's responding (in hex):

> Undefined video mode number: 31e

31E is, as you notice, 798 in hex.  Then:

> Press <enter> to see video modes available, <space> to continue or wait 30 seconds

I press <enter> and get a list of modes that look like the following (I didn't copy them all down)

> Mode: Resolution: Type:
F00   80x25       VGA
F01   .....       VGA
F02   .....       VGA
F03   80x28       VGA
etc

(VGA modes were F00,01,02,03,05 and 07).  Then there were the modes of type "VESA".

> Mode: Resolution: Type:
303   800x600x8    VESA
330   1600x1200x8  VESA
331   1600x1200x16 VESA
...
33E   1600x1200x32 VESA
etc

There were many others listed there.  So, 330 hex is 812 decimal, 331 is 813 and 33E is 826.

So there's something else we/I am not understanding here, I suppose...

---

### Post by DiagonalArg on 2011-08-30
Ok, looking at that Wikipedia page:

>  ... the modes above 1280x1024 are not covered by the standard, and every graphics card manufacturer uses its own codes. This means the modes, in red below, may not apply to your graphics card !

That can be found [here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers").

Does that resolve the issue?

---

### Post by realzippy on 2011-08-30
ok,understand,but I cannot find anything about "331" as a mode for any 
graphics,neither SIS nor XGI...

---

### Post by DiagonalArg on 2011-08-31
> ok,understand,but I cannot find anything about "331" as a mode for any graphics,neither SIS nor XGI...

Well, if you don't know what to make of that, then I *certainly* don't!

So, I picked up a used ATI Radeon 9200 PCI card (128MB) for $20. That thing works, but oh my god, it's so terribly laggy - even at 1600x1200, which is one of it's lower resolutions - and I don't even have anything else running on the PCI bus.  Forget movies altogether - just flipping through a few browser pages is painful, and the mouse freezes up in between.  I guess I've got to live with it, but are PCI video cards always like this??

> sudo lshw -c video
  *-display:0             
       description: VGA compatible controller
       product: RV280 [Radeon 9200]
       vendor: ATI Technologies Inc
       physical id: 7
       bus info: pci@0000:00:07.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64 mingnt=8
       resources: irq:27 memory:f0000000-f7ffffff ioport:e000(size=256) memory:febf0000-febfffff memory:febc0000-febdffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 7.1
       bus info: pci@0000:00:07.1
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 mingnt=8
       resources: memory:e8000000-efffffff memory:febe0000-febeffff


> xrandr -q
Screen 0: minimum 320 x 200, current 1600 x 1200, maximum 4096 x 4096
VGA-0 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 396mm x 297mm
   1600x1200      85.0*+   75.0     70.0     65.0     60.0  
   1920x1440      75.0     60.0  
   1856x1392      75.0     60.0  
   1792x1344      75.0     60.0  
   1920x1200      84.9     74.9     59.9  
   1680x1050      84.9     74.9     60.0  
   1400x1050      85.0     74.9     60.0  
   1280x1024      85.0     75.0     60.0  
   1440x900       84.8     75.0     59.9  
   1280x960       85.0     60.0  
   1360x768       60.0  
   1280x800       84.9     74.9     59.8  
   1152x864       75.0  
   1280x768       84.8     74.9     59.9  
   1024x768       85.0     75.1     75.0     70.1     60.0     43.5  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        85.0     75.0     72.8     72.8     66.7     60.0     59.9  
   720x400        85.0     87.8     70.1  
   640x400        85.1  
   640x350        85.1 

---

### Post by realzippy on 2011-08-31
> **DiagonalArg said:**
> 
So, I picked up a used ATI Radeon 9200 PCI card (128MB) for $20.
OMG,20 $ for such a piece of....
May I ask where you live?
Here (central europe) you could get those for free at the recycling center.Have a nvidia GTX 7950 256Mb pcie,nobody I know wants it as a gift.At ebay's I would get 7 euros...
Sorry,know that this doesn't help you.
> **DiagonalArg said:**
> 
I guess I've got to live with it, but are PCI video cards always like this??
..never used one.Maybe you should look out for a nvidia card.

---

### Post by DiagonalArg on 2011-08-31
OMG!  :lol:

And to add insult to injury, I had to drive 15 miles to go get it!  It's not that I don't have access to good computers, it's just that I use old junk.  There's so much used stuff around here, that I just let it come to me.  This computer, for instance, is my newest (2006), a tyan server with lousy onboard graphics.  (I suppose I'm lucky that there's any.)  But then, when I do need something specific, it's a chore finding it.

(I'm in San Francisco, by the way.  Silicone Valley is always shedding computers, but most are 1U servers which I then have to put in a reasonable enclosure, so as not to feel like there's a runway going through my living room.)

I suppose I could pick up an nVidea, but if it's a PCI throughput problem, then I'm hosed.

(And by the way, your English is better than any central european language that I'll ever speak a word of!  You know the joke that if you speak three languages your trilingual; two languages, bilingual; and if you only speak one language, you're an American?)

---

### Post by DiagonalArg on 2011-09-01
Got it!

Well, replacing the card by an nVidea card did the trick.  It works perfectly.  Not only that, but I then discovered that the Dell whose video was also having trouble, was running off the onboard graphics, as was the Tyan server.  I put in an nVidea AGP card and that also works fine!  There were two other Dells working fine, and both of them already had nVidea AGP cards.

So the moral of the story, as you so eloquently put it with regard to the ATI Radeon card ... "OMG,20 $ for such a piece of...."

I guess I should mark this thread as, in it's own way, solved.

Thanks again, realzippy!

/DA

---

### Post by realzippy on 2011-09-01
Glad you made it finally.
May be better not to ask what you've paid for the ancient nvidia cards..
So,have fun!
Send me a pm if you ever come to europe (hamburg)...we'll have a drink then.

---

