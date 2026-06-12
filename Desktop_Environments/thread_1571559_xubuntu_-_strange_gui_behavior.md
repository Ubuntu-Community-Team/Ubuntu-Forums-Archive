---
title: "xubuntu - strange gui behavior"
date: 2010-09-09
forum: Desktop Environments
---

### Post by dirty_harry on 2010-09-09
I have a very strange problem.

Recently I installed *xubuntu 10.04 i386* on my old machine:[INDENT]AMD Athlon XP 3000 @ 2.1Ghz
Mainboard: k7vta3 v5
Ram: 1,5 GB @ 333 with 613 MB/s
Graphic: Geforce 7600 GT 

[/INDENT]switched off modeset; NVIDIA driver 173.14.22 (seems to have better performance) 

But lately the screen comes to live again in power-save mode, I disabled Screensaver in xfce-controls because it only said OpenGlx-Error. And the gui responses are sometimes really slow! In Firefox, OpenOffice, even the menu needs 30sec or more to open a submenu.

**kern.log **(part of it)
```
Sep  9 23:34:58 ****-***** kernel: [   29.923680] agpgart-via 0000:00:00.0: AGP 2.0 bridge
Sep  9 23:34:58 ****-***** kernel: [   29.923701] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
Sep  9 23:34:58 ****-***** kernel: [   29.923758] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
```**Xorg.0.log**
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux ****-***** 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=953e8e4b-be05-483b-a980-bce770fc5c4b ro nomodeset
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep  9 23:34:56 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:02e0:1682:2249 nVidia Corporation G73 [GeForce 7600 GT] rev 162, Mem @ 0xe0000000/16777216, 0xd0000000/268435456, 0xe1000000/16777216, BIOS @ 0x????????/131072
(WW) **Open ACPI failed **(/var/run/acpid.socket) (No such file or directory)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.22  Sun Nov  8 21:42:44 PST 2009
(II) Loading extension GLX
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
(II) NVIDIA dlloader X Driver  173.14.22  Sun Nov  8 20:43:40 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.25.75
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     MED MD6155AN (CRT-0)
(--) NVIDIA(0): MED MD6155AN (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(==) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-32CF54508D1127B0F32CA64F4D9024E09F623E78.xkm
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
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
[B](WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.[/B]
(II) NVIDIA(0): Initialized AGP GART.
```Looks like the nvidia driver got some problems. Any idea how to get rid of this. Or is this normal( back to legacy PCI mode) and the problems with *screensaver/gui response/window-video artefacts* are coming from elsewhere?

---

### Post by dirty_harry on 2010-09-09
I tried some options in bios at it looks like "back to legacy PCI mode" has disappeared. I added 256mb shared and enabled AGP write master... whatever.

**But** opengl games are still not working and the gui still reacts slow(when the password dialog appears you can see blend-over to gray and so on).

And I found the nvidia-bug-report-shript:
```
____________________________________________

Start of NVIDIA bug report log file.  Please include this file
when reporting a graphics driver bug via the nV News NVIDIA
Linux forum (see www.nvnews.net) or by sending email to
'linux-bugs@nvidia.com'.

nvidia-bug-report.sh Version: 4401225

Date: Fr 10. Sep 04:31:01 CEST 2010
uname: Linux ****-***** 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux

____________________________________________

/etc/issue
Ubuntu 10.04.1 LTS \n \l


____________________________________________

/etc/debian_version
squeeze/sid

____________________________________________

/var/log/nvidia-installer.log does not exist

____________________________________________

/var/log/XFree86.0.log does not exist

____________________________________________

/var/log/XFree86.0.log.old does not exist

____________________________________________

/var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux hugo-kiste 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=953e8e4b-be05-483b-a980-bce770fc5c4b ro nomodeset
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 10 04:00:40 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:02e0:1682:2249 nVidia Corporation G73 [GeForce 7600 GT] rev 162, Mem @ 0xe0000000/16777216, 0xd0000000/268435456, 0xe1000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.22  Sun Nov  8 21:42:44 PST 2009
(II) Loading extension GLX
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
(II) NVIDIA dlloader X Driver  173.14.22  Sun Nov  8 20:43:40 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.25.75
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     MED MD6155AN (CRT-0)
(--) NVIDIA(0): MED MD6155AN (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(==) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-32CF54508D1127B0F32CA64F4D9024E09F623E78.xkm
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
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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

____________________________________________

/etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


____________________________________________

/var/log/Xorg.0.log.old

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux hugo-kiste 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=953e8e4b-be05-483b-a980-bce770fc5c4b ro nomodeset
Build Date: 21 July 2010  12:47:34PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep 10 03:36:25 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
    Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:02e0:1682:2249 nVidia Corporation G73 [GeForce 7600 GT] rev 162, Mem @ 0xe0000000/16777216, 0xd0000000/268435456, 0xe1000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
    compiled for 4.0.2, module version = 1.0.0
    Module class: X.Org Server Extension
(II) NVIDIA GLX Module  173.14.22  Sun Nov  8 21:42:44 PST 2009
(II) Loading extension GLX
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
(II) NVIDIA dlloader X Driver  173.14.22  Sun Nov  8 20:43:40 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
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
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.25.75
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) NVIDIA(0):     MED MD6155AN (CRT-0)
(--) NVIDIA(0): MED MD6155AN (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(==) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) XKB: reuse xkmfile /var/lib/xkb/server-32CF54508D1127B0F32CA64F4D9024E09F623E78.xkm
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
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device Sleep Button (/dev/input/event1)
(**) Sleep Button: Applying InputClass "evdev keyboard catchall"
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event1"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/event5)
(**) ImPS/2 Generic Wheel Mouse: Applying InputClass "evdev pointer catchall"
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Found relative axes
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/udev: Adding input device ImPS/2 Generic Wheel Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(EE) NVIDIA(0): Error recovery failed.
(EE) NVIDIA(0):  *** Aborting ***
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Initialized AGP GART.
(WW) NVIDIA(0): The NVIDIA X driver has encountered too many errors.  Falling
(WW) NVIDIA(0):     back to legacy PCI mode.
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "1024x768"

____________________________________________

/etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


____________________________________________

Skipping ldd output (glxinfo not found)

____________________________________________

/usr/bin/lspci -d "10de:*" -v -xxx

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a2)
    Subsystem: XFX Pine Group Inc. Device 2249
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
    Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at e1000000 (32-bit, non-prefetchable) [size=16M]
    [virtual] Expansion ROM at e2000000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [44] AGP version 3.0
    Kernel driver in use: nvidia
    Kernel modules: nvidia-current, nvidia-173, nvidiafb, nouveau
00: de 10 e0 02 07 00 b0 02 a2 00 00 03 00 f8 00 00
10: 00 00 00 e0 08 00 00 d0 00 00 00 e1 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 82 16 49 22
30: 00 00 00 00 60 00 00 00 00 00 00 00 0b 01 05 01
40: 00 00 00 00 02 00 30 00 17 02 00 1f 04 01 00 1f
50: 00 00 00 00 01 00 00 00 ce d6 23 00 0f 00 00 00
60: 01 44 02 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 80 00 00 01 04 40 c1 00 00 00 00
a0: 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


____________________________________________

/usr/bin/lspci -t

-[0000:00]-+-00.0
           +-01.0-[0000:01]----00.0
           +-0c.0
           +-10.0
           +-10.1
           +-10.2
           +-10.3
           +-11.0
           +-11.1
           +-11.5
           \-12.0

____________________________________________

/usr/sbin/dmidecode

# dmidecode 2.9
SMBIOS 2.2 present.
37 structures occupying 958 bytes.
Table at 0x000F0800.

Handle 0x0000, DMI type 0, 19 bytes
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: 6.00 PG
    Release Date: 09/03/2003
    Address: 0xE0000
    Runtime Size: 128 kB
    ROM Size: 256 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PNP is supported
        APM is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/360 KB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
    Manufacturer: VIA Technologies, Inc.
    Product Name: KT333-8235
    Version:  
    Serial Number:  
    UUID: Not Present
    Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
    Manufacturer:  
    Product Name: KT333-8235
    Version:  
    Serial Number:  

Handle 0x0003, DMI type 3, 13 bytes
Chassis Information
    Manufacturer:  
    Type: Desktop
    Lock: Not Present
    Version:  
    Serial Number:  
    Asset Tag:  
    Boot-up State: Unknown
    Power Supply State: Unknown
    Thermal State: Unknown
    Security Status: Unknown

Handle 0x0004, DMI type 4, 32 bytes
Processor Information
    Socket Designation: Socket A
    Type: Central Processor
    Family: Duron
    Manufacturer: AMD
    ID: A0 06 00 00 FF FB 83 03
    Signature: Family 6, Model 10, Stepping 0
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        MMX (MMX technology supported)
        FXSR (Fast floating-point save and restore)
        SSE (Streaming SIMD extensions)
    Version: AMD Athlon(tm) XP
    Voltage: 3.3 V
    External Clock: 166 MHz
    Max Speed: 1500 MHz
    Current Speed: 2166 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    L1 Cache Handle: 0x0009
    L2 Cache Handle: 0x000A
    L3 Cache Handle: No L3 Cache

Handle 0x0005, DMI type 5, 22 bytes
Memory Controller Information
    Error Detecting Method: None
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: Four-way Interleave
    Maximum Memory Module Size: 32 MB
    Maximum Total Memory Size: 96 MB
    Supported Speeds:
        70 ns
        60 ns
    Supported Memory Types:
        Standard
        EDO
    Memory Module Voltage: 5.0 V
    Associated Memory Slots: 3
        0x0006
        0x0007
        0x0008
    Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 0 1
    Current Speed: 60 ns
    Type: Other SDRAM
    Installed Size: 512 MB (Double-bank Connection)
    Enabled Size: 512 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: 2
    Current Speed: 60 ns
    Type: Other SDRAM
    Installed Size: 512 MB (Single-bank Connection)
    Enabled Size: 512 MB (Single-bank Connection)
    Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A2
    Bank Connections: 4 5
    Current Speed: 60 ns
    Type: Other SDRAM
    Installed Size: 512 MB (Double-bank Connection)
    Enabled Size: 512 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Internal Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 128 KB
    Maximum Size: 128 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x000A, DMI type 7, 19 bytes
Cache Information
    Socket Designation: External Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Back
    Location: External
    Installed Size: 512 KB
    Maximum Size: 512 KB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Unknown
    System Type: Unknown
    Associativity: Unknown

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PRIMARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SECONDARY IDE
    Internal Connector Type: On Board IDE
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: Other

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FDD
    Internal Connector Type: On Board Floppy
    External Reference Designator: Not Specified
    External Connector Type: None
    Port Type: 8251 FIFO Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM1
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: COM2
    Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
    External Reference Designator:  
    External Connector Type: DB-9 male
    Port Type: Serial Port 16450 Compatible

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: LPT1
    Internal Connector Type: DB-25 female
    External Reference Designator:  
    External Connector Type: DB-25 female
    Port Type: Parallel Port ECP/EPP

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Keyboard
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Keyboard Port

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: PS/2 Mouse
    Internal Connector Type: PS/2
    External Reference Designator:  
    External Connector Type: PS/2
    Port Type: Mouse Port

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: USB
    External Connector Type: Other
    Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Not Specified
    Internal Connector Type: None
    External Reference Designator: AUDIO
    External Connector Type: None
    Port Type: Audio Port

Handle 0x0015, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI0
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 1
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x0016, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI1
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 2
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x0017, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI2
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 3
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x0018, DMI type 9, 13 bytes
System Slot Information
    Designation: PCI3
    Type: 32-bit PCI
    Current Usage: Available
    Length: Long
    ID: 4
    Characteristics:
        5.0 V is provided
        PME signal is supported

Handle 0x0019, DMI type 9, 13 bytes
System Slot Information
    Designation: AGP
    Type: 32-bit AGP
    Current Usage: Available
    Length: Long
    ID: 8
    Characteristics:
        5.0 V is provided

Handle 0x001A, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 3
        n|US|iso8859-1
        n|US|iso8859-1
        r|CA|iso8859-1
    Currently Installed Language: n|US|iso8859-1

Handle 0x001B, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 768 MB
    Error Information Handle: Not Provided
    Number Of Devices: 3

Handle 0x001C, DMI type 17, 21 bytes
Memory Device
    Array Handle: 0x001B
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: Unknown
    Type Detail: None

Handle 0x001D, DMI type 17, 21 bytes
Memory Device
    Array Handle: 0x001B
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A1
    Bank Locator: Bank2/3
    Type: Unknown
    Type Detail: None

Handle 0x001E, DMI type 17, 21 bytes
Memory Device
    Array Handle: 0x001B
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: 512 MB
    Form Factor: DIMM
    Set: None
    Locator: A2
    Bank Locator: Bank4/5
    Type: Unknown
    Type Detail: None

Handle 0x001F, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0005FFFFFFF
    Range Size: 1536 MB
    Physical Array Handle: 0x001B
    Partition Width: 0

Handle 0x0020, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0001FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x001C
    Memory Array Mapped Address Handle: 0x001F
    Partition Row Position: 1

Handle 0x0021, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00020000000
    Ending Address: 0x0003FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x001D
    Memory Array Mapped Address Handle: 0x001F
    Partition Row Position: 1

Handle 0x0022, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00040000000
    Ending Address: 0x0005FFFFFFF
    Range Size: 512 MB
    Physical Device Handle: 0x001E
    Memory Array Mapped Address Handle: 0x001F
    Partition Row Position: 1

Handle 0x0023, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0x0024, DMI type 127, 4 bytes
End Of Table


____________________________________________

/sbin/modinfo nvidia | grep vermagic


____________________________________________

Scanning kernel log files for NVRM messages:

  /var/log/messages:
Sep  7 16:35:28 hugo-kiste kernel: [  442.742657] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Sep  7 20:33:40 hugo-kiste kernel: [   18.505744] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Sep  7 20:46:39 hugo-kiste kernel: [   18.756419] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Sep  7 21:22:39 hugo-kiste kernel: [   18.768254] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Sep  7 21:51:18 hugo-kiste kernel: [   18.070364] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
Sep  7 23:21:05 hugo-kiste kernel: [   23.725559] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
Sep  8 14:01:59 hugo-kiste kernel: [   30.280251] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
Sep  8 21:20:34 hugo-kiste kernel: [   24.639175] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
Sep  9 00:01:46 hugo-kiste kernel: [   33.098036] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Sep  9 00:46:03 hugo-kiste kernel: [   24.301908] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.24  Thu Apr 22 09:18:20 PDT 2010
Sep  9 03:09:17 hugo-kiste kernel: [   28.466486] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
Sep  9 18:05:54 hugo-kiste kernel: [   28.481790] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
Sep  9 21:44:09 hugo-kiste kernel: [   28.161377] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
Sep  9 23:34:56 hugo-kiste kernel: [   28.656863] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
Sep 10 03:02:49 hugo-kiste kernel: [   28.070849] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
/var/log/kernel.log is not readable

____________________________________________

dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 (Ubuntu 2.6.32-24.42-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  BIOS-e820: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x5fff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-C7FFF write-protect
[    0.000000]   C8000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-protect
[    0.000000]   F0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FC0000000 write-back
[    0.000000]   1 base 040000000 mask FE0000000 write-back
[    0.000000]   2 base 0C0000000 mask FF0000000 write-combining
[    0.000000]   3 base 0C0000000 mask FF0000000 write-combining
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005fff0000 (usable)
[    0.000000]  modified: 000000005fff0000 - 000000005fff3000 (ACPI NVS)
[    0.000000]  modified: 000000005fff3000 - 0000000060000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37367000 - 37fefe84
[    0.000000] Allocated new RAMDISK: 008e2000 - 0156ae84
[    0.000000] Move RAMDISK from 0000000037367000 - 0000000037fefe83 to 008e2000 - 0156ae83
[    0.000000] ACPI: RSDP 000f6f60 00014 (v00 VKT333)
[    0.000000] ACPI: RSDT 5fff3000 0002C (v01 VKT333 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: FACP 5fff3040 00074 (v01 VKT333 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: DSDT 5fff30c0 03E82 (v01 VKT333 AWRDACPI 00001000 MSFT 0100000D)
[    0.000000] ACPI: FACS 5fff0000 00040
[    0.000000] ACPI: APIC 5fff6f80 00054 (v01 VKT333 AWRDACPI 42302E31 AWRD 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 647MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008ddeb8]    TEXT DATA BSS ==> [0000100000 - 00008ddeb8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008de000 - 00008e108a]              BRK ==> [00008de000 - 00008e108a]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e2000 - 000156ae84]      NEW RAMDISK ==> [00008e2000 - 000156ae84]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f54a0] f54a0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005fff0
[    0.000000] On node 0 totalpages: 393087
[    0.000000] free_area_init_node: node 0, pgdat c079a780, node_mem_map c156c200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1296 pages used for memmap
[    0.000000]   HighMem zone: 164578 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:9ec00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2400000 s36056 r0 d21288 u4194304
[    0.000000] pcpu-alloc: s36056 r0 d21288 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 390015
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=953e8e4b-be05-483b-a980-bce770fc5c4b ro nomodeset
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7863680 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005fff0)
[    0.000000] Memory: 1529636k/1572800k available (4679k kernel code, 41780k reserved, 2124k data, 660k init, 663496k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084a000   ( 660 kB)
[    0.000000]       .data : 0xc0591e33 - 0xc07a4e88   (2124 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591e33   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2157.935 MHz processor.
[    0.008008] Calibrating delay loop (skipped), value calculated using timer frequency.. 4315.87 BogoMIPS (lpj=8631740)
[    0.008154] Security Framework initialized
[    0.008258] AppArmor: AppArmor initialized
[    0.008326] Mount-cache hash table entries: 512
[    0.008583] Initializing cgroup subsys ns
[    0.008647] Initializing cgroup subsys cpuacct
[    0.008709] Initializing cgroup subsys memory
[    0.008781] Initializing cgroup subsys devices
[    0.008842] Initializing cgroup subsys freezer
[    0.008902] Initializing cgroup subsys net_cls
[    0.008991] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.009055] CPU: L2 Cache: 512K (64 bytes/line)
[    0.009118] mce: CPU supports 4 MCE banks
[    0.009205] Performance Events: AMD PMU driver.
[    0.009315] ... version:                0
[    0.009374] ... bit width:              48
[    0.009433] ... generic registers:      4
[    0.009492] ... value mask:             0000ffffffffffff
[    0.009553] ... max period:             00007fffffffffff
[    0.009614] ... fixed-purpose events:   0
[    0.009673] ... event mask:             000000000000000f
[    0.009738] Checking 'hlt' instruction... OK.
[    0.024729] SMP alternatives: switching to UP code
[    0.031296] Freeing SMP alternatives: 19k freed
[    0.031393] ACPI: Core revision 20090903
[    0.040052] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040133] ftrace: allocating 21780 entries in 43 pages
[    0.048045] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.049176] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.088923] CPU0: AMD Athlon(tm) XP 3000+ stepping 00
[    0.092001] Brought up 1 CPUs
[    0.092001] Total of 1 processors activated (4315.87 BogoMIPS).
[    0.092001] CPU0 attaching NULL sched-domain.
[    0.092001] devtmpfs: initialized
[    0.092001] regulator: core version 0.5
[    0.092001] Time:  1:02:14  Date: 09/10/10
[    0.092001] NET: Registered protocol family 16
[    0.092001] EISA bus registered
[    0.092001] ACPI: bus type pci registered
[    0.092001] PCI: PCI BIOS revision 2.10 entry at 0xfb3b0, last bus=1
[    0.092001] PCI: Using configuration type 1 for base access
[    0.092130] bio: create slab <bio-0> at 0
[    0.092749] ACPI: EC: Look up EC in DSDT
[    0.098491] ACPI: Interpreter enabled
[    0.098560] ACPI: (supports S0 S1 S3 S4 S5)
[    0.098865] ACPI: Using IOAPIC for interrupt routing
[    0.103695] ACPI: No dock devices found.
[    0.103883] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.104008] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xc0000000-0xcfffffff]
[    0.104109] pci 0000:00:01.0: supports D1
[    0.104153] pci 0000:00:0c.0: reg 10 io port: [0xd000-0xd0ff]
[    0.104161] pci 0000:00:0c.0: reg 14 32bit mmio: [0xe3000000-0xe3000fff]
[    0.104250] pci 0000:00:10.0: reg 20 io port: [0xd400-0xd41f]
[    0.104276] pci 0000:00:10.0: supports D1 D2
[    0.104279] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.104344] pci 0000:00:10.0: PME# disabled
[    0.104450] pci 0000:00:10.1: reg 20 io port: [0xd800-0xd81f]
[    0.104476] pci 0000:00:10.1: supports D1 D2
[    0.104478] pci 0000:00:10.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.104543] pci 0000:00:10.1: PME# disabled
[    0.104649] pci 0000:00:10.2: reg 20 io port: [0xdc00-0xdc1f]
[    0.104675] pci 0000:00:10.2: supports D1 D2
[    0.104677] pci 0000:00:10.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.104742] pci 0000:00:10.2: PME# disabled
[    0.104834] pci 0000:00:10.3: reg 10 32bit mmio: [0xe3001000-0xe30010ff]
[    0.104877] pci 0000:00:10.3: supports D1 D2
[    0.104879] pci 0000:00:10.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.104944] pci 0000:00:10.3: PME# disabled
[    0.105067] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.105135] pci 0000:00:11.0: quirk: region 4000-407f claimed by vt8235 PM
[    0.105200] pci 0000:00:11.0: quirk: region 5000-500f claimed by vt8235 SMB
[    0.105326] pci 0000:00:11.1: reg 20 io port: [0xe000-0xe00f]
[    0.105390] pci 0000:00:11.5: reg 10 io port: [0xe400-0xe4ff]
[    0.105435] pci 0000:00:11.5: supports D1 D2
[    0.105470] pci 0000:00:12.0: reg 10 io port: [0xe800-0xe8ff]
[    0.105478] pci 0000:00:12.0: reg 14 32bit mmio: [0xe3002000-0xe30020ff]
[    0.105517] pci 0000:00:12.0: supports D1 D2
[    0.105519] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.105584] pci 0000:00:12.0: PME# disabled
[    0.106789] pci 0000:01:00.0: reg 10 32bit mmio: [0xe0000000-0xe0ffffff]
[    0.106796] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.106804] pci 0000:01:00.0: reg 18 32bit mmio: [0xe1000000-0xe1ffffff]
[    0.106823] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.106878] pci 0000:00:01.0: bridge 32bit mmio: [0xe0000000-0xe2ffffff]
[    0.106884] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.106892] pci_bus 0000:00: on NUMA node 0
[    0.106898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.127347] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.128177] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.129000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[    0.129822] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.130635] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0
[    0.131042] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0
[    0.131475] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0
[    0.131881] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0
[    0.132229] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.132304] vgaarb: loaded
[    0.132523] SCSI subsystem initialized
[    0.132681] libata version 3.00 loaded.
[    0.132784] usbcore: registered new interface driver usbfs
[    0.132859] usbcore: registered new interface driver hub
[    0.132955] usbcore: registered new device driver usb
[    0.133168] ACPI: WMI: Mapper loaded
[    0.133227] PCI: Using ACPI for IRQ routing
[    0.133460] NetLabel: Initializing
[    0.133519] NetLabel:  domain hash size = 128
[    0.133578] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.133656] NetLabel:  unlabeled traffic allowed by default
[    0.133759] Switching to clocksource tsc
[    0.135980] AppArmor: AppArmor Filesystem Enabled
[    0.135980] pnp: PnP ACPI init
[    0.135980] ACPI: bus type pnp registered
[    0.138267] pnp: PnP ACPI: found 13 devices
[    0.138328] ACPI: ACPI bus type pnp unregistered
[    0.138391] PnPBIOS: Disabled by ACPI PNP
[    0.138466] system 00:00: iomem range 0xcec00-0xcffff has been reserved
[    0.138530] system 00:00: iomem range 0xf0000-0xf7fff could not be reserved
[    0.138594] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    0.138658] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
[    0.138722] system 00:00: iomem range 0x5fff0000-0x5fffffff could not be reserved
[    0.138796] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.138860] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.138924] system 00:00: iomem range 0x100000-0x5ffeffff could not be reserved
[    0.138997] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.139070] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.139144] system 00:00: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.139213] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.139276] system 00:02: ioport range 0x800-0x805 has been reserved
[    0.174076] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.174156] pci 0000:00:01.0:   IO window: disabled
[    0.174221] pci 0000:00:01.0:   MEM window: 0xe0000000-0xe2ffffff
[    0.174286] pci 0000:00:01.0:   PREFETCH window: 0xd0000000-0xdfffffff
[    0.174365] pci 0000:00:01.0: setting latency timer to 64
[    0.174372] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.174375] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.174378] pci_bus 0000:01: resource 1 mem: [0xe0000000-0xe2ffffff]
[    0.174381] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.174428] NET: Registered protocol family 2
[    0.174597] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.175184] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.177153] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.178258] TCP: Hash tables configured (established 131072 bind 65536)
[    0.178323] TCP reno registered
[    0.178522] NET: Registered protocol family 1
[    0.178605] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.178755] pci 0000:01:00.0: Boot video device
[    0.179054] cpufreq-nforce2: No nForce2 chipset.
[    0.179159] Scanning for low memory corruption every 60 seconds
[    0.179358] audit: initializing netlink socket (disabled)
[    0.179433] type=2000 audit(1284080534.178:1): initialized
[    0.188633] Trying to unpack rootfs image as initramfs...
[    0.198747] highmem bounce pool size: 64 pages
[    0.198820] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.204015] VFS: Disk quotas dquot_6.5.2
[    0.204156] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.204897] fuse init (API version 7.13)
[    0.205056] msgmni has been set to 1693
[    0.210578] alg: No test for stdrng (krng)
[    0.210741] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.210815] io scheduler noop registered
[    0.210875] io scheduler anticipatory registered
[    0.210934] io scheduler deadline registered
[    0.211055] io scheduler cfq registered (default)
[    0.211248] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.211341] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.211543] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.211620] ACPI: Power Button [PWRB]
[    0.211738] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.211818] ACPI: Sleep Button [SLPB]
[    0.211939] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.212012] ACPI: Power Button [PWRF]
[    0.212119] fan PNP0C0B:00: registered as cooling_device0
[    0.212185] ACPI: Fan [FAN] (on)
[    0.212528] Marking TSC unstable due to TSC halts in idle
[    0.212671] processor LNXCPU:00: registered as cooling_device1
[    0.214121] thermal LNXTHERM:01: registered as thermal_zone0
[    0.214121] ACPI: Thermal Zone [THRM] (40 C)
[    0.216677] Switching to clocksource acpi_pm
[    0.216780] isapnp: Scanning for PnP cards...
[    0.225565] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.225741] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.225900] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.226272] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.226456] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.227776] brd: module loaded
[    0.276156] loop: module loaded
[    0.276372] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.277038] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[    0.277103] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[    0.277169]   alloc irq_desc for 20 on node -1
[    0.277172]   alloc kstat_irqs on node -1
[    0.277183] pata_acpi 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    0.277341] pata_acpi 0000:00:11.1: PCI INT A disabled
[    0.277741] Fixed MDIO Bus: probed
[    0.277846] PPP generic driver version 2.4.2
[    0.277955] tun: Universal TUN/TAP device driver, 1.6
[    0.278017] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.278167] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.278498] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[    0.278563] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[    0.278625]   alloc irq_desc for 21 on node -1
[    0.278627]   alloc kstat_irqs on node -1
[    0.278632] ehci_hcd 0000:00:10.3: PCI INT D -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.278729] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.278835] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.278990] ehci_hcd 0000:00:10.3: irq 21, io mem 0xe3001000
[    0.288080] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.288350] usb usb1: configuration #1 chosen from 1 choice
[    0.288455] hub 1-0:1.0: USB hub found
[    0.288531] hub 1-0:1.0: 6 ports detected
[    0.288672] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.288755] uhci_hcd: USB Universal Host Controller Interface driver
[    0.288912] uhci_hcd 0000:00:10.0: PCI INT A -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.288996] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.289104] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.289206] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000d400
[    0.289387] usb usb2: configuration #1 chosen from 1 choice
[    0.289475] hub 2-0:1.0: USB hub found
[    0.289545] hub 2-0:1.0: 2 ports detected
[    0.289652] uhci_hcd 0000:00:10.1: PCI INT B -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.289730] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.289838] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.289929] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000d800
[    0.290118] usb usb3: configuration #1 chosen from 1 choice
[    0.290206] hub 3-0:1.0: USB hub found
[    0.290275] hub 3-0:1.0: 2 ports detected
[    0.290379] uhci_hcd 0000:00:10.2: PCI INT C -> Link[ALKB] -> GSI 21 (level, low) -> IRQ 21
[    0.290457] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.290558] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.290649] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000dc00
[    0.290832] usb usb4: configuration #1 chosen from 1 choice
[    0.290919] hub 4-0:1.0: USB hub found
[    0.290988] hub 4-0:1.0: 2 ports detected
[    0.291148] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.296397] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.296478] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.296777] mice: PS/2 mouse device common for all mice
[    0.297020] rtc_cmos 00:04: RTC can wake from S4
[    0.297140] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.297247] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.297439] device-mapper: uevent: version 1.0.3
[    0.297663] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.299805] device-mapper: multipath: version 1.1.0 loaded
[    0.299870] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.300171] EISA: Probing bus 0 at eisa.0
[    0.300249] Cannot allocate resource for EISA slot 4
[    0.300309] Cannot allocate resource for EISA slot 5
[    0.300380] EISA: Detected 0 cards.
[    0.302138] cpuidle: using governor ladder
[    0.302250] cpuidle: using governor menu
[    0.302791] TCP cubic registered
[    0.303012] NET: Registered protocol family 10
[    0.303555] lo: Disabled Privacy Extensions
[    0.307989] NET: Registered protocol family 17
[    0.308163] powernow-k8: Processor cpuid 6a0 not supported
[    0.308264] Using IPI No-Shortcut mode
[    0.308480] PM: Resume from disk failed.
[    0.308500] registered taskstats version 1
[    0.308814]   Magic number: 10:831:2
[    0.309020] rtc_cmos 00:04: setting system clock to 2010-09-10 01:02:15 UTC (1284080535)
[    0.309095] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.309156] EDD information not available.
[    0.316308] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.899560] isapnp: No Plug & Play device found
[    0.949232] Freeing initrd memory: 12835k freed
[    0.970329] Freeing unused kernel memory: 660k freed
[    0.971647] Write protecting the kernel text: 4680k
[    0.971740] Write protecting the kernel read-only data: 1844k
[    0.999306] udev: starting version 151
[    1.247742] pata_via 0000:00:11.1: version 0.3.4
[    1.247771] pata_via 0000:00:11.1: PCI INT A -> Link[ALKA] -> GSI 20 (level, low) -> IRQ 20
[    1.255459] Linux agpgart interface v0.103
[    1.257638] vga16fb: initializing
[    1.257648] vga16fb: mapped to 0xc00a0000
[    1.257811] fb0: VGA16 VGA frame buffer device
[    1.263453] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.263532] via-rhine: Broken BIOS detected, avoid_D3 enabled.
[    1.263638] scsi0 : pata_via
[    1.265749] scsi1 : pata_via
[    1.270130] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
[    1.270195] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
[    1.271927] FDC 0 is a post-1991 82077
[    1.276610] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[    1.276681] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[    1.276747]   alloc irq_desc for 23 on node -1
[    1.276750]   alloc kstat_irqs on node -1
[    1.276761] via-rhine 0000:00:12.0: PCI INT A -> Link[ALKD] -> GSI 23 (level, low) -> IRQ 23
[    1.281630] eth0: VIA Rhine II at 0xe3002000, 00:0a:e6:66:1d:ad, IRQ 23.
[    1.282406] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[    1.282502] agpgart: Detected VIA KT266/KY266x/KT333 chipset
[    1.298372] agpgart-via 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.298499]   alloc irq_desc for 16 on node -1
[    1.298502]   alloc kstat_irqs on node -1
[    1.298513] aic7xxx 0000:00:0c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.299704] ahc_pci:0:12:0: Host Adapter Bios disabled.  Using default SCSI device parameters
[    1.604590] ata1.00: ATA-6: ST340014A, 3.06, max UDMA/100
[    1.604654] ata1.00: 78165360 sectors, multi 16: LBA48 
[    1.604742] ata1.01: ATAPI: IDE DVD-ROM 16X, VER 2.21, max UDMA/33
[    1.620433] ata1.00: configured for UDMA/100
[    1.628402] ata1.01: configured for UDMA/33
[    1.628824] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        3.06 PQ: 0 ANSI: 5
[    1.629119] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.629710] scsi 0:0:1:0: CD-ROM            IDE      DVD-ROM 16X      2.21 PQ: 0 ANSI: 5
[    1.630551] sr0: scsi3-mmc drive: 4x/48x cd/rw xa/form2 cdda tray
[    1.630616] Uniform CD-ROM driver Revision: 3.20
[    1.630944] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.631076] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.631380] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.631525] sd 0:0:0:0: [sda] Write Protect is off
[    1.631587] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.631618] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.631847]  sda: sda1 sda2 < sda5 >
[    1.661143] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.968591] ata2.00: ATA-6: ST3120023A, 3.30, max UDMA/100
[    1.968654] ata2.00: 234441648 sectors, multi 16: LBA 
[    1.968744] ata2.01: ATAPI: HL-DT-ST DVDRAM GSA-4167B, DL11, max UDMA/33
[    1.984452] ata2.00: configured for UDMA/100
[    2.000270] ata2.01: configured for UDMA/33
[    2.002705] scsi 1:0:0:0: Direct-Access     ATA      ST3120023A       3.30 PQ: 0 ANSI: 5
[    2.002971] sd 1:0:0:0: Attached scsi generic sg2 type 0
[    2.005221] sd 1:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    2.005354] sd 1:0:0:0: [sdb] Write Protect is off
[    2.005416] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.005447] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.005699]  sdb:
[    2.009213] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVDRAM GSA-4167B DL11 PQ: 0 ANSI: 5
[    2.055274] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.055840] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    2.056091] sr 1:0:1:0: Attached scsi generic sg3 type 5
[    2.090569]  [LDM] sdb1
[    2.091583] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.294838] Console: switching to colour frame buffer device 80x30
[   16.304040] scsi2 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   16.304043]         <Adaptec 2902/04/10/15/20C/30C SCSI adapter>
[   16.304045]         aic7850: Single Channel A, SCSI Id=7, 3/253 SCBs
[   16.304046] 
[   16.540820] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   25.412167] Adding 1648632k swap on /dev/sda5.  Priority:-1 extents:1 across:1648632k 
[   25.437742] udev: starting version 151
[   25.591028] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   25.677547] lp: driver loaded but no devices found
[   26.055432] parport_pc 00:0a: reported by Plug and Play ACPI
[   26.055534] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   26.060356] irda_init()
[   26.060387] NET: Registered protocol family 23
[   26.152333] lp0: using parport0 (interrupt-driven).
[   26.206992] psmouse serio1: ID: 10 00 64
[   26.253389] type=1505 audit(1284080561.442:2):  operation="profile_load" pid=546 name="/sbin/dhclient3"
[   26.253716] type=1505 audit(1284080561.442:3):  operation="profile_load" pid=546 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   26.253904] type=1505 audit(1284080561.442:4):  operation="profile_load" pid=546 name="/usr/lib/connman/scripts/dhclient-script"
[   26.730421] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   27.104070] nvidia: module license 'NVIDIA' taints kernel.
[   27.104078] Disabling lock debugging due to kernel taint
[   27.633455] ppdev: user-space parallel port driver
[   28.068615] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   28.068620] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   28.068628]   alloc irq_desc for 22 on node -1
[   28.068630]   alloc kstat_irqs on node -1
[   28.068641] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[   28.068809] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   28.069030] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.070849] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
[   34.238691] type=1505 audit(1284080569.426:5):  operation="profile_replace" pid=729 name="/sbin/dhclient3"
[   34.239029] type=1505 audit(1284080569.426:6):  operation="profile_replace" pid=729 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   34.239219] type=1505 audit(1284080569.426:7):  operation="profile_replace" pid=729 name="/usr/lib/connman/scripts/dhclient-script"
[   34.271574] type=1505 audit(1284080569.458:8):  operation="profile_load" pid=731 name="/usr/bin/evince"
[   34.295474] type=1505 audit(1284080569.482:9):  operation="profile_load" pid=731 name="/usr/bin/evince-previewer"
[   34.318321] type=1505 audit(1284080569.506:10):  operation="profile_load" pid=731 name="/usr/bin/evince-thumbnailer"
[   34.330817] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   34.358142] type=1505 audit(1284080569.546:11):  operation="profile_load" pid=798 name="/usr/lib/cups/backend/cups-pdf"
[   34.358563] type=1505 audit(1284080569.546:12):  operation="profile_load" pid=798 name="/usr/sbin/cupsd"
[   34.369759] type=1505 audit(1284080569.558:13):  operation="profile_load" pid=801 name="/usr/sbin/tcpdump"
[   35.689904] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   35.689925] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   35.689984] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   44.344032] eth0: no IPv6 routers present
[  432.366252] NVRM: Xid (0001:00): 6, PE0000 0998 00ffffff 00005f44 00000000 00000000
[  432.417668] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[  432.435949] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[  432.454287] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[  432.472623] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[  432.490869] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[  432.509209] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[  432.527494] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[ 1897.829181] SysRq : SAK
[ 1897.829215] SAK: killed process 839 (Xorg): task_session(p)==tty->session
[ 1897.829299] SAK: killed process 733 (console-kit-dae): fd#11 opened to the tty
[ 1897.829411] SAK: killed process 734 (console-kit-dae): fd#11 opened to the tty
[ 1897.829415] SAK: killed process 735 (console-kit-dae): fd#11 opened to the tty
[ 1897.829418] SAK: killed process 737 (console-kit-dae): fd#11 opened to the tty
[ 1897.829421] SAK: killed process 738 (console-kit-dae): fd#11 opened to the tty
[ 1897.829423] SAK: killed process 739 (console-kit-dae): fd#11 opened to the tty
[ 1897.829426] SAK: killed process 740 (console-kit-dae): fd#11 opened to the tty
[ 1897.829429] SAK: killed process 741 (console-kit-dae): fd#11 opened to the tty
[ 1897.829432] SAK: killed process 742 (console-kit-dae): fd#11 opened to the tty
[ 1897.829435] SAK: killed process 743 (console-kit-dae): fd#11 opened to the tty
[ 1897.829438] SAK: killed process 744 (console-kit-dae): fd#11 opened to the tty
[ 1897.829440] SAK: killed process 745 (console-kit-dae): fd#11 opened to the tty
[ 1897.829444] SAK: killed process 746 (console-kit-dae): fd#11 opened to the tty
[ 1897.829446] SAK: killed process 747 (console-kit-dae): fd#11 opened to the tty
[ 1897.829449] SAK: killed process 748 (console-kit-dae): fd#11 opened to the tty
[ 1897.829452] SAK: killed process 749 (console-kit-dae): fd#11 opened to the tty
[ 1897.829455] SAK: killed process 750 (console-kit-dae): fd#11 opened to the tty
[ 1897.829458] SAK: killed process 751 (console-kit-dae): fd#11 opened to the tty
[ 1897.829461] SAK: killed process 752 (console-kit-dae): fd#11 opened to the tty
[ 1897.829464] SAK: killed process 753 (console-kit-dae): fd#11 opened to the tty
[ 1897.829466] SAK: killed process 754 (console-kit-dae): fd#11 opened to the tty
[ 1897.829469] SAK: killed process 755 (console-kit-dae): fd#11 opened to the tty
[ 1897.829472] SAK: killed process 756 (console-kit-dae): fd#11 opened to the tty
[ 1897.829475] SAK: killed process 757 (console-kit-dae): fd#11 opened to the tty
[ 1897.829478] SAK: killed process 758 (console-kit-dae): fd#11 opened to the tty
[ 1897.829481] SAK: killed process 759 (console-kit-dae): fd#11 opened to the tty
[ 1897.829483] SAK: killed process 760 (console-kit-dae): fd#11 opened to the tty
[ 1897.829486] SAK: killed process 761 (console-kit-dae): fd#11 opened to the tty
[ 1897.829489] SAK: killed process 762 (console-kit-dae): fd#11 opened to the tty
[ 1897.829492] SAK: killed process 763 (console-kit-dae): fd#11 opened to the tty
[ 1897.829495] SAK: killed process 764 (console-kit-dae): fd#11 opened to the tty
[ 1897.829497] SAK: killed process 765 (console-kit-dae): fd#11 opened to the tty
[ 1897.829500] SAK: killed process 766 (console-kit-dae): fd#11 opened to the tty
[ 1897.829503] SAK: killed process 767 (console-kit-dae): fd#11 opened to the tty
[ 1897.829506] SAK: killed process 768 (console-kit-dae): fd#11 opened to the tty
[ 1897.829509] SAK: killed process 769 (console-kit-dae): fd#11 opened to the tty
[ 1897.829512] SAK: killed process 770 (console-kit-dae): fd#11 opened to the tty
[ 1897.829514] SAK: killed process 771 (console-kit-dae): fd#11 opened to the tty
[ 1897.829517] SAK: killed process 772 (console-kit-dae): fd#11 opened to the tty
[ 1897.829520] SAK: killed process 773 (console-kit-dae): fd#11 opened to the tty
[ 1897.829523] SAK: killed process 774 (console-kit-dae): fd#11 opened to the tty
[ 1897.829526] SAK: killed process 775 (console-kit-dae): fd#11 opened to the tty
[ 1897.829529] SAK: killed process 776 (console-kit-dae): fd#11 opened to the tty
[ 1897.829532] SAK: killed process 777 (console-kit-dae): fd#11 opened to the tty
[ 1897.829534] SAK: killed process 778 (console-kit-dae): fd#11 opened to the tty
[ 1897.829537] SAK: killed process 779 (console-kit-dae): fd#11 opened to the tty
[ 1897.829540] SAK: killed process 780 (console-kit-dae): fd#11 opened to the tty
[ 1897.829543] SAK: killed process 781 (console-kit-dae): fd#11 opened to the tty
[ 1897.829546] SAK: killed process 782 (console-kit-dae): fd#11 opened to the tty
[ 1897.829549] SAK: killed process 783 (console-kit-dae): fd#11 opened to the tty
[ 1897.829552] SAK: killed process 784 (console-kit-dae): fd#11 opened to the tty
[ 1897.829554] SAK: killed process 785 (console-kit-dae): fd#11 opened to the tty
[ 1897.829557] SAK: killed process 786 (console-kit-dae): fd#11 opened to the tty
[ 1897.829560] SAK: killed process 787 (console-kit-dae): fd#11 opened to the tty
[ 1897.829563] SAK: killed process 788 (console-kit-dae): fd#11 opened to the tty
[ 1897.829566] SAK: killed process 789 (console-kit-dae): fd#11 opened to the tty
[ 1897.829569] SAK: killed process 790 (console-kit-dae): fd#11 opened to the tty
[ 1897.829571] SAK: killed process 791 (console-kit-dae): fd#11 opened to the tty
[ 1897.829574] SAK: killed process 792 (console-kit-dae): fd#11 opened to the tty
[ 1897.829577] SAK: killed process 793 (console-kit-dae): fd#11 opened to the tty
[ 1897.829580] SAK: killed process 794 (console-kit-dae): fd#11 opened to the tty
[ 1897.829583] SAK: killed process 795 (console-kit-dae): fd#11 opened to the tty
[ 1897.829586] SAK: killed process 800 (console-kit-dae): fd#11 opened to the tty
[ 1897.829589] SAK: killed process 2582 (console-kit-dae): fd#11 opened to the tty
[ 1897.829599] SAK: killed process 839 (Xorg): task_session(p)==tty->session
[ 1898.564964] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[ 1898.564986] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[ 1898.565043] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[ 2009.939422] NVRM: Xid (0001:00): 6, PE0002 0404 00010200 0000fdf8 0008007f 00000000
[ 2010.056867] NVRM: Xid (0001:00): 1, Channel 00000002 Method 00000000 Data beef0200
[ 2010.118131] NVRM: Xid (0001:00): 1, Channel 00000002 Method 00000000 Data beef0200
[ 2010.168857] NVRM: Xid (0001:00): 1, Channel 00000002 Method 00000000 Data beef0200
[ 2010.225880] NVRM: Xid (0001:00): 6, PE0002 0000 beef0200 00000000 0000007f 00000000
[ 2010.274411] NVRM: Xid (0001:00): 1, Channel 00000002 Method 00000000 Data beef0200
[ 2010.334406] NVRM: Xid (0001:00): 1, Channel 00000002 Method 00000000 Data beef0200
[ 2010.387031] NVRM: Xid (0001:00): 1, Channel 00000002 Method 00000000 Data beef0200
[ 2050.489119] SysRq : SAK
[ 2050.489328] SAK: killed process 3553 (Xorg): task_session(p)==tty->session
[ 2050.489575] SAK: killed process 3553 (Xorg): task_session(p)==tty->session
[ 2050.916412] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[ 2050.916433] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[ 2050.916491] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[ 2133.602233] NVRM: Xid (0001:00): 6, PE0000 0ffc 00ffffff 0000efd0 00ffffff 00000000
[ 2133.651634] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[ 2133.669920] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[ 2133.688228] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[ 2133.706482] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[ 2133.724762] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[ 2133.743059] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[ 2133.761379] NVRM: Xid (0001:00): 6, PE0000 0180 01017c00 0000005c 00000000 01010201
[ 3505.507439] SysRq : SAK
[ 3505.507480] SAK: killed process 4016 (Xorg): task_session(p)==tty->session
[ 3505.507726] SAK: killed process 4016 (Xorg): task_session(p)==tty->session
[ 3505.915944] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[ 3505.915965] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[ 3505.916052] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[ 5249.244035] usb 1-1: new high speed USB device using ehci_hcd and address 2
[ 5249.379081] usb 1-1: configuration #1 chosen from 1 choice
[ 5249.432237] Initializing USB Mass Storage driver...
[ 5249.432434] scsi3 : SCSI emulation for USB Mass Storage devices
[ 5249.432668] usbcore: registered new interface driver usb-storage
[ 5249.432672] USB Mass Storage support registered.
[ 5249.444455] usb-storage: device found at 2
[ 5249.444460] usb-storage: waiting for device to settle before scanning
[ 5250.990319] usb 1-1: USB disconnect, address 2
[ 5252.392035] usb 1-1: new high speed USB device using ehci_hcd and address 3
[ 5252.527169] usb 1-1: configuration #1 chosen from 1 choice
[ 5252.540313] scsi4 : SCSI emulation for USB Mass Storage devices
[ 5252.545560] usb-storage: device found at 3
[ 5252.545564] usb-storage: waiting for device to settle before scanning
[ 5252.902324] usb 1-1: USB disconnect, address 3
[ 5257.176035] usb 1-2: new high speed USB device using ehci_hcd and address 4
[ 5257.311127] usb 1-2: configuration #1 chosen from 1 choice
[ 5257.324194] scsi5 : SCSI emulation for USB Mass Storage devices
[ 5257.330624] usb-storage: device found at 4
[ 5257.330629] usb-storage: waiting for device to settle before scanning
[ 5262.328325] usb-storage: device scan complete
[ 5262.328911] scsi 5:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 5262.332939] sd 5:0:0:0: Attached scsi generic sg4 type 0
[ 5264.531245] sd 5:0:0:0: [sdc] 15874048 512-byte logical blocks: (8.12 GB/7.56 GiB)
[ 5264.531725] sd 5:0:0:0: [sdc] Write Protect is off
[ 5264.531729] sd 5:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 5264.531732] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 5264.535978] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 5264.535989]  sdc: sdc1
[ 5264.585980] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 5264.585990] sd 5:0:0:0: [sdc] Attached SCSI removable disk
____________________________________________

Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.3-4ubuntu5' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-plugin --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 
____________________________________________

