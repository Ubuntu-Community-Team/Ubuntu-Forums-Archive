---
title: "Update from 13.04 to 13.10 =&gt; XFCE only shows black screen"
date: 2014-01-11
forum: Desktop Environments
---

### Post by mercury1981 on 2014-01-11
Hi!

Today I upgraded from 13.04 to 13.10 and now I cannot work in XFCE:
The computer starts normally, lightdm is displayed and I can enter my username / password - after this the screen gets black (but my monitor light is still "green" so it gets a signal) and nothing more happens.

If I press ALT+F1 I can switch to console.

I tried to kill xfce processes and I can start unity with "startx" but with "startxfce4" the same happens as described above.

I also checked X.org log files but did not find anything helpful (see below) - can anybody please help or give me hints?

Thanks a lot!

```

[   167.475] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[   167.475] X Protocol Version 11, Revision 0
[   167.475] Build Operating System: Linux 3.2.0-54-generic i686 Ubuntu
[   167.475] Current Operating System: Linux oracle 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686
[   167.475] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=3738e2a6-acf8-4602-8f61-040291507042 ro quiet splash vt.handoff=7
[   167.476] Build Date: 17 December 2013  10:03:52AM
[   167.476] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[   167.476] Current version of pixman: 0.30.2
[   167.476]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   167.476] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   167.477] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 11 20:53:37 2014
[   167.507] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   167.508] (==) No Layout section.  Using the first Screen section.
[   167.508] (==) No screen section available. Using defaults.
[   167.508] (**) |-->Screen "Default Screen Section" (0)
[   167.508] (**) |   |-->Monitor "<default monitor>"
[   167.513] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   167.513] (==) Automatically adding devices
[   167.513] (==) Automatically enabling devices
[   167.513] (==) Automatically adding GPU devices
[   167.514] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   167.514]     Entry deleted from font path.
[   167.514] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   167.514]     Entry deleted from font path.
[   167.514] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   167.514]     Entry deleted from font path.
[   167.514] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   167.514]     Entry deleted from font path.
[   167.514] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   167.514]     Entry deleted from font path.
[   167.514] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   167.515] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   167.515] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   167.515] (II) Loader magic: 0xb77ce6a0
[   167.515] (II) Module ABI versions:
[   167.515]     X.Org ANSI C Emulation: 0.4
[   167.515]     X.Org Video Driver: 14.1
[   167.515]     X.Org XInput driver : 19.1
[   167.515]     X.Org Server Extension : 7.0
[   167.516] (II) xfree86: Adding drm device (/dev/dri/card0)
[   167.527] (--) PCI:*(0:0:2:0) 8086:2772:1462:7418 rev 2, Mem @ 0xfea80000/524288, 0xe0000000/268435456, 0xfea40000/262144, I/O @ 0x0000dc00/8
[   167.532] (II) Open ACPI successful (/var/run/acpid.socket)
[   167.533] Initializing built-in extension Generic Event Extension
[   167.533] Initializing built-in extension SHAPE
[   167.533] Initializing built-in extension MIT-SHM
[   167.533] Initializing built-in extension XInputExtension
[   167.533] Initializing built-in extension XTEST
[   167.533] Initializing built-in extension BIG-REQUESTS
[   167.533] Initializing built-in extension SYNC
[   167.533] Initializing built-in extension XKEYBOARD
[   167.533] Initializing built-in extension XC-MISC
[   167.533] Initializing built-in extension SECURITY
[   167.533] Initializing built-in extension XINERAMA
[   167.533] Initializing built-in extension XFIXES
[   167.535] Initializing built-in extension RENDER
[   167.535] Initializing built-in extension RANDR
[   167.535] Initializing built-in extension COMPOSITE
[   167.535] Initializing built-in extension DAMAGE
[   167.535] Initializing built-in extension MIT-SCREEN-SAVER
[   167.536] Initializing built-in extension DOUBLE-BUFFER
[   167.536] Initializing built-in extension RECORD
[   167.536] Initializing built-in extension DPMS
[   167.536] Initializing built-in extension X-Resource
[   167.536] Initializing built-in extension XVideo
[   167.536] Initializing built-in extension XVideo-MotionCompensation
[   167.536] Initializing built-in extension SELinux
[   167.536] Initializing built-in extension XFree86-VidModeExtension
[   167.536] Initializing built-in extension XFree86-DGA
[   167.536] Initializing built-in extension XFree86-DRI
[   167.536] Initializing built-in extension DRI2
[   167.536] (II) "glx" will be loaded by default.
[   167.536] (WW) "xmir" is not to be loaded by default. Skipping.
[   167.537] (II) LoadModule: "dri2"
[   167.537] (II) Module "dri2" already built-in
[   167.537] (II) LoadModule: "glamoregl"
[   167.613] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   168.474] (II) Module glamoregl: vendor="X.Org Foundation"
[   168.475]     compiled for 1.14.3, module version = 0.5.1
[   168.475]     ABI class: X.Org ANSI C Emulation, version 0.4
[   168.475] (II) LoadModule: "glx"
[   168.476] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   168.476] (II) Module glx: vendor="X.Org Foundation"
[   168.476]     compiled for 1.14.5, module version = 1.0.0
[   168.476]     ABI class: X.Org Server Extension, version 7.0
[   168.476] (==) AIGLX enabled
[   168.476] Loading extension GLX
[   168.477] (==) Matched intel as autoconfigured driver 0
[   168.477] (==) Matched intel as autoconfigured driver 1
[   168.477] (==) Matched vesa as autoconfigured driver 2
[   168.477] (==) Matched modesetting as autoconfigured driver 3
[   168.477] (==) Matched fbdev as autoconfigured driver 4
[   168.477] (==) Assigned the driver to the xf86ConfigLayout
[   168.477] (II) LoadModule: "intel"
[   168.478] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   168.529] (II) Module intel: vendor="X.Org Foundation"
[   168.529]     compiled for 1.14.3, module version = 2.99.904
[   168.529]     Module class: X.Org Video Driver
[   168.529]     ABI class: X.Org Video Driver, version 14.1
[   168.529] (II) LoadModule: "vesa"
[   168.531] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   168.531] (II) Module vesa: vendor="X.Org Foundation"
[   168.531]     compiled for 1.14.1, module version = 2.3.2
[   168.531]     Module class: X.Org Video Driver
[   168.531]     ABI class: X.Org Video Driver, version 14.1
[   168.531] (II) LoadModule: "modesetting"
[   168.532] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   168.533] (II) Module modesetting: vendor="X.Org Foundation"
[   168.533]     compiled for 1.14.1, module version = 0.8.0
[   168.533]     Module class: X.Org Video Driver
[   168.533]     ABI class: X.Org Video Driver, version 14.1
[   168.533] (II) LoadModule: "fbdev"
[   168.534] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   168.535] (II) Module fbdev: vendor="X.Org Foundation"
[   168.535]     compiled for 1.14.1, module version = 0.4.3
[   168.535]     Module class: X.Org Video Driver
[   168.535]     ABI class: X.Org Video Driver, version 14.1
[   168.535] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[   168.545] (II) VESA: driver for VESA chipsets: vesa
[   168.545] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   168.545] (II) FBDEV: driver for framebuffer: fbdev
[   168.546] (++) using VT number 7

[   168.546] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.904-0ubuntu2 (Timo Aaltonen <tjaalton@ubuntu.com>)
[   168.547] (WW) Falling back to old probe method for vesa
[   168.547] (WW) Falling back to old probe method for modesetting
[   168.547] (WW) Falling back to old probe method for fbdev
[   168.547] (II) Loading sub module "fbdevhw"
[   168.547] (II) LoadModule: "fbdevhw"
[   168.548] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   168.548] (II) Module fbdevhw: vendor="X.Org Foundation"
[   168.548]     compiled for 1.14.5, module version = 0.0.2
[   168.548]     ABI class: X.Org Video Driver, version 14.1
[   168.550] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   168.550] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   168.551] (==) intel(0): RGB weight 888
[   168.551] (==) intel(0): Default visual is TrueColor
[   168.551] (--) intel(0): Integrated Graphics Chipset: Intel(R) 945G
[   168.552] (--) intel(0): CPU: x86, sse2, sse3, ssse3
[   168.552] (**) intel(0): Framebuffer tiled
[   168.552] (**) intel(0): Pixmaps tiled
[   168.552] (**) intel(0): "Tear free" disabled
[   168.553] (**) intel(0): Forcing per-crtc-pixmaps? no
[   168.553] (II) intel(0): Output VGA1 has no monitor section
[   168.553] (II) intel(0): Output VIRTUAL1 has no monitor section
[   168.553] (--) intel(0): Output VGA1 using initial mode 1920x1080 on pipe 0
[   168.553] (==) intel(0): DPI set to (96, 96)
[   168.553] (II) Loading sub module "dri2"
[   168.553] (II) LoadModule: "dri2"
[   168.553] (II) Module "dri2" already built-in
[   168.553] (II) UnloadModule: "vesa"
[   168.554] (II) Unloading vesa
[   168.554] (II) UnloadModule: "modesetting"
[   168.554] (II) Unloading modesetting
[   168.554] (II) UnloadModule: "fbdev"
[   168.554] (II) Unloading fbdev
[   168.554] (II) UnloadSubModule: "fbdevhw"
[   168.554] (II) Unloading fbdevhw
[   168.554] (==) Depth 24 pixmap format is 32 bpp
[   168.555] (II) intel(0): SNA initialized with Alviso (gen3) backend
[   168.555] (==) intel(0): Backing store disabled
[   168.555] (==) intel(0): Silken mouse enabled
[   168.555] (II) intel(0): HW Cursor enabled
[   168.555] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   168.556] (==) intel(0): DPMS enabled
[   168.556] (II) intel(0): [XvMC] i915_xvmc driver initialized.
[   168.556] (II) intel(0): [DRI2] Setup complete
[   168.556] (II) intel(0): [DRI2]   DRI driver: i915
[   168.556] (II) intel(0): direct rendering: DRI2 Enabled
[   168.556] (==) intel(0): hotplug detection: "enabled"
[   168.556] (--) RandR disabled
[   168.599] (II) SELinux: Disabled on system
[   168.923] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   168.923] (II) AIGLX: enabled GLX_INTEL_swap_event
[   168.923] (II) AIGLX: enabled GLX_ARB_create_context
[   168.923] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   168.924] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   168.924] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   168.924] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   168.924] (II) AIGLX: Loaded and initialized i915
[   168.924] (II) GLX: Initialized DRI2 GL provider for screen 0
[   168.944] (II) intel(0): switch to mode 1920x1080@60.0 on pipe 0 using VGA1, position (0, 0), rotation normal
[   168.956] (II) intel(0): Setting screen physical size to 507 x 285
[   168.986] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   168.995] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   168.995] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   168.996] (II) LoadModule: "evdev"
[   168.996] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   169.036] (II) Module evdev: vendor="X.Org Foundation"
[   169.036]     compiled for 1.14.1, module version = 2.7.3
[   169.036]     Module class: X.Org XInput Driver
[   169.036]     ABI class: X.Org XInput driver, version 19.1
[   169.036] (II) Using input driver 'evdev' for 'Power Button'
[   169.036] (**) Power Button: always reports core events
[   169.037] (**) evdev: Power Button: Device: "/dev/input/event1"
[   169.037] (--) evdev: Power Button: Vendor 0 Product 0x1
[   169.037] (--) evdev: Power Button: Found keys
[   169.037] (II) evdev: Power Button: Configuring as keyboard
[   169.037] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   169.037] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   169.037] (**) Option "xkb_rules" "evdev"
[   169.037] (**) Option "xkb_model" "pc105"
[   169.038] (**) Option "xkb_layout" "de"
[   169.038] (**) Option "xkb_variant" "nodeadkeys"
[   169.045] (II) XKB: reuse xkmfile /var/lib/xkb/server-76D2B5A359D34EEB9BFAEB1701EF70014DF39715.xkm
[   169.047] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   169.048] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   169.048] (II) Using input driver 'evdev' for 'Power Button'
[   169.048] (**) Power Button: always reports core events
[   169.048] (**) evdev: Power Button: Device: "/dev/input/event0"
[   169.048] (--) evdev: Power Button: Vendor 0 Product 0x1
[   169.048] (--) evdev: Power Button: Found keys
[   169.048] (II) evdev: Power Button: Configuring as keyboard
[   169.048] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   169.048] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   169.048] (**) Option "xkb_rules" "evdev"
[   169.048] (**) Option "xkb_model" "pc105"
[   169.048] (**) Option "xkb_layout" "de"
[   169.049] (**) Option "xkb_variant" "nodeadkeys"
[   169.050] (II) config/udev: Adding drm device (/dev/dri/card0)
[   169.050] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   169.051] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event10)
[   169.051] (II) No input driver specified, ignoring this device.
[   169.051] (II) This device may have been added with another device file.
[   169.052] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event3)
[   169.052] (II) No input driver specified, ignoring this device.
[   169.052] (II) This device may have been added with another device file.
[   169.053] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event4)
[   169.053] (II) No input driver specified, ignoring this device.
[   169.053] (II) This device may have been added with another device file.
[   169.054] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event5)
[   169.054] (II) No input driver specified, ignoring this device.
[   169.054] (II) This device may have been added with another device file.
[   169.054] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event6)
[   169.054] (II) No input driver specified, ignoring this device.
[   169.055] (II) This device may have been added with another device file.
[   169.055] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event7)
[   169.055] (II) No input driver specified, ignoring this device.
[   169.055] (II) This device may have been added with another device file.
[   169.056] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event8)
[   169.056] (II) No input driver specified, ignoring this device.
[   169.056] (II) This device may have been added with another device file.
[   169.057] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event9)
[   169.057] (II) No input driver specified, ignoring this device.
[   169.057] (II) This device may have been added with another device file.
[   169.059] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event11)
[   169.059] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[   169.059] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[   169.059] (**) BTC USB Multimedia Keyboard: always reports core events
[   169.059] (**) evdev: BTC USB Multimedia Keyboard: Device: "/dev/input/event11"
[   169.059] (--) evdev: BTC USB Multimedia Keyboard: Vendor 0x46d Product 0xc312
[   169.059] (--) evdev: BTC USB Multimedia Keyboard: Found keys
[   169.059] (II) evdev: BTC USB Multimedia Keyboard: Configuring as keyboard
[   169.060] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input11/event11"
[   169.060] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD, id 8)
[   169.060] (**) Option "xkb_rules" "evdev"
[   169.060] (**) Option "xkb_model" "pc105"
[   169.060] (**) Option "xkb_layout" "de"
[   169.060] (**) Option "xkb_variant" "nodeadkeys"
[   169.062] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event12)
[   169.063] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[   169.063] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[   169.063] (**) BTC USB Multimedia Keyboard: always reports core events
[   169.063] (**) evdev: BTC USB Multimedia Keyboard: Device: "/dev/input/event12"
[   169.063] (--) evdev: BTC USB Multimedia Keyboard: Vendor 0x46d Product 0xc312
[   169.063] (--) evdev: BTC USB Multimedia Keyboard: Found keys
[   169.063] (II) evdev: BTC USB Multimedia Keyboard: Configuring as keyboard
[   169.063] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/input/input12/event12"
[   169.063] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD, id 9)
[   169.063] (**) Option "xkb_rules" "evdev"
[   169.063] (**) Option "xkb_model" "pc105"
[   169.063] (**) Option "xkb_layout" "de"
[   169.063] (**) Option "xkb_variant" "nodeadkeys"
[   169.065] (II) config/udev: Adding input device Logitech USB Mouse (/dev/input/event2)
[   169.065] (**) Logitech USB Mouse: Applying InputClass "evdev pointer catchall"
[   169.065] (II) Using input driver 'evdev' for 'Logitech USB Mouse'
[   169.066] (**) Logitech USB Mouse: always reports core events
[   169.066] (**) evdev: Logitech USB Mouse: Device: "/dev/input/event2"
[   169.066] (--) evdev: Logitech USB Mouse: Vendor 0x46d Product 0xc00c
[   169.066] (--) evdev: Logitech USB Mouse: Found 3 mouse buttons
[   169.066] (--) evdev: Logitech USB Mouse: Found scroll wheel(s)
[   169.066] (--) evdev: Logitech USB Mouse: Found relative axes
[   169.066] (--) evdev: Logitech USB Mouse: Found x and y relative axes
[   169.066] (II) evdev: Logitech USB Mouse: Configuring as mouse
[   169.066] (II) evdev: Logitech USB Mouse: Adding scrollwheel support
[   169.066] (**) evdev: Logitech USB Mouse: YAxisMapping: buttons 4 and 5
[   169.066] (**) evdev: Logitech USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   169.066] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input2/event2"
[   169.066] (II) XINPUT: Adding extended input device "Logitech USB Mouse" (type: MOUSE, id 10)
[   169.067] (II) evdev: Logitech USB Mouse: initialized for relative axes.
[   169.067] (**) Logitech USB Mouse: (accel) keeping acceleration scheme 1
[   169.067] (**) Logitech USB Mouse: (accel) acceleration profile 0
[   169.067] (**) Logitech USB Mouse: (accel) acceleration factor: 2.000
[   169.067] (**) Logitech USB Mouse: (accel) acceleration threshold: 4
[   169.068] (II) config/udev: Adding input device Logitech USB Mouse (/dev/input/mouse0)
[   169.068] (II) No input driver specified, ignoring this device.
[   169.068] (II) This device may have been added with another device file.
[   173.800] (II) intel(0): EDID vendor "AOC", prod id 9312
[   173.800] (II) intel(0): Using EDID range info for horizontal sync
[   173.800] (II) intel(0): Using EDID range info for vertical refresh
[   173.800] (II) intel(0): Printing DDC gathered Modelines:
[   173.800] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   173.801] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   173.801] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   173.801] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   173.801] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   173.801] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   173.801] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   173.801] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   173.801] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   173.801] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   173.801] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   173.801] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   173.801] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   173.802] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   173.802] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   173.802] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   173.802] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   173.802] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[   173.802] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   173.802] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   173.802] (II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   177.924] (II) intel(0): EDID vendor "AOC", prod id 9312
[   177.924] (II) intel(0): Using hsync ranges from config file
[   177.925] (II) intel(0): Using vrefresh ranges from config file
[   177.925] (II) intel(0): Printing DDC gathered Modelines:
[   177.925] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   177.925] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   177.925] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   177.925] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   177.925] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   177.925] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   177.925] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   177.925] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   177.925] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   177.925] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   177.926] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   177.926] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   177.926] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   177.926] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   177.926] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   177.926] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz e)
[   177.926] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   177.926] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[   177.926] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   177.926] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   177.926] (II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   177.991] (II) intel(0): switch to mode 1920x1080@60.0 on pipe 0 using VGA1, position (-32768, -32768), rotation normal
[   210.496] (II) config/udev: removing device BTC USB Multimedia Keyboard
[   210.517] (II) evdev: BTC USB Multimedia Keyboard: Close
[   210.517] (II) UnloadModule: "evdev"
[   210.582] (II) config/udev: removing device BTC USB Multimedia Keyboard
[   210.596] (II) evdev: BTC USB Multimedia Keyboard: Close
[   210.597] (II) UnloadModule: "evdev"


```

---

### Post by egeezer on 2014-01-11
Does Synaptic confirm you have Xfce 4.10 installed?

---

### Post by mercury1981 on 2014-01-12
Yes - it did!
In the meantime I solved the problem - I removed xubuntu-desktop and xorg and re-installed.
Now it works again - very strange!

---

### Post by mörgæs on 2014-01-12
Good, please mark the thread 'solved'.

---

