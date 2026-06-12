---
title: "Can't login using Unity or Gnome3"
date: 2015-03-21
forum: Desktop Environments
---

### Post by l33t8l on 2015-03-21
I've been having some problems logging in since installing the cinnamon desktop shell.  I cannot switch back to using Unity or Gnome 3.

Recorded my experience here: [http://youtu.be/KdsJfJvleag](http://youtu.be/KdsJfJvleag).  Here I attempt to log in with Gnome3, then Gnome3 classic and then finally with cinnamon.

To resolve this I've done the following:


[LIST=1]
[*]Remove cinnamon (which left me with no desktop environment),
[*]I've un-installed and re-installed both,
[*]Found missing fonts and installed them,
[*]Installed gnome weather etc,
[*]Reconfigured lightdm,
[*]Tried switching to gdm,
[*]Removed ~/.Xauthority, and
[*]Checked my home folder permissions.
[/LIST]

Ideally I would like to use gnome3 again, I find using it much more efficient than cinnamon.

I'm running Ubuntu 14.04.  Everything is up-to-date.

LOG -- xorg.0.log
```
[   900.528] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   900.528] X Protocol Version 11, Revision 0
[   900.528] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[   900.528] Current Operating System: Linux horize-W550EU 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:06:50 UTC 2015 x86_64
[   900.528] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=9bd7d08b-b6a4-4e04-af7e-82840ed417cb ro quiet splash vt.handoff=7
[   900.528] Build Date: 12 February 2015  02:49:29PM
[   900.528] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   900.528] Current version of pixman: 0.30.2
[   900.528]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   900.528] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   900.528] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 21 13:33:37 2015
[   900.529] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   900.529] (==) No Layout section.  Using the first Screen section.
[   900.529] (==) No screen section available. Using defaults.
[   900.529] (**) |-->Screen "Default Screen Section" (0)
[   900.529] (**) |   |-->Monitor "<default monitor>"
[   900.529] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   900.529] (==) Automatically adding devices
[   900.529] (==) Automatically enabling devices
[   900.529] (==) Automatically adding GPU devices
[   900.529] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[   900.529] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   900.529] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   900.530] (II) Loader magic: 0x7f11caf06d40
[   900.530] (II) Module ABI versions:
[   900.530]     X.Org ANSI C Emulation: 0.4
[   900.530]     X.Org Video Driver: 15.0
[   900.530]     X.Org XInput driver : 20.0
[   900.530]     X.Org Server Extension : 8.0
[   900.530] (II) xfree86: Adding drm device (/dev/dri/card0)
[   900.531] (--) PCI:*(0:0:2:0) 8086:0166:1558:0550 rev 9, Mem @ 0xf6400000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[   900.531] Initializing built-in extension Generic Event Extension
[   900.531] Initializing built-in extension SHAPE
[   900.531] Initializing built-in extension MIT-SHM
[   900.532] Initializing built-in extension XInputExtension
[   900.532] Initializing built-in extension XTEST
[   900.532] Initializing built-in extension BIG-REQUESTS
[   900.532] Initializing built-in extension SYNC
[   900.532] Initializing built-in extension XKEYBOARD
[   900.532] Initializing built-in extension XC-MISC
[   900.532] Initializing built-in extension SECURITY
[   900.532] Initializing built-in extension XINERAMA
[   900.532] Initializing built-in extension XFIXES
[   900.532] Initializing built-in extension RENDER
[   900.532] Initializing built-in extension RANDR
[   900.532] Initializing built-in extension COMPOSITE
[   900.532] Initializing built-in extension DAMAGE
[   900.532] Initializing built-in extension MIT-SCREEN-SAVER
[   900.532] Initializing built-in extension DOUBLE-BUFFER
[   900.532] Initializing built-in extension RECORD
[   900.532] Initializing built-in extension DPMS
[   900.532] Initializing built-in extension Present
[   900.532] Initializing built-in extension DRI3
[   900.532] Initializing built-in extension X-Resource
[   900.532] Initializing built-in extension XVideo
[   900.532] Initializing built-in extension XVideo-MotionCompensation
[   900.532] Initializing built-in extension SELinux
[   900.532] Initializing built-in extension XFree86-VidModeExtension
[   900.532] Initializing built-in extension XFree86-DGA
[   900.532] Initializing built-in extension XFree86-DRI
[   900.532] Initializing built-in extension DRI2
[   900.532] (II) LoadModule: "glx"
[   900.532] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   900.533] (II) Module glx: vendor="X.Org Foundation"
[   900.533]     compiled for 1.15.1, module version = 1.0.0
[   900.533]     ABI class: X.Org Server Extension, version 8.0
[   900.533] (==) AIGLX enabled
[   900.533] Loading extension GLX
[   900.533] (==) Matched intel as autoconfigured driver 0
[   900.533] (==) Matched intel as autoconfigured driver 1
[   900.533] (==) Matched modesetting as autoconfigured driver 2
[   900.533] (==) Matched fbdev as autoconfigured driver 3
[   900.533] (==) Matched vesa as autoconfigured driver 4
[   900.533] (==) Assigned the driver to the xf86ConfigLayout
[   900.533] (II) LoadModule: "intel"
[   900.533] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   900.533] (II) Module intel: vendor="X.Org Foundation"
[   900.533]     compiled for 1.15.1, module version = 2.99.910
[   900.533]     Module class: X.Org Video Driver
[   900.533]     ABI class: X.Org Video Driver, version 15.0
[   900.533] (II) LoadModule: "modesetting"
[   900.533] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   900.533] (II) Module modesetting: vendor="X.Org Foundation"
[   900.533]     compiled for 1.15.0, module version = 0.8.1
[   900.533]     Module class: X.Org Video Driver
[   900.533]     ABI class: X.Org Video Driver, version 15.0
[   900.533] (II) LoadModule: "fbdev"
[   900.534] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   900.534] (II) Module fbdev: vendor="X.Org Foundation"
[   900.534]     compiled for 1.15.0, module version = 0.4.4
[   900.534]     Module class: X.Org Video Driver
[   900.534]     ABI class: X.Org Video Driver, version 15.0
[   900.534] (II) LoadModule: "vesa"
[   900.534] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   900.534] (II) Module vesa: vendor="X.Org Foundation"
[   900.534]     compiled for 1.15.0, module version = 2.3.3
[   900.534]     Module class: X.Org Video Driver
[   900.534]     ABI class: X.Org Video Driver, version 15.0
[   900.534] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   900.534] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[   900.534] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[   900.534] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[   900.534] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   900.534] (II) FBDEV: driver for framebuffer: fbdev
[   900.534] (II) VESA: driver for VESA chipsets: vesa
[   900.534] (++) using VT number 7


[   900.534] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.4 (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[   900.534] (WW) Falling back to old probe method for modesetting
[   900.535] (WW) Falling back to old probe method for fbdev
[   900.535] (II) Loading sub module "fbdevhw"
[   900.535] (II) LoadModule: "fbdevhw"
[   900.535] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   900.535] (II) Module fbdevhw: vendor="X.Org Foundation"
[   900.535]     compiled for 1.15.1, module version = 0.0.2
[   900.535]     ABI class: X.Org Video Driver, version 15.0
[   900.535] (WW) Falling back to old probe method for vesa
[   900.535] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[   900.535] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[   900.535] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   900.535] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   900.535] (==) intel(0): RGB weight 888
[   900.535] (==) intel(0): Default visual is TrueColor
[   900.535] (**) intel(0): Framebuffer tiled
[   900.535] (**) intel(0): Pixmaps tiled
[   900.535] (**) intel(0): "Tear free" disabled
[   900.535] (**) intel(0): Forcing per-crtc-pixmaps? no
[   900.535] (II) intel(0): Output LVDS1 has no monitor section
[   900.536] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[   900.536] (II) intel(0): Output VGA1 has no monitor section
[   900.537] (II) intel(0): Output HDMI1 has no monitor section
[   900.537] (II) intel(0): Output DP1 has no monitor section
[   900.537] (II) intel(0): Output VIRTUAL1 has no monitor section
[   900.537] (--) intel(0): Output LVDS1 using initial mode 1920x1080 on pipe 0
[   900.537] (==) intel(0): DPI set to (96, 96)
[   900.537] (II) Loading sub module "dri2"
[   900.537] (II) LoadModule: "dri2"
[   900.537] (II) Module "dri2" already built-in
[   900.539] (II) UnloadModule: "modesetting"
[   900.539] (II) Unloading modesetting
[   900.539] (II) UnloadModule: "fbdev"
[   900.539] (II) Unloading fbdev
[   900.539] (II) UnloadSubModule: "fbdevhw"
[   900.539] (II) Unloading fbdevhw
[   900.540] (II) UnloadModule: "vesa"
[   900.540] (II) Unloading vesa
[   900.540] (==) Depth 24 pixmap format is 32 bpp
[   900.540] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[   900.540] (==) intel(0): Backing store enabled
[   900.540] (==) intel(0): Silken mouse enabled
[   900.540] (II) intel(0): HW Cursor enabled
[   900.540] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   900.540] (==) intel(0): DPMS enabled
[   900.540] (II) intel(0): [DRI2] Setup complete
[   900.540] (II) intel(0): [DRI2]   DRI driver: i965
[   900.541] (II) intel(0): [DRI2]   VDPAU driver: i965
[   900.541] (II) intel(0): direct rendering: DRI2 Enabled
[   900.541] (==) intel(0): hotplug detection: "enabled"
[   900.541] (--) RandR disabled
[   900.550] (II) SELinux: Disabled on system
[   900.555] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   900.555] (II) AIGLX: enabled GLX_ARB_create_context
[   900.555] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   900.555] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   900.555] (II) AIGLX: enabled GLX_INTEL_swap_event
[   900.555] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   900.555] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[   900.556] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[   900.556] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   900.556] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[   900.556] (II) AIGLX: Loaded and initialized i965
[   900.556] (II) GLX: Initialized DRI2 GL provider for screen 0
[   900.557] (II) intel(0): switch to mode 1920x1080@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   900.577] (II) intel(0): Setting screen physical size to 508 x 285
[   900.597] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   900.598] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   900.598] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   900.598] (II) LoadModule: "evdev"
[   900.598] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   900.598] (II) Module evdev: vendor="X.Org Foundation"
[   900.598]     compiled for 1.15.0, module version = 2.8.2
[   900.598]     Module class: X.Org XInput Driver
[   900.598]     ABI class: X.Org XInput driver, version 20.0
[   900.598] (II) Using input driver 'evdev' for 'Power Button'
[   900.598] (**) Power Button: always reports core events
[   900.598] (**) evdev: Power Button: Device: "/dev/input/event3"
[   900.598] (--) evdev: Power Button: Vendor 0 Product 0x1
[   900.598] (--) evdev: Power Button: Found keys
[   900.598] (II) evdev: Power Button: Configuring as keyboard
[   900.598] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   900.598] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   900.598] (**) Option "xkb_rules" "evdev"
[   900.598] (**) Option "xkb_model" "pc105"
[   900.598] (**) Option "xkb_layout" "us"
[   900.599] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[   900.599] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   900.599] (II) Using input driver 'evdev' for 'Video Bus'
[   900.599] (**) Video Bus: always reports core events
[   900.599] (**) evdev: Video Bus: Device: "/dev/input/event10"
[   900.599] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   900.599] (--) evdev: Video Bus: Found keys
[   900.599] (II) evdev: Video Bus: Configuring as keyboard
[   900.599] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input17/event10"
[   900.599] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   900.599] (**) Option "xkb_rules" "evdev"
[   900.599] (**) Option "xkb_model" "pc105"
[   900.599] (**) Option "xkb_layout" "us"
[   900.599] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   900.599] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   900.599] (II) Using input driver 'evdev' for 'Power Button'
[   900.599] (**) Power Button: always reports core events
[   900.599] (**) evdev: Power Button: Device: "/dev/input/event0"
[   900.599] (--) evdev: Power Button: Vendor 0 Product 0x1
[   900.599] (--) evdev: Power Button: Found keys
[   900.599] (II) evdev: Power Button: Configuring as keyboard
[   900.599] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   900.599] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   900.599] (**) Option "xkb_rules" "evdev"
[   900.599] (**) Option "xkb_model" "pc105"
[   900.599] (**) Option "xkb_layout" "us"
[   900.599] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[   900.599] (II) No input driver specified, ignoring this device.
[   900.599] (II) This device may have been added with another device file.
[   900.600] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   900.600] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   900.600] (II) Using input driver 'evdev' for 'Sleep Button'
[   900.600] (**) Sleep Button: always reports core events
[   900.600] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   900.600] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   900.600] (--) evdev: Sleep Button: Found keys
[   900.600] (II) evdev: Sleep Button: Configuring as keyboard
[   900.600] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   900.600] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   900.600] (**) Option "xkb_rules" "evdev"
[   900.600] (**) Option "xkb_model" "pc105"
[   900.600] (**) Option "xkb_layout" "us"
[   900.600] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[   900.600] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   900.600] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/event7)
[   900.600] (**) Logitech USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[   900.600] (II) Using input driver 'evdev' for 'Logitech USB Laser Mouse'
[   900.600] (**) Logitech USB Laser Mouse: always reports core events
[   900.600] (**) evdev: Logitech USB Laser Mouse: Device: "/dev/input/event7"
[   900.600] (--) evdev: Logitech USB Laser Mouse: Vendor 0x46d Product 0xc069
[   900.600] (--) evdev: Logitech USB Laser Mouse: Found 12 mouse buttons
[   900.600] (--) evdev: Logitech USB Laser Mouse: Found scroll wheel(s)
[   900.600] (--) evdev: Logitech USB Laser Mouse: Found relative axes
[   900.600] (--) evdev: Logitech USB Laser Mouse: Found x and y relative axes
[   900.600] (II) evdev: Logitech USB Laser Mouse: Configuring as mouse
[   900.600] (II) evdev: Logitech USB Laser Mouse: Adding scrollwheel support
[   900.600] (**) evdev: Logitech USB Laser Mouse: YAxisMapping: buttons 4 and 5
[   900.600] (**) evdev: Logitech USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   900.600] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input14/event7"
[   900.600] (II) XINPUT: Adding extended input device "Logitech USB Laser Mouse" (type: MOUSE, id 10)
[   900.600] (II) evdev: Logitech USB Laser Mouse: initialized for relative axes.
[   900.600] (**) Logitech USB Laser Mouse: (accel) keeping acceleration scheme 1
[   900.600] (**) Logitech USB Laser Mouse: (accel) acceleration profile 0
[   900.600] (**) Logitech USB Laser Mouse: (accel) acceleration factor: 2.000
[   900.600] (**) Logitech USB Laser Mouse: (accel) acceleration threshold: 4
[   900.600] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/mouse1)
[   900.600] (II) No input driver specified, ignoring this device.
[   900.600] (II) This device may have been added with another device file.
[   900.601] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event6)
[   900.601] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[   900.601] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[   900.601] (**) BisonCam, NB Pro: always reports core events
[   900.601] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event6"
[   900.601] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x400
[   900.601] (--) evdev: BisonCam, NB Pro: Found keys
[   900.601] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[   900.601] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input13/event6"
[   900.601] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 11)
[   900.601] (**) Option "xkb_rules" "evdev"
[   900.601] (**) Option "xkb_model" "pc105"
[   900.601] (**) Option "xkb_layout" "us"
[   900.601] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event8)
[   900.601] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[   900.601] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[   900.601] (**) Microsoft Wired Keyboard 600: always reports core events
[   900.601] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event8"
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x750
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[   900.601] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[   900.601] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input15/event8"
[   900.601] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 12)
[   900.601] (**) Option "xkb_rules" "evdev"
[   900.601] (**) Option "xkb_model" "pc105"
[   900.601] (**) Option "xkb_layout" "us"
[   900.601] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event9)
[   900.601] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[   900.601] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[   900.601] (**) Microsoft Wired Keyboard 600: always reports core events
[   900.601] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event9"
[   900.601] (II) evdev: Microsoft Wired Keyboard 600: Using mtdev for this device
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x750
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Found 1 mouse buttons
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Found scroll wheel(s)
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Found relative axes
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Found absolute axes
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Found absolute multitouch axes
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Found x and y absolute axes
[   900.601] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[   900.601] (II) evdev: Microsoft Wired Keyboard 600: Forcing relative x/y axes to exist.
[   900.601] (II) evdev: Microsoft Wired Keyboard 600: Configuring as mouse
[   900.601] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[   900.601] (II) evdev: Microsoft Wired Keyboard 600: Adding scrollwheel support
[   900.601] (**) evdev: Microsoft Wired Keyboard 600: YAxisMapping: buttons 4 and 5
[   900.601] (**) evdev: Microsoft Wired Keyboard 600: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   900.601] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input16/event9"
[   900.602] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 13)
[   900.602] (**) Option "xkb_rules" "evdev"
[   900.602] (**) Option "xkb_model" "pc105"
[   900.602] (**) Option "xkb_layout" "us"
[   900.602] (II) evdev: Microsoft Wired Keyboard 600: initialized for relative axes.
[   900.602] (WW) evdev: Microsoft Wired Keyboard 600: ignoring absolute axes.
[   900.602] (**) Microsoft Wired Keyboard 600: (accel) keeping acceleration scheme 1
[   900.602] (**) Microsoft Wired Keyboard 600: (accel) acceleration profile 0
[   900.602] (**) Microsoft Wired Keyboard 600: (accel) acceleration factor: 2.000
[   900.602] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4
[   900.602] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/js0)
[   900.602] (II) No input driver specified, ignoring this device.
[   900.602] (II) This device may have been added with another device file.
[   900.602] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event13)
[   900.602] (II) No input driver specified, ignoring this device.
[   900.602] (II) This device may have been added with another device file.
[   900.602] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event12)
[   900.602] (II) No input driver specified, ignoring this device.
[   900.602] (II) This device may have been added with another device file.
[   900.602] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[   900.602] (II) No input driver specified, ignoring this device.
[   900.602] (II) This device may have been added with another device file.
[   900.602] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   900.602] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   900.602] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   900.602] (**) AT Translated Set 2 keyboard: always reports core events
[   900.602] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   900.602] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   900.602] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   900.602] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   900.602] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   900.602] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[   900.602] (**) Option "xkb_rules" "evdev"
[   900.602] (**) Option "xkb_model" "pc105"
[   900.602] (**) Option "xkb_layout" "us"
[   900.603] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   900.603] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   900.603] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   900.603] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   900.603] (II) LoadModule: "synaptics"
[   900.603] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   900.603] (II) Module synaptics: vendor="X.Org Foundation"
[   900.603]     compiled for 1.15.0, module version = 1.7.4
[   900.603]     Module class: X.Org XInput Driver
[   900.603]     ABI class: X.Org XInput driver, version 20.0
[   900.603] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   900.603] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   900.603] (**) Option "Device" "/dev/input/event5"
[   900.620] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[   900.620] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692 (res 66)
[   900.620] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680 (res 102)
[   900.620] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   900.620] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   900.620] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   900.620] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   900.620] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   900.620] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   900.632] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event5"
[   900.632] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 15)
[   900.632] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   900.632] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   900.632] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[   900.632] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   900.632] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   900.632] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   900.632] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   900.632] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   900.632] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   900.632] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   911.813] (II) intel(0): EDID vendor "LGD", prod id 894
[   911.813] (II) intel(0): Printing DDC gathered Modelines:
[   911.813] (II) intel(0): Modeline "1920x1080"x0.0  149.00  1920 1968 2040 2208  1080 1083 1088 1124 -hsync -vsync (67.5 kHz eP)
[   911.896] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   912.302] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm

-- LOG Xorg.0.log.old
[   889.860] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   889.860] X Protocol Version 11, Revision 0
[   889.860] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[   889.860] Current Operating System: Linux horize-W550EU 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:06:50 UTC 2015 x86_64
[   889.860] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-46-generic root=UUID=9bd7d08b-b6a4-4e04-af7e-82840ed417cb ro quiet splash vt.handoff=7
[   889.860] Build Date: 12 February 2015  02:49:29PM
[   889.860] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   889.860] Current version of pixman: 0.30.2
[   889.860]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   889.860] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   889.861] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 21 13:33:27 2015
[   889.861] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   889.861] (==) No Layout section.  Using the first Screen section.
[   889.861] (==) No screen section available. Using defaults.
[   889.861] (**) |-->Screen "Default Screen Section" (0)
[   889.861] (**) |   |-->Monitor "<default monitor>"
[   889.862] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   889.862] (==) Automatically adding devices
[   889.862] (==) Automatically enabling devices
[   889.862] (==) Automatically adding GPU devices
[   889.862] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[   889.862] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   889.862] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   889.862] (II) Loader magic: 0x7f97417c9d40
[   889.862] (II) Module ABI versions:
[   889.862]     X.Org ANSI C Emulation: 0.4
[   889.862]     X.Org Video Driver: 15.0
[   889.862]     X.Org XInput driver : 20.0
[   889.862]     X.Org Server Extension : 8.0
[   889.862] (II) xfree86: Adding drm device (/dev/dri/card0)
[   889.864] (--) PCI:*(0:0:2:0) 8086:0166:1558:0550 rev 9, Mem @ 0xf6400000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[   889.864] Initializing built-in extension Generic Event Extension
[   889.864] Initializing built-in extension SHAPE
[   889.864] Initializing built-in extension MIT-SHM
[   889.864] Initializing built-in extension XInputExtension
[   889.864] Initializing built-in extension XTEST
[   889.864] Initializing built-in extension BIG-REQUESTS
[   889.864] Initializing built-in extension SYNC
[   889.864] Initializing built-in extension XKEYBOARD
[   889.864] Initializing built-in extension XC-MISC
[   889.864] Initializing built-in extension SECURITY
[   889.864] Initializing built-in extension XINERAMA
[   889.864] Initializing built-in extension XFIXES
[   889.864] Initializing built-in extension RENDER
[   889.864] Initializing built-in extension RANDR
[   889.864] Initializing built-in extension COMPOSITE
[   889.864] Initializing built-in extension DAMAGE
[   889.864] Initializing built-in extension MIT-SCREEN-SAVER
[   889.864] Initializing built-in extension DOUBLE-BUFFER
[   889.864] Initializing built-in extension RECORD
[   889.864] Initializing built-in extension DPMS
[   889.864] Initializing built-in extension Present
[   889.864] Initializing built-in extension DRI3
[   889.864] Initializing built-in extension X-Resource
[   889.864] Initializing built-in extension XVideo
[   889.864] Initializing built-in extension XVideo-MotionCompensation
[   889.864] Initializing built-in extension SELinux
[   889.864] Initializing built-in extension XFree86-VidModeExtension
[   889.864] Initializing built-in extension XFree86-DGA
[   889.864] Initializing built-in extension XFree86-DRI
[   889.864] Initializing built-in extension DRI2
[   889.864] (II) LoadModule: "glx"
[   889.865] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   889.866] (II) Module glx: vendor="X.Org Foundation"
[   889.866]     compiled for 1.15.1, module version = 1.0.0
[   889.866]     ABI class: X.Org Server Extension, version 8.0
[   889.866] (==) AIGLX enabled
[   889.866] Loading extension GLX
[   889.866] (==) Matched intel as autoconfigured driver 0
[   889.866] (==) Matched intel as autoconfigured driver 1
[   889.866] (==) Matched modesetting as autoconfigured driver 2
[   889.866] (==) Matched fbdev as autoconfigured driver 3
[   889.866] (==) Matched vesa as autoconfigured driver 4
[   889.866] (==) Assigned the driver to the xf86ConfigLayout
[   889.866] (II) LoadModule: "intel"
[   889.866] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   889.867] (II) Module intel: vendor="X.Org Foundation"
[   889.867]     compiled for 1.15.1, module version = 2.99.910
[   889.867]     Module class: X.Org Video Driver
[   889.867]     ABI class: X.Org Video Driver, version 15.0
[   889.867] (II) LoadModule: "modesetting"
[   889.867] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   889.867] (II) Module modesetting: vendor="X.Org Foundation"
[   889.867]     compiled for 1.15.0, module version = 0.8.1
[   889.867]     Module class: X.Org Video Driver
[   889.867]     ABI class: X.Org Video Driver, version 15.0
[   889.867] (II) LoadModule: "fbdev"
[   889.868] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   889.868] (II) Module fbdev: vendor="X.Org Foundation"
[   889.868]     compiled for 1.15.0, module version = 0.4.4
[   889.868]     Module class: X.Org Video Driver
[   889.868]     ABI class: X.Org Video Driver, version 15.0
[   889.868] (II) LoadModule: "vesa"
[   889.868] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   889.868] (II) Module vesa: vendor="X.Org Foundation"
[   889.868]     compiled for 1.15.0, module version = 2.3.3
[   889.868]     Module class: X.Org Video Driver
[   889.868]     ABI class: X.Org Video Driver, version 15.0
[   889.868] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   889.869] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[   889.869] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[   889.869] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[   889.869] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   889.869] (II) FBDEV: driver for framebuffer: fbdev
[   889.869] (II) VESA: driver for VESA chipsets: vesa
[   889.869] (++) using VT number 7


[   889.869] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910-0ubuntu1.4 (Maarten Lankhorst <maarten.lankhorst@ubuntu.com>)
[   889.869] (WW) Falling back to old probe method for modesetting
[   889.869] (WW) Falling back to old probe method for fbdev
[   889.869] (II) Loading sub module "fbdevhw"
[   889.869] (II) LoadModule: "fbdevhw"
[   889.870] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   889.870] (II) Module fbdevhw: vendor="X.Org Foundation"
[   889.870]     compiled for 1.15.1, module version = 0.0.2
[   889.870]     ABI class: X.Org Video Driver, version 15.0
[   889.870] (WW) Falling back to old probe method for vesa
[   889.870] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[   889.870] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[   889.870] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   889.870] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   889.870] (==) intel(0): RGB weight 888
[   889.870] (==) intel(0): Default visual is TrueColor
[   889.871] (**) intel(0): Framebuffer tiled
[   889.871] (**) intel(0): Pixmaps tiled
[   889.871] (**) intel(0): "Tear free" disabled
[   889.871] (**) intel(0): Forcing per-crtc-pixmaps? no
[   889.871] (II) intel(0): Output LVDS1 has no monitor section
[   889.872] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
[   889.872] (II) intel(0): Output VGA1 has no monitor section
[   889.872] (II) intel(0): Output HDMI1 has no monitor section
[   889.872] (II) intel(0): Output DP1 has no monitor section
[   889.872] (II) intel(0): Output VIRTUAL1 has no monitor section
[   889.873] (--) intel(0): Output LVDS1 using initial mode 1920x1080 on pipe 0
[   889.873] (==) intel(0): DPI set to (96, 96)
[   889.873] (II) Loading sub module "dri2"
[   889.873] (II) LoadModule: "dri2"
[   889.873] (II) Module "dri2" already built-in
[   889.875] (II) UnloadModule: "modesetting"
[   889.875] (II) Unloading modesetting
[   889.875] (II) UnloadModule: "fbdev"
[   889.875] (II) Unloading fbdev
[   889.875] (II) UnloadSubModule: "fbdevhw"
[   889.875] (II) Unloading fbdevhw
[   889.875] (II) UnloadModule: "vesa"
[   889.875] (II) Unloading vesa
[   889.875] (==) Depth 24 pixmap format is 32 bpp
[   889.876] (II) intel(0): SNA initialized with Ivybridge (gen7, gt2) backend
[   889.876] (==) intel(0): Backing store enabled
[   889.876] (==) intel(0): Silken mouse enabled
[   889.876] (II) intel(0): HW Cursor enabled
[   889.876] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   889.876] (==) intel(0): DPMS enabled
[   889.876] (II) intel(0): [DRI2] Setup complete
[   889.876] (II) intel(0): [DRI2]   DRI driver: i965
[   889.876] (II) intel(0): [DRI2]   VDPAU driver: i965
[   889.876] (II) intel(0): direct rendering: DRI2 Enabled
[   889.876] (==) intel(0): hotplug detection: "enabled"
[   889.876] (--) RandR disabled
[   889.886] (II) SELinux: Disabled on system
[   889.890] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   889.890] (II) AIGLX: enabled GLX_ARB_create_context
[   889.890] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   889.890] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   889.890] (II) AIGLX: enabled GLX_INTEL_swap_event
[   889.890] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   889.890] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[   889.890] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[   889.890] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   889.890] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[   889.890] (II) AIGLX: Loaded and initialized i965
[   889.890] (II) GLX: Initialized DRI2 GL provider for screen 0
[   889.893] (II) intel(0): switch to mode 1920x1080@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[   889.914] (II) intel(0): Setting screen physical size to 508 x 285
[   889.930] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   889.932] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   889.932] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   889.932] (II) LoadModule: "evdev"
[   889.932] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   889.932] (II) Module evdev: vendor="X.Org Foundation"
[   889.932]     compiled for 1.15.0, module version = 2.8.2
[   889.932]     Module class: X.Org XInput Driver
[   889.932]     ABI class: X.Org XInput driver, version 20.0
[   889.932] (II) Using input driver 'evdev' for 'Power Button'
[   889.932] (**) Power Button: always reports core events
[   889.932] (**) evdev: Power Button: Device: "/dev/input/event3"
[   889.932] (--) evdev: Power Button: Vendor 0 Product 0x1
[   889.932] (--) evdev: Power Button: Found keys
[   889.932] (II) evdev: Power Button: Configuring as keyboard
[   889.932] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   889.932] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   889.932] (**) Option "xkb_rules" "evdev"
[   889.932] (**) Option "xkb_model" "pc105"
[   889.932] (**) Option "xkb_layout" "us"
[   889.933] (II) config/udev: Adding input device Video Bus (/dev/input/event10)
[   889.933] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   889.933] (II) Using input driver 'evdev' for 'Video Bus'
[   889.933] (**) Video Bus: always reports core events
[   889.933] (**) evdev: Video Bus: Device: "/dev/input/event10"
[   889.933] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   889.933] (--) evdev: Video Bus: Found keys
[   889.933] (II) evdev: Video Bus: Configuring as keyboard
[   889.933] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input17/event10"
[   889.933] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[   889.933] (**) Option "xkb_rules" "evdev"
[   889.933] (**) Option "xkb_model" "pc105"
[   889.933] (**) Option "xkb_layout" "us"
[   889.933] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   889.933] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   889.933] (II) Using input driver 'evdev' for 'Power Button'
[   889.933] (**) Power Button: always reports core events
[   889.933] (**) evdev: Power Button: Device: "/dev/input/event0"
[   889.933] (--) evdev: Power Button: Vendor 0 Product 0x1
[   889.933] (--) evdev: Power Button: Found keys
[   889.933] (II) evdev: Power Button: Configuring as keyboard
[   889.933] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   889.933] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[   889.933] (**) Option "xkb_rules" "evdev"
[   889.933] (**) Option "xkb_model" "pc105"
[   889.933] (**) Option "xkb_layout" "us"
[   889.933] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[   889.933] (II) No input driver specified, ignoring this device.
[   889.933] (II) This device may have been added with another device file.
[   889.934] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   889.934] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   889.934] (II) Using input driver 'evdev' for 'Sleep Button'
[   889.934] (**) Sleep Button: always reports core events
[   889.934] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   889.934] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   889.934] (--) evdev: Sleep Button: Found keys
[   889.934] (II) evdev: Sleep Button: Configuring as keyboard
[   889.934] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[   889.934] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[   889.934] (**) Option "xkb_rules" "evdev"
[   889.934] (**) Option "xkb_model" "pc105"
[   889.934] (**) Option "xkb_layout" "us"
[   889.934] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[   889.934] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   889.934] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/event7)
[   889.934] (**) Logitech USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[   889.934] (II) Using input driver 'evdev' for 'Logitech USB Laser Mouse'
[   889.934] (**) Logitech USB Laser Mouse: always reports core events
[   889.934] (**) evdev: Logitech USB Laser Mouse: Device: "/dev/input/event7"
[   889.934] (--) evdev: Logitech USB Laser Mouse: Vendor 0x46d Product 0xc069
[   889.934] (--) evdev: Logitech USB Laser Mouse: Found 12 mouse buttons
[   889.934] (--) evdev: Logitech USB Laser Mouse: Found scroll wheel(s)
[   889.934] (--) evdev: Logitech USB Laser Mouse: Found relative axes
[   889.934] (--) evdev: Logitech USB Laser Mouse: Found x and y relative axes
[   889.934] (II) evdev: Logitech USB Laser Mouse: Configuring as mouse
[   889.934] (II) evdev: Logitech USB Laser Mouse: Adding scrollwheel support
[   889.934] (**) evdev: Logitech USB Laser Mouse: YAxisMapping: buttons 4 and 5
[   889.934] (**) evdev: Logitech USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   889.934] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input14/event7"
[   889.934] (II) XINPUT: Adding extended input device "Logitech USB Laser Mouse" (type: MOUSE, id 10)
[   889.934] (II) evdev: Logitech USB Laser Mouse: initialized for relative axes.
[   889.934] (**) Logitech USB Laser Mouse: (accel) keeping acceleration scheme 1
[   889.934] (**) Logitech USB Laser Mouse: (accel) acceleration profile 0
[   889.934] (**) Logitech USB Laser Mouse: (accel) acceleration factor: 2.000
[   889.934] (**) Logitech USB Laser Mouse: (accel) acceleration threshold: 4
[   889.934] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/mouse1)
[   889.934] (II) No input driver specified, ignoring this device.
[   889.934] (II) This device may have been added with another device file.
[   889.935] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event6)
[   889.935] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[   889.935] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[   889.935] (**) BisonCam, NB Pro: always reports core events
[   889.935] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event6"
[   889.935] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x400
[   889.935] (--) evdev: BisonCam, NB Pro: Found keys
[   889.935] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[   889.935] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input13/event6"
[   889.935] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 11)
[   889.935] (**) Option "xkb_rules" "evdev"
[   889.935] (**) Option "xkb_model" "pc105"
[   889.935] (**) Option "xkb_layout" "us"
[   889.935] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event8)
[   889.935] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[   889.935] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[   889.935] (**) Microsoft Wired Keyboard 600: always reports core events
[   889.935] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event8"
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x750
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[   889.935] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[   889.935] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input15/event8"
[   889.935] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 12)
[   889.935] (**) Option "xkb_rules" "evdev"
[   889.935] (**) Option "xkb_model" "pc105"
[   889.935] (**) Option "xkb_layout" "us"
[   889.935] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event9)
[   889.935] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[   889.935] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[   889.935] (**) Microsoft Wired Keyboard 600: always reports core events
[   889.935] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event9"
[   889.935] (II) evdev: Microsoft Wired Keyboard 600: Using mtdev for this device
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x750
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Found 1 mouse buttons
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Found scroll wheel(s)
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Found relative axes
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Found absolute axes
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Found absolute multitouch axes
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Found x and y absolute axes
[   889.935] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[   889.935] (II) evdev: Microsoft Wired Keyboard 600: Forcing relative x/y axes to exist.
[   889.935] (II) evdev: Microsoft Wired Keyboard 600: Configuring as mouse
[   889.935] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[   889.935] (II) evdev: Microsoft Wired Keyboard 600: Adding scrollwheel support
[   889.935] (**) evdev: Microsoft Wired Keyboard 600: YAxisMapping: buttons 4 and 5
[   889.935] (**) evdev: Microsoft Wired Keyboard 600: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   889.935] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input16/event9"
[   889.936] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 13)
[   889.936] (**) Option "xkb_rules" "evdev"
[   889.936] (**) Option "xkb_model" "pc105"
[   889.936] (**) Option "xkb_layout" "us"
[   889.936] (II) evdev: Microsoft Wired Keyboard 600: initialized for relative axes.
[   889.936] (WW) evdev: Microsoft Wired Keyboard 600: ignoring absolute axes.
[   889.936] (**) Microsoft Wired Keyboard 600: (accel) keeping acceleration scheme 1
[   889.936] (**) Microsoft Wired Keyboard 600: (accel) acceleration profile 0
[   889.936] (**) Microsoft Wired Keyboard 600: (accel) acceleration factor: 2.000
[   889.936] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4
[   889.936] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/js0)
[   889.936] (II) No input driver specified, ignoring this device.
[   889.936] (II) This device may have been added with another device file.
[   889.936] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event13)
[   889.936] (II) No input driver specified, ignoring this device.
[   889.936] (II) This device may have been added with another device file.
[   889.936] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event12)
[   889.936] (II) No input driver specified, ignoring this device.
[   889.936] (II) This device may have been added with another device file.
[   889.936] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[   889.936] (II) No input driver specified, ignoring this device.
[   889.936] (II) This device may have been added with another device file.
[   889.936] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   889.936] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   889.936] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   889.936] (**) AT Translated Set 2 keyboard: always reports core events
[   889.936] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   889.936] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   889.936] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   889.936] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   889.936] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   889.937] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)
[   889.937] (**) Option "xkb_rules" "evdev"
[   889.937] (**) Option "xkb_model" "pc105"
[   889.937] (**) Option "xkb_layout" "us"
[   889.937] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   889.937] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   889.937] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   889.937] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   889.937] (II) LoadModule: "synaptics"
[   889.937] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   889.937] (II) Module synaptics: vendor="X.Org Foundation"
[   889.937]     compiled for 1.15.0, module version = 1.7.4
[   889.937]     Module class: X.Org XInput Driver
[   889.937]     ABI class: X.Org XInput driver, version 20.0
[   889.937] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   889.937] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   889.937] (**) Option "Device" "/dev/input/event5"
[   889.964] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[   889.964] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5692 (res 66)
[   889.964] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4680 (res 102)
[   889.964] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   889.964] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   889.964] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[   889.964] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   889.964] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   889.964] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   889.980] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event5"
[   889.980] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 15)
[   889.980] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   889.980] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   889.980] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[   889.980] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   889.980] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   889.980] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   889.980] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   889.980] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   889.980] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   889.980] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   900.480] (II) UnloadModule: "synaptics"
[   900.481] (II) evdev: AT Translated Set 2 keyboard: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.481] (II) evdev: Microsoft Wired Keyboard 600: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.481] (II) evdev: Microsoft Wired Keyboard 600: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.481] (II) evdev: BisonCam, NB Pro: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.481] (II) evdev: Logitech USB Laser Mouse: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.481] (II) evdev: Sleep Button: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.481] (II) evdev: Power Button: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.481] (II) evdev: Video Bus: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.481] (II) evdev: Power Button: Close
[   900.481] (II) UnloadModule: "evdev"
[   900.517] (EE) Server terminated successfully (0). Closing log file.
```

---

### Post by dino99 on 2015-03-21
boot in revory mode, then open a terminal and run : sudo dpkg-reconfigure lightdm

---

### Post by l33t8l on 2015-03-23
No joy, I'm afraid.

Where can I look (i.e. log files) to work out why i'm being logged out immediately?

---