xset -q:

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  20
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 600    Off: 660
  DPMS is Enabled
  Monitor is On
____________________________________________

nvidia-settings -q all:


Attributes queryable via hugo-kiste:0.0:

  Attribute 'OperatingSystem' (hugo-kiste:0.0): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (hugo-kiste:0.0): 173.14.22 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen.

  Attribute 'NvControlVersion' (hugo-kiste:0.0): 1.16 
    'NvControlVersion' is a string attribute.
    'NvControlVersion' is a read-only attribute.
    'NvControlVersion' can use the following target types: X Screen.

  Attribute 'GLXServerVersion' (hugo-kiste:0.0): 1.4 
    'GLXServerVersion' is a string attribute.
    'GLXServerVersion' is a read-only attribute.
    'GLXServerVersion' can use the following target types: X Screen.

  Attribute 'GLXClientVersion' (hugo-kiste:0.0): 1.4 
    'GLXClientVersion' is a string attribute.
    'GLXClientVersion' is a read-only attribute.
    'GLXClientVersion' can use the following target types: X Screen.

  Attribute 'OpenGLVersion' (hugo-kiste:0.0): 2.1.2 NVIDIA 173.14.22 
    'OpenGLVersion' is a string attribute.
    'OpenGLVersion' is a read-only attribute.
    'OpenGLVersion' can use the following target types: X Screen.

  Attribute 'XRandRVersion' (hugo-kiste:0.0): 1.3 
    'XRandRVersion' is a string attribute.
    'XRandRVersion' is a read-only attribute.
    'XRandRVersion' can use the following target types: X Screen.

  Attribute 'XF86VidModeVersion' (hugo-kiste:0.0): 2.2 
    'XF86VidModeVersion' is a string attribute.
    'XF86VidModeVersion' is a read-only attribute.
    'XF86VidModeVersion' can use the following target types: X Screen.

  Attribute 'XvVersion' (hugo-kiste:0.0): 2.2 
    'XvVersion' is a string attribute.
    'XvVersion' is a read-only attribute.
    'XvVersion' can use the following target types: X Screen.

  Attribute 'TwinView' (hugo-kiste:0.0): 0.
    'TwinView' is a boolean attribute; valid values are: 1 (on/true) and 0
    (off/false).
    'TwinView' is a read-only attribute.
    'TwinView' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (hugo-kiste:0.0): 0x00000001.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (hugo-kiste:0.0): 0x00000001.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'CursorShadow' (hugo-kiste:0.0): 0.
    'CursorShadow' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'CursorShadow' can use the following target types: X Screen.

  Attribute 'CursorShadowAlpha' (hugo-kiste:0.0): 64.
    The valid values for 'CursorShadowAlpha' are in the range 0 - 254
    (inclusive).
    'CursorShadowAlpha' can use the following target types: X Screen.

  Attribute 'CursorShadowRed' (hugo-kiste:0.0): 0.
    The valid values for 'CursorShadowRed' are in the range 0 - 255
    (inclusive).
    'CursorShadowRed' can use the following target types: X Screen.

  Attribute 'CursorShadowGreen' (hugo-kiste:0.0): 0.
    The valid values for 'CursorShadowGreen' are in the range 0 - 255
    (inclusive).
    'CursorShadowGreen' can use the following target types: X Screen.

  Attribute 'CursorShadowBlue' (hugo-kiste:0.0): 0.
    The valid values for 'CursorShadowBlue' are in the range 0 - 255
    (inclusive).
    'CursorShadowBlue' can use the following target types: X Screen.

  Attribute 'CursorShadowXOffset' (hugo-kiste:0.0): 4.
    The valid values for 'CursorShadowXOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowXOffset' can use the following target types: X Screen.

  Attribute 'CursorShadowYOffset' (hugo-kiste:0.0): 2.
    The valid values for 'CursorShadowYOffset' are in the range 0 - 32
    (inclusive).
    'CursorShadowYOffset' can use the following target types: X Screen.

  Attribute 'AssociatedDisplays' (hugo-kiste:0.0): 0x00000001.
    'AssociatedDisplays' is a bitmask attribute.
    'AssociatedDisplays' can use the following target types: X Screen.

  Attribute 'InitialPixmapPlacement' (hugo-kiste:0.0): 1.
    The valid values for 'InitialPixmapPlacement' are in the range 0 - 4
    (inclusive).
    'InitialPixmapPlacement' can use the following target types: X Screen.

  Attribute 'DynamicTwinview' (hugo-kiste:0.0): 1.
    'DynamicTwinview' is an integer attribute.
    'DynamicTwinview' is a read-only attribute.
    'DynamicTwinview' can use the following target types: X Screen.

  Attribute 'MultiGpuDisplayOwner' (hugo-kiste:0.0): 0.
    'MultiGpuDisplayOwner' is an integer attribute.
    'MultiGpuDisplayOwner' is a read-only attribute.
    'MultiGpuDisplayOwner' can use the following target types: X Screen.

  Attribute 'GlyphCache' (hugo-kiste:0.0): 0.
    The valid values for 'GlyphCache' are in the range 0 - 1 (inclusive).
    'GlyphCache' can use the following target types: X Screen.

  Attribute 'Depth30Allowed' (hugo-kiste:0.0): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

  Attribute 'SyncToVBlank' (hugo-kiste:0.0): 0.
    'SyncToVBlank' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'SyncToVBlank' can use the following target types: X Screen.

  Attribute 'LogAniso' (hugo-kiste:0.0): 0.
    The valid values for 'LogAniso' are in the range 0 - 4 (inclusive).
    'LogAniso' can use the following target types: X Screen.

  Attribute 'FSAA' (hugo-kiste:0.0): 0.
    Valid values for 'FSAA' are: 0, 1, 2, 5, 6, 7, 8 and 9.
    'FSAA' can use the following target types: X Screen.

  Attribute 'TextureSharpen' (hugo-kiste:0.0): 0.
    'TextureSharpen' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'TextureSharpen' can use the following target types: X Screen.

  Attribute 'ForceGenericCpu' (hugo-kiste:0.0): 0.
    'ForceGenericCpu' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'ForceGenericCpu' can use the following target types: X Screen.

  Attribute 'GammaCorrectedAALines' (hugo-kiste:0.0): 0.
    'GammaCorrectedAALines' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'GammaCorrectedAALines' can use the following target types: X Screen.

  Attribute 'AllowFlipping' (hugo-kiste:0.0): 1.
    'AllowFlipping' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'AllowFlipping' can use the following target types: X Screen.

  Attribute 'FSAAAppControlled' (hugo-kiste:0.0): 1.
    'FSAAAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'FSAAAppControlled' can use the following target types: X Screen.

  Attribute 'LogAnisoAppControlled' (hugo-kiste:0.0): 1.
    'LogAnisoAppControlled' is a boolean attribute; valid values are: 1
    (on/true) and 0 (off/false).
    'LogAnisoAppControlled' can use the following target types: X Screen.

  Attribute 'OpenGLImageSettings' (hugo-kiste:0.0): 2.
    The valid values for 'OpenGLImageSettings' are in the range 0 - 3
    (inclusive).
    'OpenGLImageSettings' can use the following target types: X Screen.

  Attribute 'BusType' (hugo-kiste:0.0): 0.
    The valid values for 'BusType' are in the range 0 - 3 (inclusive).
    'BusType' is a read-only attribute.
    'BusType' can use the following target types: X Screen, GPU.

  Attribute 'VideoRam' (hugo-kiste:0.0): 262144.
    'VideoRam' is an integer attribute.
    'VideoRam' is a read-only attribute.
    'VideoRam' can use the following target types: X Screen, GPU.

  Attribute 'Irq' (hugo-kiste:0.0): 16.
    'Irq' is an integer attribute.
    'Irq' is a read-only attribute.
    'Irq' can use the following target types: X Screen, GPU.

  Attribute 'GPUCoreTemp' (hugo-kiste:0.0): 44.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

  Attribute 'GPU2DClockFreqs' (hugo-kiste:0.0): 580,750.
    The valid values for 'GPU2DClockFreqs' are in the ranges 145 - 1160,
    187 - 900 (inclusive).
    'GPU2DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPU3DClockFreqs' (hugo-kiste:0.0): 580,750.
    The valid values for 'GPU3DClockFreqs' are in the ranges 145 - 1160,
    187 - 900 (inclusive).
    'GPU3DClockFreqs' can use the following target types: X Screen, GPU.

  Attribute 'GPUDefault2DClockFreqs' (hugo-kiste:0.0): 580,750.
    'GPUDefault2DClockFreqs' is a packed integer attribute.
    'GPUDefault2DClockFreqs' is a read-only attribute.
    'GPUDefault2DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUDefault3DClockFreqs' (hugo-kiste:0.0): 580,750.
    'GPUDefault3DClockFreqs' is a packed integer attribute.
    'GPUDefault3DClockFreqs' is a read-only attribute.
    'GPUDefault3DClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentClockFreqs' (hugo-kiste:0.0): 580,750.
    'GPUCurrentClockFreqs' is a packed integer attribute.
    'GPUCurrentClockFreqs' is a read-only attribute.
    'GPUCurrentClockFreqs' can use the following target types: X Screen,
    GPU.

  Attribute 'BusRate' (hugo-kiste:0.0): 4.
    The valid values for 'BusRate' are in the range 1 - 8 (inclusive).
    'BusRate' is a read-only attribute.
    'BusRate' can use the following target types: X Screen, GPU.

  Attribute 'GPUErrors' (hugo-kiste:0.0): 0.
    'GPUErrors' is an integer attribute.
    'GPUErrors' is a read-only attribute.
    'GPUErrors' can use the following target types: X Screen.

  Attribute 'GPUPowerSource' (hugo-kiste:0.0): 0.
    'GPUPowerSource' is an integer attribute.
    'GPUPowerSource' is a read-only attribute.
    'GPUPowerSource' can use the following target types: X Screen, GPU.

  Attribute 'GPUCurrentPerfMode' (hugo-kiste:0.0): 1.
    'GPUCurrentPerfMode' is an integer attribute.
    'GPUCurrentPerfMode' is a read-only attribute.
    'GPUCurrentPerfMode' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUCurrentPerfLevel' (hugo-kiste:0.0): 0.
    'GPUCurrentPerfLevel' is an integer attribute.
    'GPUCurrentPerfLevel' is a read-only attribute.
    'GPUCurrentPerfLevel' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUAdaptiveClockState' (hugo-kiste:0.0): 1.
    'GPUAdaptiveClockState' is an integer attribute.
    'GPUAdaptiveClockState' is a read-only attribute.
    'GPUAdaptiveClockState' can use the following target types: X Screen,
    GPU.

  Attribute 'GPUPerfModes' (hugo-kiste:0.0): perf=0, nvclock=580,
  memclock=750 
    'GPUPerfModes' is a string attribute.
    'GPUPerfModes' is a read-only attribute.
    'GPUPerfModes' can use the following target types: X Screen.

  Attribute 'GvoSupported' (hugo-kiste:0.0): 0.
    'GvoSupported' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'GvoSupported' is a read-only attribute.
    'GvoSupported' can use the following target types: X Screen.

  Attribute 'DigitalVibrance' (hugo-kiste:0.0; display device: CRT-0): 0.
    The valid values for 'DigitalVibrance' are in the range 0 - 63
    (inclusive).
    'DigitalVibrance' is display device specific.
    'DigitalVibrance' can use the following target types: X Screen, GPU.

  Attribute 'ImageSharpening' (hugo-kiste:0.0; display device: CRT-0): 0.
    The valid values for 'ImageSharpening' are in the range 0 - 31
    (inclusive).
    'ImageSharpening' is display device specific.
    'ImageSharpening' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate' (hugo-kiste:0.0; display device: CRT-0): 60,02
  Hz.
    'RefreshRate' is an integer attribute.
    'RefreshRate' is a read-only attribute.
    'RefreshRate' is display devThe program 'nvidia-settings' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 593 error_code 8 request_code 140 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
