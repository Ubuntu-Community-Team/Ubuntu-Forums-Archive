---
title: "X-server not start on tty8"
date: 2012-07-18
forum: Desktop Environments
---

### Post by NikTh on 2012-07-18
Hello , 
i have a question about that. 
When i used Debian(at the same machine) , i had the ability to open a new session of X-server on tty8 [Ctrl+alt+F8] with one simple command in VT
```
startx
```I am not able to do this in Ubuntu 
when i wrote startx command in VT  ended up with this error
```
Fatal server error:
Server is already active for display 0
```I can understand this error , cause tty7 is already active , but why this error does not occur in Debian distro ? 

Additional info: 
```
**cat /etc/lsb-release && uname -r **
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
3.2.0-26-generic
``````
**env | grep DESK**
DESKTOP_SESSION=ubuntu
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity
``````
**apt-cache policy xserver-xorg**
xserver-xorg:
  Installed: 1:7.6+12ubuntu1
  Candidate: 1:7.6+12ubuntu1
``````
**lspci -nnk | grep -iA2 vga**
VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
    Subsystem: Acer Incorporated [ALI] Device [1025:0601]
    Kernel driver in use: i915
```Thanks

---

### Post by NikTh on 2012-07-19
Hi , 
i found this Thread --> [http://ubuntuforums.org/showthread.php?t=213756](http://ubuntuforums.org/showthread.php?t=213756) , and tried few things. 
The only thing i can start is xterm . Nothing more. 
Here is the log file for anyone who can configure what possibly be wrong
```
**cat /var/log/Xorg.1.log**
[   830.795] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   830.799] X Protocol Version 11, Revision 0
[   830.800] Build Operating System: Linux 2.6.42-26-generic x86_64 Ubuntu
[   830.801] Current Operating System: Linux acer-ubuntu 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64
[   830.801] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-26-generic root=UUID=92d2cbe7-81a2-43ed-882f-f018d4792d19 ro quiet splash enable_mtrr_cleanup i915.i915_enable_rc6=1 acpi_osi=Linux vt.handoff=7
[   830.804] Build Date: 16 July 2012  08:06:31PM
[   830.805] xorg-server 2:1.11.4-0ubuntu10.6 (For technical support please see http://www.ubuntu.com/support) 
[   830.806] Current version of pixman: 0.24.4
[   830.809]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   830.809] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   830.813] (==) Log file: "/var/log/Xorg.1.log", Time: Fri Jul 20 06:08:10 2012
[   830.815] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   830.815] (==) No Layout section.  Using the first Screen section.
[   830.815] (==) No screen section available. Using defaults.
[   830.815] (**) |-->Screen "Default Screen Section" (0)
[   830.815] (**) |   |-->Monitor "<default monitor>"
[   830.815] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   830.815] (==) Automatically adding devices
[   830.815] (==) Automatically enabling devices
[   830.815] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   830.815]     Entry deleted from font path.
[   830.815] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   830.815]     Entry deleted from font path.
[   830.815] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   830.815]     Entry deleted from font path.
[   830.815] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   830.815]     Entry deleted from font path.
[   830.815] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   830.815]     Entry deleted from font path.
[   830.815] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   830.815]     Entry deleted from font path.
[   830.815] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   830.815] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   830.815] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   830.815] (II) Loader magic: 0x7fbc746a9b00
[   830.815] (II) Module ABI versions:
[   830.815]     X.Org ANSI C Emulation: 0.4
[   830.815]     X.Org Video Driver: 11.0
[   830.815]     X.Org XInput driver : 16.0
[   830.815]     X.Org Server Extension : 6.0
[   830.816] (--) PCI:*(0:0:2:0) 8086:0046:1025:0601 rev 2, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00003050/8
[   830.816] (II) Open ACPI successful (/var/run/acpid.socket)
[   830.816] (II) LoadModule: "extmod"
[   830.816] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   830.817] (II) Module extmod: vendor="X.Org Foundation"
[   830.817]     compiled for 1.11.3, module version = 1.0.0
[   830.817]     Module class: X.Org Server Extension
[   830.817]     ABI class: X.Org Server Extension, version 6.0
[   830.817] (II) Loading extension MIT-SCREEN-SAVER
[   830.817] (II) Loading extension XFree86-VidModeExtension
[   830.817] (II) Loading extension XFree86-DGA
[   830.817] (II) Loading extension DPMS
[   830.817] (II) Loading extension XVideo
[   830.817] (II) Loading extension XVideo-MotionCompensation
[   830.817] (II) Loading extension X-Resource
[   830.817] (II) LoadModule: "dbe"
[   830.817] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   830.817] (II) Module dbe: vendor="X.Org Foundation"
[   830.817]     compiled for 1.11.3, module version = 1.0.0
[   830.817]     Module class: X.Org Server Extension
[   830.817]     ABI class: X.Org Server Extension, version 6.0
[   830.817] (II) Loading extension DOUBLE-BUFFER
[   830.817] (II) LoadModule: "glx"
[   830.817] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   830.817] (II) Module glx: vendor="X.Org Foundation"
[   830.817]     compiled for 1.11.3, module version = 1.0.0
[   830.817]     ABI class: X.Org Server Extension, version 6.0
[   830.817] (==) AIGLX enabled
[   830.817] (II) Loading extension GLX
[   830.817] (II) LoadModule: "record"
[   830.818] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   830.818] (II) Module record: vendor="X.Org Foundation"
[   830.818]     compiled for 1.11.3, module version = 1.13.0
[   830.818]     Module class: X.Org Server Extension
[   830.818]     ABI class: X.Org Server Extension, version 6.0
[   830.818] (II) Loading extension RECORD
[   830.818] (II) LoadModule: "dri"
[   830.818] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   830.818] (II) Module dri: vendor="X.Org Foundation"
[   830.818]     compiled for 1.11.3, module version = 1.0.0
[   830.818]     ABI class: X.Org Server Extension, version 6.0
[   830.818] (II) Loading extension XFree86-DRI
[   830.818] (II) LoadModule: "dri2"
[   830.818] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   830.818] (II) Module dri2: vendor="X.Org Foundation"
[   830.818]     compiled for 1.11.3, module version = 1.2.0
[   830.818]     ABI class: X.Org Server Extension, version 6.0
[   830.818] (II) Loading extension DRI2
[   830.818] (==) Matched intel as autoconfigured driver 0
[   830.818] (==) Matched vesa as autoconfigured driver 1
[   830.818] (==) Matched fbdev as autoconfigured driver 2
[   830.818] (==) Assigned the driver to the xf86ConfigLayout
[   830.818] (II) LoadModule: "intel"
[   830.818] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   830.819] (II) Module intel: vendor="X.Org Foundation"
[   830.819]     compiled for 1.11.3, module version = 2.19.0
[   830.819]     Module class: X.Org Video Driver
[   830.819]     ABI class: X.Org Video Driver, version 11.0
[   830.819] (II) LoadModule: "vesa"
[   830.819] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   830.819] (II) Module vesa: vendor="X.Org Foundation"
[   830.819]     compiled for 1.11.3, module version = 2.3.0
[   830.819]     Module class: X.Org Video Driver
[   830.819]     ABI class: X.Org Video Driver, version 11.0
[   830.819] (II) LoadModule: "fbdev"
[   830.819] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   830.819] (II) Module fbdev: vendor="X.Org Foundation"
[   830.819]     compiled for 1.11.3, module version = 0.4.2
[   830.819]     ABI class: X.Org Video Driver, version 11.0
[   830.819] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2)
[   830.819] (II) VESA: driver for VESA chipsets: vesa
[   830.819] (II) FBDEV: driver for framebuffer: fbdev
[   830.819] (--) using VT number 8

[   830.824] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   830.824] (WW) Falling back to old probe method for vesa
[   830.824] (WW) Falling back to old probe method for fbdev
[   830.824] (II) Loading sub module "fbdevhw"
[   830.824] (II) LoadModule: "fbdevhw"
[   830.825] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   830.825] (II) Module fbdevhw: vendor="X.Org Foundation"
[   830.825]     compiled for 1.11.3, module version = 0.0.2
[   830.825]     ABI class: X.Org Video Driver, version 11.0
[   830.825] drmOpenDevice: node name is /dev/dri/card0
[   830.825] drmOpenDevice: open result is 11, (OK)
[   830.825] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   830.825] drmOpenDevice: node name is /dev/dri/card0
[   830.825] drmOpenDevice: open result is 11, (OK)
[   830.825] drmOpenByBusid: drmOpenMinor returns 11
[   830.825] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   830.825] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   830.825] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   830.825] (==) intel(0): RGB weight 888
[   830.825] (==) intel(0): Default visual is TrueColor
[   830.825] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[   830.825] (--) intel(0): Chipset: "Arrandale"
[   830.825] (**) intel(0): Relaxed fencing enabled
[   830.825] (**) intel(0): Wait on SwapBuffers? enabled
[   830.825] (**) intel(0): Triple buffering? enabled
[   830.825] (**) intel(0): Framebuffer tiled
[   830.825] (**) intel(0): Pixmaps tiled
[   830.825] (**) intel(0): 3D buffers tiled
[   830.825] (**) intel(0): SwapBuffers wait enabled
[   830.825] (==) intel(0): video overlay key set to 0x101fe
[   830.825] (II) intel(0): Output LVDS1 has no monitor section
[   830.924] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[   830.924] (II) intel(0): Output VGA1 has no monitor section
[   830.924] (II) intel(0): EDID for output LVDS1
[   830.924] (II) intel(0): Manufacturer: LGD  Model: 2dc  Serial#: 0
[   830.924] (II) intel(0): Year: 2010  Week: 0
[   830.924] (II) intel(0): EDID Version: 1.3
[   830.924] (II) intel(0): Digital Display Input
[   830.924] (II) intel(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[   830.924] (II) intel(0): Gamma: 2.20
[   830.924] (II) intel(0): No DPMS capabilities specified
[   830.924] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   830.924] (II) intel(0): First detailed timing is preferred mode
[   830.924] (II) intel(0): redX: 0.623 redY: 0.369   greenX: 0.346 greenY: 0.610
[   830.924] (II) intel(0): blueX: 0.148 blueY: 0.098   whiteX: 0.313 whiteY: 0.329
[   830.924] (II) intel(0): Manufacturer's mask: 0
[   830.924] (II) intel(0): Supported detailed timing:
[   830.924] (II) intel(0): clock: 70.0 MHz   Image Size:  344 x 194 mm
[   830.924] (II) intel(0): h_active: 1366  h_sync: 1402  h_sync_end 1450 h_blank_end 1492 h_border: 0
[   830.924] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 782 v_border: 0
[   830.924] (II) intel(0):  LG Display
[   830.924] (II) intel(0):  LP156WH4-TLA1
[   830.924] (II) intel(0): EDID (in hex):
[   830.924] (II) intel(0):     00ffffffffffff0030e4dc0200000000
[   830.924] (II) intel(0):     00140103802213780aa9059f5e589c26
[   830.924] (II) intel(0):     19505400000001010101010101010101
[   830.924] (II) intel(0):     010101010101581b567e50000e302430
[   830.924] (II) intel(0):     350058c2100000190000000000000000
[   830.924] (II) intel(0):     00000000000000000000000000fe004c
[   830.924] (II) intel(0):     4720446973706c61790a2020000000fe
[   830.924] (II) intel(0):     004c503135365748342d544c41310079
[   830.924] (II) intel(0): EDID vendor "LGD", prod id 732
[   830.924] (II) intel(0): Printing DDC gathered Modelines:
[   830.924] (II) intel(0): Modeline "1366x768"x0.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz)
[   830.924] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[   830.924] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   830.924] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[   830.924] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[   830.925] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[   830.925] (II) intel(0): Printing probed modes for output LVDS1
[   830.925] (II) intel(0): Modeline "1366x768"x60.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz)
[   830.925] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[   830.925] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[   830.925] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   830.925] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   830.925] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   830.925] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   830.925] (II) intel(0): EDID for output VGA1
[   830.925] (II) intel(0): Output LVDS1 connected
[   830.925] (II) intel(0): Output VGA1 disconnected
[   830.925] (II) intel(0): Using exact sizes for initial modes
[   830.925] (II) intel(0): Output LVDS1 using initial mode 1366x768
[   830.925] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   830.925] (II) intel(0): Kernel page flipping support detected, enabling
[   830.925] (**) intel(0): Display dimensions: (340, 190) mm
[   830.925] (**) intel(0): DPI set to (102, 102)
[   830.925] (II) Loading sub module "fb"
[   830.925] (II) LoadModule: "fb"
[   830.925] (II) Loading /usr/lib/xorg/modules/libfb.so
[   830.926] (II) Module fb: vendor="X.Org Foundation"
[   830.926]     compiled for 1.11.3, module version = 1.0.0
[   830.926]     ABI class: X.Org ANSI C Emulation, version 0.4
[   830.926] (II) Loading sub module "dri2"
[   830.926] (II) LoadModule: "dri2"
[   830.926] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   830.926] (II) Module dri2: vendor="X.Org Foundation"
[   830.926]     compiled for 1.11.3, module version = 1.2.0
[   830.926]     ABI class: X.Org Server Extension, version 6.0
[   830.926] (II) UnloadModule: "vesa"
[   830.926] (II) Unloading vesa
[   830.926] (II) UnloadModule: "fbdev"
[   830.926] (II) Unloading fbdev
[   830.926] (II) UnloadModule: "fbdevhw"
[   830.926] (II) Unloading fbdevhw
[   830.926] (==) Depth 24 pixmap format is 32 bpp
[   830.926] (II) intel(0): [DRI2] Setup complete
[   830.926] (II) intel(0): [DRI2]   DRI driver: i965
[   830.926] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[   830.938] (II) UXA(0): Driver registered support for the following operations:
[   830.938] (II)         solid
[   830.938] (II)         copy
[   830.938] (II)         composite (RENDER acceleration)
[   830.938] (II)         put_image
[   830.938] (II)         get_image
[   830.938] (==) intel(0): Backing store disabled
[   830.938] (==) intel(0): Silken mouse enabled
[   830.938] (II) intel(0): Initializing HW Cursor
[   830.938] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   830.939] (==) intel(0): DPMS enabled
[   830.939] (==) intel(0): Intel XvMC decoder enabled
[   830.939] (II) intel(0): Set up textured video
[   830.940] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[   830.940] (II) intel(0): direct rendering: DRI2 Enabled
[   830.940] (==) intel(0): hotplug detection: "enabled"
[   831.012] (--) RandR disabled
[   831.012] (II) Initializing built-in extension Generic Event Extension
[   831.012] (II) Initializing built-in extension SHAPE
[   831.012] (II) Initializing built-in extension MIT-SHM
[   831.012] (II) Initializing built-in extension XInputExtension
[   831.012] (II) Initializing built-in extension XTEST
[   831.012] (II) Initializing built-in extension BIG-REQUESTS
[   831.012] (II) Initializing built-in extension SYNC
[   831.012] (II) Initializing built-in extension XKEYBOARD
[   831.012] (II) Initializing built-in extension XC-MISC
[   831.012] (II) Initializing built-in extension SECURITY
[   831.012] (II) Initializing built-in extension XINERAMA
[   831.012] (II) Initializing built-in extension XFIXES
[   831.012] (II) Initializing built-in extension RENDER
[   831.012] (II) Initializing built-in extension RANDR
[   831.012] (II) Initializing built-in extension COMPOSITE
[   831.012] (II) Initializing built-in extension DAMAGE
[   831.024] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   831.024] (II) AIGLX: enabled GLX_INTEL_swap_event
[   831.024] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   831.024] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   831.024] (II) AIGLX: Loaded and initialized i965
[   831.024] (II) GLX: Initialized DRI2 GL provider for screen 0
[   831.024] (II) intel(0): Setting screen physical size to 361 x 203
[   831.031] (II) XKB: reuse xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   831.033] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   831.033] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   831.033] (II) LoadModule: "evdev"
[   831.033] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   831.033] (II) Module evdev: vendor="X.Org Foundation"
[   831.033]     compiled for 1.11.3, module version = 2.7.0
[   831.033]     Module class: X.Org XInput Driver
[   831.033]     ABI class: X.Org XInput driver, version 16.0
[   831.033] (II) Using input driver 'evdev' for 'Power Button'
[   831.033] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   831.033] (**) Power Button: always reports core events
[   831.033] (**) evdev: Power Button: Device: "/dev/input/event3"
[   831.033] (--) evdev: Power Button: Vendor 0 Product 0x1
[   831.033] (--) evdev: Power Button: Found keys
[   831.033] (II) evdev: Power Button: Configuring as keyboard
[   831.033] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   831.033] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   831.033] (**) Option "xkb_rules" "evdev"
[   831.033] (**) Option "xkb_model" "pc105"
[   831.033] (**) Option "xkb_layout" "us"
[   831.034] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[   831.034] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   831.034] (II) Using input driver 'evdev' for 'Video Bus'
[   831.034] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   831.034] (**) Video Bus: always reports core events
[   831.034] (**) evdev: Video Bus: Device: "/dev/input/event6"
[   831.034] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   831.034] (--) evdev: Video Bus: Found keys
[   831.034] (II) evdev: Video Bus: Configuring as keyboard
[   831.034] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6/event6"
[   831.034] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   831.034] (**) Option "xkb_rules" "evdev"
[   831.034] (**) Option "xkb_model" "pc105"
[   831.034] (**) Option "xkb_layout" "us"
[   831.034] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   831.034] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   831.034] (II) Using input driver 'evdev' for 'Power Button'
[   831.034] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   831.034] (**) Power Button: always reports core events
[   831.034] (**) evdev: Power Button: Device: "/dev/input/event0"
[   831.035] (--) evdev: Power Button: Vendor 0 Product 0x1
[   831.035] (--) evdev: Power Button: Found keys
[   831.035] (II) evdev: Power Button: Configuring as keyboard
[   831.035] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/PNP0C0C:00/input/input0/event0"
[   831.035] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   831.035] (**) Option "xkb_rules" "evdev"
[   831.035] (**) Option "xkb_model" "pc105"
[   831.035] (**) Option "xkb_layout" "us"
[   831.035] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[   831.035] (II) No input driver specified, ignoring this device.
[   831.035] (II) This device may have been added with another device file.
[   831.035] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   831.035] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   831.035] (II) Using input driver 'evdev' for 'Sleep Button'
[   831.035] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   831.035] (**) Sleep Button: always reports core events
[   831.035] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[   831.035] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   831.035] (--) evdev: Sleep Button: Found keys
[   831.035] (II) evdev: Sleep Button: Configuring as keyboard
[   831.035] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:0d/PNP0C0E:00/input/input2/event2"
[   831.035] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   831.035] (**) Option "xkb_rules" "evdev"
[   831.035] (**) Option "xkb_model" "pc105"
[   831.035] (**) Option "xkb_layout" "us"
[   831.036] (II) config/udev: Adding input device 1.3M HD WebCam (/dev/input/event5)
[   831.036] (**) 1.3M HD WebCam: Applying InputClass "evdev keyboard catchall"
[   831.036] (II) Using input driver 'evdev' for '1.3M HD WebCam'
[   831.036] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   831.036] (**) 1.3M HD WebCam: always reports core events
[   831.036] (**) evdev: 1.3M HD WebCam: Device: "/dev/input/event5"
[   831.036] (--) evdev: 1.3M HD WebCam: Vendor 0x64e Product 0xd250
[   831.036] (--) evdev: 1.3M HD WebCam: Found keys
[   831.036] (II) evdev: 1.3M HD WebCam: Configuring as keyboard
[   831.036] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input5/event5"
[   831.036] (II) XINPUT: Adding extended input device "1.3M HD WebCam" (type: KEYBOARD, id 10)
[   831.036] (**) Option "xkb_rules" "evdev"
[   831.036] (**) Option "xkb_model" "pc105"
[   831.036] (**) Option "xkb_layout" "us"
[   831.036] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event7)
[   831.036] (II) No input driver specified, ignoring this device.
[   831.036] (II) This device may have been added with another device file.
[   831.037] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event8)
[   831.037] (II) No input driver specified, ignoring this device.
[   831.037] (II) This device may have been added with another device file.
[   831.037] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   831.037] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   831.037] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   831.037] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   831.037] (**) AT Translated Set 2 keyboard: always reports core events
[   831.037] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   831.037] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   831.037] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   831.037] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   831.037] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   831.037] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[   831.037] (**) Option "xkb_rules" "evdev"
[   831.037] (**) Option "xkb_model" "pc105"
[   831.037] (**) Option "xkb_layout" "us"
[   831.037] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[   831.037] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   831.037] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   831.037] (II) LoadModule: "synaptics"
[   831.038] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   831.038] (II) Module synaptics: vendor="X.Org Foundation"
[   831.038]     compiled for 1.11.3, module version = 1.6.2
[   831.038]     Module class: X.Org XInput Driver
[   831.038]     ABI class: X.Org XInput driver, version 16.0
[   831.038] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   831.038] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   831.038] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   831.038] (**) Option "Device" "/dev/input/event9"
[   831.080] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[   831.080] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5772
[   831.080] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5086
[   831.080] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   831.080] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   831.080] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   831.080] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   831.080] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   831.080] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   831.120] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[   831.120] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[   831.120] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   831.120] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   831.120] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.035
[   831.120] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   831.120] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   831.120] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   831.120] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   831.120] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   831.120] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   831.120] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   838.844] (II) AIGLX: Suspending AIGLX clients for VT switch
[   839.788] (II) Open ACPI successful (/var/run/acpid.socket)
[   839.788] (II) AIGLX: Resuming AIGLX clients after VT switch
[   839.848] (II) intel(0): EDID vendor "LGD", prod id 732
[   839.848] (II) intel(0): Printing DDC gathered Modelines:
[   839.848] (II) intel(0): Modeline "1366x768"x0.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz)
[   839.849] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   841.200] (II) AIGLX: Suspending AIGLX clients for VT switch
[   842.331] (II) UnloadModule: "synaptics"
[   842.331] (II) Unloading synaptics
[   842.331] (II) evdev: AT Translated Set 2 keyboard: Close
[   842.331] (II) UnloadModule: "evdev"
[   842.331] (II) Unloading evdev
[   842.331] (II) evdev: 1.3M HD WebCam: Close
[   842.331] (II) UnloadModule: "evdev"
[   842.331] (II) Unloading evdev
[   842.331] (II) evdev: Sleep Button: Close
[   842.331] (II) UnloadModule: "evdev"
[   842.331] (II) Unloading evdev
[   842.331] (II) evdev: Power Button: Close
[   842.331] (II) UnloadModule: "evdev"
[   842.331] (II) Unloading evdev
[   842.331] (II) evdev: Video Bus: Close
[   842.332] (II) UnloadModule: "evdev"
[   842.332] (II) Unloading evdev
[   842.332] (II) evdev: Power Button: Close
[   842.332] (II) UnloadModule: "evdev"
[   842.332] (II) Unloading evdev
[   842.343]  ddxSigGiveUp: Closing log
[   842.346] Server terminated successfully (0). Closing log file.
```
Thanks

---

### Post by NikTh on 2012-07-21
Ok , 
I think its time for apologies.. :P 

I thought that session would open more quickly  than it is.. 
It wants about 45secs to 1 min to open the new session , but it opens Ok. 

The correct command is ```
startx -- :1 
```it uses the /usr/share/X11/Xorg.conf.d/ folder to initialize the connection , and X-server runs without problems . 
Runs automatically to Vt8 [tty8]. 

[SIZE=3]**Edit:  **[/SIZE]

Sometimes wants ```
unity --reset
``` to initialize the session correct. 

**And what is the point of all this attempt ? **

The point is that i can have 2 users connected simultaneously , and is not necessary to logout , login to connect to another user.. just hit Ctrl + alt + F8 . :)
Thanks.

---

