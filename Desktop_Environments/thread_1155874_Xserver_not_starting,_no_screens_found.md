---
title: "Xserver not starting, no screens found"
date: 2009-05-11
forum: Desktop Environments
---

### Post by jfmanamtr on 2009-05-11
I just downloaded & burned Ubuntu Studio 9.04 yesterday & did an install over my copy of Vista Ultimate. The install seemed to go smoothly & finished without any errors. After I did the reboot, gdm would not start. It tells me that there were fatal errors & that no screens were found. I am not at home to post the error log or my xorg.conf file (which was blank after the initial install). The computer specs are:

Asus P5GC-MX motherboard
3.0 GHx PentiumD 
2x 1GB DDR2 667
Nvidia GeForce 8500 GT

I will post anything you need to help me out. Thanks for all your help in advance.

~John

---

### Post by micio on 2009-05-11
Can you post the xorg.conf and /var/log/Xorg.0.log ?

Have you already installed the nvidia driver?
If yes, what kind of installation you did? from debs (using apt or synaptic) or .run file provided by Nvidia.com?

---

### Post by jfmanamtr on 2009-05-11
> Have you already installed the nvidia driver?
If yes, what kind of installation you did? from debs (using apt or synaptic) or .run file provided by Nvidia.com?

I guess I was under the impression that the drivers for the card would be there when I installed the OS. You will have to forgive my ignorance & note that I am used to Windows (thank goodness that I found a better OS!). How do I install the Nvidia drivers?

~John

---

### Post by micio on 2009-05-11
using debs:

sudo apt-get install nvidia-glx   

(simplest way for new user :) )

---

### Post by jfmanamtr on 2009-05-11
Sweet. I will give that a shot when I get home. I will post if I have anymore issues after that. 

~John

---

### Post by jfmanamtr on 2009-05-11
Ok. So I tried the apt-get install nvidia-glx. I still couldn't get the Nvidia GeForce 8500 GS working. It still told me no screens found. So, I swapped out the GeForce 8500 GS for a GeForce 7300 GTS, & well, here I am. I guess GNOME hates the GeForce 8500. Oh well, I am just happy the thing runs. Thanks for all the help!

~John:lolflag:

---

### Post by micio on 2009-05-11
Excuse me dear, but i can't understand why you want use this video card insted of 8500.:confused::confused:
Coursly it must work. If you want use the better videocard, try to post /etc/X11/xorg.conf and /var/log/Xorg.0.log and we may can help you.
Otherwise, if you feel good also without the newest video card, no problem we are happy too :)

cheers,

Micio! :popcorn:

---

### Post by jfmanamtr on 2009-05-11
I do want the better graphics card. I was just happy to have the thing working. Here are the files from when I had the 8500 GT in this desktop:

/var/log/Xorg.0.lof:
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux media-pc 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May 11 20:55:04 2009
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

(--) PCI:*(0@4:0:0) nVidia Corporation G71 [GeForce 7300 GS] rev 161, Mem @ 0xdd000000/16777216, 0xe0000000/268435456, 0xdc000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 04@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GS (G72) at PCI:4:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.31.6a
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GS at PCI:4:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: TV-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
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
(II) Initializing extension GLX
(II) config/hal: Adding input device Logitech USB Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 9 mouse buttons
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
(**) Logitech USB Receiver: (accel) filter chain progression: 2.00
(**) Logitech USB Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Receiver: (accel) set acceleration profile 0
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
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Logitech USB Receiver: xkb_layout: "us"
(II) NVIDIA(0): Setting mode "800x600"
```

And /etc/X11/xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```

I hope they give you a clue as too what is preventing my card from working. 

~John

---

### Post by micio on 2009-05-12
ehm.. are you sure that is the correct file? :KS

```
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GS (G72) at PCI:4:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.31.6a
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GS at PCI:4:0:0:

```

Here it speaks about a 7300GS :P

---

### Post by jfmanamtr on 2009-05-12
Ok. So, I may have posted the wrong logs. Sorry about that :oops:. I put the 8500 GT back into my machine so that I could get you the correct logs. When I started up the PC, X Windows seems to have started up without errors :confused:. The only issue that I am having now is that the screen isn't the right size. I have the resolution set to 1024x768, but it isn't fitting it to my TV screen. The top bar is off the viewable screen. I have tried to use the Nvidia X Server settings to adjust the screen size, but it is still not displaying the screen correctly. I am not sure what is going on. Any ideas?

~John

---

### Post by jfmanamtr on 2009-05-12
bump

---

### Post by jfmanamtr on 2009-05-12
Ok. So, that seems to have just been temporary. I was having troubles with GNOME freezing. So, I tried to remove the nvidia-glx-180 driver package, to reinstall it & see if that cleared it up. Xwindows crashed & caused me to have to hard boot the PC. Now it is back to not loading the Xserver on boot. I also seemed to have meesed up apt-get as well (it was crashing the computer) & it will not uninstall or install anything. . So, here are the Xorg.0.log & Dmesg off a fresh install. The file /etc/X11/xorg.conf is completely empty, so I won't post it.
 