ice specific.
    'RefreshRate' can use the following target types: X Screen, GPU.

  Attribute 'RefreshRate3' (hugo-kiste:0.0; display device: CRT-0): 60,020
  Hz.
    'RefreshRate3' is an integer attribute.
    'RefreshRate3' is a read-only attribute.
    'RefreshRate3' is display device specific.
    'RefreshRate3' can use the following target types: X Screen, GPU.

  Attribute 'XVideoTextureSyncToVBlank' (hugo-kiste:0.0): 1.
    The valid values for 'XVideoTextureSyncToVBlank' are in the range 0 - 1
    (inclusive).
    'XVideoTextureSyncToVBlank' can use the following target types: X
    Screen.

  Attribute 'XVideoBlitterSyncToVBlank' (hugo-kiste:0.0): 0.
    The valid values for 'XVideoBlitterSyncToVBlank' are in the range 0 - 1
    (inclusive).
    'XVideoBlitterSyncToVBlank' can use the following target types: X
    Screen.

  Attribute 'XVideoSyncToDisplay' (hugo-kiste:0.0): 0x00000001.
    'XVideoSyncToDisplay' is a bitmask attribute.
    'XVideoSyncToDisplay' can use the following target types: X Screen.

Attributes queryable via hugo-kiste:0[gpu:0]:

  Attribute 'OperatingSystem' (hugo-kiste:0[gpu:0]): 0.
    The valid values for 'OperatingSystem' are in the range 0 - 2
    (inclusive).
    'OperatingSystem' is a read-only attribute.
    'OperatingSystem' can use the following target types: X Screen, GPU.

  Attribute 'NvidiaDriverVersion' (hugo-kiste:0[gpu:0]): 173.14.22 
    'NvidiaDriverVersion' is a string attribute.
    'NvidiaDriverVersion' is a read-only attribute.
    'NvidiaDriverVersion' can use the following target types: X Screen.

  Attribute 'ConnectedDisplays' (hugo-kiste:0[gpu:0]): 0x00000001.
    'ConnectedDisplays' is a bitmask attribute.
    'ConnectedDisplays' is a read-only attribute.
    'ConnectedDisplays' can use the following target types: X Screen, GPU.

  Attribute 'EnabledDisplays' (hugo-kiste:0[gpu:0]): 0x00000001.
    'EnabledDisplays' is a bitmask attribute.
    'EnabledDisplays' is a read-only attribute.
    'EnabledDisplays' can use the following target types: X Screen, GPU.

  Attribute 'Depth30Allowed' (hugo-kiste:0[gpu:0]): 0.
    'Depth30Allowed' is a boolean attribute; valid values are: 1 (on/true)
    and 0 (off/false).
    'Depth30Allowed' is a read-only attribute.
    'Depth30Allowed' can use the following target types: X Screen, GPU.

