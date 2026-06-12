---
title: "Xorg Desktop Problem on Ubuntu 10.04"
date: 2011-03-30
forum: Desktop Environments
---

### Post by webusr1 on 2011-03-30
I am running Ubuntu 10.04 and the desktop Gnome GUI no longer allows me to login. Initially I upgraded from Ubuntu 8.04 to 10.04 on April 2010 and have been running 10.04 with no major problems. The system now displays Ubuntu and never provides a login prompt from the Gnome GUI. 

I can boot into recovery mode and login without X running in terminal mode. Once I login, I type "startx" and the Gnome GUI in good to go, but don't know how to fix this issue. I have tried reconfiguring X, but doesn't fix my problem.

Tried the following with NO SUCCESS:

1)     sudo service gdm stop

Then create an Xorg configuration file with the command below:

    sudo Xorg -configure

2)   sudo dpkg-reconfigure xserver-xorg

Can you guys tell me what the process is for logging into the  Gnome GUI?  Any help would be appreciated.

Thanks!

---

### Post by Krytarik on 2011-03-30
So, you are saying that Ubuntu freezes at the boot splash screen when you boot normal, right?

First, check "/var/log/Xorg.0.log", respectively "/var/log/Xorg.0.log.old" for error messages.

Also, what video card/chip do you have? Check with
```
lspci |grep VGA
```
if you don't know.

What video driver are you running?
How did you install those?

---

### Post by webusr1 on 2011-03-31
Correct it freezes at the Ubuntu splash scree. Would nice to remove it to see what's locking up. I have an Nvidia card. I installed about 4 months ago and installed the Ubuntu approved nvidia drivers. During troubleshooting yesterday I uninstalled them (System-->Admin-->Hardware Drivers) think that that might be the problem, but it didn't fix my issue...

etcmon@dell-desktop:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation Device 10c3 (rev a2)

I'm not sure how to analyze the  /var/log/Xorg.0.log 

