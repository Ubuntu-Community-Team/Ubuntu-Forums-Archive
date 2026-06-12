---
title: "Xorg segfaults on libc-2.9.so"
date: 2009-08-19
forum: Desktop Environments
---

### Post by infecticide on 2009-08-19
Hey folks,

I've encountered an issue over the last two days and I'm not sure what to do with it.

DMESG Indicates:
```

Aug 13 17:45:45 avatar kernel: [348556.229604] Xorg[13985]: segfault at 18 ip 00007f68553726e3 sp 00007fff5f7fc390 error 4 in libc-2.9.so[7f68552fa000+168000]

```

Xorg.0.log Indicates:
```


X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux avatar 2.6.28-15-generic #48-Ubuntu SMP Wed Jul 29 08:53:35 UTC 2009 x86_64
Build Date: 09 April 2009  02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 19 08:43:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "DontZap" "False"
(**) Option "Xinerama" "0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI: (0@2:0:0) nVidia Corporation nForce 780a SLI rev 162, Mem @ 0xfb000000/16777216, 0xd0000000/134217728, 0xde000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI:*(0@5:0:0) nVidia Corporation GeForce 9800 GTX rev 162, Mem @ 0xe8000000/16777216, 0x80000000/536870912, 0xe6000000/33554432, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
(--) PCI: (0@6:0:0) nVidia Corporation GeForce 8600 GTS rev 161, Mem @ 0xe4000000/16777216, 0xb0000000/268435456, 0xe2000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.18  Wed Jul 22 16:35:50 PDT 2009
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.18  Wed Jul 22 15:47:48 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05@00:00:0
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "TwinView" "1"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: 1680x1050,1440x900 +0+0, DFP-1: 1680x1050,NULL +1680+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) Aug 19 08:43:23 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 19 08:43:23 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 19 08:43:23 NVIDIA(0):     enabled.
(II) Aug 19 08:43:24 NVIDIA(0): NVIDIA GPU GeForce 9800 GTX/9800 GTX+ (G92) at PCI:5:0:0
(II) Aug 19 08:43:24 NVIDIA(0):     (GPU-0)
(--) Aug 19 08:43:24 NVIDIA(0): Memory: 524288 kBytes
(--) Aug 19 08:43:24 NVIDIA(0): VideoBIOS: 62.92.62.00.0c
(II) Aug 19 08:43:24 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Aug 19 08:43:24 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Aug 19 08:43:24 NVIDIA(0): Connected display device(s) on GeForce 9800 GTX/9800 GTX+ at
(--) Aug 19 08:43:24 NVIDIA(0):     PCI:5:0:0:
(--) Aug 19 08:43:24 NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) Aug 19 08:43:24 NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) Aug 19 08:43:24 NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) Aug 19 08:43:24 NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(--) Aug 19 08:43:24 NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) Aug 19 08:43:24 NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(**) Aug 19 08:43:24 NVIDIA(0): TwinView enabled
(II) Aug 19 08:43:24 NVIDIA(0): Display Devices found referenced in MetaMode: DFP-0, DFP-1
(II) Aug 19 08:43:24 NVIDIA(0): Assigned Display Devices: DFP-0, DFP-1
(WW) Aug 19 08:43:24 NVIDIA(0): Invalid display device in Mode Description "1440x900+0+0"
(WW) Aug 19 08:43:24 NVIDIA(0): Invalid display device in Mode Description "NULL+1680+0"
(WW) Aug 19 08:43:24 NVIDIA(0): Not using mode description "1440x900+0+0"; unable to map to
(WW) Aug 19 08:43:24 NVIDIA(0):     display device
(WW) Aug 19 08:43:24 NVIDIA(0): Not using mode description "NULL+1680+0"; unable to map to
(WW) Aug 19 08:43:24 NVIDIA(0):     display device
(II) Aug 19 08:43:24 NVIDIA(0): Validated modes:
(II) Aug 19 08:43:24 NVIDIA(0):    
(II) Aug 19 08:43:24 NVIDIA(0):     "DFP-0:1680x1050,1440x900+0+0,DFP-1:1680x1050,NULL+1680+0"
(II) Aug 19 08:43:24 NVIDIA(0): Virtual screen size determined to be 3360 x 1050
(--) Aug 19 08:43:24 NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) Aug 19 08:43:24 NVIDIA(0):     option
(==) Aug 19 08:43:24 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
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
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Aug 19 08:43:29 NVIDIA(GPU-1): NVIDIA GPU nForce 980a/780a SLI (C77) at PCI:2:0:0 (GPU-1)
(--) Aug 19 08:43:29 NVIDIA(GPU-1): Memory: 524288 kBytes
(--) Aug 19 08:43:29 NVIDIA(GPU-1): VideoBIOS: 62.77.24.00.06
(--) Aug 19 08:43:29 NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
(--) Aug 19 08:43:29 NVIDIA(GPU-1): Connected display device(s) on nForce 980a/780a SLI at
(--) Aug 19 08:43:29 NVIDIA(GPU-1):     PCI:2:0:0:
(II) Aug 19 08:43:30 NVIDIA(GPU-2): NVIDIA GPU GeForce 8600 GTS (G84) at PCI:6:0:0 (GPU-2)
(--) Aug 19 08:43:30 NVIDIA(GPU-2): Memory: 262144 kBytes
(--) Aug 19 08:43:30 NVIDIA(GPU-2): VideoBIOS: 60.84.35.00.90
(II) Aug 19 08:43:30 NVIDIA(GPU-2): Detected PCI Express Link width: 16X
(--) Aug 19 08:43:30 NVIDIA(GPU-2): Interlaced video modes are supported on this GPU
(--) Aug 19 08:43:30 NVIDIA(GPU-2): Connected display device(s) on GeForce 8600 GTS at PCI:6:0:0:
(WW) Aug 19 08:43:30 NVIDIA(0): Failed to allocate GLX video capture device array.
(II) Aug 19 08:43:30 NVIDIA(0): Initialized GPU GART.
(II) Aug 19 08:43:30 NVIDIA(0): Setting mode
(II) Aug 19 08:43:30 NVIDIA(0):     "DFP-0:1680x1050,1440x900+0+0,DFP-1:1680x1050,NULL+1680+0"
(II) Loading extension NV-GLX
(II) Aug 19 08:43:30 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Aug 19 08:43:30 NVIDIA(0): Initialized X Rendering Acceleration
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
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device bttv IR (card=34)
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) bttv IR (card=34): always reports core events
(**) bttv IR (card=34): Device: "/dev/input/event6"
(II) bttv IR (card=34): Found keys
(II) bttv IR (card=34): Configuring as keyboard
(II) XINPUT: Adding extended input device "bttv IR (card=34)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) bttv IR (card=34): xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) bttv IR (card=34): xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) bttv IR (card=34): xkb_layout: "us"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event4"
(II) Logitech USB Receiver: Found 32 mouse buttons
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

Backtrace:

```

What baffles me is that the backtrace is empty and the log stops.

At this point the screen and keyboard are unresponsive, I can login via SSH however.   I've attempted to restart KDM with no luck, nothing happens.   I'm also unable to gracefully reboot the machine as the shutdown process hangs at some point.

I thought it might be the CUDA drivers I installed so I got the latest stable drivers but the same issue exists.

---

### Post by krazyd on 2009-08-19
I'd strongly suspect the nvidia drivers. Can you try a different version and see how it goes?

---

### Post by infecticide on 2009-08-20
Interestingly I had install vuze earlier and I know that the SWT toolkit it uses is pretty flaky.  I removed all traces of Vuze and supporting libraries and the lockup hasn't happened since.

Here's to hoping it was just some crappy libraries.

---