____________________________________________

/proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=953e8e4b-be05-483b-a980-bce770fc5c4b ro nomodeset

____________________________________________

/proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 6
model        : 10
model name    : AMD Athlon(tm) XP 3000+
stepping    : 0
cpu MHz        : 2157.935
cache size    : 512 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 1
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
bogomips    : 4315.87
clflush size    : 32
cache_alignment    : 32
address sizes    : 34 bits physical, 32 bits virtual
power management: ts


____________________________________________

/proc/interrupts
           CPU0       
  0:     221438   IO-APIC-edge      timer
  1:       2635   IO-APIC-edge      i8042
  3:          1   IO-APIC-edge    
  4:          2   IO-APIC-edge    
  6:          2   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 12:     109682   IO-APIC-edge      i8042
 14:      43587   IO-APIC-edge      pata_via
 15:      81007   IO-APIC-edge      pata_via
 16:     366894   IO-APIC-fasteoi   aic7xxx, nvidia
 21:        653   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4
 22:        540   IO-APIC-fasteoi   VIA8233
 23:     269504   IO-APIC-fasteoi   eth0
NMI:          0   Non-maskable interrupts
LOC:     224094   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         18   Machine check polls
ERR:          0
MIS:          0

____________________________________________

/proc/meminfo
MemTotal:        1544084 kB
MemFree:          155904 kB
Buffers:          124892 kB
Cached:          1081424 kB
SwapCached:            0 kB
Active:           661220 kB
Inactive:         652008 kB
Active(anon):     110336 kB
Inactive(anon):       16 kB
Active(file):     550884 kB
Inactive(file):   651992 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:        663496 kB
HighFree:          15872 kB
LowTotal:         880588 kB
LowFree:          140032 kB
SwapTotal:       1648632 kB
SwapFree:        1648632 kB
Dirty:                 0 kB
Writeback:            32 kB
AnonPages:        106908 kB
Mapped:            44268 kB
Shmem:              3444 kB
Slab:              52240 kB
SReclaimable:      45776 kB
SUnreclaim:         6464 kB
KernelStack:        1672 kB
PageTables:         3240 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2420672 kB
Committed_AS:     443856 kB
VmallocTotal:     122880 kB
VmallocUsed:       48024 kB
VmallocChunk:      61436 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       53240 kB
DirectMap4M:      856064 kB

