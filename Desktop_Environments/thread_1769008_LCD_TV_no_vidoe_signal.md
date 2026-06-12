---
title: "LCD TV no vidoe signal"
date: 2011-05-27
forum: Desktop Environments
---

### Post by inckiekage on 2011-05-27
i installed Kubuntu on my mediacenter, due to a hard drive crash (before i ran Ubuntu 10.10, but Ubuntu 11.04 sucks), and now i'm having trouble getting a video signal to my TV.

My computer has Nvidia 9400 GT grapich card, and a Philips 32" LCD TV 32PFL5405H connected via VGA.

The computer only support one monitor connected at a time, so i have to do everything using a SSH connection.

Here is my X log:
```
kimse@mediacenter:~$ cat /var/log/Xorg.0.log
[    16.564]                                                                                                                                                                        
X.Org X Server 1.10.1                                                                                                                                                               
Release Date: 2011-04-15                                                                                                                                                            
[    16.593] X Protocol Version 11, Revision 0                                                                                                                                      
[    16.593] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu                                                                                                           
[    16.593] Current Operating System: Linux mediacenter 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64                                                        
[    16.593] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=c4ce3dd3-38a6-449c-a904-5bee3e3229b0 ro quiet splash vt.handoff=7                             
[    16.593] Build Date: 19 April 2011  03:40:45PM                                                                                                                                  
[    16.593] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support)                                                                         
[    16.593] Current version of pixman: 0.20.2                                                                                                                                      
[    16.593]    Before reporting problems, check http://wiki.x.org                                                                                                                  
        to make sure that you have the latest version.                                                                                                                              
[    16.593] Markers: (--) probed, (**) from config file, (==) default setting,                                                                                                     
        (++) from command line, (!!) notice, (II) informational,                                                                                                                    
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.                                                                                                               
[    16.594] (==) Log file: "/var/log/Xorg.0.log", Time: Fri May 27 20:06:18 2011                                                                                                   
[    16.650] (==) Using config file: "/etc/X11/xorg.conf"                                                                                                                           
[    16.650] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.768] (==) No Layout section.  Using the first Screen section.
[    16.768] (==) No screen section available. Using defaults.
[    16.768] (**) |-->Screen "Default Screen Section" (0)
[    16.768] (**) |   |-->Monitor "<default monitor>"
[    16.785] (==) No device specified for screen "Default Screen Section".
        Using the first device section listed.
[    16.785] (**) |   |-->Device "Default Device"
[    16.785] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[    16.785] (==) Automatically adding devices
[    16.785] (==) Automatically enabling devices
[    16.899] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.899]    Entry deleted from font path.
[    16.899] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.899]    Entry deleted from font path.
[    16.899] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.899]    Entry deleted from font path.
[    16.899] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.899]    Entry deleted from font path.
[    16.899] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.899]    Entry deleted from font path.
[    16.964] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    16.964] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.964] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.964] (II) Loader magic: 0x7e0280
[    16.964] (II) Module ABI versions:
[    16.964]    X.Org ANSI C Emulation: 0.4
[    16.964]    X.Org Video Driver: 10.0
[    16.964]    X.Org XInput driver : 12.3
[    16.964]    X.Org Server Extension : 5.0
[    16.965] (--) PCI:*(0:2:0:0) 10de:06e4:0000:0000 rev 161, Mem @ 0xd4000000/16777216, 0xc0000000/268435456, 0xd2000000/33554432, I/O @ 0x00001100/128, BIOS @ 0x????????/131072
[    16.965] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.965] (II) LoadModule: "extmod"
[    17.417] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    17.502] (II) Module extmod: vendor="X.Org Foundation"
[    17.502]    compiled for 1.10.1, module version = 1.0.0
[    17.502]    Module class: X.Org Server Extension
[    17.502]    ABI class: X.Org Server Extension, version 5.0
[    17.502] (II) Loading extension MIT-SCREEN-SAVER
[    17.502] (II) Loading extension XFree86-VidModeExtension
[    17.502] (II) Loading extension XFree86-DGA
[    17.502] (II) Loading extension DPMS
[    17.502] (II) Loading extension XVideo
[    17.502] (II) Loading extension XVideo-MotionCompensation
[    17.502] (II) Loading extension X-Resource
[    17.502] (II) LoadModule: "dbe"
[    17.503] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    17.663] (II) Module dbe: vendor="X.Org Foundation"
[    17.663]    compiled for 1.10.1, module version = 1.0.0
[    17.663]    Module class: X.Org Server Extension
[    17.663]    ABI class: X.Org Server Extension, version 5.0
[    17.663] (II) Loading extension DOUBLE-BUFFER
[    17.663] (II) LoadModule: "glx"
[    17.663] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    19.691] (II) Module glx: vendor="NVIDIA Corporation"
[    19.691]    compiled for 4.0.2, module version = 1.0.0
[    19.691]    Module class: X.Org Server Extension
[    19.691] (II) NVIDIA GLX Module  173.14.30  Sat Apr 16 22:45:09 PDT 2011
[    19.691] (II) Loading extension GLX
[    19.691] (II) LoadModule: "record"
[    19.691] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    19.733] (II) Module record: vendor="X.Org Foundation"
[    19.733]    compiled for 1.10.1, module version = 1.13.0
[    19.733]    Module class: X.Org Server Extension
[    19.733]    ABI class: X.Org Server Extension, version 5.0
[    19.733] (II) Loading extension RECORD
[    19.733] (II) LoadModule: "dri"
[    19.734] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    19.753] (II) Module dri: vendor="X.Org Foundation"
[    19.753]    compiled for 1.10.1, module version = 1.0.0
[    19.753]    ABI class: X.Org Server Extension, version 5.0
[    19.753] (II) Loading extension XFree86-DRI
[    19.753] (II) LoadModule: "dri2"
[    19.754] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    19.764] (II) Module dri2: vendor="X.Org Foundation"
[    19.764]    compiled for 1.10.1, module version = 1.2.0
[    19.764]    ABI class: X.Org Server Extension, version 5.0
[    19.764] (II) Loading extension DRI2
[    19.764] (==) Matched nvidia as autoconfigured driver 0
[    19.764] (==) Matched nouveau as autoconfigured driver 1
[    19.764] (==) Matched nv as autoconfigured driver 2
[    19.764] (==) Matched vesa as autoconfigured driver 3
[    19.764] (==) Matched fbdev as autoconfigured driver 4
[    19.764] (==) Assigned the driver to the xf86ConfigLayout
[    19.764] (II) LoadModule: "nvidia"
[    19.764] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    20.097] (II) Module nvidia: vendor="NVIDIA Corporation"
[    20.097]    compiled for 4.0.2, module version = 1.0.0
[    20.097]    Module class: X.Org Video Driver
[    20.189] (II) LoadModule: "nouveau"
[    20.216] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    20.366] (II) Module nouveau: vendor="X.Org Foundation"
[    20.366]    compiled for 1.10.0, module version = 0.0.16
[    20.366]    Module class: X.Org Video Driver
[    20.366]    ABI class: X.Org Video Driver, version 10.0
[    20.366] (II) LoadModule: "nv"
[    20.374] (WW) Warning, couldn't open module nv
[    20.374] (II) UnloadModule: "nv"
[    20.374] (II) Unloading nv
[    20.374] (EE) Failed to load module "nv" (module does not exist, 0)
[    20.374] (II) LoadModule: "vesa"
[    20.375] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    20.385] (II) Module vesa: vendor="X.Org Foundation"
[    20.385]    compiled for 1.10.0, module version = 2.3.0
[    20.385]    Module class: X.Org Video Driver
[    20.385]    ABI class: X.Org Video Driver, version 10.0
[    20.385] (II) LoadModule: "fbdev"
[    20.385] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    20.389] (II) Module fbdev: vendor="X.Org Foundation"
[    20.389]    compiled for 1.10.0, module version = 0.4.2
[    20.389]    ABI class: X.Org Video Driver, version 10.0
[    20.413] (II) NVIDIA dlloader X Driver  173.14.30  Sat Apr 16 22:18:29 PDT 2011
[    20.421] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    20.421] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    20.421] (II) NOUVEAU driver for NVIDIA chipset families :
[    20.421]    RIVA TNT    (NV04)
[    20.421]    RIVA TNT2   (NV05)
[    20.421]    GeForce 256 (NV10)
[    20.421]    GeForce 2   (NV11, NV15)
[    20.421]    GeForce 4MX (NV17, NV18)
[    20.421]    GeForce 3   (NV20)
[    20.421]    GeForce 4Ti (NV25, NV28)
[    20.421]    GeForce FX  (NV3x)
[    20.421]    GeForce 6   (NV4x)
[    20.421]    GeForce 7   (G7x)
[    20.421]    GeForce 8   (G8x)
[    20.421] (II) VESA: driver for VESA chipsets: vesa
[    20.421] (II) FBDEV: driver for framebuffer: fbdev
[    20.421] (++) using VT number 7

[    20.433] (II) Loading sub module "fb"
[    20.433] (II) LoadModule: "fb"
[    20.433] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.463] (II) Module fb: vendor="X.Org Foundation"
[    20.463]    compiled for 1.10.1, module version = 1.0.0
[    20.463]    ABI class: X.Org ANSI C Emulation, version 0.4
[    20.463] (II) Loading sub module "wfb"
[    20.463] (II) LoadModule: "wfb"
[    20.463] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    20.472] (II) Module wfb: vendor="X.Org Foundation"
[    20.472]    compiled for 1.10.1, module version = 1.0.0
[    20.472]    ABI class: X.Org ANSI C Emulation, version 0.4
[    20.473] (II) Loading sub module "ramdac"
[    20.473] (II) LoadModule: "ramdac"
[    20.473] (II) Module "ramdac" already built-in
[    20.473] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    20.473] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    20.473] (II) Loading /usr/lib/xorg/modules/libfb.so
[    20.473] (WW) Falling back to old probe method for vesa
[    20.473] (WW) Falling back to old probe method for fbdev
[    20.473] (II) Loading sub module "fbdevhw"
[    20.473] (II) LoadModule: "fbdevhw"
[    20.473] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    20.474] (II) Module fbdevhw: vendor="X.Org Foundation"
[    20.474]    compiled for 1.10.1, module version = 0.0.2
[    20.474]    ABI class: X.Org Video Driver, version 10.0
[    20.474] (EE) open /dev/fb0: No such file or directory
[    20.500] (II) NVIDIA(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[    20.500] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    20.500] (==) NVIDIA(0): RGB weight 888
[    20.500] (==) NVIDIA(0): Default visual is TrueColor
[    20.500] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    20.500] (**) NVIDIA(0): Option "NoLogo" "True"
[    20.551] (**) NVIDIA(0): Enabling RENDER acceleration
[    20.551] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    20.551] (II) NVIDIA(0):     enabled.
[    22.966] (II) NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:2:0:0 (GPU-0)
[    22.966] (--) NVIDIA(0): Memory: 524288 kBytes
[    22.966] (--) NVIDIA(0): VideoBIOS: 62.98.29.00.42
[    22.966] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    22.966] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.966] (--) NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:2:0:0:
[    22.966] (--) NVIDIA(0):     Philips FTV (DFP-0)
[    22.966] (--) NVIDIA(0): Philips FTV (DFP-0): 330.0 MHz maximum pixel clock
[    22.966] (--) NVIDIA(0): Philips FTV (DFP-0): Internal Dual Link TMDS
[    23.337] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.337] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    23.337] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    23.337] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    23.337] (WW) NVIDIA(0):     check for mode "1920x1080".
[    23.337] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.337] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    23.337] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    23.337] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    23.337] (WW) NVIDIA(0):     check for mode "1920x1080".
[    23.337] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.337] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    23.337] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    23.337] (WW) NVIDIA(0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
[    23.337] (WW) NVIDIA(0):     check for mode "1920x1080".
[    23.337] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.337] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    23.337] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    23.337] (WW) NVIDIA(0):     this mode's VertRefresh (25.0 Hz); ignoring VertRefresh
[    23.337] (WW) NVIDIA(0):     check for mode "1920x1080".
[    23.337] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.337] (WW) NVIDIA(0):     "1600x1200" is specified in the EDID; however, the EDID's
[    23.337] (WW) NVIDIA(0):     valid HorizSync range (15.000-70.000 kHz) would exclude
[    23.337] (WW) NVIDIA(0):     this mode's HorizSync (75.0 kHz); ignoring HorizSync check
[    23.337] (WW) NVIDIA(0):     for mode "1600x1200".
[    23.337] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.337] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    23.337] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    23.337] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    23.337] (WW) NVIDIA(0):     check for mode "1920x1080".
[    23.338] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.338] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    23.338] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    23.338] (WW) NVIDIA(0):     this mode's VertRefresh (24.0 Hz); ignoring VertRefresh
[    23.338] (WW) NVIDIA(0):     check for mode "1920x1080".
[    23.338] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.338] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    23.338] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    23.338] (WW) NVIDIA(0):     this mode's VertRefresh (30.0 Hz); ignoring VertRefresh
[    23.338] (WW) NVIDIA(0):     check for mode "1920x1080".
[    23.339] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.339] (WW) NVIDIA(0):     "1920x1080" is specified in the EDID; however, the EDID's
[    23.339] (WW) NVIDIA(0):     valid VertRefresh range (48.000-62.000 Hz) would exclude
[    23.339] (WW) NVIDIA(0):     this mode's VertRefresh (25.0 Hz); ignoring VertRefresh
[    23.339] (WW) NVIDIA(0):     check for mode "1920x1080".
[    23.342] (WW) NVIDIA(0): The EDID for Philips FTV (DFP-0) contradicts itself: mode
[    23.342] (WW) NVIDIA(0):     "1600x1200" is specified in the EDID; however, the EDID's
[    23.342] (WW) NVIDIA(0):     valid HorizSync range (15.000-70.000 kHz) would exclude
[    23.342] (WW) NVIDIA(0):     this mode's HorizSync (75.0 kHz); ignoring HorizSync check
[    23.342] (WW) NVIDIA(0):     for mode "1600x1200".
[    23.352] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    23.352] (==) NVIDIA(0): 
[    23.352] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    23.352] (==) NVIDIA(0):     will be used as the requested mode.
[    23.352] (==) NVIDIA(0): 
[    23.352] (II) NVIDIA(0): Validated modes:
[    23.352] (II) NVIDIA(0):     "nvidia-auto-select"
[    23.352] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    23.382] (--) NVIDIA(0): DPI set to (38, 38); computed from "UseEdidDpi" X config
[    23.382] (--) NVIDIA(0):     option
[    23.382] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    23.417] (II) UnloadModule: "nouveau"
[    23.417] (II) Unloading nouveau
[    23.417] (II) UnloadModule: "vesa"
[    23.417] (II) Unloading vesa
[    23.417] (II) UnloadModule: "fbdev"
[    23.417] (II) Unloading fbdev
[    23.417] (II) UnloadModule: "fbdevhw"
[    23.417] (II) Unloading fbdevhw
[    23.417] (--) Depth 24 pixmap format is 32 bpp
[    23.420] (II) NVIDIA(0): Initialized GPU GART.
[    23.424] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    23.459] (II) Loading extension NV-GLX
[    23.652] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    23.702] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    23.702] (==) NVIDIA(0): Backing store disabled
[    23.702] (==) NVIDIA(0): Silken mouse enabled
[    23.708] (==) NVIDIA(0): DPMS enabled
[    23.720] (II) Loading extension NV-CONTROL
[    23.720] (==) RandR enabled
[    23.720] (II) Initializing built-in extension Generic Event Extension
[    23.720] (II) Initializing built-in extension SHAPE
[    23.720] (II) Initializing built-in extension MIT-SHM
[    23.720] (II) Initializing built-in extension XInputExtension
[    23.720] (II) Initializing built-in extension XTEST
[    23.720] (II) Initializing built-in extension BIG-REQUESTS
[    23.720] (II) Initializing built-in extension SYNC
[    23.720] (II) Initializing built-in extension XKEYBOARD
[    23.720] (II) Initializing built-in extension XC-MISC
[    23.720] (II) Initializing built-in extension SECURITY
[    23.720] (II) Initializing built-in extension XINERAMA
[    23.720] (II) Initializing built-in extension XFIXES
[    23.720] (II) Initializing built-in extension RENDER
[    23.720] (II) Initializing built-in extension RANDR
[    23.720] (II) Initializing built-in extension COMPOSITE
[    23.720] (II) Initializing built-in extension DAMAGE
[    23.720] (II) Initializing built-in extension GESTURE
[    23.723] (II) Initializing extension GLX
[    24.234] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    24.343] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    24.344] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.344] (II) LoadModule: "evdev"
[    24.344] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.469] (II) Module evdev: vendor="X.Org Foundation"
[    24.469]    compiled for 1.10.0.902, module version = 2.6.0
[    24.469]    Module class: X.Org XInput Driver
[    24.469]    ABI class: X.Org XInput driver, version 12.3
[    24.469] (II) Using input driver 'evdev' for 'Power Button'
[    24.469] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.469] (**) Power Button: always reports core events
[    24.469] (**) Power Button: Device: "/dev/input/event1"
[    24.510] (--) Power Button: Found keys
[    24.510] (II) Power Button: Configuring as keyboard
[    24.510] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    24.510] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.510] (**) Option "xkb_rules" "evdev"
[    24.510] (**) Option "xkb_model" "pc105"
[    24.510] (**) Option "xkb_layout" "dk"
[    24.513] (II) XKB: reuse xkmfile /var/lib/xkb/server-709407198873F5BF4583E7D562E34285659E3DFF.xkm
[    24.621] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    24.621] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    24.621] (II) Using input driver 'evdev' for 'Power Button'
[    24.621] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.621] (**) Power Button: always reports core events
[    24.621] (**) Power Button: Device: "/dev/input/event0"
[    24.670] (--) Power Button: Found keys
[    24.670] (II) Power Button: Configuring as keyboard
[    24.670] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    24.670] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    24.670] (**) Option "xkb_rules" "evdev"
[    24.670] (**) Option "xkb_model" "pc105"
[    24.670] (**) Option "xkb_layout" "dk"
[    24.674] (II) config/udev: Adding input device iMON Panel, Knob and Mouse(15c2:ffdc) (/dev/input/event6)
[    24.674] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Applying InputClass "evdev pointer catchall"
[    24.674] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Applying InputClass "evdev keyboard catchall"
[    24.674] (II) Using input driver 'evdev' for 'iMON Panel, Knob and Mouse(15c2:ffdc)'
[    24.674] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.674] (**) iMON Panel, Knob and Mouse(15c2:ffdc): always reports core events
[    24.674] (**) iMON Panel, Knob and Mouse(15c2:ffdc): Device: "/dev/input/event6"
[    24.710] (--) iMON Panel, Knob and Mouse(15c2:ffdc): Found 3 mouse buttons
[    24.710] (--) iMON Panel, Knob and Mouse(15c2:ffdc): Found scroll wheel(s)
[    24.710] (--) iMON Panel, Knob and Mouse(15c2:ffdc): Found relative axes
[    24.710] (--) iMON Panel, Knob and Mouse(15c2:ffdc): Found x and y relative axes
[    24.710] (--) iMON Panel, Knob and Mouse(15c2:ffdc): Found keys
[    24.710] (II) iMON Panel, Knob and Mouse(15c2:ffdc): Configuring as mouse
[    24.710] (II) iMON Panel, Knob and Mouse(15c2:ffdc): Configuring as keyboard
[    24.710] (II) iMON Panel, Knob and Mouse(15c2:ffdc): Adding scrollwheel support
[    24.710] (**) iMON Panel, Knob and Mouse(15c2:ffdc): YAxisMapping: buttons 4 and 5
[    24.710] (**) iMON Panel, Knob and Mouse(15c2:ffdc): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.710] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input6/event6"
[    24.710] (II) XINPUT: Adding extended input device "iMON Panel, Knob and Mouse(15c2:ffdc)" (type: KEYBOARD)
[    24.710] (**) Option "xkb_rules" "evdev"
[    24.710] (**) Option "xkb_model" "pc105"
[    24.710] (**) Option "xkb_layout" "dk"
[    24.710] (II) iMON Panel, Knob and Mouse(15c2:ffdc): initialized for relative axes.
[    24.711] (**) iMON Panel, Knob and Mouse(15c2:ffdc): (accel) keeping acceleration scheme 1
[    24.711] (**) iMON Panel, Knob and Mouse(15c2:ffdc): (accel) acceleration profile 0
[    24.711] (**) iMON Panel, Knob and Mouse(15c2:ffdc): (accel) acceleration factor: 2.000
[    24.711] (**) iMON Panel, Knob and Mouse(15c2:ffdc): (accel) acceleration threshold: 4
[    24.711] (II) config/udev: Adding input device iMON Panel, Knob and Mouse(15c2:ffdc) (/dev/input/mouse1)
[    24.711] (II) No input driver/identifier specified (ignoring)
[    24.711] (II) config/udev: Adding input device iMON Remote (15c2:ffdc) (/dev/input/event7)
[    24.712] (**) iMON Remote (15c2:ffdc): Applying InputClass "evdev keyboard catchall"
[    24.712] (II) Using input driver 'evdev' for 'iMON Remote (15c2:ffdc)'
[    24.712] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.712] (**) iMON Remote (15c2:ffdc): always reports core events
[    24.712] (**) iMON Remote (15c2:ffdc): Device: "/dev/input/event7"
[    24.780] (--) iMON Remote (15c2:ffdc): Found 3 mouse buttons
[    24.780] (--) iMON Remote (15c2:ffdc): Found keys
[    24.780] (II) iMON Remote (15c2:ffdc): Configuring as mouse
[    24.780] (II) iMON Remote (15c2:ffdc): Configuring as keyboard
[    24.780] (**) iMON Remote (15c2:ffdc): YAxisMapping: buttons 4 and 5
[    24.780] (**) iMON Remote (15c2:ffdc): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.780] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/rc/rc0/input7/event7"
[    24.780] (II) XINPUT: Adding extended input device "iMON Remote (15c2:ffdc)" (type: KEYBOARD)
[    24.780] (**) Option "xkb_rules" "evdev"
[    24.780] (**) Option "xkb_model" "pc105"
[    24.780] (**) Option "xkb_layout" "dk"
[    24.782] (II) config/udev: Adding input device VISENTA V1  (/dev/input/event2)
[    24.782] (**) VISENTA V1 : Applying InputClass "evdev keyboard catchall"
[    24.782] (II) Using input driver 'evdev' for 'VISENTA V1 '
[    24.782] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.782] (**) VISENTA V1 : always reports core events
[    24.782] (**) VISENTA V1 : Device: "/dev/input/event2"
[    24.820] (--) VISENTA V1 : Found keys
[    24.820] (II) VISENTA V1 : Configuring as keyboard
[    24.820] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.0/input/input2/event2"
[    24.820] (II) XINPUT: Adding extended input device "VISENTA V1 " (type: KEYBOARD)
[    24.820] (**) Option "xkb_rules" "evdev"
[    24.820] (**) Option "xkb_model" "pc105"
[    24.820] (**) Option "xkb_layout" "dk"
[    24.821] (II) config/udev: Adding input device VISENTA V1  (/dev/input/event3)
[    24.821] (**) VISENTA V1 : Applying InputClass "evdev pointer catchall"
[    24.821] (**) VISENTA V1 : Applying InputClass "evdev keyboard catchall"
[    24.821] (II) Using input driver 'evdev' for 'VISENTA V1 '
[    24.821] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.821] (**) VISENTA V1 : always reports core events
[    24.821] (**) VISENTA V1 : Device: "/dev/input/event3"
[    24.842] (--) VISENTA V1 : Found 3 mouse buttons
[    24.842] (--) VISENTA V1 : Found scroll wheel(s)
[    24.842] (--) VISENTA V1 : Found relative axes
[    24.842] (--) VISENTA V1 : Found x and y relative axes
[    24.842] (--) VISENTA V1 : Found absolute axes
[    24.842] (II) evdev-grail: failed to open grail, no gesture support
[    24.842] (--) VISENTA V1 : Found keys
[    24.842] (II) VISENTA V1 : Configuring as mouse
[    24.842] (II) VISENTA V1 : Configuring as keyboard
[    24.842] (II) VISENTA V1 : Adding scrollwheel support
[    24.842] (**) VISENTA V1 : YAxisMapping: buttons 4 and 5
[    24.842] (**) VISENTA V1 : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.842] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.4/usb6/6-1/6-1:1.1/input/input3/event3"
[    24.842] (II) XINPUT: Adding extended input device "VISENTA V1 " (type: KEYBOARD)
[    24.842] (**) Option "xkb_rules" "evdev"
[    24.842] (**) Option "xkb_model" "pc105"
[    24.842] (**) Option "xkb_layout" "dk"
[    24.842] (II) VISENTA V1 : initialized for relative axes.
[    24.842] (WW) VISENTA V1 : ignoring absolute axes.
[    24.843] (**) VISENTA V1 : (accel) keeping acceleration scheme 1
[    24.843] (**) VISENTA V1 : (accel) acceleration profile 0
[    24.843] (**) VISENTA V1 : (accel) acceleration factor: 2.000
[    24.843] (**) VISENTA V1 : (accel) acceleration threshold: 4
[    24.843] (II) config/udev: Adding input device VISENTA V1  (/dev/input/mouse0)
[    24.843] (II) No input driver/identifier specified (ignoring)
[    24.844] (II) config/udev: Adding input device CHICONY HP Basic USB Keyboard (/dev/input/event4)
[    24.844] (**) CHICONY HP Basic USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    24.844] (II) Using input driver 'evdev' for 'CHICONY HP Basic USB Keyboard'
[    24.844] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.844] (**) CHICONY HP Basic USB Keyboard: always reports core events
[    24.844] (**) CHICONY HP Basic USB Keyboard: Device: "/dev/input/event4"
[    24.880] (--) CHICONY HP Basic USB Keyboard: Found keys
[    24.880] (II) CHICONY HP Basic USB Keyboard: Configuring as keyboard
[    24.880] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.4/usb6/6-2/6-2:1.0/input/input4/event4"
[    24.880] (II) XINPUT: Adding extended input device "CHICONY HP Basic USB Keyboard" (type: KEYBOARD)
[    24.880] (**) Option "xkb_rules" "evdev"
[    24.880] (**) Option "xkb_model" "pc105"
[    24.880] (**) Option "xkb_layout" "dk"
[    24.888] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    24.888] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    24.888] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    24.888] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    24.889] (**) HP WMI hotkeys: always reports core events
[    24.889] (**) HP WMI hotkeys: Device: "/dev/input/event5"
[    24.890] (--) HP WMI hotkeys: Found keys
[    24.890] (II) HP WMI hotkeys: Configuring as keyboard
[    24.890] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    24.890] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    24.890] (**) Option "xkb_rules" "evdev"
[    24.890] (**) Option "xkb_model" "pc105"
[    24.890] (**) Option "xkb_layout" "dk"
[    40.542] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    40.857] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    41.074] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
```

---

### Post by papibe on 2011-05-27
Could you post your /etc/X11/xorg.conf ?

Regards.

---

### Post by inckiekage on 2011-05-28
```
kimse@mediacenter:~$ cat /etc/X11/xorg.conf 

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

```

---

### Post by papibe on 2011-05-28
Do you want to use the Nvidia driver? it's not properly used.

If so enable it in System -> Administration -> Hardware Drivers. Once it's installed, run:
```
$ gksudo nvidia-settings
```
There you can configure your monitors. When you have anything up and running as you want, save your settings by pressing "Save to X Configuration File". Reboot to see if every was saved properly.

Regards.

---

### Post by inckiekage on 2011-05-28
How do i apply settings that applies to my LCD TV, when i have to connect a regular LCD computer monitor, to get a picture?

---

### Post by papibe on 2011-05-28
To configure a monitor/TV it has to be connected, so nvidia-settings can read its attributes and make the proper configuration.

Did I answer your question?

Regards.

---

### Post by inckiekage on 2011-05-28
as i also stated in my post, i can only have one monitor connected at a time, since i only has one VGA output in my computer.

i managing the computer sing a SSH connection, i need some commands ;-), no GUI tools.

---