I'll list it here....

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux dell-desktop 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686
Kernel command line: root=UUID=ec7c6819-18d1-4e2a-9464-6fa18fd0a742 ro all_generic_ide  single
Build Date: 10 December 2010  05:53:04PM
xorg-server 2:1.7.6-2ubuntu7.5 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 31 00:12:21 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Default Layout"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:1:0:0) 10de:10c3:3842:1302 nVidia Corporation rev 162, Mem @ 0xfb000000/16777216, 0xb0000000/268435456, 0xce000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/524288
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
(==) Matched nouveau as autoconfigured driver 0
(==) Matched nv as autoconfigured driver 1
(==) Matched vesa as autoconfigured driver 2
(==) Matched fbdev as autoconfigured driver 3
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.15
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.7.3.901, module version = 2.1.15
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
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) NOUVEAU driver Date:   Wed Feb 10 18:43:39 2010 +0100
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:00:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] nouveau interface version: 0.0.15
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(--) NOUVEAU(0): Chipset: "NVIDIA NVa8"
(II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(==) NOUVEAU(0): Using HW cursor
(II) NOUVEAU(0): Output DVI-I-1 using monitor section Configured Monitor
(II) NOUVEAU(0): Output DVI-D-1 has no monitor section
(II) NOUVEAU(0): Output VGA-1 has no monitor section
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): EDID for output DVI-D-1
(II) NOUVEAU(0): EDID for output VGA-1
(II) NOUVEAU(0): Manufacturer: DEL  Model: f003  Serial#: 826753357
(II) NOUVEAU(0): Year: 2008  Week: 30
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 41  vert.: 26
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NOUVEAU(0): Default color space is primary color space
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.640 redY: 0.336   greenX: 0.293 greenY: 0.599
(II) NOUVEAU(0): blueX: 0.152 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@67Hz
(II) NOUVEAU(0): 640x480@72Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@72Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@70Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x864@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #3: hsize: 1440  vsize 900  refresh: 75  vid: 3989
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 106.5 MHz   Image Size:  408 x 255 mm
(II) NOUVEAU(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
(II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Serial No: 7373187O1GAM
(II) NOUVEAU(0): Monitor name: DELL SE198WFP
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0):     00ffffffffffff0010ac03f04d414731
(II) NOUVEAU(0):     1e12010368291a78eec125a3564b9927
(II) NOUVEAU(0):     115054bfef809500714f8180950f0101
(II) NOUVEAU(0):     0101010101019a29a0d0518422305098
(II) NOUVEAU(0):     360098ff1000001c000000fd00384b1e
(II) NOUVEAU(0):     530e000a202020202020000000ff0037
(II) NOUVEAU(0):     3337333138374f3147414d20000000fc
(II) NOUVEAU(0):     0044454c4c20534531393857465000ed
(II) NOUVEAU(0): Printing probed modes for output VGA-1
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Output DVI-I-1 disconnected
(II) NOUVEAU(0): Output DVI-D-1 disconnected
(II) NOUVEAU(0): Output VGA-1 connected
(II) NOUVEAU(0): Using exact sizes for initial modes
(II) NOUVEAU(0): Output VGA-1 using initial mode 1440x900
(II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(--) NOUVEAU(0): Virtual size is 1440x900 (pitch 1440)
(**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NOUVEAU(0):  Driver mode "1440x900": 136.8 MHz (scaled from 0.0 MHz), 70.6 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
(II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(==) NOUVEAU(0): DPI set to (96, 96)
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules/libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.5.0
    ABI class: X.Org Video Driver, version 6.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) NOUVEAU(0): Opened GPU channel 2
(II) NOUVEAU(0): [DRI2] Setup complete
(II) NOUVEAU(0): GART: 512MiB available
(II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
(II) EXA(0): Driver allocated offscreen pixmaps
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) NOUVEAU(0): Backing store disabled
(==) NOUVEAU(0): Silken mouse enabled
(II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
(II) NOUVEAU(0): [XvMC] Extension initialized.
(II) NOUVEAU(0): NVEnterVT is called.
(==) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
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
(II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(II) AIGLX: reverting to software rendering
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 380 x 238
resize called 1440 900
(II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
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
(II) config/udev: Adding input device ATEN Advance Tech Inc. CS62USV1.0.071 (/dev/input/event3)
(**) ATEN Advance Tech Inc. CS62USV1.0.071: Applying InputClass "evdev keyboard catchall"
(**) ATEN Advance Tech Inc. CS62USV1.0.071: always reports core events
(**) ATEN Advance Tech Inc. CS62USV1.0.071: Device: "/dev/input/event3"
(II) ATEN Advance Tech Inc. CS62USV1.0.071: Found keys
(II) ATEN Advance Tech Inc. CS62USV1.0.071: Configuring as keyboard
(II) XINPUT: Adding extended input device "ATEN Advance Tech Inc. CS62USV1.0.071" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device ATEN Advance Tech Inc. CS62USV1.0.071 (/dev/input/event4)
(**) ATEN Advance Tech Inc. CS62USV1.0.071: Applying InputClass "evdev pointer catchall"
(**) ATEN Advance Tech Inc. CS62USV1.0.071: always reports core events
(**) ATEN Advance Tech Inc. CS62USV1.0.071: Device: "/dev/input/event4"
(II) ATEN Advance Tech Inc. CS62USV1.0.071: Found 9 mouse buttons
(II) ATEN Advance Tech Inc. CS62USV1.0.071: Found scroll wheel(s)
(II) ATEN Advance Tech Inc. CS62USV1.0.071: Found relative axes
(II) ATEN Advance Tech Inc. CS62USV1.0.071: Found x and y relative axes
(II) ATEN Advance Tech Inc. CS62USV1.0.071: Configuring as mouse
(**) ATEN Advance Tech Inc. CS62USV1.0.071: YAxisMapping: buttons 4 and 5
(**) ATEN Advance Tech Inc. CS62USV1.0.071: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ATEN Advance Tech Inc. CS62USV1.0.071" (type: MOUSE)
(II) ATEN Advance Tech Inc. CS62USV1.0.071: initialized for relative axes.
(II) config/udev: Adding input device ATEN Advance Tech Inc. CS62USV1.0.071 (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech Trackball (/dev/input/event5)
(**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
(**) Logitech Trackball: always reports core events
(**) Logitech Trackball: Device: "/dev/input/event5"
(II) Logitech Trackball: Found 3 mouse buttons
(II) Logitech Trackball: Found scroll wheel(s)
(II) Logitech Trackball: Found relative axes
(II) Logitech Trackball: Found x and y relative axes
(II) Logitech Trackball: Configuring as mouse
(**) Logitech Trackball: YAxisMapping: buttons 4 and 5
(**) Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE)
(II) Logitech Trackball: initialized for relative axes.
(II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
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
(II) NOUVEAU(0): EDID vendor "DEL", prod id 61443
(II) NOUVEAU(0): Using EDID range info for horizontal sync
(II) NOUVEAU(0): Using EDID range info for vertical refresh
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NOUVEAU(0): EDID vendor "DEL", prod id 61443
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NOUVEAU(0): EDID vendor "DEL", prod id 61443
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
(II) NOUVEAU(0): EDID vendor "DEL", prod id 61443
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)

---

### Post by Krytarik on 2011-03-31
Because you removed the previously used proprietary driver, the "nouveau" driver came into play. And because it is apparently faulty, it is causing those issue.

** Suggestion 1:** Install the proprietary driver through Ubuntu-X-Swat's PPA, it offers more recent drivers than the offical repos:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-current

```Make sure that a proper xorg.conf is present:
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```**Suggestion 2:** Upgrade the nouveau driver through Xorg-Edgers' PPA, it too offers more recent drivers than the offical repos:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```In both cases, reboot/relogin afterwards.

---

### Post by webusr1 on 2011-04-01
Yes, re-installing the latest Nvidia driver fixed the problem. However, I used System-->Admin-->Hardware. Selected proprietary driver for Nvidia. That's a very simple method.

Thanks!!!

I will create a new post. My Dad loaded Ubuntu 10.04 on his Compaq PC and he has Gnone GDM related problem too after two logins!

Thanks again.

---

