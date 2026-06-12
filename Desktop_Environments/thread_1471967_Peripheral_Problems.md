---
title: "Peripheral Problems"
date: 2010-05-04
forum: Desktop Environments
---

### Post by saseith on 2010-05-04
[I]Hi Everyone,

   I just upgraded to Lucid today, and I am rather dismayed to find that the support for my MX3100 cordless desktop in Gnome is even worse than it was when I made my last post about Karmic (which was never solved BTW).  I now have no ability to use the keyboard or the mouse unless I am in a recovery console (then everything seems to be fine).  I have reconfigured the Xorg.conf multiple times with no success.  The Xorg.0.log shows a huge number of devices (basically every peripheral I have) that were not properly loaded due to not finding drivers and then ignoring the device and moving on.  The log is pasted below.  

Any help you can provide with either manually configuring the keyboard and mouse or correcting the detection issue in xorg would be much appreciated.


X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux mako 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686
Kernel command line: root=UUID=95d8e40c-734a-4b8e-b04d-4bfccd0a67ad ro quiet splash 
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May  3 17:42:50 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:8:0:0) 10de:0622:1682:2362 nVidia Corporation G94 [GeForce 9600 GT] rev 161, Mem @ 0xcf000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x0000e800/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Thu Mar 11 23:39:48 PST 2010
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
(II) NVIDIA dlloader X Driver  195.36.15  Thu Mar 11 22:01:49 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 08@00:00:0
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
(**) NVIDIA(0): Option "NoLogo" "True"
(**) May 03 17:42:51 NVIDIA(0): Enabling RENDER acceleration
(II) May 03 17:42:51 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) May 03 17:42:51 NVIDIA(0):     enabled.
(II) May 03 17:42:53 NVIDIA(0): NVIDIA GPU GeForce 9600 GT (G94) at PCI:8:0:0 (GPU-0)
(--) May 03 17:42:53 NVIDIA(0): Memory: 524288 kBytes
(--) May 03 17:42:53 NVIDIA(0): VideoBIOS: 62.94.29.00.28
(II) May 03 17:42:53 NVIDIA(0): Detected PCI Express Link width: 16X
(--) May 03 17:42:53 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) May 03 17:42:53 NVIDIA(0): Connected display device(s) on GeForce 9600 GT at PCI:8:0:0:
(--) May 03 17:42:53 NVIDIA(0):     DELL 2405FPW (DFP-1)
(--) May 03 17:42:53 NVIDIA(0): DELL 2405FPW (DFP-1): 330.0 MHz maximum pixel clock
(--) May 03 17:42:53 NVIDIA(0): DELL 2405FPW (DFP-1): Internal Dual Link TMDS
(II) May 03 17:42:53 NVIDIA(0): Assigned Display Device: DFP-1
(==) May 03 17:42:53 NVIDIA(0): 
(==) May 03 17:42:53 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) May 03 17:42:53 NVIDIA(0):     will be used as the requested mode.
(==) May 03 17:42:53 NVIDIA(0): 
(II) May 03 17:42:53 NVIDIA(0): Validated modes:
(II) May 03 17:42:53 NVIDIA(0):     "nvidia-auto-select"
(II) May 03 17:42:53 NVIDIA(0): Virtual screen size determined to be 1920 x 1200
(--) May 03 17:42:53 NVIDIA(0): DPI set to (93, 92); computed from "UseEdidDpi" X config
(--) May 03 17:42:53 NVIDIA(0):     option
(==) May 03 17:42:53 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) May 03 17:42:53 NVIDIA: Using 768.00 MB of virtual memory for indirect framebuffer
(II) May 03 17:42:53 NVIDIA:     access.
(II) May 03 17:42:53 NVIDIA(0): Initialized GPU GART.
(II) May 03 17:42:53 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) May 03 17:42:53 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) May 03 17:42:54 NVIDIA(0): Initialized X Rendering Acceleration
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
(**) Option "xkb_model" "logicda"
(**) Option "xkb_layout" "us"
(II) XKB: reuse xkmfile /var/lib/xkb/server-D378AD8F86E560F712A83EE36E4E5E92C595B9BD.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "logicda"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mx1000)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mx1000)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsoft SideWinder Force Feedback 2 Joystick (/dev/input/event3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Microsoft SideWinder Force Feedback 2 Joystick (/dev/input/js0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device CH PRODUCTS CH PRO PEDALS USB  (/dev/input/event4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device CH PRODUCTS CH PRO PEDALS USB  (/dev/input/js1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device CH PRODUCTS CH FLIGHT SIM YOKE USB  (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device CH PRODUCTS CH FLIGHT SIM YOKE USB  (/dev/input/js2)
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
(II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event9)
(**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event9"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "logicda"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device MouseCenter LASER Mouse (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device MouseCenter LASER Mouse (/dev/input/event10)
(**) MouseCenter LASER Mouse: Applying InputClass "evdev pointer catchall"
(**) MouseCenter LASER Mouse: always reports core events
(**) MouseCenter LASER Mouse: Device: "/dev/input/event10"
(II) MouseCenter LASER Mouse: Found 12 mouse buttons
(II) MouseCenter LASER Mouse: Found scroll wheel(s)
(II) MouseCenter LASER Mouse: Found relative axes
(II) MouseCenter LASER Mouse: Found x and y relative axes
(II) MouseCenter LASER Mouse: Configuring as mouse
(**) MouseCenter LASER Mouse: YAxisMapping: buttons 4 and 5
(**) MouseCenter LASER Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "MouseCenter LASER Mouse" (type: MOUSE)
(II) MouseCenter LASER Mouse: initialized for relative axes.


Saseith
[/I]

---

### Post by Zebro on 2010-05-20
I have exactely the same problem and no idea how to deal with it!
It occured after updating ubuntu from 9.04 to 10.04. In the console I have keyboard ... but when starting gdm from the login screen I have neither trackball nor keyboard nor external mouse.

How can I fix that? I read somewhere that:
"x11_options.* in udev is not used anymore.  You can set options from
/etc/X11/xorg.conf using an "InputClass" section (see the xorg.conf
manpage for details).
"
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=577773](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=577773)
But wehat does it mean?

Error log see below ...

----

II) config/udev: Adding input device Power Button (FF) (/dev/event0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Video Bus (/dev/event6)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Lid Switch (/dev/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Sleep Button (CM) (/dev/event2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device UVC Camera (17ef:4807) (/dev/event8)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/event4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/event9)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device TPPS/2 IBM TrackPoint (/dev/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/event3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device ThinkPad Extra Buttons (/dev/event7)
(II) No input driver/identifier specified (ignoring)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0

---

### Post by saseith on 2010-05-24
I will take a look at the new xorg format and see if I can find a way to at least fix it for these devices.  I'm tempted to simply bug this though given how many devices fail to be auto-identified on boot up, especially since nearly all of these devices worked perfectly in 9.10 and 9.04.  I will either have some successful tinkering or total failure to report within the next few days I think.

---

