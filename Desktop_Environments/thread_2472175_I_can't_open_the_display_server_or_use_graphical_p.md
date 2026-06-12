---
title: "I can't open the display server or use graphical programs and desktop environments"
date: 2022-02-20
forum: Desktop Environments
---

### Post by ash22 on 2022-02-20
I suspended network manager to test something and resumed it and now I can't boot into a desktop environment or use anything graphical. I can only use the tty. When I use startx, nothing happens. Ive been looking online for different solutions and a lot of answers said to try xhost +. But that didnt work either. It says ```
xhost: unable to open display ":0.0"
```
When I echo the display varible, it's empty, so I exported DISPLAY as 0.0 with xhost but it says ```
Invalid MIT-MAGIC-COOKIE-1 keyxhost: unable to open display ":0.0"
```
When I try to launch mate-session, it says ```
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: could not connect: connection refused
```
When I launch Plasma it says something similar but also says it can't start because Plasma's graphical platform plugin could be initialized. I don't know how to fix it.

---

### Post by TheFu on 2022-02-20
Did you enable networking?
Are you certain that X/Windows is used, not Wayland?
What are the errors in the system logs?

---

### Post by ash22 on 2022-02-20
I selected enable networking in recovery mode and I was able to install software with apt so it should be working. 
I don't have wayland installed.
When I use journalctl after trying to startx, It says
```
GLib_GIO-CRITICAL: g_gsettings_schema_source_lookup: assertion 'source != NULL' failed
GLib-GIO-ERROR: No GSettings schemas are installed on the system aborting...

```
Using "reinstall gsetting schemas" didn't fix it.

---

### Post by TheFu on 2022-02-20
Did you happen to use sudo with any GUI program? Looks like a permissions issue for gnome stuff.
Can you create a new userid, then login with that?

In my testing of 20.04 Mate and later, Wayland is the default.

---

### Post by ash22 on 2022-02-20
Should I try startx with sudo? I use Plasma as well as MATE so it's not just permissions with Gnome.

---

### Post by ash22 on 2022-02-20
I rebooted into recovery mode and tried startx as root. It said there was a fatal server error and no screens were found.

---

### Post by TheFu on 2022-02-20
So you won't try creating a new userid?
What do syslog and the Xorg.0.log say?  Anything in dmesg?

---

### Post by ash22 on 2022-02-21
Starting X logs it as Xorg.1.log

```

[    74.066] 
X.Org X Server 1.20.13
X Protocol Version 11, Revision 0
[    74.066] Build Operating System: linux Ubuntu
[    74.066] Current Operating System: Linux boxx 5.4.0-100-generic #113-Ubuntu SMP Thu Feb 3 18:43:29 UTC 2022 x86_64
[    74.066] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-100-generic root=UUID=5c2b9425-cdab-488a-b848-c936c19ddafd ro quiet splash acpi=force vt.handoff=1
[    74.066] Build Date: 14 December 2021  02:14:13PM
[    74.066] xorg-server 2:1.20.13-1ubuntu1~20.04.2 (For technical support please see http://www.ubuntu.com/support) 
[    74.066] Current version of pixman: 0.38.4
[    74.066]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    74.066] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    74.067] (==) Log file: "/home/trashly/.local/share/xorg/Xorg.1.log", Time: Mon Feb 21 11:33:46 2022
[    74.067] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    74.067] (==) No Layout section.  Using the first Screen section.
[    74.067] (==) No screen section available. Using defaults.
[    74.067] (**) |-->Screen "Default Screen Section" (0)
[    74.067] (**) |   |-->Monitor "<default monitor>"
[    74.067] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    74.067] (==) Automatically adding devices
[    74.067] (==) Automatically enabling devices
[    74.067] (==) Automatically adding GPU devices
[    74.067] (==) Automatically binding GPU devices
[    74.067] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    74.067] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    74.067]     Entry deleted from font path.
[    74.067] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    74.067]     Entry deleted from font path.
[    74.067] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    74.067]     Entry deleted from font path.
[    74.067] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    74.067]     Entry deleted from font path.
[    74.067] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    74.067]     Entry deleted from font path.
[    74.067] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    74.067] (==) ModulePath set to "/usr/lib/xorg/modules"
[    74.067] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    74.067] (II) Loader magic: 0x55a1a41ce020
[    74.067] (II) Module ABI versions:
[    74.067]     X.Org ANSI C Emulation: 0.4
[    74.067]     X.Org Video Driver: 24.1
[    74.067]     X.Org XInput driver : 24.1
[    74.067]     X.Org Server Extension : 10.0
[    74.068] (++) using VT number 2

