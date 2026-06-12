---
title: "Blank screen after login - startx fails with &quot;No protocol specified&quot;"
date: 2014-03-07
forum: Desktop Environments
---

### Post by davidmiller252-4 on 2014-03-07
I am able to get to the login screen and after entering my password and hitting enter the screen goes blank. When I ctrl-alt-f1 into a shell and run 'startx' I get a bunch of stuff being loaded and then this is where it get's stuck:
```

Loading extension GLX
No protocol specified

waiting for X server to begin accepting connections
No protocol specified
.(II) AIGLX: Suspending AIGLX clients for VT switch
.
No protocol specified
..
No protocol specified
..
.
.

```

I've been on 13.10 for a while without any issues. This occurred after restoring my computer from a suspended state. Possibly a driver upgrade may have caused it?
My Xorg.0.log is the following:

```

[    26.918] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    26.918] X Protocol Version 11, Revision 0
[    26.918] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    26.918] Current Operating System: Linux Skynet 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64
[    26.918] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=89d155c5-aea6-4ace-86ca-c5142ec158c1 ro quiet splash vt.handoff=7
[    26.918] Build Date: 17 December 2013  10:06:15AM
[    26.918] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    26.918] Current version of pixman: 0.30.2
[    26.918]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    26.918] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.918] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  7 16:05:10 2014
[    26.999] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.013] (==) No Layout section.  Using the first Screen section.
[    27.013] (==) No screen section available. Using defaults.
[    27.013] (**) |-->Screen "Default Screen Section" (0)
[    27.013] (**) |   |-->Monitor "<default monitor>"
[    27.013] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    27.013] (==) Automatically adding devices
[    27.013] (==) Automatically enabling devices
[    27.013] (==) Automatically adding GPU devices
[    27.013] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.013]     Entry deleted from font path.
[    27.013] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.013]     Entry deleted from font path.
[    27.013] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.013]     Entry deleted from font path.
[    27.013] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.013]     Entry deleted from font path.
[    27.014] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.014]     Entry deleted from font path.
[    27.014] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    27.014] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.014] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.014] (II) Loader magic: 0x7f8276228d20
[    27.014] (II) Module ABI versions:
[    27.014]     X.Org ANSI C Emulation: 0.4
[    27.014]     X.Org Video Driver: 14.1
[    27.014]     X.Org XInput driver : 19.1
[    27.014]     X.Org Server Extension : 7.0
[    27.014] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.015] (--) PCI:*(0:0:2:0) 8086:0116:1043:1652 rev 9, Mem @ 0xdd000000/4194304, 0xc0000000/268435456, I/O @ 0x0000e000/64
[    27.015] (II) Open ACPI successful (/var/run/acpid.socket)
[    27.015] Initializing built-in extension Generic Event Extension
[    27.015] Initializing built-in extension SHAPE
[    27.015] Initializing built-in extension MIT-SHM
[    27.015] Initializing built-in extension XInputExtension
[    27.015] Initializing built-in extension XTEST
[    27.015] Initializing built-in extension BIG-REQUESTS
[    27.015] Initializing built-in extension SYNC
[    27.015] Initializing built-in extension XKEYBOARD
[    27.015] Initializing built-in extension XC-MISC
[    27.015] Initializing built-in extension SECURITY
[    27.015] Initializing built-in extension XINERAMA
[    27.015] Initializing built-in extension XFIXES
[    27.015] Initializing built-in extension RENDER
[    27.015] Initializing built-in extension RANDR
[    27.015] Initializing built-in extension COMPOSITE
[    27.015] Initializing built-in extension DAMAGE
[    27.015] Initializing built-in extension MIT-SCREEN-SAVER
[    27.015] Initializing built-in extension DOUBLE-BUFFER
[    27.015] Initializing built-in extension RECORD
[    27.015] Initializing built-in extension DPMS
[    27.015] Initializing built-in extension X-Resource
[    27.015] Initializing built-in extension XVideo
[    27.015] Initializing built-in extension XVideo-MotionCompensation
[    27.015] Initializing built-in extension SELinux
[    27.015] Initializing built-in extension XFree86-VidModeExtension
[    27.015] Initializing built-in extension XFree86-DGA
[    27.015] Initializing built-in extension XFree86-DRI
[    27.015] Initializing built-in extension DRI2
[    27.015] (II) "glx" will be loaded by default.
[    27.015] (WW) "xmir" is not to be loaded by default. Skipping.
[    27.015] (II) LoadModule: "dri2"
[    27.015] (II) Module "dri2" already built-in
[    27.015] (II) LoadModule: "glamoregl"
[    27.106] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    28.053] (II) Module glamoregl: vendor="X.Org Foundation"
[    28.053]     compiled for 1.14.5, module version = 0.5.1
[    28.053]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.053] (II) LoadModule: "glx"
[    28.053] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.053] (II) Module glx: vendor="X.Org Foundation"
[    28.053]     compiled for 1.14.5, module version = 1.0.0
[    28.053]     ABI class: X.Org Server Extension, version 7.0
[    28.053] (==) AIGLX enabled
[    28.053] Loading extension GLX
[    28.053] (==) Matched intel as autoconfigured driver 0
[    28.053] (==) Matched intel as autoconfigured driver 1
[    28.053] (==) Matched vesa as autoconfigured driver 2
[    28.053] (==) Matched modesetting as autoconfigured driver 3
[    28.054] (==) Matched fbdev as autoconfigured driver 4
[    28.054] (==) Assigned the driver to the xf86ConfigLayout
[    28.054] (II) LoadModule: "intel"
[    28.054] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    28.133] (II) Module intel: vendor="X.Org Foundation"
[    28.133]     compiled for 1.14.5, module version = 2.99.910
[    28.133]     Module class: X.Org Video Driver
[    28.133]     ABI class: X.Org Video Driver, version 14.1
[    28.133] (II) LoadModule: "vesa"
[    28.133] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.133] (II) Module vesa: vendor="X.Org Foundation"
[    28.133]     compiled for 1.14.1, module version = 2.3.2
[    28.133]     Module class: X.Org Video Driver
[    28.133]     ABI class: X.Org Video Driver, version 14.1
[    28.133] (II) LoadModule: "modesetting"
[    28.133] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.133] (II) Module modesetting: vendor="X.Org Foundation"
[    28.133]     compiled for 1.14.1, module version = 0.8.0
[    28.133]     Module class: X.Org Video Driver
[    28.133]     ABI class: X.Org Video Driver, version 14.1
[    28.133] (II) LoadModule: "fbdev"
[    28.133] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.133] (II) Module fbdev: vendor="X.Org Foundation"
[    28.133]     compiled for 1.14.1, module version = 0.4.3
[    28.133]     Module class: X.Org Video Driver
[    28.133]     ABI class: X.Org Video Driver, version 14.1
[    28.133] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    28.133] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    28.133] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    28.133] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    28.133] (II) VESA: driver for VESA chipsets: vesa
[    28.133] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    28.133] (II) FBDEV: driver for framebuffer: fbdev
[    28.133] (++) using VT number 7


[    28.134] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.910+git20140305.a2b4f265-0ubuntu0sarvatt~saucy (Robert Hooker <sarvatt@ubuntu.com>)
[    28.134] (WW) Falling back to old probe method for vesa
[    28.134] (WW) Falling back to old probe method for modesetting
[    28.134] (WW) Falling back to old probe method for fbdev
[    28.134] (II) Loading sub module "fbdevhw"
[    28.134] (II) LoadModule: "fbdevhw"
[    28.134] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.134] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.134]     compiled for 1.14.5, module version = 0.0.2
[    28.134]     ABI class: X.Org Video Driver, version 14.1
[    28.134] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 3000
[    28.134] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    28.134] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.134] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    28.134] (==) intel(0): RGB weight 888
[    28.134] (==) intel(0): Default visual is TrueColor
[    28.134] (**) intel(0): Framebuffer tiled
[    28.134] (**) intel(0): Pixmaps tiled
[    28.134] (**) intel(0): "Tear free" disabled
[    28.134] (**) intel(0): Forcing per-crtc-pixmaps? no
[    28.134] (II) intel(0): Output LVDS1 has no monitor section
[    28.135] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output LVDS1
[    28.135] (II) intel(0): Output VGA1 has no monitor section
[    28.135] (II) intel(0): Output HDMI1 has no monitor section
[    28.135] (II) intel(0): Output DP1 has no monitor section
[    28.135] (II) intel(0): Output VIRTUAL1 has no monitor section
[    28.135] (--) intel(0): Output LVDS1 using initial mode 1366x768 on pipe 0
[    28.135] (==) intel(0): DPI set to (96, 96)
[    28.135] (II) Loading sub module "dri2"
[    28.135] (II) LoadModule: "dri2"
[    28.135] (II) Module "dri2" already built-in
[    28.135] (II) UnloadModule: "vesa"
[    28.135] (II) Unloading vesa
[    28.135] (II) UnloadModule: "modesetting"
[    28.135] (II) Unloading modesetting
[    28.135] (II) UnloadModule: "fbdev"
[    28.135] (II) Unloading fbdev
[    28.135] (II) UnloadSubModule: "fbdevhw"
[    28.135] (II) Unloading fbdevhw
[    28.135] (==) Depth 24 pixmap format is 32 bpp
[    28.135] (II) intel(0): SNA initialized with Sandybridge (gen6, gt2) backend
[    28.135] (==) intel(0): Backing store disabled
[    28.135] (==) intel(0): Silken mouse enabled
[    28.135] (II) intel(0): HW Cursor enabled
[    28.135] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.135] (==) intel(0): DPMS enabled
[    28.135] (II) intel(0): [DRI2] Setup complete
[    28.135] (II) intel(0): [DRI2]   DRI driver: i965
[    28.135] (II) intel(0): [DRI2]   VDPAU driver: i965
[    28.135] (II) intel(0): direct rendering: DRI2 Enabled
[    28.135] (==) intel(0): hotplug detection: "enabled"
[    28.135] (--) RandR disabled
[    28.139] (II) SELinux: Disabled on system
[    28.349] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    28.349] (II) AIGLX: enabled GLX_INTEL_swap_event
[    28.349] (II) AIGLX: enabled GLX_ARB_create_context
[    28.349] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    28.349] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    28.349] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    28.349] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    28.350] (II) AIGLX: Loaded and initialized i965
[    28.350] (II) GLX: Initialized DRI2 GL provider for screen 0
[    28.351] (II) intel(0): switch to mode 1366x768@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none
[    28.368] (II) intel(0): Setting screen physical size to 361 x 203
[    28.374] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.375] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    28.375] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.375] (II) LoadModule: "evdev"
[    28.375] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.418] (II) Module evdev: vendor="X.Org Foundation"
[    28.418]     compiled for 1.14.1, module version = 2.7.3
[    28.418]     Module class: X.Org XInput Driver
[    28.418]     ABI class: X.Org XInput driver, version 19.1
[    28.418] (II) Using input driver 'evdev' for 'Power Button'
[    28.418] (**) Power Button: always reports core events
[    28.418] (**) evdev: Power Button: Device: "/dev/input/event2"
[    28.418] (--) evdev: Power Button: Vendor 0 Product 0x1
[    28.418] (--) evdev: Power Button: Found keys
[    28.418] (II) evdev: Power Button: Configuring as keyboard
[    28.418] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    28.418] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    28.418] (**) Option "xkb_rules" "evdev"
[    28.418] (**) Option "xkb_model" "pc105"
[    28.418] (**) Option "xkb_layout" "us"
[    28.418] (**) Option "xkb_variant" "dvorak"
[    28.420] (II) XKB: reuse xkmfile /var/lib/xkb/server-67E01E0DB470BCE62CC253395E30321B147B483E.xkm
[    28.420] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    28.420] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.420] (II) Using input driver 'evdev' for 'Video Bus'
[    28.420] (**) Video Bus: always reports core events
[    28.420] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    28.420] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    28.420] (--) evdev: Video Bus: Found keys
[    28.420] (II) evdev: Video Bus: Configuring as keyboard
[    28.420] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input4/event4"
[    28.420] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    28.420] (**) Option "xkb_rules" "evdev"
[    28.420] (**) Option "xkb_model" "pc105"
[    28.420] (**) Option "xkb_layout" "us"
[    28.420] (**) Option "xkb_variant" "dvorak"
[    28.421] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.421] (II) No input driver specified, ignoring this device.
[    28.421] (II) This device may have been added with another device file.
[    28.421] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    28.421] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.421] (II) Using input driver 'evdev' for 'Sleep Button'
[    28.421] (**) Sleep Button: always reports core events
[    28.421] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    28.421] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    28.421] (--) evdev: Sleep Button: Found keys
[    28.421] (II) evdev: Sleep Button: Configuring as keyboard
[    28.421] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    28.421] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    28.421] (**) Option "xkb_rules" "evdev"
[    28.421] (**) Option "xkb_model" "pc105"
[    28.421] (**) Option "xkb_layout" "us"
[    28.421] (**) Option "xkb_variant" "dvorak"
[    28.421] (II) config/udev: Adding drm device (/dev/dri/card0)
[    28.421] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    28.421] (II) config/udev: Adding input device USB 2.0 UVC VGA WebCam (/dev/input/event7)
[    28.421] (**) USB 2.0 UVC VGA WebCam: Applying InputClass "evdev keyboard catchall"
[    28.421] (II) Using input driver 'evdev' for 'USB 2.0 UVC VGA WebCam'
[    28.421] (**) USB 2.0 UVC VGA WebCam: always reports core events
[    28.421] (**) evdev: USB 2.0 UVC VGA WebCam: Device: "/dev/input/event7"
[    28.421] (--) evdev: USB 2.0 UVC VGA WebCam: Vendor 0x13d3 Product 0x5710
[    28.421] (--) evdev: USB 2.0 UVC VGA WebCam: Found keys
[    28.421] (II) evdev: USB 2.0 UVC VGA WebCam: Configuring as keyboard
[    28.421] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input7/event7"
[    28.421] (II) XINPUT: Adding extended input device "USB 2.0 UVC VGA WebCam" (type: KEYBOARD, id 9)
[    28.421] (**) Option "xkb_rules" "evdev"
[    28.421] (**) Option "xkb_model" "pc105"
[    28.421] (**) Option "xkb_layout" "us"
[    28.421] (**) Option "xkb_variant" "dvorak"
[    28.422] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    28.422] (II) No input driver specified, ignoring this device.
[    28.422] (II) This device may have been added with another device file.
[    28.422] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event8)
[    28.422] (II) No input driver specified, ignoring this device.
[    28.422] (II) This device may have been added with another device file.
[    28.422] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    28.422] (II) No input driver specified, ignoring this device.
[    28.422] (II) This device may have been added with another device file.
[    28.422] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event5)
[    28.422] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    28.422] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    28.422] (**) Asus WMI hotkeys: always reports core events
[    28.422] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event5"
[    28.422] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    28.422] (--) evdev: Asus WMI hotkeys: Found keys
[    28.422] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    28.422] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input5/event5"
[    28.422] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 10)
[    28.422] (**) Option "xkb_rules" "evdev"
[    28.422] (**) Option "xkb_model" "pc105"
[    28.422] (**) Option "xkb_layout" "us"
[    28.422] (**) Option "xkb_variant" "dvorak"
[    28.422] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    28.422] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.422] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    28.422] (**) AT Translated Set 2 keyboard: always reports core events
[    28.422] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    28.423] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    28.423] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    28.423] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    28.423] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    28.423] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    28.423] (**) Option "xkb_rules" "evdev"
[    28.423] (**) Option "xkb_model" "pc105"
[    28.423] (**) Option "xkb_layout" "us"
[    28.423] (**) Option "xkb_variant" "dvorak"
[    28.423] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    28.423] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    28.423] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    28.423] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    28.423] (II) LoadModule: "synaptics"
[    28.423] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.423] (II) Module synaptics: vendor="X.Org Foundation"
[    28.423]     compiled for 1.14.2, module version = 1.7.1
[    28.423]     Module class: X.Org XInput Driver
[    28.423]     ABI class: X.Org XInput driver, version 19.1
[    28.423] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    28.423] (**) ETPS/2 Elantech Touchpad: always reports core events
[    28.423] (**) Option "Device" "/dev/input/event6"
[    28.476] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508 (res 0)
[    28.476] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320 (res 0)
[    28.476] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    28.476] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    28.476] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    28.476] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    28.476] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    28.476] (**) ETPS/2 Elantech Touchpad: always reports core events
[    28.492] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    28.492] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    28.492] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    28.492] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    28.492] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.071
[    28.492] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    28.492] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    28.492] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    28.492] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    28.492] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    28.492] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    28.492] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.421] (II) intel(0): EDID vendor "SEC", prod id 21569
[    30.421] (II) intel(0): Printing DDC gathered Modelines:
[    30.421] (II) intel(0): Modeline "1366x768"x0.0   78.05  1366 1414 1446 1646  768 770 775 790 +hsync -vsync (47.4 kHz eP)
[    30.421] (II) intel(0): Modeline "1366x768"x0.0   78.05  1366 1414 1446 1644  768 770 775 790 +hsync -vsync (47.5 kHz e)
[    31.818] (II) XKB: reuse xkmfile /var/lib/xkb/server-214897094EF3487F6600C13FDFE2B6CB9A6493EF.xkm
[    31.844] (II) XKB: reuse xkmfile /var/lib/xkb/server-214897094EF3487F6600C13FDFE2B6CB9A6493EF.xkm
[    31.848] (II) XKB: reuse xkmfile /var/lib/xkb/server-214897094EF3487F6600C13FDFE2B6CB9A6493EF.xkm
[    39.828] (II) AIGLX: Suspending AIGLX clients for VT switch
[    25.914] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    25.914] X Protocol Version 11, Revision 0
[    25.914] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    25.914] Current Operating System: Linux Skynet 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64
[    25.914] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=89d155c5-aea6-4ace-86ca-c5142ec158c1 ro quiet splash vt.handoff=7
[    25.914] Build Date: 17 December 2013  10:06:15AM
[    25.914] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    25.914] Current version of pixman: 0.30.2
[    25.914]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    25.914] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    25.914] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar  7 16:20:58 2014
[    25.914] (==) Using config file: "/etc/X11/xorg.conf"
[    25.914] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.051] (==) No Layout section.  Using the first Screen section.
[    26.051] (**) |-->Screen "Default Screen" (0)
[    26.052] (**) |   |-->Monitor "Configured Monitor"
[    26.052] (**) |   |-->Device "Configured Video Device"
[    26.052] (==) Automatically adding devices
[    26.052] (==) Automatically enabling devices
[    26.052] (==) Automatically adding GPU devices
[    26.052] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.052]     Entry deleted from font path.
[    26.052] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.052]     Entry deleted from font path.
[    26.052] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.052]     Entry deleted from font path.
[    26.052] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.052]     Entry deleted from font path.
[    26.052] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.052]     Entry deleted from font path.
[    26.052] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    26.052] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.052] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.052] (II) Loader magic: 0x7fbba0b50d20
[    26.052] (II) Module ABI versions:
[    26.052]     X.Org ANSI C Emulation: 0.4
[    26.052]     X.Org Video Driver: 14.1
[    26.052]     X.Org XInput driver : 19.1
[    26.052]     X.Org Server Extension : 7.0
[    26.052] (II) xfree86: Adding drm device (/dev/dri/card0)
[    26.053] (--) PCI:*(0:0:2:0) 8086:0116:1043:1652 rev 9, Mem @ 0xdd000000/4194304, 0xc0000000/268435456, I/O @ 0x0000e000/64
[    26.053] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.053] Initializing built-in extension Generic Event Extension
[    26.053] Initializing built-in extension SHAPE
[    26.053] Initializing built-in extension MIT-SHM
[    26.053] Initializing built-in extension XInputExtension
[    26.053] Initializing built-in extension XTEST
[    26.053] Initializing built-in extension BIG-REQUESTS
[    26.053] Initializing built-in extension SYNC
[    26.053] Initializing built-in extension XKEYBOARD
[    26.053] Initializing built-in extension XC-MISC
[    26.053] Initializing built-in extension SECURITY
[    26.053] Initializing built-in extension XINERAMA
[    26.053] Initializing built-in extension XFIXES
[    26.053] Initializing built-in extension RENDER
[    26.053] Initializing built-in extension RANDR
[    26.053] Initializing built-in extension COMPOSITE
[    26.053] Initializing built-in extension DAMAGE
[    26.053] Initializing built-in extension MIT-SCREEN-SAVER
[    26.053] Initializing built-in extension DOUBLE-BUFFER
[    26.053] Initializing built-in extension RECORD
[    26.053] Initializing built-in extension DPMS
[    26.053] Initializing built-in extension X-Resource
[    26.053] Initializing built-in extension XVideo
[    26.053] Initializing built-in extension XVideo-MotionCompensation
[    26.053] Initializing built-in extension SELinux
[    26.053] Initializing built-in extension XFree86-VidModeExtension
[    26.053] Initializing built-in extension XFree86-DGA
[    26.053] Initializing built-in extension XFree86-DRI
[    26.053] Initializing built-in extension DRI2
[    26.053] (II) "glx" will be loaded by default.
[    26.053] (WW) "xmir" is not to be loaded by default. Skipping.
[    26.053] (II) LoadModule: "dri2"
[    26.053] (II) Module "dri2" already built-in
[    26.053] (II) LoadModule: "glamoregl"
[    26.147] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    27.139] (II) Module glamoregl: vendor="X.Org Foundation"
[    27.139]     compiled for 1.14.3, module version = 0.5.1
[    27.139]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.139] (II) LoadModule: "glx"
[    27.139] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    27.139] (II) Module glx: vendor="X.Org Foundation"
[    27.139]     compiled for 1.14.5, module version = 1.0.0
[    27.139]     ABI class: X.Org Server Extension, version 7.0
[    27.140] (==) AIGLX enabled
[    27.140] Loading extension GLX
[    27.140] (II) LoadModule: "fbdev"
[    27.140] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.140] (II) Module fbdev: vendor="X.Org Foundation"
[    27.140]     compiled for 1.14.1, module version = 0.4.3
[    27.140]     Module class: X.Org Video Driver
[    27.140]     ABI class: X.Org Video Driver, version 14.1
[    27.140] (II) FBDEV: driver for framebuffer: fbdev
[    27.140] (++) using VT number 7


[    27.140] (II) Loading sub module "fbdevhw"
[    27.140] (II) LoadModule: "fbdevhw"
[    27.140] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.140] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.140]     compiled for 1.14.5, module version = 0.0.2
[    27.140]     ABI class: X.Org Video Driver, version 14.1
[    27.140] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    27.140] (II) FBDEV(0): using default device
[    27.140] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    27.140] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    27.140] (==) FBDEV(0): RGB weight 888
[    27.140] (==) FBDEV(0): Default visual is TrueColor
[    27.140] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.140] (II) FBDEV(0): hardware: inteldrmfb (video memory: 4128kB)
[    27.140] (II) FBDEV(0): checking modes against framebuffer device...
[    27.140] (II) FBDEV(0): checking modes against monitor...
[    27.140] (--) FBDEV(0): Virtual size is 1366x768 (pitch 1366)
[    27.140] (**) FBDEV(0):  Built-in mode "current"
[    27.140] (==) FBDEV(0): DPI set to (96, 96)
[    27.140] (II) Loading sub module "fb"
[    27.140] (II) LoadModule: "fb"
[    27.140] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.180] (II) Module fb: vendor="X.Org Foundation"
[    27.180]     compiled for 1.14.5, module version = 1.0.0
[    27.180]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.180] (**) FBDEV(0): using shadow framebuffer
[    27.180] (II) Loading sub module "shadow"
[    27.180] (II) LoadModule: "shadow"
[    27.180] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    27.193] (II) Module shadow: vendor="X.Org Foundation"
[    27.193]     compiled for 1.14.5, module version = 1.1.0
[    27.193]     ABI class: X.Org ANSI C Emulation, version 0.4
[    27.193] (==) Depth 24 pixmap format is 32 bpp
[    27.193] (==) FBDEV(0): Backing store disabled
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.193] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.194] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    27.195] (==) FBDEV(0): DPMS enabled
[    27.195] (==) RandR enabled
[    27.198] (II) SELinux: Disabled on system
[    27.198] (II) AIGLX: Screen 0 is not DRI2 capable
[    27.198] (II) AIGLX: Screen 0 is not DRI capable
[    28.546] (II) AIGLX: Loaded and initialized swrast
[    28.546] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    28.553] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.555] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    28.555] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.555] (II) LoadModule: "evdev"
[    28.555] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.570] (II) Module evdev: vendor="X.Org Foundation"
[    28.570]     compiled for 1.14.1, module version = 2.7.3
[    28.570]     Module class: X.Org XInput Driver
[    28.570]     ABI class: X.Org XInput driver, version 19.1
[    28.570] (II) Using input driver 'evdev' for 'Power Button'
[    28.570] (**) Power Button: always reports core events
[    28.570] (**) evdev: Power Button: Device: "/dev/input/event2"
[    28.570] (--) evdev: Power Button: Vendor 0 Product 0x1
[    28.571] (--) evdev: Power Button: Found keys
[    28.571] (II) evdev: Power Button: Configuring as keyboard
[    28.571] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    28.571] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    28.571] (**) Option "xkb_rules" "evdev"
[    28.571] (**) Option "xkb_model" "pc105"
[    28.571] (**) Option "xkb_layout" "us"
[    28.571] (**) Option "xkb_variant" "dvorak"
[    28.572] (II) XKB: reuse xkmfile /var/lib/xkb/server-67E01E0DB470BCE62CC253395E30321B147B483E.xkm
[    28.573] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    28.573] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.573] (II) Using input driver 'evdev' for 'Video Bus'
[    28.573] (**) Video Bus: always reports core events
[    28.573] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    28.573] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    28.573] (--) evdev: Video Bus: Found keys
[    28.573] (II) evdev: Video Bus: Configuring as keyboard
[    28.573] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input4/event4"
[    28.573] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    28.573] (**) Option "xkb_rules" "evdev"
[    28.573] (**) Option "xkb_model" "pc105"
[    28.573] (**) Option "xkb_layout" "us"
[    28.573] (**) Option "xkb_variant" "dvorak"
[    28.573] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.573] (II) No input driver specified, ignoring this device.
[    28.573] (II) This device may have been added with another device file.
[    28.573] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    28.573] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.573] (II) Using input driver 'evdev' for 'Sleep Button'
[    28.573] (**) Sleep Button: always reports core events
[    28.573] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    28.573] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    28.573] (--) evdev: Sleep Button: Found keys
[    28.573] (II) evdev: Sleep Button: Configuring as keyboard
[    28.573] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    28.573] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    28.573] (**) Option "xkb_rules" "evdev"
[    28.573] (**) Option "xkb_model" "pc105"
[    28.573] (**) Option "xkb_layout" "us"
[    28.573] (**) Option "xkb_variant" "dvorak"
[    28.574] (II) config/udev: Adding drm device (/dev/dri/card0)
[    28.574] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    28.574] (II) config/udev: Adding input device USB 2.0 UVC VGA WebCam (/dev/input/event5)
[    28.574] (**) USB 2.0 UVC VGA WebCam: Applying InputClass "evdev keyboard catchall"
[    28.574] (II) Using input driver 'evdev' for 'USB 2.0 UVC VGA WebCam'
[    28.574] (**) USB 2.0 UVC VGA WebCam: always reports core events
[    28.574] (**) evdev: USB 2.0 UVC VGA WebCam: Device: "/dev/input/event5"
[    28.574] (--) evdev: USB 2.0 UVC VGA WebCam: Vendor 0x13d3 Product 0x5710
[    28.574] (--) evdev: USB 2.0 UVC VGA WebCam: Found keys
[    28.574] (II) evdev: USB 2.0 UVC VGA WebCam: Configuring as keyboard
[    28.574] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5/event5"
[    28.574] (II) XINPUT: Adding extended input device "USB 2.0 UVC VGA WebCam" (type: KEYBOARD, id 9)
[    28.574] (**) Option "xkb_rules" "evdev"
[    28.574] (**) Option "xkb_model" "pc105"
[    28.574] (**) Option "xkb_layout" "us"
[    28.574] (**) Option "xkb_variant" "dvorak"
[    28.574] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    28.574] (II) No input driver specified, ignoring this device.
[    28.574] (II) This device may have been added with another device file.
[    28.574] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event8)
[    28.574] (II) No input driver specified, ignoring this device.
[    28.574] (II) This device may have been added with another device file.
[    28.574] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    28.574] (II) No input driver specified, ignoring this device.
[    28.574] (II) This device may have been added with another device file.
[    28.575] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event7)
[    28.575] (**) Asus WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    28.575] (II) Using input driver 'evdev' for 'Asus WMI hotkeys'
[    28.575] (**) Asus WMI hotkeys: always reports core events
[    28.575] (**) evdev: Asus WMI hotkeys: Device: "/dev/input/event7"
[    28.575] (--) evdev: Asus WMI hotkeys: Vendor 0 Product 0
[    28.575] (--) evdev: Asus WMI hotkeys: Found keys
[    28.575] (II) evdev: Asus WMI hotkeys: Configuring as keyboard
[    28.575] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input7/event7"
[    28.575] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 10)
[    28.575] (**) Option "xkb_rules" "evdev"
[    28.575] (**) Option "xkb_model" "pc105"
[    28.575] (**) Option "xkb_layout" "us"
[    28.575] (**) Option "xkb_variant" "dvorak"
[    28.575] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    28.575] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.575] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    28.575] (**) AT Translated Set 2 keyboard: always reports core events
[    28.575] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    28.575] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    28.575] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    28.575] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    28.575] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    28.575] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    28.575] (**) Option "xkb_rules" "evdev"
[    28.575] (**) Option "xkb_model" "pc105"
[    28.575] (**) Option "xkb_layout" "us"
[    28.575] (**) Option "xkb_variant" "dvorak"
[    28.575] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[    28.575] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    28.575] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    28.575] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    28.575] (II) LoadModule: "synaptics"
[    28.576] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    28.576] (II) Module synaptics: vendor="X.Org Foundation"
[    28.576]     compiled for 1.14.2, module version = 1.7.1
[    28.576]     Module class: X.Org XInput Driver
[    28.576]     ABI class: X.Org XInput driver, version 19.1
[    28.576] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    28.576] (**) ETPS/2 Elantech Touchpad: always reports core events
[    28.576] (**) Option "Device" "/dev/input/event6"
[    28.596] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2508 (res 0)
[    28.596] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 1320 (res 0)
[    28.596] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    28.596] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    28.596] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    28.596] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    28.596] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    28.596] (**) ETPS/2 Elantech Touchpad: always reports core events
[    28.608] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input6/event6"
[    28.608] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    28.608] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    28.608] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    28.608] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.071
[    28.608] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    28.608] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    28.608] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    28.608] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    28.608] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    28.608] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    28.608] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    32.817] (II) XKB: reuse xkmfile /var/lib/xkb/server-214897094EF3487F6600C13FDFE2B6CB9A6493EF.xkm
[    32.854] (II) XKB: reuse xkmfile /var/lib/xkb/server-214897094EF3487F6600C13FDFE2B6CB9A6493EF.xkm
[    32.857] (II) XKB: reuse xkmfile /var/lib/xkb/server-214897094EF3487F6600C13FDFE2B6CB9A6493EF.xkm

```

Thank you

---

### Post by davidmiller252-4 on 2014-03-08
So it turns out this was all a result of me messing around with my /etc/environment variables and adding $HOME. It completely escaped my mind that I had made this change

---