/var/log/Xorg.0.log
```
 
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux media-pc 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009 i686
Build Date: 09 April 2009 02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 12 21:32:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section. Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) | |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
Using a default monitor configuration.
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
(--) PCI:*(0@4:0:0) nVidia Corporation GeForce 8500 GT rev 161, Mem @ 0xdd000000/16777216, 0xe0000000/268435456, 0xda000000/33554432, I/O @ 0x0000e800/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
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
(II) Module glx: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.Org Server Extension
(II) NVIDIA GLX Module 180.44 Mon Mar 23 15:29:02 PST 2009
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
(II) Primary Device is: PCI 04@00:00:0
(--) NV: Found NVIDIA GeForce 8500 GT at 04@00:00:0
(II) resource ranges after probing:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[5] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
compiled for 1.6.0, module version = 1.0.0
ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(II) NV(0): Creating default Display subsection in Screen section
"Default Screen Section" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0xb582a000
(--) NV(0): Total video RAM: 512.0 MB
(--) NV(0): BAR1 size: 256.0 MB
(--) NV(0): Mapped memory: 256.0 MB
(II) NV(0): Linear framebuffer mapped at 0xa582a000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) NV(0): Connector map:
(--) NV(0): Bus 0 -> DAC1
(--) NV(0): Bus 0 -> SOR0
(--) NV(0): Bus 1 -> DAC2
(--) NV(0): Load detection: 340
(II) NV(0): I2C bus "I2C0" initialized.
(II) NV(0): Output VGA1 has no monitor section
(II) NV(0): Output DVI0 has no monitor section
(II) NV(0): I2C bus "I2C1" initialized.
(II) NV(0): Output VGA2 has no monitor section
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0): I2C device "I2C1:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "I2C1:ddc2" registered at address 0xA0.
(II) NV(0): ... none found
(--) NV(0): Trying load detection on VGA2 ... nothing.
(II) NV(0): Output VGA1 disconnected
(II) NV(0): Output DVI0 disconnected
(II) NV(0): Output VGA2 disconnected
(WW) NV(0): No outputs definitely connected, trying again...
(II) NV(0): Output VGA1 disconnected
(II) NV(0): Output DVI0 disconnected
(II) NV(0): Output VGA2 disconnected
(WW) NV(0): Unable to find initial modes
(EE) NV(0): No valid initial configuration found
(II) UnloadModule: "nv"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found
Please consult the The X.Org Foundation support 
at http://wiki.x.org
for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
ddxSigGiveUp: Closing log

```
 
