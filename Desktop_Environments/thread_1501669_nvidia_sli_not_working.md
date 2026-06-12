---
title: "nvidia sli not working"
date: 2010-06-04
forum: Desktop Environments
---

### Post by neovandeen on 2010-06-04
Hi guys,

I'm struggling around with my SLI config under lucid. I tried to configure it with "nvidia-xconfig --sli=sfr" and other modes.
The result is, that I restart my X server and get nothing. No video on my monitor. 

My sys:
```

Linux falco-pc 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:18:25 UTC 2010 x86_64 GNU/Linux

root@falco-pc:/# lspci|grep -i vga
04:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GX2] (rev a1)

root@falco-pc:/# Xorg -version

X.Org X Server 1.7.6

NVIDIA Driver version: 195.36.15


```

So what I already did is to drop the default xorg.conf and create a new one with the nvidia-settings utility. The new one looks pretty impressive with many options and switches. This one works too. 
If I'm adding the SLI option, my screen keeps blank.
Same result like the default Ubuntu one.

Looking in the logs shows nothing spectacular.

BUT, with the SLI option the startup hangs without any error, but also it doesn't boot to the login screen:

Sorry for the much code, but I hope you can see, what I mean:

**WITHOUT SLI**
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux falco-pc 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:18:25 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=64cec496-3c0e-4fde-be13-6ac98076e0c4 ro splash quiet vga=771 quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  4 20:19:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:3:0:0) 10de:0294:1682:2214 nVidia Corporation G71 [GeForce 7950 GX2] rev 161, Mem @ 0xf8000000/16777216, 0xc0000000/268435456, 0xf7000000/16777216, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI:*(0:4:0:0) 10de:0294:1682:2214 nVidia Corporation G71 [GeForce 7950 GX2] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf9000000/16777216, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
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
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Fri Mar 12 01:17:05 PST 2010
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Fri Mar 12 00:38:50 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 04@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1680x1050_60_0 +0+0; nvidia-auto-select +0+0"
(**) Jun 04 20:19:05 NVIDIA(0): Enabling RENDER acceleration
(II) Jun 04 20:19:05 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 04 20:19:05 NVIDIA(0):     enabled.
(II) Jun 04 20:19:07 NVIDIA(0): NVIDIA GPU GeForce 7950 GX2 (G71) at PCI:4:0:0 (GPU-0)
(--) Jun 04 20:19:07 NVIDIA(0): Memory: 524288 kBytes
(--) Jun 04 20:19:07 NVIDIA(0): VideoBIOS: 05.71.22.33.31
(II) Jun 04 20:19:07 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jun 04 20:19:07 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jun 04 20:19:07 NVIDIA(0): Connected display device(s) on GeForce 7950 GX2 at PCI:4:0:0:
(--) Jun 04 20:19:07 NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) Jun 04 20:19:07 NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) Jun 04 20:19:07 NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(II) Jun 04 20:19:07 NVIDIA(0): Assigned Display Device: DFP-0
(II) Jun 04 20:19:07 NVIDIA(0): Validated modes:
(II) Jun 04 20:19:07 NVIDIA(0):     "1680x1050_60_0+0+0"
(II) Jun 04 20:19:07 NVIDIA(0):     "nvidia-auto-select+0+0"
(II) Jun 04 20:19:07 NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) Jun 04 20:19:07 NVIDIA(0): DPI set to (90, 88); computed from "UseEdidDpi" X config
(--) Jun 04 20:19:07 NVIDIA(0):     option
(==) Jun 04 20:19:07 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jun 04 20:19:08 NVIDIA(GPU-1): NVIDIA GPU GeForce 7950 GX2 (G71) at PCI:3:0:0 (GPU-1)
(--) Jun 04 20:19:08 NVIDIA(GPU-1): Memory: 524288 kBytes
(--) Jun 04 20:19:08 NVIDIA(GPU-1): VideoBIOS: 05.71.22.33.31
(II) Jun 04 20:19:08 NVIDIA(GPU-1): Detected PCI Express Link width: 16X
(--) Jun 04 20:19:08 NVIDIA(GPU-1): Interlaced video modes are supported on this GPU
(--) Jun 04 20:19:08 NVIDIA(GPU-1): Connected display device(s) on GeForce 7950 GX2 at PCI:3:0:0:
(--) Jun 04 20:19:08 NVIDIA(GPU-1):     none
(II) Jun 04 20:19:08 NVIDIA(0): Initialized GPU GART.
(II) Jun 04 20:19:08 NVIDIA(0): Setting mode "1680x1050_60_0+0+0"
(II) Loading extension NV-GLX
(II) Jun 04 20:19:08 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jun 04 20:19:08 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
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
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
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
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "mac_nodeadkeys"
(II) XKB: reuse xkmfile /var/lib/xkb/server-59F54317C6A1A6C0C864064DA0340945F7BA1792.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "mac_nodeadkeys"
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
(**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event3"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Found relative axes
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Apple, Inc Apple Keyboard (/dev/input/event4)
(**) Apple, Inc Apple Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Apple, Inc Apple Keyboard: always reports core events
(**) Apple, Inc Apple Keyboard: Device: "/dev/input/event4"
(II) Apple, Inc Apple Keyboard: Found keys
(II) Apple, Inc Apple Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "mac_nodeadkeys"
(II) config/udev: Adding input device Apple, Inc Apple Keyboard (/dev/input/event5)
(**) Apple, Inc Apple Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Apple, Inc Apple Keyboard: always reports core events
(**) Apple, Inc Apple Keyboard: Device: "/dev/input/event5"
(II) Apple, Inc Apple Keyboard: Found keys
(II) Apple, Inc Apple Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "mac_nodeadkeys"
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
(II) Jun 04 20:19:32 NVIDIA(0): Setting mode "nvidia-auto-select+0+0"


```

**WITH SLI**
```


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux falco-pc 2.6.32-22-generic #35-Ubuntu SMP Tue Jun 1 14:18:25 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=64cec496-3c0e-4fde-be13-6ac98076e0c4 ro splash quiet vga=771 quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  4 20:07:43 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI: (0:3:0:0) 10de:0294:1682:2214 nVidia Corporation G71 [GeForce 7950 GX2] rev 161, Mem @ 0xf8000000/16777216, 0xc0000000/268435456, 0xf7000000/16777216, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI:*(0:4:0:0) 10de:0294:1682:2214 nVidia Corporation G71 [GeForce 7950 GX2] rev 161, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf9000000/16777216, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
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
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Fri Mar 12 01:17:05 PST 2010
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Fri Mar 12 00:38:50 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 04@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "1680x1050_60_0 +0+0; nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "SLI" "sfr"
(**) Jun 04 20:07:44 NVIDIA(0): Enabling RENDER acceleration
(**) Jun 04 20:07:44 NVIDIA(0): NVIDIA SLI split-frame rendering selected.
(II) Jun 04 20:07:44 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 04 20:07:44 NVIDIA(0):     enabled.


```

Looks like he stops before initializing the card itsself.

Hope you guys can help me and sorry for my bad english.

Regards, Neo

---

### Post by wojox on 2010-06-04
Shouldn't the command be:

```
sudo nvidia-xconfig --sli=AFR
```

---

### Post by neovandeen on 2010-06-04
there are three modes:

afr: alternate frame rendering
sfr: split frame rendering
aa:  antialiasing

I did everything as root, in case you mind the sudo

In the log you can see, the option is regognized:

(**) Jun 04 20:07:44 NVIDIA(0): NVIDIA SLI split-frame rendering selected.

---

### Post by wojox on 2010-06-04
I got ya. Sorry about that. :)

Did you try the old 9.04 way [Enabling SLI Technology in Ubuntu 9.04]("http://z0manifest.blogspot.com/2009/10/enabling-sli-technology-in-ubuntu-904.html")

---

### Post by neovandeen on 2010-06-04
looks similar to my config:

```
root@falco-pc:~# lspci|grep VGA
04:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GX2] (rev a1)
```

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7950 GX2"
    BusID          "PCI:4:0:0"
EndSection

```

isn't it the same?

---

### Post by wojox on 2010-06-04
Add

*Option         "SLI" "Auto"*

To it.

---

### Post by neovandeen on 2010-06-04
Uhh, got a new behaviour: my fans on the gpu gone wild and it dopped me out to  low graphics mode.
I recovered it with the console.

---

### Post by neovandeen on 2010-06-06
bump - any ideas?

---

### Post by Leldoren on 2010-06-18
I have two 9800GTX's and have had weird results with SLI.
In Doom3 I have had these results:
sli=on 112fps,
sli=off 177fps,
sli=afr 104fps,
sli=sfr 89fps.
I run "timedemo demo1.demo usecache".
X.Org X Server 1.7.6.
NVIDIA Driver Version: 195.36.24

---

