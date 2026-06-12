---
title: "Can't make multiple displays (two screens) work"
date: 2010-02-06
forum: Desktop Environments
---

### Post by LukeKendall on 2010-02-06
I used to use nvidia and Twinview to drive an LCD and CRT monitor as one big area.  I've changed over to using the nv driver, and I gather that xinerama is deprecated now in favour of xrandr.  But I can't get xrandr to even report anything about my two displays, and can't get any picture on the CRT.  This is despite both being fully detected by X (according to the log file).

I've just changed over from using the nvidia driver to the nv driver.  I did this because I discovered that the frequent system crashes while watching video was caused by the nvidia driver, partly because my card is a GeForce FX 5200, not supported by the current nvidia driver which contains bug fixes for the problem.  So I've used Synaptic to remove all the nvidia drivers and add-ons, and installed nv and the libgl1-mesa-dri and libgl1-mesa-glx drivers.

I moved my old xorg.conf file aside and on a second X display ran
X :1 -configure
to generate a clean new xorg.conf and started from there.  But so far, no joy.

I'm doing all these experiments by modifying xorg.conf, and then on a second console running up X on display :1 to try it out.

Another odd thing:  xrandr doesn't report any "outputs" (since I'm using the nv driver, I'd expect to see DVI0 and VGA1), instead it just reports this:

```

# xrandr
Screen 0: minimum 640 x 200, current 2560 x 1024, maximum 2560 x 1024
default connected 2560x1024+0+0 0mm x 0mm
   2560x1024      61.0* 
   2048x768       61.0  
   1600x600       61.0  
   1280x480       60.0  
   1280x400        0.0  
   640x400         0.0  
   640x240         0.0  
   640x200         0.0  

```

From [HowToRandR12]("http://wiki.debian.org/XStrikeForce/HowToRandR12")
> 
For the internal laptop panel, external VGA, external DVI and TV, the drivers currently use:

    * the Intel driver uses LVDS, VGA, TMDS-1 (TMDS-2, ...), TV
    * the ATI driver uses LVDS, VGA-0 (VGA-1, ...), DVI-0 (DVI-1, ...), S-video
    * the RadeonHD driver uses PANEL, VGA_1 (VGA_2, ...), DVI-I_1/digital or DVI-I_1/analog (DVI-I_2/digital or DVI-I_1/analog, ...), TV_7PIN_DIN
    * the NV driver uses LVDS, VGA0 (VGA1, ...), DVI0 (DVI1, ...), ???
    * the MGA driver uses ???, VGA (or VGA1, VGA2, ...), DVI (or DVI1, DVI2, ...), ???
    * the Nouveau driver uses ???, Analog-0 (Analog-1, ...), Digital-0 (Digital-1, ...), ??? 


Yet X seems to detect both monitors just fine:
```

(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: IBM  Model: 1a4f  Serial#: 16843009
(II) NV(0): Year: 2004  Week: 33
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
...
...
(II) NV(0): Probing for EDID on I2C bus B...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: BNQ  Model: 76c3  Serial#: 3302
(II) NV(0): Year: 2006  Week: 11
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
...
...

```

If I run gnome-display-properties, it just reports a single screen called unknown, of size 2560x1024.  Any suggestions?

I'll attach my xorg.con and xorg.1.log files.
Er, no I won't, the upload said "invalid file" for each of them, despite me making sure they were readable:

```

drwxr-xr-x 16 root root  4096 2010-02-07 13:18 /etc/X11/
drwxr-xr-x 21 root root 12288 2010-02-07 13:21 /var/log/

```

I'll put the xorg.conf and log files in here directly, sorry about this:
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	# Maybe try adding:
	#Screen      1  RightOf "Screen0"
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
	Load  "extmod"
	Load  "record"
	#Load  "vnc"
	Load  "dri"
	Load  "dri2"
	Load  "glx"
	Load  "dbe"
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
    Identifier     "Benq"
    HorizSync       28.0 - 96.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
	#DisplaySize	  410   300	# mm
	Identifier   "IBM"
	VendorName   "IBM"
	ModelName    "IBM C220P CRT"
	HorizSync    30.0 - 130.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
	Option      "RightOf" "Benq"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "UseFBDev"           	# [<bool>]
        #Option     "Rotate"             	# [<str>]
        #Option     "VideoKey"           	# <i>
        #Option     "FlatPanel"          	# [<bool>]
        #Option     "FPDither"           	# [<bool>]
        #Option     "CrtcNumber"         	# <i>
        #Option     "FPScale"            	# [<bool>]
        #Option     "FPTweak"            	# <i>
        #Option     "DualHead"           	# [<bool>]
        Option     "DualHead" "true"
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV34 [GeForce FX 5200]"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Benq"
	DefaultDepth    24
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
	Device     "Card0"
	Monitor    "IBM"
	DefaultDepth    24
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