[    74.071] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_37
[    74.072] (II) xfree86: Adding drm device (/dev/dri/card0)
[    74.073] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 11 paused 0
[    74.077] (--) PCI:*(9@0:0:0) 1002:6939:1462:2015 rev 241, Mem @ 0xe0000000/268435456, 0xf0000000/2097152, 0xfce00000/262144, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    74.077] (II) LoadModule: "glx"
[    74.077] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    74.078] (II) Module glx: vendor="X.Org Foundation"
[    74.078]     compiled for 1.20.13, module version = 1.0.0
[    74.078]     ABI class: X.Org Server Extension, version 10.0
[    74.078] (II) Applying OutputClass "AMDgpu" to /dev/dri/card0
[    74.078]     loading driver: amdgpu
[    74.078] (==) Matched amdgpu as autoconfigured driver 0
[    74.078] (==) Matched ati as autoconfigured driver 1
[    74.078] (==) Matched modesetting as autoconfigured driver 2
[    74.078] (==) Matched fbdev as autoconfigured driver 3
[    74.078] (==) Matched vesa as autoconfigured driver 4
[    74.078] (==) Assigned the driver to the xf86ConfigLayout
[    74.078] (II) LoadModule: "amdgpu"
[    74.078] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[    74.078] (II) Module amdgpu: vendor="X.Org Foundation"
[    74.078]     compiled for 1.20.5, module version = 19.1.0
[    74.078]     Module class: X.Org Video Driver
[    74.078]     ABI class: X.Org Video Driver, version 24.0
[    74.078] (II) LoadModule: "ati"
[    74.078] (WW) Warning, couldn't open module ati
[    74.078] (EE) Failed to load module "ati" (module does not exist, 0)
[    74.078] (II) LoadModule: "modesetting"
[    74.078] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    74.078] (II) Module modesetting: vendor="X.Org Foundation"
[    74.078]     compiled for 1.20.13, module version = 1.20.13
[    74.078]     Module class: X.Org Video Driver
[    74.078]     ABI class: X.Org Video Driver, version 24.1
[    74.078] (II) LoadModule: "fbdev"
[    74.079] (WW) Warning, couldn't open module fbdev
[    74.079] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    74.079] (II) LoadModule: "vesa"
[    74.079] (WW) Warning, couldn't open module vesa
[    74.079] (EE) Failed to load module "vesa" (module does not exist, 0)
[    74.079] (II) Applying OutputClass "AMDgpu" to /dev/dri/card0
[    74.079]     loading driver: amdgpu
[    74.079] (==) Matched amdgpu as autoconfigured driver 0
[    74.079] (==) Matched ati as autoconfigured driver 1
[    74.079] (==) Matched modesetting as autoconfigured driver 2
[    74.079] (==) Matched fbdev as autoconfigured driver 3
[    74.079] (==) Matched vesa as autoconfigured driver 4
[    74.079] (==) Assigned the driver to the xf86ConfigLayout
[    74.079] (II) LoadModule: "amdgpu"
[    74.079] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
[    74.079] (II) Module amdgpu: vendor="X.Org Foundation"
[    74.079]     compiled for 1.20.5, module version = 19.1.0
[    74.079]     Module class: X.Org Video Driver
[    74.079]     ABI class: X.Org Video Driver, version 24.0
[    74.079] (II) LoadModule: "ati"
[    74.079] (WW) Warning, couldn't open module ati
[    74.079] (EE) Failed to load module "ati" (module does not exist, 0)
[    74.079] (II) LoadModule: "modesetting"
[    74.079] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    74.079] (II) Module modesetting: vendor="X.Org Foundation"
[    74.079]     compiled for 1.20.13, module version = 1.20.13
[    74.079]     Module class: X.Org Video Driver
[    74.079]     ABI class: X.Org Video Driver, version 24.1
[    74.079] (II) UnloadModule: "modesetting"
[    74.079] (II) Unloading modesetting
[    74.079] (II) Failed to load module "modesetting" (already loaded, 0)
[    74.079] (II) LoadModule: "fbdev"
[    74.079] (WW) Warning, couldn't open module fbdev
[    74.079] (EE) Failed to load module "fbdev" (module does not exist, 0)
[    74.079] (II) LoadModule: "vesa"
[    74.079] (WW) Warning, couldn't open module vesa
[    74.079] (EE) Failed to load module "vesa" (module does not exist, 0)
[    74.079] (II) AMDGPU: Driver for AMD Radeon:
    All GPUs supported by the amdgpu kernel driver