____________________________________________

/proc/modules
usb_storage 39425 0 - Live 0xf82a6000
dm_crypt 11331 0 - Live 0xf8051000
snd_via82xx 20058 6 - Live 0xf92c2000
gameport 9089 1 snd_via82xx, Live 0xf92ad000
snd_ac97_codec 100646 1 snd_via82xx, Live 0xf9282000
ac97_bus 1002 1 snd_ac97_codec, Live 0xf9257000
snd_pcm_oss 35308 0 - Live 0xf9245000
snd_mixer_oss 13746 3 snd_pcm_oss, Live 0xf922d000
snd_pcm 70662 3 snd_via82xx,snd_ac97_codec,snd_pcm_oss, Live 0xf9209000
snd_page_alloc 7076 2 snd_via82xx,snd_pcm, Live 0xf91e7000
snd_mpu401_uart 5617 1 snd_via82xx, Live 0xf91da000
snd_seq_dummy 1338 0 - Live 0xf91cf000
snd_seq_oss 26726 0 - Live 0xf91bd000
snd_seq_midi 4557 0 - Live 0xf91a9000
snd_rawmidi 19056 2 snd_mpu401_uart,snd_seq_midi, Live 0xf9197000
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi, Live 0xf82b6000
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xf917b000
snd_timer 19098 2 snd_pcm,snd_seq, Live 0xf8253000
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xf811a000
snd 54148 19 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xf8233000
i2c_viapro 5573 0 - Live 0xf8113000
ppdev 5259 0 - Live 0xf8109000
via_ircc 21745 0 - Live 0xf805c000
nvidia 7087672 24 - Live 0xf8a3f000 (P)
psmouse 63245 0 - Live 0xf8201000
serio_raw 3978 0 - Live 0xf8038000
parport_pc 25962 1 - Live 0xf80ce000
soundcore 6620 3 snd, Live 0xf8019000
irda 186556 1 via_ircc, Live 0xf8264000
shpchp 28820 0 - Live 0xf8212000
crc_ccitt 1339 1 irda, Live 0xf81fe000
lp 7028 0 - Live 0xf811d000
parport 32635 3 ppdev,parport_pc,lp, Live 0xf80dd000
fbcon 35102 73 - Live 0xf8085000
tileblit 2031 1 fbcon, Live 0xf804e000
font 7557 1 fbcon, Live 0xf803b000
bitblit 4707 1 fbcon, Live 0xf801d000
softcursor 1189 1 bitblit, Live 0xf8120000
via_agp 5310 1 - Live 0xf8116000
aic7xxx 120719 0 - Live 0xf80e9000
vga16fb 11385 1 - Live 0xf80b4000
vgastate 8961 1 vga16fb, Live 0xf80a5000
via_rhine 19154 0 - Live 0xf8094000
mii 4381 1 via_rhine, Live 0xf8081000
floppy 53016 0 - Live 0xf8068000
scsi_transport_spi 21096 1 aic7xxx, Live 0xf8046000
pata_via 7272 2 - Live 0xf8034000
agpgart 31724 2 nvidia,via_agp, Live 0xf8024000

