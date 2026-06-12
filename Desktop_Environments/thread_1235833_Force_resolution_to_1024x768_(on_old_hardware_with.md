---
title: "Force resolution to 1024x768 (on old hardware with new Xorg)"
date: 2009-08-09
forum: Desktop Environments
---

### Post by ola on 2009-08-09
Hi, I'm using an old computer (P3 600mhz) with a Nvidia TNT video card and a ViewSonic VG150 TFT screen. The computer ran Win2000 in 1024x768 but in Xubuntu 9.04 I can't get it to above 800x600.

I can't find anything in the default *xorg.conf* to set the resolution so I guess it should be automatically detected.
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

I added some mode lines to *xorg.conf* but can't get it working.
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

My Xorg log file running with default xorg.config. As you can see it can't find any mode lines at 1024x768 that works.
```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Barbazoo 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug  9 22:03:23 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation NV4 [RIVA TNT] rev 4, Mem @ 0xe4000000/16777216, 0xe6000000/16777216, BIOS @ 0x????????/65536
(II) Open ACPI successful (/var/run/acpid.socket)
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
	compiled for 1.6.0, module version = 1.0.0
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
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched nv from file name nv.ids
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.12
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
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
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT,
	GeForce 6200, GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7300 GT,
	GeForce 7600 GT, GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE,
	GeForce 7300 GT, GeForce Go 7700, GeForce Go 7600,
	GeForce Go 7600 GT, Quadro NVS 300M, GeForce Go 7900 SE,
	Quadro FX 550M, Quadro FX 560, GeForce 7900 GTX, GeForce 7900 GT,
	GeForce 7900 GS, GeForce Go 7900 GS, GeForce Go 7900 GTX,
	Quadro FX 2500M, Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500,
	Quadro FX 1500, Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE,
	GeForce 6100, GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX,
	GeForce 8800 GTS, GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600,
	GeForce 8600 GTS, GeForce 8600 GT, GeForce 8600 GT, GeForce 8600 GS,
	GeForce 8400 GS, GeForce 9500M GS, GeForce 8600M GT,
	GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370, Quadro NVS 320M,
	Quadro FX 570M, Quadro FX 1600M, Quadro FX 570, Quadro FX 1700,
	GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS, GeForce 8300 GS,
	GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, GeForce 9400 GT, Quadro FX 360M, GeForce 9300M G,
	Quadro NVS 290, GeForce GTX 280, GeForce GTX 260,
	GeForce 8800 GTS 512, GeForce 8800 GT, GeForce 9800 GX2,
	GeForce 8800 GS, GeForce 8800M GTS, GeForce 8800M GTX,
	GeForce 8800 GS, GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX,
	GeForce 9800 GTK+, GeForce 9800 GT, GeForce GTS 250, Quadro FX 3700,
	Quadro FX 3600M, GeForce 9600 GT, GeForce 9600 GS, GeForce 9800M GTS,
	GeForce 9700M GTS, GeForce 9800M GTS, GeForce 9500 GT,
	GeForce 9600M GT, GeForce 9600M GS, GeForce 9600M GT,
	GeForce 9500M G, GeForce 9300 GS, GeForce 8400 GS, GeForce 9300M GS,
	GeForce 9200M GS, GeForce 9300M GS, Quadro NVS 150M, Quadro NVS 160M
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA RIVA TNT at 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "RIVA TNT"
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE6000000
(--) NV(0): MMIO registers at 0xE4000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(--) NV(0): HW is currently programmed for CRT
(II) NV(0): Using CRT on CRTC 0
(--) NV(0): VideoRAM: 16384 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) NV(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) NV(0): Unable to estimate virtual size
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (vrefresh out of range)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (vrefresh out of range)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (vrefresh out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (vrefresh out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (hsync out of range)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (hsync out of range)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (hsync out of range)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (hsync out of range)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (hsync out of range)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (hsync out of range)
(II) NV(0): Not using default mode "960x540" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (hsync out of range)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (hsync out of range)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(--) NV(0): Virtual size is 800x600 (pitch 800)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"x60.3   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"x56.3   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		20 256x256 slots
		6 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
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
(II) config/hal: Adding input device HID 05f3:0007
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) HID 05f3:0007: always reports core events
(**) HID 05f3:0007: Device: "/dev/input/event6"
(II) HID 05f3:0007: Found keys
(II) HID 05f3:0007: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 05f3:0007" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID 05f3:0007: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID 05f3:0007: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) HID 05f3:0007: xkb_layout: "se"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) AT Translated Set 2 keyboard: xkb_layout: "se"
(II) config/hal: Adding input device HID 05f3:0007
(**) HID 05f3:0007: always reports core events
(**) HID 05f3:0007: Device: "/dev/input/event5"
(II) HID 05f3:0007: Found keys
(II) HID 05f3:0007: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 05f3:0007" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID 05f3:0007: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID 05f3:0007: xkb_model: "pc105"
(**) Option "xkb_layout" "se"
(**) HID 05f3:0007: xkb_layout: "se"
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
(II) config/hal: Adding input device Microsoft Microsoft Wheel Mouse Optical?
(**) Microsoft Microsoft Wheel Mouse Optical?: always reports core events
(**) Microsoft Microsoft Wheel Mouse Optical?: Device: "/dev/input/event4"
(II) Microsoft Microsoft Wheel Mouse Optical?: Found 3 mouse buttons
(II) Microsoft Microsoft Wheel Mouse Optical?: Found x and y relative axes
(II) Microsoft Microsoft Wheel Mouse Optical?: Configuring as mouse
(**) Microsoft Microsoft Wheel Mouse Optical?: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wheel Mouse Optical?: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wheel Mouse Optical?" (type: MOUSE)
(**) Microsoft Microsoft Wheel Mouse Optical?: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Wheel Mouse Optical?: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Wheel Mouse Optical?: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Wheel Mouse Optical?: (accel) set acceleration profile 0

```

Ideas? Thanks in advance!

---

### Post by gjoellee on 2009-08-09
Have you installed the graphics driver for your card?

[B]And another solution...maybe [COLOR="Red"](use it at own risk, I do not know if it is safe)![/COLOR]
[/B]
Change the line
> Modes "1024x768" "800x600" "640x480"

to 
> Modes "1024x768"

---

### Post by ola on 2009-08-10
@gjoellee: Thanks for replying! I'm using the nv driver (included in Xorg) for my card and it says it's supported in the log. I think the problem is that my monitor doesn't report 1024x768 correctly...

I found documentation in [Ubuntu Wiki for how to add undetected resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions"). Here is what I've tried so far.

When I boot my computer and run *xrandr* I get the following:
```

$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  

```
No 1024x768 here :(

I try to find a mode that would give me 1024x768 with *cvt*:
```

$ cvt -v 1024 768 60
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```
The modeline might look a bit strange but I'll try it anyways...

Then I add the mode with *xrandr*:
```

$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```

After I added the mode I run *xrandr* again to see the newly added mode. I can see one mode but it looks a bit strange.
```

$ xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0  
  1024x768_60.00 (0x13e)   63.5MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz


```

Then I try to change to my newly added resolution:
```

$ xrandr --output default --mode 1024x768_60.00 --rate 60
xrandr: cannot find mode 1024x768_60.00
$ xrandr --output default --mode 1024x768 --rate 60
xrandr: cannot find mode 1024x768

```

Any ideas?

---

### Post by ola on 2009-08-10
Just found out that I must add the mode I added with *xrandr --newmode ..* as a valid mode as well.

That's done with:

```

$ xrandr --addmode default 1024x768_60.00

```

If I try to change to the new mode now I get another error message:
```

$ xrandr --output default --mode 1024x768_60.00
xrandr: Configure crtc 0 failed

```

Not sure why but I guess that's something with my refresh rates. Will try more!

---

### Post by ola on 2009-08-10
I finally got it working by adding *HorizSync* & *VertRefresh* to */etc/X11/xorlg.conf*. (The values are for a *ViewSonic VG150 TFT* monitor so if anyone use another monitor find the values for that monitor instead.)

I make all rows I have added from the original */etc/X11/xorlg.conf* file bold.

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	**HorizSync       30.0 - 62.0**
	**VertRefresh     50.0 - 70.0**
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	**DefaultDepth	24**
	**SubSection "Display"**
		**Depth	24**
		**Modes 	"1024x768" "800x600"**
	**EndSubSection**
EndSection

```

---

### Post by gjoellee on 2009-08-11
I just have to ask...have you installed the driver for your card?
Was the screen resolution at 1024x786 when you installed Xubuntu from USB or live CD?

If it was you may consider trying xfix. It will reset your Xorg settings to the default, and make Xorg run like it did when you ran the live CD. You can read more about xfix here: [http://kshoster.net/index.php?q=tutorials/ubuntu/xfix](http://kshoster.net/index.php?q=tutorials/ubuntu/xfix)

---

### Post by gunther123 on 2009-10-02
For posterity...  I ran into almost exactly the same problem.  I am running Ubuntu 9.04 using an nvidia 5500FX and a NEC MultiSync 3V CRT.  Ubuntu GDM would not go higher than 800x600.

I did find that Ubuntu is unable to detect the CRT and lists it as unknown.  If I connected a 15" Sony LCD display, Ubuntu correctly detects the monitor and allows me to increase res. to 1024x768.  If I hot swapped my video to the NEC 3V CRT, the display was out of synch.  I swapped back to the sony LCD, opened the display preferences and manually decreased the refresh rate to 60 Hz.  Then I swapped back to the 3V CRT and the display was fine.  It was running at 1024x768 @ 60 Hz and everything was good.  However, if I reboot the system, the resolution reverts to 800x600 max.

Following the steps here, I did the following:

1. Edit /etc/X11/xorg.conf file
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	**HorizSync       30.0 - 62.0**
	**VertRefresh     50.0 - 70.0**
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	**DefaultDepth	24**
	**SubSection "Display"**
		**Depth	24**
		**Modes 	"1024x768" "800x600"**
	**EndSubSection**
EndSection
NOTE: I changed my H. Sync and V. Refresh values for the NEC 3V 
HorizSync = 31.0 - 50.0
VertRefresh = 55.0 - 90.0

HINT: I ended up making a copy of xorg.conf in my home folder because I was having some other problems where I had to use the recovery console and repair the xconf which would overwrite my changes.  So keeping the copy in my home folder allowed me to just re-copy to /etc/X11/xorg.conf whenever that happened.


2. Found modeline for 1024x768
Used "X/Config/Resolution" ([https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)) to find this command:
[FONT=Courier New]$cvt 1024 768[/FONT]


3.
$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

4. 
xrandr --addmode default 1024x768_60.00

Now, after all this, I was getting the same "xrandr: Configure crtc 0 failed" error that ola was getting.  He seemed to resolve the problem but based on the information he posted, I didn't see the solution.

Here is what I did next:

5. Stop the GDM
[FONT=Courier New]$ sudo /etc/init.d/gdm stop
[/FONT]
I issued this commend from within the GDM so it promptly booted me out to a message about reloading the logging deamon or something like that.

6. Enter the terminal
[FONT=Courier New]<ctrl>+<alt>+<F1>
[/FONT]
I found that in here "xrandr" would do nothing.  I guess it only works from within the GDM or when the GDM is running.


7. Start the GDM
[FONT=Courier New]$ sudo /etc/init.d/gdm start
[/FONT]
When the GDM starts back up, it was in 1024x768.  Additionally, xrandr and the Display preferences showed 15 or so resolutions, where before I only had a few.  Additionally, I found that after rebooting, the resolution remained set.

Just to make sure I had all the steps down, I formatted and re-installed Ubuntu from scratch and I was able to repeat all the steps as listed here.

I hope this might help someone out there... or maybe just me if I run into it again.  ;-)

---

### Post by halitech on 2009-10-21
thanks for this, allowed me to get 1024x768 on an old TNT2 model 64 with 32meg of ram :) looks much nicer on a 19inch monitor then 800x600 :D

---