/var/log/dmesg
```

[ 0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.28-3-rt (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009 (Ubuntu 2.6.28-3.12-rt)
[ 0.000000] KERNEL supported cpus:
[ 0.000000] Intel GenuineIntel
[ 0.000000] AMD AuthenticAMD
[ 0.000000] NSC Geode by NSC
[ 0.000000] Cyrix CyrixInstead
[ 0.000000] Centaur CentaurHauls
[ 0.000000] Transmeta GenuineTMx86
[ 0.000000] Transmeta TransmetaCPU
[ 0.000000] UMC UMC UMC UMC
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[ 0.000000] BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007ffa0000 (usable)
[ 0.000000] BIOS-e820: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[ 0.000000] BIOS-e820: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[ 0.000000] DMI 2.4 present.
[ 0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[ 0.000000] last_pfn = 0x7ffa0 max_arch_pfn = 0x100000
[ 0.000000] Scanning 0 areas for low memory corruption
[ 0.000000] modified physical RAM map:
[ 0.000000] modified: 0000000000000000 - 0000000000010000 (reserved)
[ 0.000000] modified: 0000000000010000 - 000000000009fc00 (usable)
[ 0.000000] modified: 000000000009fc00 - 00000000000a0000 (reserved)
[ 0.000000] modified: 00000000000e4000 - 0000000000100000 (reserved)
[ 0.000000] modified: 0000000000100000 - 000000007ffa0000 (usable)
[ 0.000000] modified: 000000007ffa0000 - 000000007ffae000 (ACPI data)
[ 0.000000] modified: 000000007ffae000 - 000000007ffe0000 (ACPI NVS)
[ 0.000000] modified: 000000007ffe0000 - 0000000080000000 (reserved)
[ 0.000000] modified: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] modified: 00000000fff80000 - 0000000100000000 (reserved)
[ 0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[ 0.000000] RAMDISK: 3789d000 - 37fefff5
[ 0.000000] Allocated new RAMDISK: 008e4000 - 01036ff5
[ 0.000000] Move RAMDISK from 000000003789d000 - 0000000037fefff4 to 008e4000 - 01036ff4
[ 0.000000] ACPI: RSDP 000FB030, 0024 (r2 ACPIAM)
[ 0.000000] ACPI: XSDT 7FFA0100, 0054 (r1 _ASUS_ Notebook 12000704 MSFT 97)
[ 0.000000] ACPI: FACP 7FFA0290, 00F4 (r3 A_M_I_ OEMFACP 12000704 MSFT 97)
[ 0.000000] ACPI: DSDT 7FFA05C0, 6941 (r1 A0798 A0798000 0 INTL 20051117)
[ 0.000000] ACPI: FACS 7FFAE000, 0040
[ 0.000000] ACPI: APIC 7FFA0390, 006C (r1 A_M_I_ OEMAPIC 12000704 MSFT 97)
[ 0.000000] ACPI: MCFG 7FFA0400, 003C (r1 A_M_I_ OEMMCFG 12000704 MSFT 97)
[ 0.000000] ACPI: SLIC 7FFA0440, 0176 (r1 _ASUS_ Notebook 12000704 MSFT 97)
[ 0.000000] ACPI: OEMB 7FFAE040, 0080 (r1 A_M_I_ AMI_OEM 12000704 MSFT 97)
[ 0.000000] ACPI: HPET 7FFA6F10, 0038 (r1 A_M_I_ OEMHPET 12000704 MSFT 97)
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] 1163MB HIGHMEM available.
[ 0.000000] 883MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 373fe000
[ 0.000000] low ram: 00000000 - 373fe000
[ 0.000000] bootmap 00012000 - 00018e80
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 00008df3cc] TEXT DATA BSS ==> [0000100000 - 00008df3cc]
[ 0.000000] #4 [00008e0000 - 00008e4000] INIT_PG_TABLE ==> [00008e0000 - 00008e4000]
[ 0.000000] #5 [000009fc00 - 0000100000] BIOS reserved ==> [000009fc00 - 0000100000]
[ 0.000000] #6 [0000010000 - 0000012000] PGTABLE ==> [0000010000 - 0000012000]
[ 0.000000] #7 [00008e4000 - 0001036ff5] NEW RAMDISK ==> [00008e4000 - 0001036ff5]
[ 0.000000] #8 [0000012000 - 0000019000] BOOTMAP ==> [0000012000 - 0000019000]
[ 0.000000] found SMP MP-table at [c00ff780] 000ff780
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000010 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x000373fe
[ 0.000000] HighMem 0x000373fe -> 0x0007ffa0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000010 -> 0x0000009f
[ 0.000000] 0: 0x00000100 -> 0x0007ffa0
[ 0.000000] On node 0 totalpages: 524079
[ 0.000000] free_area_init_node: node 0, pgdat c06e7300, node_mem_map c1037340
[ 0.000000] DMA zone: 52 pages used for memmap
[ 0.000000] DMA zone: 0 pages reserved
[ 0.000000] DMA zone: 3931 pages, LIFO batch:0
[ 0.000000] Normal zone: 2821 pages used for memmap
[ 0.000000] Normal zone: 219385 pages, LIFO batch:31
[ 0.000000] HighMem zone: 3782 pages used for memmap
[ 0.000000] HighMem zone: 294108 pages, LIFO batch:31
[ 0.000000] Movable zone: 0 pages used for memmap
[ 0.000000] ACPI: PM-Timer IO Port: 0x808
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[ 0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[ 0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[ 0.000000] ACPI: IRQ0 used by override.
[ 0.000000] ACPI: IRQ2 used by override.
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[ 0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ee00000)
[ 0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[ 0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 517424
[ 0.000000] Kernel command line: root=UUID=d90e86c8-a728-4033-b86f-1d959c579eac ro quiet splash 
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] Preemptible RCU implementation.
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] Fast TSC calibration using PIT
[ 0.000000] Detected 2999.925 MHz processor.
[ 0.000999] Console: colour VGA+ 80x25
[ 0.000999] console [tty0] enabled
[ 0.000999] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.000999] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.000999] allocated 10483520 bytes of page_cgroup
[ 0.000999] please try cgroup_disable=memory option if you don't want
[ 0.000999] Scanning for low memory corruption every 60 seconds
[ 0.000999] Memory: 2041872k/2096768k available (4187k kernel code, 53552k reserved, 2546k data, 512k init, 1191560k highmem)
[ 0.000999] virtual kernel memory layout:
[ 0.000999] fixmap : 0xffc77000 - 0xfffff000 (3616 kB)
[ 0.000999] pkmap : 0xff400000 - 0xff800000 (4096 kB)
[ 0.000999] vmalloc : 0xf7bfe000 - 0xff3fe000 ( 120 MB)
[ 0.000999] lowmem : 0xc0000000 - 0xf73fe000 ( 883 MB)
[ 0.000999] .init : 0xc079a000 - 0xc081a000 ( 512 kB)
[ 0.000999] .data : 0xc0516e69 - 0xc07938e0 (2546 kB)
[ 0.000999] .text : 0xc0100000 - 0xc0516e69 (4187 kB)
[ 0.000999] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.000999] hpet clockevent registered
[ 0.000999] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[ 0.000999] Calibrating delay loop (skipped), value calculated using timer frequency.. 5999.85 BogoMIPS (lpj=2999925)
[ 0.000999] Security Framework initialized
[ 0.000999] SELinux: Disabled at boot.
[ 0.000999] AppArmor: AppArmor initialized
[ 0.000999] Mount-cache hash table entries: 512
[ 0.000999] Initializing cgroup subsys ns
[ 0.000999] Initializing cgroup subsys cpuacct
[ 0.000999] Initializing cgroup subsys memory
[ 0.000999] Initializing cgroup subsys freezer
[ 0.000999] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 0.000999] CPU: L2 cache: 2048K
[ 0.000999] CPU: Physical Processor ID: 0
[ 0.000999] CPU: Processor Core ID: 0
[ 0.000999] using mwait in idle threads.
[ 0.000999] Checking 'hlt' instruction... OK.
[ 0.005003] ACPI: Core revision 20080926
[ 0.009429] ACPI: Checking initramfs for custom DSDT
[ 0.319418] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[ 0.329647] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 02
[ 0.331300] Booting processor 1 APIC 0x1 ip 0x6000
[ 0.330990] Initializing CPU#1
[ 0.330990] Calibrating delay using timer specific routine.. 5999.68 BogoMIPS (lpj=2999840)
[ 0.330990] CPU: Trace cache: 12K uops, L1 D cache: 16K
[ 0.330990] CPU: L2 cache: 2048K
[ 0.330990] CPU: Physical Processor ID: 0
[ 0.330990] CPU: Processor Core ID: 1
[ 0.402524] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 02
[ 0.402544] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[ 0.403063] Brought up 2 CPUs
[ 0.403067] Total of 2 processors activated (11999.53 BogoMIPS).
[ 0.403119] CPU0 attaching sched-domain:
[ 0.403122] domain 0: span 0-1 level CPU
[ 0.403126] groups: 0 1
[ 0.403133] CPU1 attaching sched-domain:
[ 0.403136] domain 0: span 0-1 level CPU
[ 0.403139] groups: 1 0
[ 0.403297] net_namespace: 840 bytes
[ 0.403313] Booting paravirtualized kernel on bare hardware
[ 0.404257] Time: 1:32:03 Date: 05/13/09
[ 0.404257] regulator: core version 0.5
[ 0.404257] NET: Registered protocol family 16
[ 0.404304] EISA bus registered
[ 0.404316] ACPI: bus type pci registered
[ 0.404380] PCI: Found Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub without MMCONFIG support.
[ 0.405017] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=4
[ 0.405020] PCI: Using configuration type 1 for base access
[ 0.408050] ACPI: EC: Look up EC in DSDT
[ 0.420663] ACPI: Interpreter enabled
[ 0.420671] ACPI: (supports S0 S1 S3 S4 S5)
[ 0.420706] ACPI: Using IOAPIC for interrupt routing
[ 0.431527] ACPI: No dock devices found.
[ 0.431603] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.431726] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[ 0.431732] pci 0000:00:01.0: PME# disabled
[ 0.431807] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd9df8000-0xd9dfbfff]
[ 0.431842] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[ 0.431847] pci 0000:00:1b.0: PME# disabled
[ 0.431902] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[ 0.431907] pci 0000:00:1c.0: PME# disabled
[ 0.431963] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[ 0.431968] pci 0000:00:1c.1: PME# disabled
[ 0.432043] pci 0000:00:1d.0: reg 20 io port: [0x8000-0x801f]
[ 0.432100] pci 0000:00:1d.1: reg 20 io port: [0x8400-0x841f]
[ 0.432156] pci 0000:00:1d.2: reg 20 io port: [0x8800-0x881f]
[ 0.432211] pci 0000:00:1d.3: reg 20 io port: [0x9000-0x901f]
[ 0.432273] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd9dffc00-0xd9dfffff]
[ 0.432318] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[ 0.432323] pci 0000:00:1d.7: PME# disabled
[ 0.432456] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[ 0.432462] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[ 0.432496] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[ 0.432504] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[ 0.432512] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[ 0.432519] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[ 0.432527] pci 0000:00:1f.1: reg 20 io port: [0xffa0-0xffaf]
[ 0.432575] pci 0000:00:1f.2: reg 10 io port: [0xa800-0xa807]
[ 0.432582] pci 0000:00:1f.2: reg 14 io port: [0xa400-0xa403]
[ 0.432589] pci 0000:00:1f.2: reg 18 io port: [0xa000-0xa007]
[ 0.432596] pci 0000:00:1f.2: reg 1c io port: [0x9800-0x9803]
[ 0.432603] pci 0000:00:1f.2: reg 20 io port: [0x9400-0x940f]
[ 0.432624] pci 0000:00:1f.2: PME# supported from D3hot
[ 0.432629] pci 0000:00:1f.2: PME# disabled
[ 0.432681] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[ 0.432743] pci 0000:04:00.0: reg 10 32bit mmio: [0xdd000000-0xddffffff]
[ 0.432755] pci 0000:04:00.0: reg 14 64bit mmio: [0xe0000000-0xefffffff]
[ 0.432766] pci 0000:04:00.0: reg 1c 64bit mmio: [0xda000000-0xdbffffff]
[ 0.432773] pci 0000:04:00.0: reg 24 io port: [0xe800-0xe87f]
[ 0.432781] pci 0000:04:00.0: reg 30 32bit mmio: [0xdcfe0000-0xdcffffff]
[ 0.432836] pci 0000:00:01.0: bridge io port: [0xe000-0xefff]
[ 0.432841] pci 0000:00:01.0: bridge 32bit mmio: [0xda000000-0xddffffff]
[ 0.432847] pci 0000:00:01.0: bridge 64bit mmio pref: [0xe0000000-0xefffffff]
[ 0.432895] pci 0000:00:1c.0: bridge io port: [0xd000-0xdfff]
[ 0.432961] pci 0000:02:00.0: reg 10 64bit mmio: [0xd9fc0000-0xd9ffffff]
[ 0.433013] pci 0000:02:00.0: reg 30 32bit mmio: [0xd9fa0000-0xd9fbffff]
[ 0.433028] pci 0000:02:00.0: PME# supported from D3hot D3cold
[ 0.433034] pci 0000:02:00.0: PME# disabled
[ 0.433087] pci 0000:00:1c.1: bridge io port: [0xc000-0xcfff]
[ 0.433092] pci 0000:00:1c.1: bridge 32bit mmio: [0xd9f00000-0xd9ffffff]
[ 0.433145] pci 0000:01:01.0: reg 10 32bit mmio: [0xd9e00000-0xd9efffff]
[ 0.433154] pci 0000:01:01.0: reg 14 32bit mmio: [0xde000000-0xdfffffff]
[ 0.433245] pci 0000:00:1e.0: transparent bridge
[ 0.433250] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[ 0.433255] pci 0000:00:1e.0: bridge 32bit mmio: [0xd9e00000-0xd9efffff]
[ 0.433262] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xde000000-0xdfffffff]
[ 0.433284] bus 00 -> node 0
[ 0.433294] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.433652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[ 0.433805] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[ 0.434034] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[ 0.434185] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[ 0.437862] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[ 0.438054] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[ 0.438226] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[ 0.438396] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.438572] ACPI: PCI Interrupt Link [LNKE] (IRQs *3 4 5 6 7 10 11 12 14 15)
[ 0.438743] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[ 0.438915] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[ 0.439105] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[ 0.439371] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - CA, should be BD [20080926]
[ 0.439423] ACPI: WMI: Mapper loaded
[ 0.440219] SCSI subsystem initialized
[ 0.440242] libata version 3.00 loaded.
[ 0.440242] usbcore: registered new interface driver usbfs
[ 0.440242] usbcore: registered new interface driver hub
[ 0.440242] usbcore: registered new device driver usb
[ 0.440242] PCI: Using ACPI for IRQ routing
[ 0.446016] Bluetooth: Core ver 2.13
[ 0.446041] NET: Registered protocol family 31
[ 0.446041] Bluetooth: HCI device and connection manager initialized
[ 0.446041] Bluetooth: HCI socket layer initialized
[ 0.446042] NET: Registered protocol family 8
[ 0.446045] NET: Registered protocol family 20
[ 0.446061] NetLabel: Initializing
[ 0.446063] NetLabel: domain hash size = 128
[ 0.446065] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.446085] NetLabel: unlabeled traffic allowed by default
[ 0.446105] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[ 0.446112] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[ 0.448128] AppArmor: AppArmor Filesystem Enabled
[ 0.454598] pnp: PnP ACPI init
[ 0.454611] ACPI: bus type pnp registered
[ 0.461334] pnp: PnP ACPI: found 18 devices
[ 0.461337] ACPI: ACPI bus type pnp unregistered
[ 0.461342] PnPBIOS: Disabled by ACPI PNP
[ 0.461356] system 00:01: iomem range 0xfed13000-0xfed19fff has been reserved
[ 0.461368] system 00:08: ioport range 0x290-0x297 has been reserved
[ 0.461376] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[ 0.461381] system 00:09: ioport range 0x800-0x87f has been reserved
[ 0.461384] system 00:09: ioport range 0x480-0x4bf has been reserved
[ 0.461388] system 00:09: ioport range 0x900-0x91f has been reserved
[ 0.461391] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[ 0.461395] system 00:09: iomem range 0xfed20000-0xfed8ffff has been reserved
[ 0.461398] system 00:09: iomem range 0xffb00000-0xffbfffff has been reserved
[ 0.461402] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[ 0.461412] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[ 0.461416] system 00:0c: iomem range 0xfee00000-0xfee00fff has been reserved
[ 0.461426] system 00:0f: iomem range 0xffc00000-0xfff7ffff has been reserved
[ 0.461433] system 00:10: iomem range 0xf0000000-0xf3ffffff has been reserved
[ 0.461442] system 00:11: iomem range 0x0-0x9ffff could not be reserved
[ 0.461445] system 00:11: iomem range 0xc0000-0xdffff could not be reserved
[ 0.461449] system 00:11: iomem range 0xe0000-0xfffff could not be reserved
[ 0.461452] system 00:11: iomem range 0x100000-0x7fffffff could not be reserved
[ 0.496373] pci 0000:00:01.0: PCI bridge, secondary bus 0000:04
[ 0.496378] pci 0000:00:01.0: IO window: 0xe000-0xefff
[ 0.496384] pci 0000:00:01.0: MEM window: 0xda000000-0xddffffff
[ 0.496388] pci 0000:00:01.0: PREFETCH window: 0x000000e0000000-0x000000efffffff
[ 0.496395] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[ 0.496399] pci 0000:00:1c.0: IO window: 0xd000-0xdfff
[ 0.496404] pci 0000:00:1c.0: MEM window: disabled
[ 0.496409] pci 0000:00:1c.0: PREFETCH window: disabled
[ 0.496416] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[ 0.496420] pci 0000:00:1c.1: IO window: 0xc000-0xcfff
[ 0.496426] pci 0000:00:1c.1: MEM window: 0xd9f00000-0xd9ffffff
[ 0.496430] pci 0000:00:1c.1: PREFETCH window: disabled
[ 0.496438] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[ 0.496442] pci 0000:00:1e.0: IO window: 0xb000-0xbfff
[ 0.496448] pci 0000:00:1e.0: MEM window: 0xd9e00000-0xd9efffff
[ 0.496453] pci 0000:00:1e.0: PREFETCH window: 0x000000de000000-0x000000dfffffff
[ 0.496474] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 0.496481] pci 0000:00:01.0: setting latency timer to 64
[ 0.496490] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 0.496495] pci 0000:00:1c.0: setting latency timer to 64
[ 0.496506] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 0.496511] pci 0000:00:1c.1: setting latency timer to 64
[ 0.496519] pci 0000:00:1e.0: setting latency timer to 64
[ 0.496524] bus: 00 index 0 io port: [0x00-0xffff]
[ 0.496527] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[ 0.496530] bus: 04 index 0 io port: [0xe000-0xefff]
[ 0.496533] bus: 04 index 1 mmio: [0xda000000-0xddffffff]
[ 0.496535] bus: 04 index 2 mmio: [0xe0000000-0xefffffff]
[ 0.496538] bus: 04 index 3 mmio: [0x0-0x0]
[ 0.496541] bus: 03 index 0 io port: [0xd000-0xdfff]
[ 0.496543] bus: 03 index 1 mmio: [0x0-0x0]
[ 0.496545] bus: 03 index 2 mmio: [0x0-0x0]
[ 0.496547] bus: 03 index 3 mmio: [0x0-0x0]
[ 0.496550] bus: 02 index 0 io port: [0xc000-0xcfff]
[ 0.496553] bus: 02 index 1 mmio: [0xd9f00000-0xd9ffffff]
[ 0.496555] bus: 02 index 2 mmio: [0x0-0x0]
[ 0.496557] bus: 02 index 3 mmio: [0x0-0x0]
[ 0.496560] bus: 01 index 0 io port: [0xb000-0xbfff]
[ 0.496563] bus: 01 index 1 mmio: [0xd9e00000-0xd9efffff]
[ 0.496565] bus: 01 index 2 mmio: [0xde000000-0xdfffffff]
[ 0.496568] bus: 01 index 3 io port: [0x00-0xffff]
[ 0.496570] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[ 0.496608] NET: Registered protocol family 2
[ 0.500589] Switched to high resolution mode on CPU 1
[ 0.501003] Switched to high resolution mode on CPU 0
[ 0.514111] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.514544] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.514889] TCP bind hash table entries: 65536 (order: 9, 2097152 bytes)
[ 0.515822] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.515826] TCP reno registered
[ 0.521155] NET: Registered protocol family 1
[ 0.521331] checking if image is initramfs... it is
[ 1.166802] Freeing initrd memory: 7499k freed
[ 1.167000] cpufreq: No nForce2 chipset.
[ 1.167229] audit: initializing netlink socket (disabled)
[ 1.167247] type=2000 audit(1242178324.167:1): initialized
[ 1.170604] krcupreemptd setsched 0
[ 1.170608] prio = 98
[ 1.170875] highmem bounce pool size: 64 pages
[ 1.170883] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 1.171075] VFS: Disk quotas dquot_6.5.1
[ 1.171120] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1.171498] fuse init (API version 7.10)
[ 1.171547] msgmni has been set to 1677
[ 1.171750] alg: No test for stdrng (krng)
[ 1.171772] io scheduler noop registered
[ 1.171775] io scheduler anticipatory registered
[ 1.171778] io scheduler deadline registered
[ 1.171795] io scheduler cfq registered (default)
[ 1.171924] pci 0000:04:00.0: Boot video device
[ 1.176721] pcieport-driver 0000:00:01.0: setting latency timer to 64
[ 1.176764] pcieport-driver 0000:00:01.0: found MSI capability
[ 1.176794] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[ 1.176806] pci_express 0000:00:01.0:pcie00: allocate port service
[ 1.176876] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[ 1.176913] pcieport-driver 0000:00:1c.0: found MSI capability
[ 1.176941] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[ 1.176956] pci_express 0000:00:1c.0:pcie00: allocate port service
[ 1.176976] pci_express 0000:00:1c.0:pcie02: allocate port service
[ 1.177065] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[ 1.177101] pcieport-driver 0000:00:1c.1: found MSI capability
[ 1.177130] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[ 1.177146] pci_express 0000:00:1c.1:pcie00: allocate port service
[ 1.177239] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 1.177449] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[ 1.177624] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[ 1.177628] ACPI: Power Button (FF) [PWRF]
[ 1.177702] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[ 1.177706] ACPI: Power Button (CM) [PWRB]
[ 1.178677] processor ACPI_CPU:00: registered as cooling_device0
[ 1.179341] processor ACPI_CPU:01: registered as cooling_device1
[ 1.182519] isapnp: Scanning for PnP cards...
[ 1.537076] isapnp: No Plug & Play device found
[ 1.550302] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[ 1.550407] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.550932] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 1.552124] brd: module loaded
[ 1.552619] loop: module loaded
[ 1.552719] Fixed MDIO Bus: probed
[ 1.552725] PPP generic driver version 2.4.2
[ 1.552803] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[ 1.552843] Driver 'sd' needs updating - please use bus_type methods
[ 1.552857] Driver 'sr' needs updating - please use bus_type methods
[ 1.552951] ata_piix 0000:00:1f.1: version 2.12
[ 1.552966] ata_piix 0000:00:1f.1: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1.553028] ata_piix 0000:00:1f.1: setting latency timer to 64
[ 1.553231] scsi0 : ata_piix
[ 1.553350] scsi1 : ata_piix
[ 1.555760] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[ 1.555764] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[ 1.714369] ata1.00: ATA-5: WDC WD1000BB-00CAA1, 17.07W17, max UDMA/100
[ 1.714373] ata1.00: 195371568 sectors, multi 16: LBA 
[ 1.714419] ata1.01: ATAPI: HL-DT-ST DVDRAM GSA-H40N, RG01, max UDMA/66
[ 1.721328] ata1.00: configured for UDMA/100
[ 1.727458] ata1.01: configured for UDMA/66
[ 1.914134] scsi 0:0:0:0: Direct-Access ATA WDC WD1000BB-00C 17.0 PQ: 0 ANSI: 5
[ 1.914269] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[ 1.914293] sd 0:0:0:0: [sda] Write Protect is off
[ 1.914296] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.914335] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.914414] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors: (100 GB/93.1 GiB)
[ 1.914437] sd 0:0:0:0: [sda] Write Protect is off
[ 1.914441] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1.914478] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1.914484] sda: sda1 sda2 < sda5 >
[ 1.961789] sd 0:0:0:0: [sda] Attached SCSI disk
[ 1.961872] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 1.965285] scsi 0:0:1:0: CD-ROM HL-DT-ST DVDRAM GSA-H40N RG01 PQ: 0 ANSI: 5
[ 1.977044] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[ 1.977049] Uniform CD-ROM driver Revision: 3.20
[ 1.977197] sr 0:0:1:0: Attached scsi CD-ROM sr0
[ 1.977253] sr 0:0:1:0: Attached scsi generic sg1 type 5
[ 1.977292] ata_piix 0000:00:1f.2: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[ 1.977297] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[ 1.977349] ata_piix 0000:00:1f.2: setting latency timer to 64
[ 1.977455] scsi2 : ata_piix
[ 1.977541] scsi3 : ata_piix
[ 1.979550] ata3: SATA max UDMA/133 cmd 0xa800 ctl 0xa400 bmdma 0x9400 irq 23
[ 1.979553] ata4: SATA max UDMA/133 cmd 0xa000 ctl 0x9800 bmdma 0x9408 irq 23
[ 2.326936] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[ 2.326967] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 2.326993] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 2.326998] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[ 2.327097] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[ 2.330994] ehci_hcd 0000:00:1d.7: debug port 1
[ 2.331018] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[ 2.331081] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd9dffc00
[ 2.340142] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[ 2.340254] usb usb1: configuration #1 chosen from 1 choice
[ 2.340293] hub 1-0:1.0: USB hub found
[ 2.340304] hub 1-0:1.0: 8 ports detected
[ 2.340467] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[ 2.340503] uhci_hcd: USB Universal Host Controller Interface driver
[ 2.340546] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 2.340554] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 2.340558] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[ 2.340622] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[ 2.340649] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00008000
[ 2.340744] usb usb2: configuration #1 chosen from 1 choice
[ 2.340779] hub 2-0:1.0: USB hub found
[ 2.340789] hub 2-0:1.0: 2 ports detected
[ 2.340899] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 2.340907] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 2.340911] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[ 2.340973] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[ 2.341043] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00008400
[ 2.341156] usb usb3: configuration #1 chosen from 1 choice
[ 2.341193] hub 3-0:1.0: USB hub found
[ 2.341207] hub 3-0:1.0: 2 ports detected
[ 2.341323] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 2.341331] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 2.341335] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[ 2.341399] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[ 2.341503] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00008800
[ 2.341597] usb usb4: configuration #1 chosen from 1 choice
[ 2.341636] hub 4-0:1.0: USB hub found
[ 2.341644] hub 4-0:1.0: 2 ports detected
[ 2.341756] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[ 2.341763] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[ 2.341767] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[ 2.341826] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[ 2.341898] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00009000
[ 2.341993] usb usb5: configuration #1 chosen from 1 choice
[ 2.342029] hub 5-0:1.0: USB hub found
[ 2.342039] hub 5-0:1.0: 2 ports detected
[ 2.342218] usbcore: registered new interface driver libusual
[ 2.342263] usbcore: registered new interface driver usbserial
[ 2.342278] USB Serial support registered for generic
[ 2.342301] usbcore: registered new interface driver usbserial_generic
[ 2.342304] usbserial: USB Serial Driver core
[ 2.342378] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[ 2.342381] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[ 2.342837] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2.348197] mice: PS/2 mouse device common for all mice
[ 2.366222] rtc_cmos 00:03: RTC can wake from S4
[ 2.366268] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[ 2.366354] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[ 2.366414] device-mapper: uevent: version 1.0.3
[ 2.366504] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[ 2.366637] device-mapper: multipath: version 1.0.5 loaded
[ 2.366641] device-mapper: multipath round-robin: version 1.0.0 loaded
[ 2.366753] EISA: Probing bus 0 at eisa.0
[ 2.366783] Cannot allocate resource for EISA slot 8
[ 2.366785] EISA: Detected 0 cards.
[ 2.366794] cpuidle: using governor ladder
[ 2.366797] cpuidle: using governor menu
[ 2.367458] TCP cubic registered
[ 2.367509] NET: Registered protocol family 10
[ 2.368197] lo: Disabled Privacy Extensions
[ 2.368627] NET: Registered protocol family 17
[ 2.368653] Bluetooth: L2CAP ver 2.11
[ 2.368656] Bluetooth: L2CAP socket layer initialized
[ 2.368660] Bluetooth: SCO (Voice Link) ver 0.6
[ 2.368662] Bluetooth: SCO socket layer initialized
[ 2.368710] Bluetooth: RFCOMM socket layer initialized
[ 2.368720] Bluetooth: RFCOMM TTY layer initialized
[ 2.368722] Bluetooth: RFCOMM ver 1.10
[ 2.368876] p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available
[ 2.368884] Using IPI No-Shortcut mode
[ 2.368982] registered taskstats version 1
[ 2.369118] Magic number: 9:549:508
[ 2.369185] pcieport-driver 0000:00:01.0: hash matches
[ 2.369228] rtc_cmos 00:03: setting system clock to 2009-05-13 01:32:05 UTC (1242178325)
[ 2.369232] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 2.369234] EDD information not available.
[ 2.369576] Freeing unused kernel memory: 512k freed
[ 2.369745] Write protecting the kernel text: 4188k
[ 2.369807] Write protecting the kernel read-only data: 1552k
[ 2.693159] usb 1-7: new high speed USB device using ehci_hcd and address 3
[ 2.694772] ------------[ cut here ]------------
[ 2.694778] WARNING: at /build/buildd/linux-rt-2.6.28/arch/x86/kernel/signal_32.c:608 do_signal+0x171/0x180()
[ 2.694782] Modules linked in: fbcon tileblit font bitblit softcursor
[ 2.694792] Pid: 193, comm: udevd Not tainted 2.6.28-3-rt #12-Ubuntu
[ 2.694795] Call Trace:
[ 2.694803] [<c050f991>] ? printk+0x18/0x1f
[ 2.694809] [<c013be54>] warn_on_slowpath+0x54/0x80
[ 2.694814] [<c0135eff>] ? resched_task+0x1f/0xd0
[ 2.694819] [<c02d271d>] ? rb_erase+0xcd/0x150
[ 2.694823] [<c0102da7>] ? __switch_to+0xb7/0x1a0
[ 2.694827] [<c0511ed8>] ? _spin_unlock_irq+0x8/0x40
[ 2.694832] [<c0130850>] ? finish_task_switch+0x50/0x120
[ 2.694835] [<c0510117>] ? schedule+0x457/0x760
[ 2.694839] [<c0103eb1>] do_signal+0x171/0x180
[ 2.694843] [<c0510694>] ? preempt_schedule+0x74/0x80
[ 2.694847] [<c0511f5a>] ? _spin_unlock_irqrestore+0x4a/0x50
[ 2.694850] [<c0135e94>] ? wake_up_new_task+0xf4/0x140
[ 2.694854] [<c013b5a0>] ? do_fork+0x130/0x320
[ 2.694859] [<c01c41ef>] ? fput+0x1f/0x30
[ 2.694863] [<c01c0b29>] ? filp_close+0x49/0x70
[ 2.694867] [<c0103efd>] do_notify_resume+0x3d/0x40
[ 2.694871] [<c0104200>] work_notifysig+0x13/0x23
[ 2.694874] ---[ end trace 0983c4e30c1bbb2b ]---
[ 2.763684] Floppy drive(s): fd0 is 1.44M
[ 2.780979] FDC 0 is a post-1991 82077
[ 2.899111] usb 1-7: configuration #1 chosen from 1 choice
[ 2.935870] Initializing USB Mass Storage driver...
[ 2.938811] scsi4 : SCSI emulation for USB Mass Storage devices
[ 2.958412] usbcore: registered new interface driver usb-storage
[ 2.958424] USB Mass Storage support registered.
[ 2.961174] usb-storage: device found at 3
[ 2.961178] usb-storage: waiting for device to settle before scanning
[ 3.125183] usb 2-1: new low speed USB device using uhci_hcd and address 2
[ 3.289823] usb 2-1: configuration #1 chosen from 1 choice
[ 3.467748] usbcore: registered new interface driver hiddev
[ 3.467983] usbcore: registered new interface driver usbhid
[ 3.467990] usbhid: v2.6:USB HID core driver
[ 3.516057] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input3
[ 3.525250] logitech 0003:046D:C50C.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.0-1/input0
[ 3.553725] logitech 0003:046D:C50C.0002: fixing up Logitech keyboard report descriptor
[ 3.554517] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1/input/input4
[ 3.572254] logitech 0003:046D:C50C.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1/input1
[ 3.670821] PM: Starting manual resume from disk
[ 3.670826] PM: Resume from partition 8:5
[ 3.670828] PM: Checking hibernation image.
[ 3.671010] PM: Resume from disk failed.
[ 3.708064] kjournald starting. Commit interval 5 seconds
[ 3.708091] EXT3-fs: mounted filesystem with ordered data mode.
[ 7.961792] usb-storage: device scan complete
[ 7.992893] scsi 4:0:0:0: Direct-Access Generic 2.0 Reader-CF 1.00 PQ: 0 ANSI: 0 CCS
[ 8.023255] scsi 4:0:0:1: Direct-Access Generic 2.0 Reader-Multi 1.00 PQ: 0 ANSI: 0 CCS
[ 8.024617] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 8.024703] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 8.025697] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[ 8.025756] sd 4:0:0:1: Attached scsi generic sg3 type 0
[ 10.546528] udev: starting version 141
[ 10.879369] Atheros(R) L2 Ethernet Driver - version 2.2.3
[ 10.879373] Copyright (c) 2007 Atheros Corporation.
[ 10.879424] atl2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 10.879435] atl2 0000:02:00.0: setting latency timer to 64
[ 10.898091] Linux agpgart interface v0.103
[ 11.653669] nvidia: module license 'NVIDIA' taints kernel.
[ 11.693578] intel_rng: FWH not detected
[ 11.704815] input: PC Speaker as /devices/platform/pcspkr/input/input5
[ 11.712316] parport_pc 00:07: reported by Plug and Play ACPI
[ 11.712427] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[ 11.773942] iTCO_vendor_support: vendor-support=0
[ 11.776389] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[ 11.776856] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[ 11.776960] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[ 11.998306] nvidia 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 11.998317] nvidia 0000:04:00.0: setting latency timer to 64
[ 11.998863] NVRM: loading NVIDIA UNIX x86 Kernel Module 180.44 Mon Mar 23 14:59:10 PST 2009
[ 12.151915] ppdev: user-space parallel port driver
[ 12.255609] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 12.255953] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 12.526118] lp0: using parport0 (interrupt-driven).
[ 12.655716] Adding 4016208k swap on /dev/sda5. Priority:-1 extents:1 across:4016208k
[ 13.221163] EXT3 FS on sda1, internal journal
[ 14.669233] type=1505 audit(1242178337.799:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2070
[ 14.860650] type=1505 audit(1242178337.990:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2074
[ 14.861139] type=1505 audit(1242178337.990:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2074
[ 14.861332] type=1505 audit(1242178337.991:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2074
[ 14.861503] type=1505 audit(1242178337.991:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2074
[ 15.407753] type=1505 audit(1242178338.537:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2079
[ 15.408446] type=1505 audit(1242178338.538:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2079
[ 15.455999] type=1505 audit(1242178338.585:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2091
[ 15.575477] atl2 0000:02:00.0: irq 2300 for MSI/MSI-X
[ 15.576326] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 15.780273] atl2: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 15.780415] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 19.692781] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 19.692786] Bluetooth: BNEP filters: protocol multicast
[ 19.748651] Bridge firewalling registered

```
 