____________________________________________

/proc/version
Linux version 2.6.32-24-generic (buildd@palmer) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010

____________________________________________

/proc/pci does not exist

____________________________________________

/proc/iomem
00000000-0000ffff : reserved
00010000-0009fbff : System RAM
0009fc00-0009ffff : reserved
000a0000-000bffff : Video RAM area
000c0000-000cebff : Video ROM
000cec00-000cffff : pnp 00:00
000f0000-000fffff : reserved
  000f0000-000fffff : System ROM
00100000-5ffeffff : System RAM
  00100000-00591e32 : Kernel code
  00591e33-007a4e87 : Kernel data
  0084f000-008ddeb7 : Kernel bss
5fff0000-5fff2fff : ACPI Non-volatile Storage
5fff3000-5fffffff : ACPI Tables
c0000000-cfffffff : 0000:00:00.0
d0000000-dfffffff : PCI Bus 0000:01
  d0000000-dfffffff : 0000:01:00.0
e0000000-e2ffffff : PCI Bus 0000:01
  e0000000-e0ffffff : 0000:01:00.0
    e0000000-e0ffffff : nvidia
  e1000000-e1ffffff : 0000:01:00.0
  e2000000-e201ffff : 0000:01:00.0
e3000000-e3000fff : 0000:00:0c.0
  e3000000-e3000fff : aic7xxx