```

Xorg.1.log
```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux potter 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686
Kernel command line: root=/dev/md1 quiet splash 
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Feb  7 13:19:09 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Benq"
(**) |   |-->Device "Card0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(**) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Mouse0
(WW) Disabling Keyboard0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:0322:1458:3103 nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xe0000000/16777216, 0xd8000000/134217728, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.1.14
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) NV: driver for NVIDIA chipsets:  RIVA 128,  RIVA TNT,  RIVA TNT2,
	 RIVA TNT2 Ultra,  Unknown TNT2,  Vanta,  RIVA TNT2 Model 64,
	 GeForce 6800 Ultra,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XE,  GeForce 6800 XT,  GeForce 6800 GT,
	 GeForce 6800 GT,  GeForce 6800 GS,  GeForce 6800 XT,
	 Quadro FX 4000,  GeForce 7800 GTX,  GeForce 7800 GTX,
	 GeForce 7800 GT,  GeForce 7800 GS,  GeForce 7800 SLI,
	 GeForce Go 7800,  GeForce Go 7800 GTX,  Quadro FX 4500,
	 Aladdin TNT2,  GeForce 6800 GS,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 XT,  GeForce Go 6800,  GeForce Go 6800 Ultra,
	 Quadro FX Go1400,  Quadro FX 3450/4000 SDI,  Quadro FX 1400,
	 GeForce 256,  GeForce DDR,  Quadro,  GeForce2 MX/MX 400,
	 GeForce2 MX 100/200,  GeForce2 Go,  Quadro2 MXR/EX/Go,
	 GeForce 6600 GT,  GeForce 6600,  GeForce 6600 LE,  GeForce 6600 VE,
	 GeForce Go 6600,  GeForce 6610 XL,  GeForce Go 6600 TE/6200 TE,
	 GeForce 6700 XL,  GeForce Go 6600,  GeForce Go 6600 GT,
	 Quadro NVS 440,  Quadro FX 550,  Quadro FX 550,  Quadro FX 540,
	 GeForce 6200,  GeForce2 GTS,  GeForce2 Ti,  GeForce2 Ultra,
	 Quadro2 Pro,  GeForce 6500,  GeForce 6200 TurboCache(TM),
	 GeForce 6200SE TurboCache(TM),  GeForce 6200 LE,  GeForce Go 6200,
	 Quadro NVS 285,  GeForce Go 6400,  GeForce Go 6200,
	 GeForce Go 6400,  GeForce 6250,  GeForce 7100 GS,  GeForce4 MX 460,
	 GeForce4 MX 440,  GeForce4 MX 420,  GeForce4 MX 440-SE,
	 GeForce4 440 Go,  GeForce4 420 Go,  GeForce4 420 Go 32M,
	 GeForce4 460 Go,  Quadro4 550 XGL,  GeForce4 440 Go 64M,
	 Quadro NVS,  Quadro4 500 GoGL,  GeForce4 410 Go 16M,
	 GeForce4 MX 440 with AGP8X,  GeForce4 MX 440SE with AGP8X,
	 GeForce4 MX 420 with AGP8X,  GeForce4 MX 4000,  GeForce4 448 Go,
	 GeForce4 488 Go,  Quadro4 580 XGL,  Quadro4 NVS 280 SD,
	 Quadro4 380 XGL,  Quadro NVS 50 PCI,  GeForce4 448 Go,
	 GeForce 8800 GTX,  GeForce 8800 GTS,  GeForce 8800 Ultra,
	 Quadro FX 5600,  Quadro FX 4600,  GeForce2 Integrated GPU,
	 GeForce 7350 LE,  GeForce 7300 LE,  GeForce 7300 SE,
	 GeForce Go 7200,  GeForce Go 7300,  GeForce Go 7400,
	 GeForce Go 7400 GS,  Quadro NVS 110M,  Quadro NVS 120M,
	 Quadro FX 350M,  GeForce 7500 LE,  Quadro FX 350,  GeForce 7300 GS,
	 GeForce4 MX Integrated GPU,  GeForce3,  GeForce3 Ti 200,
	 GeForce3 Ti 500,  Quadro DCC,  GeForce 6800,  GeForce 6800 LE,
	 GeForce 6800 GT,  GeForce 6800 XT,  GeForce 6200,
	 GeForce 6200 A-LE,  GeForce 6150,  GeForce 6150 LE,  GeForce 6100,
	 GeForce Go 6150,  Quadro NVS 210S / NVIDIA GeForce 6150LE,
	 GeForce Go 6100,  GeForce4 Ti 4600,  GeForce4 Ti 4400,
	 GeForce4 Ti 4200,  Quadro4 900 XGL,  Quadro4 750 XGL,
	 Quadro4 700 XGL,  GeForce4 Ti 4800,  GeForce4 Ti 4200 with AGP8X,
	 GeForce4 Ti 4800 SE,  GeForce4 4200 Go,  Quadro4 980 XGL,
	 Quadro4 780 XGL,  Quadro4 700 GoGL,  GeForce 7900 GTX,
	 GeForce 7900 GT,  GeForce 7900 GS,  GeForce 7950 GX2,
	 GeForce 7950 GX2,  GeForce 7950 GT},  GeForce Go 7950 GTX,
	 GeForce Go 7900 GS,  GeForce Go 7900 GTX,  Quadro FX 2500M,
	 Quadro FX 1500M,  Quadro FX 5500,  Quadro FX 3500,  Quadro FX 1500,
	 Quadro FX 4500 X2,  GeForce FX 5800 Ultra,  GeForce FX 5800,
	 Quadro FX 2000,  Quadro FX 1000,  GeForce FX 5600 Ultra,
	 GeForce FX 5600,  GeForce FX 560T,  GeForce FX Go5600,
	 GeForce FX Go5650,  Quadro FX Go700,  GeForce FX 5200,
	 GeForce FX 5200 Ultra,  GeForce FX 5200,  GeForce FX 5200LE,
	 GeForce FX Go5200,  GeForce FX Go5250,  GeForce FX 5500,
	 GeForce FX 5100,  GeForce FX Go5200 32M/64M,  Quadro NVS 55/280 PCI,
	 Quadro FX 500/600 PCI,  GeForce FX Go53xx Series,
	 GeForce FX Go5100,  GeForce FX 5900 Ultra,  GeForce FX 5900,
	 GeForce FX 590T,  GeForce FX 5950 Ultra,  GeForce FX 5900ZT,
	 Quadro FX 3000,  Quadro FX 700,  GeForce FX 5700 Ultra,
	 GeForce FX 5700,  GeForce FX 5700LE,  GeForce FX 5700VE,
	 GeForce FX Go5700,  GeForce FX Go5700,  Quadro FX Go1000,
	 Quadro FX 1100,  GeForce 7650 GS,  GeForce 7600 GT,
	 GeForce 7600 GS,  GeForce 7300 GT,  GeForce 7600 LE,
	 GeForce 7300 GT,  GeForce Go 7700,  GeForce Go 7600,
	 GeForce Go 7600 GT},  Quadro NVS 300M,  GeForce Go 7900 SE,
	 Quadro FX 550M,  Quadro FX 560,  GeForce 6150SE,
	 GeForce 6100 nForce 405,  GeForce 6100 nForce 400,
	 GeForce 6100 nForce 420,  GeForce 8600 GTS,  GeForce 8600 GT,
	 GeForce 8600 GT,  GeForce 8600 GS,  GeForce 8400 GS,
	 GeForce 9500M GS,  GeForce 8600M GT,  GeForce 9650M GS,
	 GeForce 8700M GT,  Quadro FX 370,  Quadro NVS 320M,  Quadro FX 570M,
	 Quadro FX 1600M,  Quadro FX 570,  Quadro FX 1700,  GeForce 8400 SE,
	 GeForce 8500 GT,  GeForce 8400 GS,  GeForce 8300 GS,
	 GeForce 8400 GS,  GeForce 8600M GS,  GeForce 8400M GT,
	 GeForce 8400M GS,  GeForce 8400M G,  Quadro NVS 140M,
	 Quadro NVS 130M,  Quadro NVS 135M,  GeForce 9400 GT,
	 Quadro FX 360M,  GeForce 9300M G,  Quadro NVS 290,  GeForce GTX 295,
	 GeForce GTX 280,  GeForce GTX 260,  GeForce GTX 285,  GeForce 7050,
	 GeForce 7025,  Quadro CX,  Quadro FX 5800,  Quadro FX 4800,
	 Quadro FX 3800,  GeForce 8800 GTS 512,  GeForce 9800 GT,
	 GeForce 8800 GT,  GeForce 9800 GX2,  GeForce 9800 GT,
	 GeForce 8800 GS,  GeForce 9800M GTX,  GeForce 8800M GTS,
	 GeForce 9800M GT,  GeForce 8800M GTX,  GeForce 8800 GS,
	 GeForce 9600 GSO,  GeForce 8800 GT,  GeForce 9800 GTX,
	 GeForce 9800 GTX+,  GeForce 9800 GT,  GeForce GTS 250,
	 GeForce 9800M GTX,  Quadro FX 3700,  Quadro FX 3600M,
	 Quadro FX 3700M,  GeForce 9600 GT,  GeForce 9600 GS,
	 GeForce 9600 GSO 512,  GeForce GT 130,  GeForce GT 140,
	 GeForce 9800M GTS,  GeForce 9700M GTS,  GeForce 9800M GS,
	 GeForce 9800M GTS,  Quadro FX 1800,  Quadro FX 2700M,
	 GeForce 9500 GT,  GeForce 9400 GT,  GeForce 9500 GT,
	 GeForce GT 120,  GeForce 9600M GT,  GeForce 9600M GS,
	 GeForce 9600M GT,  GeForce 9700M GT,  GeForce 9500M G,
	 GeForce 9650M GT,  GeForce 9500 GT,  Quadro FX 380,  Quadro FX 580,
	 Quadro FX 770M,  GeForce 9300 GE,  GeForce 9300 GS,
	 GeForce 8400 GS,  GeForce 9300M GS,  GeForce G100,
	 GeForce 9200M GS,  GeForce 9300M GS,  Quadro NVS 150M,
	 Quadro NVS 160M,  Quadro NVS 420,  Quadro FX 370 LP,
	 Quadro NVS 450,  Quadro NVS 295
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA  GeForce FX 5200 at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: " GeForce FX 5200"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(**) NV(0): Option "DualHead" "true"
(==) NV(0): Using HW cursor
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) NV(0): initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(II) NV(0): VESA BIOS detected
(II) NV(0): VESA VBE Version 3.0
(II) NV(0): VESA VBE Total Mem: 131072 kB
(II) NV(0): VESA VBE OEM: NVIDIA
(II) NV(0): VESA VBE OEM Software Rev: 4.52
(II) NV(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) NV(0): VESA VBE OEM Product: NV34 Board - p162-1n 
(II) NV(0): VESA VBE OEM Product Rev: Chip Rev   
(**) NV(0): Using VBE dual-head mode.
(II) NV(0): Using software cursor.
(--) NV(0): Linear framebuffer at 0xD8000000
(--) NV(0): MMIO registers at 0xE0000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: IBM  Model: 1a4f  Serial#: 16843009
(II) NV(0): Year: 2004  Week: 33
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreen
(II) NV(0): Max Image Size [cm]: horiz.: 41  vert.: 30
(II) NV(0): Gamma: 2.72
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): GTF timings supported
(II) NV(0): redX: 0.627 redY: 0.341   greenX: 0.292 greenY: 0.605
(II) NV(0): blueX: 0.149 blueY: 0.072   whiteX: 0.283 whiteY: 0.297
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1920  vsize 1440  refresh: 85  vid: 22993
(II) NV(0): #1: hsize: 1792  vsize 1344  refresh: 85  vid: 22977
(II) NV(0): #2: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) NV(0): #3: hsize: 2048  vsize 1536  refresh: 75  vid: 20449
(II) NV(0): #4: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): #5: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #6: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) NV(0): #7: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 229.5 MHz   Image Size:  392 x 294 mm
(II) NV(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
(II) NV(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
(II) NV(0): Serial No: 24-CD058
(II) NV(0): Monitor name: IBM C220P CRT
(II) NV(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 130 kHz, PixClock max 370 MHz
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff00244d4f1a01010101
(II) NV(0): 	210e01036e291eaceb9c68a0574a9b26
(II) NV(0): 	12484ca44300d159c1598199e14f6159
(II) NV(0): 	4559a94f3159a659403062b0324040c0
(II) NV(0): 	130088261100001e000000ff0032342d
(II) NV(0): 	43443035380a20202020000000fc0049
(II) NV(0): 	424d20433232305020435254000000fd
(II) NV(0): 	0032a01e8225000a2020202020200009
(II) NV(0): Probing for EDID on I2C bus B...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: BNQ  Model: 76c3  Serial#: 3302
(II) NV(0): Year: 2006  Week: 11
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.640 redY: 0.332   greenX: 0.288 greenY: 0.601
(II) NV(0): blueX: 0.146 blueY: 0.065   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) NV(0): #1: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #4: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
(II) NV(0): #5: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 119.0 MHz   Image Size:  433 x 271 mm
(II) NV(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) NV(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) NV(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 84 kHz, PixClock max 170 MHz
(II) NV(0): Monitor name: BenQ FP202W
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0009d1c376e60c0000
(II) NV(0): 	0b100103802b1b78eecfb5a355499925
(II) NV(0): 	105054a56f80454f614f81408180818f
(II) NV(0): 	714fb30001017c2e90a0601a1e403020
(II) NV(0): 	3600b10f1100001ad50980a0205e6310
(II) NV(0): 	10605208782d1100001a000000fd0038
(II) NV(0): 	4c1e5411000a202020202020000000fc
(II) NV(0): 	0042656e51204650323032570a2000b9
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1680 x 1050
(II) NV(0): NOTE: This driver cannot reconfigure the BIOS-programmed size.
(II) NV(0): These dimensions will be used as the panel size for mode validation.
(II) NV(0): EDID vendor "IBM", prod id 6735
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1600x1200"x0.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (106.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1920x1440"x85.0  341.35  1920 2072 2288 2656  1440 1441 1444 1512 -hsync +vsync (128.5 kHz)
(II) NV(0): Modeline "1792x1344"x85.0  295.52  1792 1928 2128 2464  1344 1345 1348 1411 -hsync +vsync (119.9 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
(II) NV(0): Modeline "2048x1536"x75.0  340.48  2048 2216 2440 2832  1536 1537 1540 1603 -hsync +vsync (120.2 kHz)
(II) NV(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NV(0): Modeline "1600x1200"x0.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
(II) NV(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NV(0): Panel is TMDS
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 11b (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 147 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 1400
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 1400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 148 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc000b373
	BytesPerScanline: 2800
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd8000000
	LinBytesPerScanLine: 2800
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
(II) NV(0): Benq: Using hsync range of 28.00-96.00 kHz
(II) NV(0): Benq: Using vrefresh range of 43.00-60.00 Hz
(II) NV(0): Benq: Using maximum pixel clock of 370.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 1.3667 is 2048x1536
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(WW) NV(0): Shrinking virtual size estimate from 2048x1536 to 1280x1024
(II) NV(0): Attempting to use 60Hz refresh for mode "1280x1024" (11b)
(II) NV(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) NV(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) NV(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(--) NV(0): Virtual size is 2560x1024 (pitch 2560)
(**) NV(0): *Built-in mode "1280x1024": 0.0 MHz, 63981.5 kHz, 60.5 Hz
(II) NV(0): Modeline "1280x1024"x60.5    0.00  2560 0 0 0  1024 0 0 0 (63981.5 kHz)
(**) NV(0): *Built-in mode "1024x768": 0.0 MHz, 48363.6 kHz, 60.5 Hz
(II) NV(0): Modeline "1024x768"x60.5    0.00  2048 0 0 0  768 0 0 0 (48363.6 kHz)
(**) NV(0): *Built-in mode "800x600": 0.0 MHz, 37879.3 kHz, 60.8 Hz
(II) NV(0): Modeline "800x600"x60.8    0.00  1600 0 0 0  600 0 0 0 (37879.3 kHz)
(**) NV(0): *Built-in mode "640x480": 0.0 MHz, 31469.2 kHz, 60.4 Hz
(II) NV(0): Modeline "640x480"x60.4    0.00  1280 0 0 0  480 0 0 0 (31469.2 kHz)
(**) NV(0): *Built-in mode "640x400"
(**) NV(0): *Built-in mode "320x400"
(**) NV(0): *Built-in mode "320x240"
(**) NV(0): *Built-in mode "320x200"
(++) NV(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device bttv IR (card=104)
(**) bttv IR (card=104): always reports core events
(**) bttv IR (card=104): Device: "/dev/input/event6"
(II) bttv IR (card=104): Found keys
(II) bttv IR (card=104): Configuring as keyboard
(II) XINPUT: Adding extended input device "bttv IR (card=104)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device cx88 IR (digitalnow DNTV Live!
(**) cx88 IR (digitalnow DNTV Live!: always reports core events
(**) cx88 IR (digitalnow DNTV Live!: Device: "/dev/input/event7"
(II) cx88 IR (digitalnow DNTV Live!: Found keys
(II) cx88 IR (digitalnow DNTV Live!: Configuring as keyboard
(II) XINPUT: Adding extended input device "cx88 IR (digitalnow DNTV Live!" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) config/hal: Adding input device Genius NetScroll + Traveler
(**) Genius NetScroll + Traveler: always reports core events
(**) Genius NetScroll + Traveler: Device: "/dev/input/event4"
(II) Genius NetScroll + Traveler: Found 3 mouse buttons
(II) Genius NetScroll + Traveler: Found x and y relative axes
(II) Genius NetScroll + Traveler: Found scroll wheel(s)
(II) Genius NetScroll + Traveler: Configuring as mouse
(**) Genius NetScroll + Traveler: YAxisMapping: buttons 4 and 5
(**) Genius NetScroll + Traveler: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Genius NetScroll + Traveler" (type: MOUSE)
(**) Genius NetScroll + Traveler: (accel) keeping acceleration scheme 1
(**) Genius NetScroll + Traveler: (accel) filter chain progression: 2.00
(**) Genius NetScroll + Traveler: (accel) filter stage 0: 20.00 ms
(**) Genius NetScroll + Traveler: (accel) set acceleration profile 0
(II) Genius NetScroll + Traveler: initialized for relative axes.

```

One thing I haven't tried is killing my X session on display :0 (it's just running the LCD and can't see the CRT) and trying that directly.  But that shouldn't matter, surely?

---

### Post by LukeKendall on 2010-02-07
Some more googling (looking for "default connected" and xrandr) lead me to reports that the nv driver doesn't fully support randr.  That xrandr doesn't report a useful error message when it's talking to a driver that doesn't allow it to work properly sounds like a bug to me!

Anyway, there were also hints that the newer open source driver for nvidia cards, called "nouveau", has better support for randr.  So I installed that, changed the driver from nv to nouveau in xorg.conf, and ran up my 2nd display, and presto, a mirrored display, and finally I'm also seeing the sort of output that xrandr is supposed to provide.  For nouveau, the outputs for me are called DVD-D-0 and VGA-0.

Oops, it is beta.  After flipping back to display :1 to continue experiments, the nouveau-driven X session crashed, left a message on the console about possible strangeness, and when I restarted X on :1 the screen blanked to grey on both monitors, the mouse pointer(s) appeared, and then the system locked and I had to do a hard reset.

Anyway, after the reboot, I ran up gnome-display-properties, turned off mirroring, and configured both displays with no problems.

So it looks like the problem is solved by the Beta nouveau driver.

Now I just need to find out how to tell gnome to use the left monitor, the LCD, as the primary display for the panel and dock, and see how stable the nouveau driver is...

---

### Post by LukeKendall on 2010-02-07
Hmm, another crash, this time when playing with gnome-display-properties.  (The LCD frequency was set to 59.9Hz, which seemed strange, so I selected 60Hz from the menu, clicked Apply, the screen blanked, then I got a kernel oops.

---

### Post by LukeKendall on 2010-02-07
Well, holding the Alt key down and clicking on the panel allows me to drag it to the other monitor.  Ditto for the dock.

---

### Post by Mariane on 2011-06-04
How did you install this nouveau driver? I tried and it starts with packages but then you have to run ./autogen.sh, and sort that out, and then you have to run make, and when that failed I gave up... 

Mariane

---

### Post by bcschmerker on 2011-06-06
Thanks for a heads up on a problem I am anticipating, concerning the rebuild of an [eMachines®/Acer® EL1210-09](http://www.emachines.com/) (factory-equipped with an Advance Micro Devices® Athlon 64® LE-1620, Socket AM2) as a 64-bit Lucid box.  The stock planar of my system-in-rebuild packs an all-nVIDIA® chipset: MCP78S integrated system support and a single GeForce 8200 driving one analog VGA and one HDMI ports.  RAM is 2 GB x 2; I substituted a 500GB [Western Digital® Scorpio Black®](http://www.wdc.com/) for the down 320GB [Hitachi® stock hard drive](http://www.hitachigst.com/).

I am currently using a 26" RCA® fluorescent-backlit LCD television as an interim Primary Display (I really need a proper computer display unit for HDMI) and anticipate an Optima® VGA-format projector limited to 1024x768 as the Secondary Display; what I do *not* know as of 6 June 2011 is whether the single GeForce 8200 can handle a slide-show display from Sun® OpenOffice.org Impress, or I be forced to add a low-profile PCI-Express x8 VDA using a GeForce 8400 GPU (for driver compatibility) to run the Secondary Display.

---