Any ideas or clues as to what is going on?
 
~John

---

### Post by jfmanamtr on 2009-05-13
So, no ideas? Anyone?

~John

---

### Post by micio on 2009-05-13
xorg.conf is empty?????? are you sure???
this is not normal.. try the command
```
nvidia-xsettings
```

or something similar (I'm not at home now)
Then reboot and retry.

If it doesn't still works, I suggest you to reinstall from zero your system.. only god knows what you did :P

While, about freeze.. I rollback to intrepid since jaunty freeze randomly for me.. the only log that I was able to see was a "CPU1 Core dump.. blablabla" 
In effect I had the CPU a little bit overclocked :P
However I turn back CPU to a default value, but without success.. and so I decided to overclock again my CPU and run Intrepid instead Jaunty :P

---

### Post by jfmanamtr on 2009-05-13
Yeah. I am sure that /etc/X11/xorg.conf is completely empty after a fresh install of Ubuntu Studio 9.04. I google searched & was told this is the command:

```
sudo nvidia-xconfig
```

I will try this command out when I get home. I am stuck at work & I will wander home on my hour lunch. I may also try to do a re-install using Ubuntu Studio 8.04. I have been hearing that the newer version still isn't completely fixed & ready for production PCs. So, I may just give Hardy a run just for kicks.

~John

---

### Post by jfmanamtr on 2009-05-13
Ok. So I went home & ran nvidia-xconfig. My computer will boot into Gnome, but I am having the same issue as before; I can't see part of the screen. It is putting the taskbar at the top outside the viewable screen. I can still click on the ubuntu symbol & get the menu. I just can't see the whole screen. It is also still freezing up on me. I think I may just have to install 8.04 Hardy & try it with that since 9.04 Intrepid to see if that  clears up the crashing issue. I want it to boot without crashing before I worry about getting it to show the screen correctly. Any ideas as to what could be causing it to display the screen like this?

~John

---

### Post by jfmanamtr on 2009-05-18
Ok. So I tried to doing a reinstall of Ubuntu 9.04 & still no luck. Then I tried to use Ubuntu 8.04 & I can't get into XWindows at all. I reinstalled Ubuntu 9.04 & can get the computer to boot into XWindows, but the screen is still the wrong size. I have the computer set to output from the GeForce 8500 GT to a TV using S-video. the screen shows, but it is bigger than what you can view on the screen. I am not sure what to change to correct this. Any ideas?

~John

---

### Post by micio on 2009-05-18
have you tried to set manually the screen resolution?

System ---> preference ---> screen resolution

---

### Post by jfmanamtr on 2009-05-18
Yeah. I have tried all the available resolutions & all of them are out of sync. It is like the graphics card is broadcasting the screen too big for the screen.

~John

---

### Post by micio on 2009-05-18
Try adding those lines to xorg.conf under section screen after DefaultDepth 24

```
SubSection "Display"
			Depth	24
			Modes	"1280x1024" "1024x768" "800x600" "640x480"
		EndSubSection

```

At this point the resolution should be 1280x1024, in you need other resolution just write there.
Then if you got the same error, try by forcing the Frequency too by adding (or maybe changing) those others lines in the screens section.

```
Section "Monitor"

	Identifier	"Your monitor"
	HorizSync	30.0 - 83.0
	VertRefresh	56.0 - 75.0
	Option		"DPMS"

EndSection

```

---

### Post by jfmanamtr on 2009-05-18
Ok. so I added both those & am still not seeing the entire screen. here is my xorg.conf file:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon Mar 23 15:33:27 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        modes       "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```I have no idea what to do about this. I can't see about 1 inch all the way around my TV screen (note that this is an old CRT TV, not a LCD or plasma). Any other plans of attack?

~John

---

### Post by jfmanamtr on 2009-05-19
bump

---