e3001000-e30010ff : 0000:00:10.3
  e3001000-e30010ff : ehci_hcd
e3002000-e30020ff : 0000:00:12.0
  e3002000-e30020ff : via-rhine
fec00000-fec00fff : IOAPIC 0
  fec00000-fec00fff : reserved
fee00000-fee00fff : Local APIC
  fee00000-fee00fff : reserved
    fee00000-fee00fff : pnp 00:00
fff80000-fffeffff : pnp 00:00
ffff0000-ffffffff : reserved
  ffff0000-ffffffff : pnp 00:00

____________________________________________

/proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x040000000 ( 1024MB), size=  512MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining
reg03: base=0x0c0000000 ( 3072MB), size=  256MB, count=1: write-combining

____________________________________________

/proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  173.14.22  Sun Nov  8 20:26:31 PST 2009
GCC version:  gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) 

____________________________________________

/proc/driver/nvidia/cards/0
Model:          GeForce 7600 GT
IRQ:            16
Video BIOS:      05.73.22.25.75
Card Type:      AGP
DMA Size:      32 bits
DMA Mask:      0xffffffff
Bus Location:      01.00.0

____________________________________________

/proc/driver/nvidia/agp/card
Fast Writes:      Supported
SBA:          Supported
AGP Rates:      4x 2x 1x 
Registers:      0x1f000217:0x1f000104

