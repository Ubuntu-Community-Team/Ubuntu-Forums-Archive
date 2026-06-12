---
title: "KDE doesn't start. XRANDR issue."
date: 2009-09-23
forum: Desktop Environments
---

### Post by ilyk on 2009-09-23
Problem. KDE doesn't starts, I mean after KDE initialization it returns back to KDM login form.

**xorg.conf**
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    FontPath       "unix/:7100"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver          "kbd"
    Option          "CoreKeyboard"
    Option          "XkbRules"      "xorg"
    Option          "XkbModel"      "logitech_g15"
    Option          "XkbLayout"     "us,ru(winkeys),ua(winkeys)"
    Option          "XkbOptions" "grp:caps_toggle,grp_led:scroll"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Viewport  0 0
        Depth     24
        Modes     "1280x1024"
    EndSubSection
EndSection

```

**.xsession-errors**
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=ru_UA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
User id(1000) name = ilyk
euid = root
dir '/var/turboprint/ilyk' already existing
startkde: Starting up...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_klauncher.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kded4.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kbuildsycoca4.so
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kcminit_startup.so
kdeinit4: preparing to launch /usr/lib/libkdeinit4_ksmserver.so
<unknown program name>(1414)/ KStartupInfo::createNewStartupId: creating:  "localhost;1253696412;183224;1414_TIME0" : "unnamed app"
kephald starting up 
XRANDR error base:  172 
RRInput mask is set!! 
kded4: Fatal IO error: client killed
kdeinit4: Fatal IO error: client killed
kdeinit4: sending SIGHUP to children.
klauncher: Exiting on signal 1
could not access kephald, falling back to QDesktopWidget 
adding an output 0 with geom:  QRect(0,0 1280x1024) 

```

**PS.** yes, I tried to run with "vesa" video driver. Doesn't helps
**PS2.** and yes, I tried to start fluxbox, no problems occured. But if I try to run "xrandr" from terminal in fluxbox, it turns my display off, and also keybord.

---

### Post by Lars Noodén on 2009-09-23
Have you tried stopping X, running and running
```
sudo Xorg -configure
```

and then testing X with the resulting file?

what does ```
xrandr
``` by itself say?

---

### Post by ilyk on 2009-09-23
> **Lars Noodén said:**
> Have you tried stopping X, running and running
```
sudo Xorg -configure
```

and then testing X with the resulting file?
Yes, I tried this. Nothing changed.

> **Lars Noodén said:**
> what does ```
xrandr
``` by itself say?
As I already said, it turns off my display and blocks keyboard. So nothing can help except of hard reset.

any other suggestions?

---

### Post by krazyd on 2009-09-23
can you post your Xorg.log showing the crash?

---

### Post by ilyk on 2009-09-23
> **krazyd said:**
> can you post your Xorg.log showing the crash?

Xorg.log doesn't shows any warnings or errors, except those:
```

(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0

```
but then hal detects both keyboard and mouse.

if you want to see Xorg.log anyway, here it is:
```

X.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.30.2-dsa-amd64 x86_64 Debian
Current Operating System: Linux tob-ilyk 2.6.27 #1 SMP Sat Dec 20 04:20:28 EET 2008 x86_64
Build Date: 01 August 2009  07:44:36AM
xorg-server 2:1.6.3-1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.777.log", Time: Wed Sep 23 21:04:42 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	unix/:7100,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3740
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:0640:10de:0560 nVidia Corporation G96 [GeForce 9500 GT] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
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
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension SELinux
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 18:27:24 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:51:02 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
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
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "true"
(**) NVIDIA(0): Option "DisableGLXRootClipping" "true"
(**) NVIDIA(0): Option "UseCompositeWrapper" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.94.26.00.08
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9500 GT at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
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
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
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
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
SELinux: Disabled on system, not enabling in X server
(II) Initializing extension GLX
(II) config/hal: Adding input device Power Button (FF)
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Power Button (FF): always reports core events
(**) Power Button (FF): Device: "/dev/input/event3"
(II) Power Button (FF): Found keys
(II) Power Button (FF): Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button (FF)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc104"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button (CM)
(**) Power Button (CM): always reports core events
(**) Power Button (CM): Device: "/dev/input/event4"
(II) Power Button (CM): Found keys
(II) Power Button (CM): Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button (CM)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc104"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Microsoft Microsoft? Digital Media Keyboard
(**) Microsoft Microsoft? Digital Media Keyboard: always reports core events
(**) Microsoft Microsoft? Digital Media Keyboard: Device: "/dev/input/event1"
(II) Microsoft Microsoft? Digital Media Keyboard: Found 1 mouse buttons
(II) Microsoft Microsoft? Digital Media Keyboard: Found scroll wheel(s)
(II) Microsoft Microsoft? Digital Media Keyboard: Found x and y absolute axes
(II) Microsoft Microsoft? Digital Media Keyboard: Found keys
(II) Microsoft Microsoft? Digital Media Keyboard: Configuring as mouse
(II) Microsoft Microsoft? Digital Media Keyboard: Configuring as keyboard
(**) Microsoft Microsoft? Digital Media Keyboard: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft? Digital Media Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft? Digital Media Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc104"
(**) Option "xkb_layout" "us"
(**) Microsoft Microsoft? Digital Media Keyboard: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft? Digital Media Keyboard: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft? Digital Media Keyboard: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft? Digital Media Keyboard: (accel) set acceleration profile 0
(II) Microsoft Microsoft? Digital Media Keyboard: initialized for absolute axes.
(II) config/hal: Adding input device Microsoft Microsoft? Digital Media Keyboard
(**) Microsoft Microsoft? Digital Media Keyboard: always reports core events
(**) Microsoft Microsoft? Digital Media Keyboard: Device: "/dev/input/event0"
(II) Microsoft Microsoft? Digital Media Keyboard: Found keys
(II) Microsoft Microsoft? Digital Media Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Microsoft? Digital Media Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc104"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found 9 mouse buttons
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0
(II) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): initialized for relative axes.

```

---

### Post by ilyk on 2009-09-23
Okay. Problem is solved. Just should to downgrade xorg from 1.6 to 1.4 and all works cool now :) thanks to all ... 

:popcorn:

You can close thread.

---