[    74.079] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    74.079] (WW) Falling back to old probe method for modesetting
[    74.079] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    74.079] (II) AMDGPU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    74.079] (==) AMDGPU(0): Depth 24, (--) framebuffer bpp 32
[    74.079] (II) AMDGPU(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    74.079] (==) AMDGPU(0): Default visual is TrueColor
[    74.080] (==) AMDGPU(0): RGB weight 888
[    74.080] (II) AMDGPU(0): Using 8 bits per RGB (8 bit DAC)
[    74.080] (--) AMDGPU(0): Chipset: "AMD Radeon (TM) R9 380 Series" (ChipID = 0x6939)
[    74.080] (II) Loading sub module "fb"
[    74.080] (II) LoadModule: "fb"
[    74.080] (II) Loading /usr/lib/xorg/modules/libfb.so
[    74.080] (II) Module fb: vendor="X.Org Foundation"
[    74.080]     compiled for 1.20.13, module version = 1.0.0
[    74.080]     ABI class: X.Org ANSI C Emulation, version 0.4
[    74.080] (II) Loading sub module "dri2"
[    74.080] (II) LoadModule: "dri2"
[    74.080] (II) Module "dri2" already built-in
[    74.099] (II) Loading sub module "glamoregl"
[    74.100] (II) LoadModule: "glamoregl"
[    74.100] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    74.105] (II) Module glamoregl: vendor="X.Org Foundation"
[    74.105]     compiled for 1.20.13, module version = 1.0.1
[    74.105]     ABI class: X.Org ANSI C Emulation, version 0.4
[    74.112] (II) AMDGPU(0): glamor X acceleration enabled on AMD Radeon (TM) R9 380 Series (TONGA, DRM 3.35.0, 5.4.0-100-generic, LLVM 12.0.0)
[    74.112] (II) AMDGPU(0): glamor detected, initialising EGL layer.
[    74.112] (==) AMDGPU(0): TearFree property default: auto
[    74.112] (==) AMDGPU(0): VariableRefresh: disabled
[    74.112] (II) AMDGPU(0): KMS Pageflipping: enabled
[    74.112] (II) AMDGPU(0): Output DisplayPort-0 has no monitor section
[    74.112] (II) AMDGPU(0): Output HDMI-A-0 has no monitor section
[    74.112] (II) AMDGPU(0): Output DVI-D-0 has no monitor section
[    74.112] (II) AMDGPU(0): Output DVI-D-1 has no monitor section
[    74.124] (II) AMDGPU(0): EDID for output DisplayPort-0
[    74.124] (II) AMDGPU(0): Manufacturer: DEL  Model: a07b  Serial#: 860369228
[    74.124] (II) AMDGPU(0): Year: 2012  Week: 45
[    74.124] (II) AMDGPU(0): EDID Version: 1.4
[    74.124] (II) AMDGPU(0): Digital Display Input
[    74.124] (II) AMDGPU(0): 8 bits per channel
[    74.124] (II) AMDGPU(0): Digital interface is DisplayPort
[    74.124] (II) AMDGPU(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    74.124] (II) AMDGPU(0): Gamma: 2.20
[    74.124] (II) AMDGPU(0): DPMS capabilities: Off
[    74.124] (II) AMDGPU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 YCrCb 4:2:2
[    74.124] (II) AMDGPU(0): First detailed timing is preferred mode
[    74.124] (II) AMDGPU(0): Preferred mode is native pixel format and refresh rate
[    74.124] (II) AMDGPU(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    74.124] (II) AMDGPU(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    74.124] (II) AMDGPU(0): Supported established timings:
[    74.124] (II) AMDGPU(0): 720x400@70Hz
[    74.124] (II) AMDGPU(0): 640x480@60Hz
[    74.124] (II) AMDGPU(0): 800x600@60Hz
[    74.124] (II) AMDGPU(0): 1024x768@60Hz
[    74.124] (II) AMDGPU(0): Manufacturer's mask: 0
[    74.124] (II) AMDGPU(0): Supported standard timings:
[    74.124] (II) AMDGPU(0): #0: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    74.124] (II) AMDGPU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    74.124] (II) AMDGPU(0): #2: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    74.124] (II) AMDGPU(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    74.124] (II) AMDGPU(0): #4: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[    74.124] (II) AMDGPU(0): Supported detailed timing:
[    74.124] (II) AMDGPU(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
[    74.124] (II) AMDGPU(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    74.124] (II) AMDGPU(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[    74.124] (II) AMDGPU(0): Serial No: Y1H5T2B83H1L
[    74.124] (II) AMDGPU(0): Monitor name: DELL U2412M
[    74.124] (II) AMDGPU(0): Ranges: V min: 50 V max: 61 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[    74.124] (II) AMDGPU(0): EDID (in hex):
[    74.124] (II) AMDGPU(0):     00ffffffffffff0010ac7ba04c314833
[    74.124] (II) AMDGPU(0):     2d160104a53420783aee95a3544c9926
[    74.125] (II) AMDGPU(0):     0f5054a1080081408180a940b300d1c0
[    74.125] (II) AMDGPU(0):     010101010101283c80a070b023403020
[    74.125] (II) AMDGPU(0):     360006442100001a000000ff00593148
[    74.125] (II) AMDGPU(0):     35543242383348314c0a000000fc0044
[    74.125] (II) AMDGPU(0):     454c4c2055323431324d0a20000000fd
[    74.125] (II) AMDGPU(0):     00323d1e5311000a20202020202000ca
[    74.125] (II) AMDGPU(0): Printing probed modes for output DisplayPort-0
[    74.125] (II) AMDGPU(0): Modeline "1920x1200"x60.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz eP)
[    74.125] (II) AMDGPU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "1440x900"x60.0  154.00  1440 1968 2000 2080  900 1203 1209 1235 +hsync -vsync (74.0 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "1280x800"x60.0  154.00  1280 1968 2000 2080  800 1203 1209 1235 +hsync -vsync (74.0 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "1280x720"x60.0  154.00  1280 1968 2000 2080  720 1203 1209 1235 +hsync -vsync (74.0 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    74.125] (II) AMDGPU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    74.125] (II) AMDGPU(0): EDID for output HDMI-A-0
[    74.125] (II) AMDGPU(0): EDID for output DVI-D-0
[    74.125] (II) AMDGPU(0): EDID for output DVI-D-1
[    74.125] (II) AMDGPU(0): Output DisplayPort-0 connected
[    74.125] (II) AMDGPU(0): Output HDMI-A-0 disconnected
[    74.125] (II) AMDGPU(0): Output DVI-D-0 disconnected
[    74.125] (II) AMDGPU(0): Output DVI-D-1 disconnected
[    74.125] (II) AMDGPU(0): Using exact sizes for initial modes
[    74.125] (II) AMDGPU(0): Output DisplayPort-0 using initial mode 1920x1200 +0+0
[    74.125] (II) AMDGPU(0): mem size init: gart size :ff978000 vram size: s:ff209000 visible:f209000
[    74.125] (==) AMDGPU(0): DPI set to (96, 96)
[    74.125] (==) AMDGPU(0): Using gamma correction (1.0, 1.0, 1.0)
[    74.125] (II) Loading sub module "ramdac"
[    74.125] (II) LoadModule: "ramdac"
[    74.125] (II) Module "ramdac" already built-in
[    74.125] (II) UnloadModule: "modesetting"
[    74.125] (II) Unloading modesetting
[    74.125] (II) AMDGPU(0): [DRI2] Setup complete
[    74.125] (II) AMDGPU(0): [DRI2]   DRI driver: radeonsi
[    74.125] (II) AMDGPU(0): [DRI2]   VDPAU driver: radeonsi
[    74.125] (II) AMDGPU(0): Front buffer pitch: 8192 bytes
[    74.126] (II) AMDGPU(0): SYNC extension fences enabled
[    74.126] (II) AMDGPU(0): Present extension enabled
[    74.126] (==) AMDGPU(0): DRI3 enabled
[    74.126] (==) AMDGPU(0): Backing store enabled
[    74.126] (II) AMDGPU(0): Direct rendering enabled
[    74.139] (II) AMDGPU(0): Use GLAMOR acceleration.
[    74.139] (II) AMDGPU(0): Acceleration enabled
[    74.139] (==) AMDGPU(0): DPMS enabled
[    74.139] (==) AMDGPU(0): Silken mouse enabled
[    74.139] (II) AMDGPU(0): Set up textured video (glamor)
[    74.159] (II) Initializing extension Generic Event Extension
[    74.159] (II) Initializing extension SHAPE
[    74.159] (II) Initializing extension MIT-SHM
[    74.159] (II) Initializing extension XInputExtension
[    74.160] (II) Initializing extension XTEST
[    74.160] (II) Initializing extension BIG-REQUESTS
[    74.160] (II) Initializing extension SYNC
[    74.160] (II) Initializing extension XKEYBOARD
[    74.160] (II) Initializing extension XC-MISC
[    74.161] (II) Initializing extension SECURITY
[    74.161] (II) Initializing extension XFIXES
[    74.161] (II) Initializing extension RENDER
[    74.161] (II) Initializing extension RANDR
[    74.162] (II) Initializing extension COMPOSITE
[    74.162] (II) Initializing extension DAMAGE
[    74.162] (II) Initializing extension MIT-SCREEN-SAVER
[    74.162] (II) Initializing extension DOUBLE-BUFFER
[    74.162] (II) Initializing extension RECORD
[    74.163] (II) Initializing extension DPMS
[    74.163] (II) Initializing extension Present
[    74.163] (II) Initializing extension DRI3
[    74.163] (II) Initializing extension X-Resource
[    74.163] (II) Initializing extension XVideo
[    74.164] (II) Initializing extension XVideo-MotionCompensation
[    74.164] (II) Initializing extension SELinux
[    74.164] (II) SELinux: Disabled on system
[    74.164] (II) Initializing extension GLX
[    74.172] (II) AIGLX: Loaded and initialized radeonsi
[    74.172] (II) GLX: Initialized DRI2 GL provider for screen 0
[    74.172] (II) Initializing extension XFree86-VidModeExtension
[    74.172] (II) Initializing extension XFree86-DGA
[    74.172] (II) Initializing extension XFree86-DRI
[    74.172] (II) Initializing extension DRI2
[    74.172] (II) AMDGPU(0): Setting screen physical size to 508 x 317
[    74.247] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    74.247] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    74.247] (II) LoadModule: "libinput"
[    74.248] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[    74.248] (II) Module libinput: vendor="X.Org Foundation"
[    74.248]     compiled for 1.20.4, module version = 0.29.0
[    74.248]     Module class: X.Org XInput Driver
[    74.248]     ABI class: X.Org XInput driver, version 24.1
[    74.248] (II) Using input driver 'libinput' for 'Power Button'
[    74.250] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 25 paused 0
[    74.250] (**) Power Button: always reports core events
[    74.250] (**) Option "Device" "/dev/input/event1"
[    74.250] (**) Option "_source" "server/udev"
[    74.253] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    74.253] (II) event1  - Power Button: device is a keyboard
[    74.253] (II) event1  - Power Button: device removed
[    74.253] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    74.253] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    74.253] (**) Option "xkb_model" "pc105"
[    74.253] (**) Option "xkb_layout" "gb"
[    74.276] (II) event1  - Power Button: is tagged by udev as: Keyboard
[    74.276] (II) event1  - Power Button: device is a keyboard
[    74.277] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    74.277] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[    74.277] (II) Using input driver 'libinput' for 'Power Button'
[    74.278] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 28 paused 0
[    74.278] (**) Power Button: always reports core events
[    74.278] (**) Option "Device" "/dev/input/event0"
[    74.278] (**) Option "_source" "server/udev"
[    74.279] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    74.279] (II) event0  - Power Button: device is a keyboard
[    74.279] (II) event0  - Power Button: device removed
[    74.279] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    74.279] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    74.279] (**) Option "xkb_model" "pc105"
[    74.279] (**) Option "xkb_layout" "gb"
[    74.280] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    74.281] (II) event0  - Power Button: device is a keyboard
[    74.281] (II) config/udev: Adding input device SIGMACHIP USB Keyboard (/dev/input/event3)
[    74.281] (**) SIGMACHIP USB Keyboard: Applying InputClass "libinput keyboard catchall"
[    74.281] (II) Using input driver 'libinput' for 'SIGMACHIP USB Keyboard'
[    74.282] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 29 paused 0
[    74.282] (**) SIGMACHIP USB Keyboard: always reports core events
[    74.282] (**) Option "Device" "/dev/input/event3"
[    74.282] (**) Option "_source" "server/udev"
[    74.284] (II) event3  - SIGMACHIP USB Keyboard: is tagged by udev as: Keyboard
[    74.284] (II) event3  - SIGMACHIP USB Keyboard: device is a keyboard
[    74.284] (II) event3  - SIGMACHIP USB Keyboard: device removed
[    74.284] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:01.3/0000:02:00.0/usb1/1-6/1-6:1.0/0003:1C4F:0024.0002/input/input3/event3"
[    74.284] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard" (type: KEYBOARD, id 8)
[    74.284] (**) Option "xkb_model" "pc105"
[    74.284] (**) Option "xkb_layout" "gb"
[    74.286] (II) event3  - SIGMACHIP USB Keyboard: is tagged by udev as: Keyboard
[    74.286] (II) event3  - SIGMACHIP USB Keyboard: device is a keyboard
[    74.287] (II) config/udev: Adding input device SIGMACHIP USB Keyboard Consumer Control (/dev/input/event4)
[    74.287] (**) SIGMACHIP USB Keyboard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    74.287] (II) Using input driver 'libinput' for 'SIGMACHIP USB Keyboard Consumer Control'
[    74.288] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 30 paused 0
[    74.288] (**) SIGMACHIP USB Keyboard Consumer Control: always reports core events
[    74.288] (**) Option "Device" "/dev/input/event4"
[    74.288] (**) Option "_source" "server/udev"
[    74.290] (II) event4  - SIGMACHIP USB Keyboard Consumer Control: is tagged by udev as: Keyboard
[    74.290] (II) event4  - SIGMACHIP USB Keyboard Consumer Control: device is a keyboard
[    74.290] (II) event4  - SIGMACHIP USB Keyboard Consumer Control: device removed
[    74.290] (II) libinput: SIGMACHIP USB Keyboard Consumer Control: needs a virtual subdevice
[    74.290] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:01.3/0000:02:00.0/usb1/1-6/1-6:1.1/0003:1C4F:0024.0003/input/input4/event4"
[    74.290] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard Consumer Control" (type: MOUSE, id 9)
[    74.290] (**) Option "AccelerationScheme" "none"
[    74.290] (**) SIGMACHIP USB Keyboard Consumer Control: (accel) selected scheme none/0
[    74.290] (**) SIGMACHIP USB Keyboard Consumer Control: (accel) acceleration factor: 2.000
[    74.290] (**) SIGMACHIP USB Keyboard Consumer Control: (accel) acceleration threshold: 4
[    74.292] (II) event4  - SIGMACHIP USB Keyboard Consumer Control: is tagged by udev as: Keyboard
[    74.292] (II) event4  - SIGMACHIP USB Keyboard Consumer Control: device is a keyboard
[    74.292] (II) config/udev: Adding input device SIGMACHIP USB Keyboard System Control (/dev/input/event5)
[    74.292] (**) SIGMACHIP USB Keyboard System Control: Applying InputClass "libinput keyboard catchall"
[    74.292] (II) Using input driver 'libinput' for 'SIGMACHIP USB Keyboard System Control'
[    74.293] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 31 paused 0
[    74.293] (**) SIGMACHIP USB Keyboard System Control: always reports core events
[    74.293] (**) Option "Device" "/dev/input/event5"
[    74.293] (**) Option "_source" "server/udev"
[    74.294] (II) event5  - SIGMACHIP USB Keyboard System Control: is tagged by udev as: Keyboard
[    74.294] (II) event5  - SIGMACHIP USB Keyboard System Control: device is a keyboard
[    74.294] (II) event5  - SIGMACHIP USB Keyboard System Control: device removed
[    74.294] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:01.3/0000:02:00.0/usb1/1-6/1-6:1.1/0003:1C4F:0024.0003/input/input5/event5"
[    74.294] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard System Control" (type: KEYBOARD, id 10)
[    74.294] (**) Option "xkb_model" "pc105"
[    74.294] (**) Option "xkb_layout" "gb"
[    74.295] (II) event5  - SIGMACHIP USB Keyboard System Control: is tagged by udev as: Keyboard
[    74.295] (II) event5  - SIGMACHIP USB Keyboard System Control: device is a keyboard
[    74.296] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event10)
[    74.296] (II) No input driver specified, ignoring this device.
[    74.296] (II) This device may have been added with another device file.
[    74.296] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event11)
[    74.296] (II) No input driver specified, ignoring this device.
[    74.296] (II) This device may have been added with another device file.
[    74.296] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event12)
[    74.296] (II) No input driver specified, ignoring this device.
[    74.296] (II) This device may have been added with another device file.
[    74.296] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event7)
[    74.296] (II) No input driver specified, ignoring this device.
[    74.296] (II) This device may have been added with another device file.
[    74.297] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event8)
[    74.297] (II) No input driver specified, ignoring this device.
[    74.297] (II) This device may have been added with another device file.
[    74.297] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event9)
[    74.297] (II) No input driver specified, ignoring this device.
[    74.297] (II) This device may have been added with another device file.
[    74.297] (II) config/udev: Adding input device Primax Kensington Eagle Trackball (/dev/input/event2)
[    74.297] (**) Primax Kensington Eagle Trackball: Applying InputClass "libinput pointer catchall"
[    74.297] (II) Using input driver 'libinput' for 'Primax Kensington Eagle Trackball'
[    74.356] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 32 paused 0
[    74.356] (**) Primax Kensington Eagle Trackball: always reports core events
[    74.356] (**) Option "Device" "/dev/input/event2"
[    74.356] (**) Option "_source" "server/udev"
[    74.359] (II) event2  - Primax Kensington Eagle Trackball: is tagged by udev as: Mouse Trackball
[    74.359] (II) event2  - Primax Kensington Eagle Trackball: device is a pointer
[    74.359] (II) event2  - Primax Kensington Eagle Trackball: device removed
[    74.359] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:07.1/0000:0a:00.3/usb5/5-3/5-3:1.0/0003:047D:2048.0001/input/input2/event2"
[    74.359] (II) XINPUT: Adding extended input device "Primax Kensington Eagle Trackball" (type: MOUSE, id 11)
[    74.359] (**) Option "AccelerationScheme" "none"
[    74.359] (**) Primax Kensington Eagle Trackball: (accel) selected scheme none/0
[    74.359] (**) Primax Kensington Eagle Trackball: (accel) acceleration factor: 2.000
[    74.359] (**) Primax Kensington Eagle Trackball: (accel) acceleration threshold: 4
[    74.362] (II) event2  - Primax Kensington Eagle Trackball: is tagged by udev as: Mouse Trackball
[    74.362] (II) event2  - Primax Kensington Eagle Trackball: device is a pointer
[    74.363] (II) config/udev: Adding input device Primax Kensington Eagle Trackball (/dev/input/mouse0)
[    74.363] (II) No input driver specified, ignoring this device.
[    74.363] (II) This device may have been added with another device file.
[    74.364] (II) config/udev: Adding input device HD-Audio Generic Front Mic (/dev/input/event13)
[    74.364] (II) No input driver specified, ignoring this device.
[    74.364] (II) This device may have been added with another device file.
[    74.365] (II) config/udev: Adding input device HD-Audio Generic Rear Mic (/dev/input/event14)
[    74.365] (II) No input driver specified, ignoring this device.
[    74.365] (II) This device may have been added with another device file.
[    74.365] (II) config/udev: Adding input device HD-Audio Generic Line (/dev/input/event15)
[    74.365] (II) No input driver specified, ignoring this device.
[    74.365] (II) This device may have been added with another device file.
[    74.366] (II) config/udev: Adding input device HD-Audio Generic Line Out Front (/dev/input/event16)
[    74.366] (II) No input driver specified, ignoring this device.
[    74.366] (II) This device may have been added with another device file.
[    74.366] (II) config/udev: Adding input device HD-Audio Generic Line Out Surround (/dev/input/event17)
[    74.366] (II) No input driver specified, ignoring this device.
[    74.366] (II) This device may have been added with another device file.
[    74.367] (II) config/udev: Adding input device HD-Audio Generic Line Out CLFE (/dev/input/event18)
[    74.367] (II) No input driver specified, ignoring this device.
[    74.367] (II) This device may have been added with another device file.
[    74.367] (II) config/udev: Adding input device HD-Audio Generic Front Headphone (/dev/input/event19)
[    74.367] (II) No input driver specified, ignoring this device.
[    74.367] (II) This device may have been added with another device file.
[    74.368] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event6)
[    74.368] (**) Eee PC WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[    74.368] (II) Using input driver 'libinput' for 'Eee PC WMI hotkeys'
[    74.369] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 33 paused 0
[    74.369] (**) Eee PC WMI hotkeys: always reports core events
[    74.369] (**) Option "Device" "/dev/input/event6"
[    74.369] (**) Option "_source" "server/udev"
[    74.369] (II) event6  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
[    74.370] (II) event6  - Eee PC WMI hotkeys: device is a keyboard
[    74.370] (II) event6  - Eee PC WMI hotkeys: device removed
[    74.370] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input6/event6"
[    74.370] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 12)
[    74.370] (**) Option "xkb_model" "pc105"
[    74.370] (**) Option "xkb_layout" "gb"
[    74.370] (II) event6  - Eee PC WMI hotkeys: is tagged by udev as: Keyboard
[    74.370] (II) event6  - Eee PC WMI hotkeys: device is a keyboard
[    74.374] (**) SIGMACHIP USB Keyboard Consumer Control: Applying InputClass "libinput keyboard catchall"
[    74.374] (II) Using input driver 'libinput' for 'SIGMACHIP USB Keyboard Consumer Control'
[    74.374] (II) systemd-logind: returning pre-existing fd for /dev/input/event4 13:68
[    74.374] (**) SIGMACHIP USB Keyboard Consumer Control: always reports core events
[    74.374] (**) Option "Device" "/dev/input/event4"
[    74.374] (**) Option "_source" "_driver/libinput"
[    74.374] (II) libinput: SIGMACHIP USB Keyboard Consumer Control: is a virtual subdevice
[    74.374] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:01.3/0000:02:00.0/usb1/1-6/1-6:1.1/0003:1C4F:0024.0003/input/input4/event4"
[    74.374] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard Consumer Control" (type: KEYBOARD, id 13)
[    74.374] (**) Option "xkb_model" "pc105"
[    74.374] (**) Option "xkb_layout" "gb"
[    74.817] (**) Option "fd" "25"
[    74.817] (II) event1  - Power Button: device removed
[    74.817] (**) Option "fd" "28"
[    74.817] (II) event0  - Power Button: device removed
[    74.817] (**) Option "fd" "29"
[    74.817] (II) event3  - SIGMACHIP USB Keyboard: device removed
[    74.817] (**) Option "fd" "30"
[    74.817] (**) Option "fd" "31"
[    74.817] (II) event5  - SIGMACHIP USB Keyboard System Control: device removed
[    74.817] (**) Option "fd" "32"
[    74.817] (II) event2  - Primax Kensington Eagle Trackball: device removed
[    74.817] (**) Option "fd" "33"
[    74.817] (II) event6  - Eee PC WMI hotkeys: device removed
[    74.817] (**) Option "fd" "30"
[    74.817] (II) event4  - SIGMACHIP USB Keyboard Consumer Control: device removed
[    74.818] (II) UnloadModule: "libinput"
[    74.818] (II) systemd-logind: not releasing fd for 13:68, still in use
[    74.818] (II) UnloadModule: "libinput"
[    74.818] (II) systemd-logind: releasing fd for 13:70
[    74.852] (II) UnloadModule: "libinput"
[    74.852] (II) systemd-logind: releasing fd for 13:66
[    74.892] (II) UnloadModule: "libinput"
[    74.892] (II) systemd-logind: releasing fd for 13:69
[    74.908] (II) UnloadModule: "libinput"
[    74.908] (II) systemd-logind: releasing fd for 13:68
[    74.932] (II) UnloadModule: "libinput"
[    74.932] (II) systemd-logind: releasing fd for 13:67
[    74.952] (II) UnloadModule: "libinput"
[    74.952] (II) systemd-logind: releasing fd for 13:64
[    74.976] (II) UnloadModule: "libinput"
[    74.976] (II) systemd-logind: releasing fd for 13:65
[    75.019] (II) Server terminated successfully (0). Closing log file.

```

---

### Post by ash22 on 2022-02-21
Create a new userid? What would that do? When I log in with the tty, I log in with the user I always use. But when I echo $USER, it doesn't show anything. If I'm already logged as the user I use, could it still be the problem?

---

### Post by ash22 on 2022-02-21
I just looked at dmesg and found a few error:0 lines. They said something about "traps". Like Traps: mate-session trap int3. Traps: xdg-desktop-por. I don't know what they mean but I think they have something to do with not being able to start the desktops.

---

