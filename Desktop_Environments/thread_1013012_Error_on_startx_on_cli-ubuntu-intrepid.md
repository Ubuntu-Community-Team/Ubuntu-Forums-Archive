---
title: "Error on startx on cli-ubuntu-intrepid"
date: 2008-12-16
forum: Desktop Environments
---

### Post by lardandweed on 2008-12-16
[SIZE=2]I'm trying to setup openbox on a cli install of intrepid, but i'm running into errors trying to start the Xserver.

It seems i can sort of get X to start, as I get the X-cursor thingy with a blank background. However, i do not get any response from my mouse or keyboard. I am able to switch virtual consoles with ALT-F(*) however. Switching back to tty1 reveals that i have an error:
(EE) config/hal: couldn't initialise context: (null) ((null))

this is what my var/log/Xorg.0.log looks like
[/SIZE][SIZE=2]```
[/SIZE]    [SIZE=2][SIZE=2]X.Org X Serv[/SIZE]er 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux Fluff 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
      Before reporting problems, check http://wiki.x.org
      to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
      (++) from command line, (!!) notice, (II) informational,
      (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 17 01:36:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
      Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
      Entry deleted from font path.
(==) FontPath set to:
      /usr/share/fonts/X11/misc,
      /usr/share/fonts/X11/100dpi/:unscaled,
      /usr/share/fonts/X11/75dpi/:unscaled,
      /usr/share/fonts/X11/Type1,
      /usr/share/fonts/X11/100dpi,
      /usr/share/fonts/X11/75dpi
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
      If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
      X.Org ANSI C Emulation: 0.4
      X.Org Video Driver: 4.1
      X.Org XInput driver : 2.1
      X.Org Server Extension : 1.1
      X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G71 [GeForce 7900 GTX] rev 161, Mem @ 0xf5000000/0, 0xc0000000/0, 0xf4000000/0, I/O @ 0x00008c00/0, BIOS @ 0x????????/131072
(II) System resource ranges:
      [0] -1      0     0xffffffff - 0xffffffff (0x1) MX[B]
      [1] -1      0     0x000f0000 - 0x000fffff (0x10000) MX[B]
      [2] -1      0     0x000c0000 - 0x000effff (0x30000) MX[B]
      [3] -1      0     0x00000000 - 0x0009ffff (0xa0000) MX[B]
      [4] -1      0     0x0000ffff - 0x0000ffff (0x1) IX[B]
      [5] -1      0     0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 1.0.0
      Module class: X.Org Server Extension
      ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 1.0.0
      Module class: X.Org Server Extension
      ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 1.0.0
      ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
      compiled for 1.5.2, module version = 2.1.0
      Module class: X.Org Font Renderer
      ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 1.13.0
      Module class: X.Org Server Extension
      ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 1.0.0
      ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched nv from file name nv.ids
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
      compiled for 1.5.0, module version = 2.1.10
      Module class: X.Org Video Driver
      ABI class: X.Org Video Driver, version 4.1
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
      GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
      GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
      GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
      GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
      GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
      GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
      GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
      GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
      GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
      GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
      Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
      GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
      GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
      Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
      Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
      GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
      GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
      GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
      GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
      Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
      Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
      GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
      GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
      Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
      GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
      GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
      GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
      GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
      Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
      GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
      GeForce 9200M GS, GeForce 9300M GS
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA GeForce 7900 GTX at 01@00:00:0
(II) resource ranges after probing:
      [0] -1      0     0xffffffff - 0xffffffff (0x1) MX[B]
      [1] -1      0     0x000f0000 - 0x000fffff (0x10000) MX[B]
      [2] -1      0     0x000c0000 - 0x000effff (0x30000) MX[B]
      [3] -1      0     0x00000000 - 0x0009ffff (0xa0000) MX[B]
      [4] -1      0     0x0000ffff - 0x0000ffff (0x1) IX[B]
      [5] -1      0     0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 1.0.0
      ABI class: X.Org Video Driver, version 4.1
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 7900 GTX"
(II) NV(0): Creating default Display subsection in Screen section
      "Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 0.1.0
      ABI class: X.Org Video Driver, version 4.1
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xC0000000
(--) NV(0): MMIO registers at 0xF5000000
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
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: SAM  Model: 218  Serial#: 1296380217
(II) NV(0): Year: 2006  Week: 20
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 38  vert.: 30
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: Off
(II) NV(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
(II) NV(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
(II) NV(0): Monitor name: SyncMaster
(II) NV(0): Serial No: HMEL502837
(II) NV(0): EDID (in hex):
(II) NV(0):       00ffffffffffff004c2d18023931454d
(II) NV(0):       1410010380261e782a3d85a6564a9a24
(II) NV(0):       125054bfef8081808140714f01010101
(II) NV(0):       010101010101302a009851002a403070
(II) NV(0):       1300782d1100001e000000fd00384b1e
(II) NV(0):       510e000a202020202020000000fc0053
(II) NV(0):       796e634d61737465720a2020000000ff
(II) NV(0):       00484d454c3530323833370a202000c1
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): CRTC 0 is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 1024
(II) NV(0): NOTE: This driver cannot reconfigure the BIOS-programmed size.
(II) NV(0): These dimensions will be used as the panel size for mode validation.
(II) NV(0): EDID vendor "SAM", prod id 536
(II) NV(0): Using EDID range info for horizontal sync
(II) NV(0): Using EDID range info for vertical refresh
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) NV(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) NV(0): Panel is TMDS
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Configured Monitor: Using hsync range of 30.00-81.00 kHz
(II) NV(0): Configured Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) NV(0): Configured Monitor: Using maximum pixel clock of 140.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 1.2667 is 1280x1024
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1360x768" (width too large for virtual size)
(II) NV(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1360x768" (width too large for virtual size)
(II) NV(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) NV(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NV(0): Virtual size is 1280x1024 (pitch 1280)
(**) NV(0): *Driver mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0): *Driver mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0): *Driver mode "1280x1024": 108.9 MHz, 63.6 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(**) NV(0): *Driver mode "1280x1024": 90.8 MHz, 63.0 kHz, 59.8 Hz
(II) NV(0): Modeline "1280x1024"x59.8   90.75  1280 1328 1360 1440  1024 1027 1034 1054 +hsync -vsync (63.0 kHz)
(**) NV(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0): *Driver mode "1280x960": 102.1 MHz, 59.6 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(**) NV(0): *Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NV(0): *Driver mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Driver mode "1152x864": 105.0 MHz, 67.7 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0): *Default mode "1152x864": 105.0 MHz, 67.6 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) NV(0): *Default mode "1152x864": 96.8 MHz, 63.0 kHz, 70.0 Hz
(II) NV(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) NV(0): *Default mode "1152x864": 81.6 MHz, 53.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NV(0): *Driver mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0): *Driver mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Driver mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Driver mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Driver mode "640x480": 30.2 MHz, 35.0 kHz, 66.7 Hz
(II) NV(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0): Display dimensions: (380, 300) mm
(**) NV(0): DPI set to (85, 86)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 1.0.0
      ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
      compiled for 1.5.2, module version = 1.2.0
      ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
      [0] -1      0     0xffffffff - 0xffffffff (0x1) MX[B]
      [1] -1      0     0x000f0000 - 0x000fffff (0x10000) MX[B]
      [2] -1      0     0x000c0000 - 0x000effff (0x30000) MX[B]
      [3] -1      0     0x00000000 - 0x0009ffff (0xa0000) MX[B]
      [4] -1      0     0x0000ffff - 0x0000ffff (0x1) IX[B]
      [5] -1      0     0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(EE) config/hal: couldn't initialise context: (null) ((null))
[/SIZE]
  [SIZE=2]
```

and a look at my /etc/X11/xorg.conf reveals that it is ... **blank???**
[/SIZE]

---

### Post by ScarySquirrel on 2009-02-26
I have heard of Openbox, but not CLI.  I probably can't help you here, but if I know a bit more I could help research it.

---