____________________________________________

/proc/driver/nvidia/agp/host-bridge
Host Bridge:      PCI device 1106:3099
Fast Writes:      Not Supported
SBA:          Supported
AGP Rates:      4x 2x 1x 
Registers:      0x1f000207:0x00000104

____________________________________________

/proc/driver/nvidia/agp/status
Status:      Enabled
Driver:      AGPGART
AGP Rate:      4x
Fast Writes:      Disabled
SBA:          Disabled

____________________________________________

/proc/driver/nvidia/warnings/README
The NVIDIA graphics driver tries to detect potential problems
with the host system and warns about them using the system's
logging mechanisms. Important warning message are also logged
to dedicated text files in this directory.

____________________________________________

/proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
MapRegistersEarly: 0
RegistryDwords: ""

____________________________________________

End of NVIDIA bug report log file.
```




###
That's enough for today :mrgreen:

---

### Post by dirty_harry on 2010-09-10
OK, looks like I underestimated the whole thing:

switched to nvidia 195.36.24 (current); my chipset KT333 is not support by nvidia; apggart seems to work; but the rest is still broken!

```
*****@*****-*****:~$ lsmod | grep agp
via_agp                 5310  1 
agpgart                31724  2 nvidia,via_agp
*****@****-*****:~$ cat /proc/driver/nvidia/agp/status 
Status:      Enabled
Driver:      AGPGART
AGP Rate:      4x
Fast Writes:      Disabled
SBA:          Disabled
```can someone please point me the right direction...?

I attached the nvidia-bug-report and a photo of my screen when I tried to start foobilliard(opengl...)

---

### Post by dirty_harry on 2010-09-10
hm,

#    got rid of all nvidia packages
#    downloaded NVIDIA-Linux-x86-256.53
#    installed and enabled NvAGP to run agpgart
#    my mainboard chipset is KT333, which is not support by nvidia, but agpgart -> [NVIDIA README]("http://us.download.nvidia.com/XFree86/Linux-x86/256.53/README/configuringagp.html")
#    agpstatus cat /proc... -> loaded
#    lsmd -> via_agp, nvidia, agpgart
#    now when I run an opengl-app I see something for about 30 sec, then xorg.0.log says nvidia had errors and switched back to legacy pci

---

### Post by dirty_harry on 2010-09-11
now it is running smooth!

# had to blacklist **via_agp** and **agpgart **in **/etc/modprobe.d/blacklist**
# and add** nvidia_agp** in** /etc/modules**

everything works. flash, video, opengl... :D

---

### Post by dirty_harry on 2010-09-12
OK, ok

well yesterday all of a sudden the nvidia driver decided to switch back to legacy mode...

I found this and decide to try it out:
[http://ubuntuforums.org/showthread.php?t=1527353&highlight=nvidia+lucid+lynx&page=2](http://ubuntuforums.org/showthread.php?t=1527353&highlight=nvidia+lucid+lynx&page=2)

# lucid-proposed-updates
# new kernel 2.6.32-25
# installed kernel headers/sources
# reinstalled NVIDIA-Linux-x86-256.53 (website version)

now everything works again, even after a couple of reboots;
**but**  *cat /proc/driver/nvidia/agp/status* says agp is disabled *?*

I will no longer update this thread and open a new one for advice!

---

