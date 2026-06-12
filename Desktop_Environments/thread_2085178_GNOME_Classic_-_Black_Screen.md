---
title: "GNOME Classic - Black Screen"
date: 2012-11-17
forum: Desktop Environments
---

### Post by 3246251196 on 2012-11-17
```

[ 24868.771] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[ 24868.771] X Protocol Version 11, Revision 0
[ 24868.771] Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
[ 24868.771] Current Operating System: Linux rjd-324-Ubu-Bri 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64
[ 24868.771] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-32-generic root=UUID=a8b64efd-1310-4a44-a892-ad3b4b900188 ro quiet splash nomodeset vt.handoff=7
[ 24868.771] Build Date: 29 August 2012  12:12:33AM
[ 24868.771] xorg-server 2:1.11.4-0ubuntu10.8 (For technical support please see http://www.ubuntu.com/support) 
[ 24868.771] Current version of pixman: 0.24.4
[ 24868.771]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[ 24868.771] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 24868.771] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov 17 16:31:51 2012
[ 24868.771] (==) Using config file: "/etc/X11/xorg.conf"
[ 24868.771] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 24868.772] (==) ServerLayout "Layout0"
[ 24868.772] (**) |-->Screen "Screen0" (0)
[ 24868.772] (**) |   |-->Monitor "Monitor0"
[ 24868.772] (**) |   |-->Device "Device0"
[ 24868.772] (**) |-->Input Device "Keyboard0"
[ 24868.772] (**) |-->Input Device "Mouse0"
[ 24868.772] (==) Automatically adding devices
[ 24868.772] (==) Automatically enabling devices
[ 24868.772] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 24868.772]     Entry deleted from font path.
[ 24868.772] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[ 24868.772] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[ 24868.772] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 24868.772] (WW) Disabling Keyboard0
[ 24868.772] (WW) Disabling Mouse0
[ 24868.772] (II) Loader magic: 0x7effb164bb00
[ 24868.772] (II) Module ABI versions:
[ 24868.772]     X.Org ANSI C Emulation: 0.4
[ 24868.772]     X.Org Video Driver: 11.0
[ 24868.772]     X.Org XInput driver : 16.0
[ 24868.772]     X.Org Server Extension : 6.0
[ 24868.772] (--) PCI:*(0:1:0:0) 10de:1087:3842:2066 rev 161, Mem @ 0xfa000000/16777216, 0xf0000000/134217728, 0xf8000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[ 24868.773] (II) Open ACPI successful (/var/run/acpid.socket)
[ 24868.773] (II) LoadModule: "extmod"
[ 24868.773] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 24868.773] (II) Module extmod: vendor="X.Org Foundation"
[ 24868.773]     compiled for 1.11.3, module version = 1.0.0
[ 24868.773]     Module class: X.Org Server Extension
[ 24868.773]     ABI class: X.Org Server Extension, version 6.0
[ 24868.773] (II) Loading extension MIT-SCREEN-SAVER
[ 24868.773] (II) Loading extension XFree86-VidModeExtension
[ 24868.773] (II) Loading extension XFree86-DGA
[ 24868.773] (II) Loading extension DPMS
[ 24868.773] (II) Loading extension XVideo
[ 24868.773] (II) Loading extension XVideo-MotionCompensation
[ 24868.773] (II) Loading extension X-Resource
[ 24868.773] (II) LoadModule: "dbe"
[ 24868.773] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 24868.773] (II) Module dbe: vendor="X.Org Foundation"
[ 24868.773]     compiled for 1.11.3, module version = 1.0.0
[ 24868.773]     Module class: X.Org Server Extension
[ 24868.773]     ABI class: X.Org Server Extension, version 6.0
[ 24868.773] (II) Loading extension DOUBLE-BUFFER
[ 24868.773] (II) LoadModule: "glx"
[ 24868.773] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[ 24868.778] (II) Module glx: vendor="NVIDIA Corporation"
[ 24868.778]     compiled for 4.0.2, module version = 1.0.0
[ 24868.778]     Module class: X.Org Server Extension
[ 24868.778] (II) NVIDIA GLX Module  304.64  Tue Oct 30 11:18:32 PDT 2012
[ 24868.778] (II) Loading extension GLX
[ 24868.778] (II) LoadModule: "record"
[ 24868.778] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 24868.778] (II) Module record: vendor="X.Org Foundation"
[ 24868.778]     compiled for 1.11.3, module version = 1.13.0
[ 24868.778]     Module class: X.Org Server Extension
[ 24868.778]     ABI class: X.Org Server Extension, version 6.0
[ 24868.778] (II) Loading extension RECORD
[ 24868.778] (II) LoadModule: "dri"
[ 24868.778] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 24868.778] (II) Module dri: vendor="X.Org Foundation"
[ 24868.778]     compiled for 1.11.3, module version = 1.0.0
[ 24868.778]     ABI class: X.Org Server Extension, version 6.0
[ 24868.778] (II) Loading extension XFree86-DRI
[ 24868.778] (II) LoadModule: "dri2"
[ 24868.778] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 24868.778] (II) Module dri2: vendor="X.Org Foundation"
[ 24868.778]     compiled for 1.11.3, module version = 1.2.0
[ 24868.778]     ABI class: X.Org Server Extension, version 6.0
[ 24868.778] (II) Loading extension DRI2
[ 24868.778] (II) LoadModule: "nvidia"
[ 24868.779] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[ 24868.779] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 24868.779]     compiled for 4.0.2, module version = 1.0.0
[ 24868.779]     Module class: X.Org Video Driver
[ 24868.779] (II) NVIDIA dlloader X Driver  304.64  Tue Oct 30 10:59:51 PDT 2012
[ 24868.779] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 24868.779] (++) using VT number 7

[ 24868.779] (II) Loading sub module "fb"
[ 24868.779] (II) LoadModule: "fb"
[ 24868.779] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 24868.779] (II) Module fb: vendor="X.Org Foundation"
[ 24868.779]     compiled for 1.11.3, module version = 1.0.0
[ 24868.779]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 24868.779] (II) Loading sub module "wfb"
[ 24868.779] (II) LoadModule: "wfb"
[ 24868.779] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 24868.779] (II) Module wfb: vendor="X.Org Foundation"
[ 24868.779]     compiled for 1.11.3, module version = 1.0.0
[ 24868.779]     ABI class: X.Org ANSI C Emulation, version 0.4
[ 24868.779] (II) Loading sub module "ramdac"
[ 24868.779] (II) LoadModule: "ramdac"
[ 24868.779] (II) Module "ramdac" already built-in
[ 24868.779] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[ 24868.779] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 24868.779] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 24868.779] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[ 24868.779] (==) NVIDIA(0): RGB weight 888
[ 24868.779] (==) NVIDIA(0): Default visual is TrueColor
[ 24868.779] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 24868.779] (**) NVIDIA(0): Enabling 2D acceleration
[ 24869.064] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[ 24869.064] (II) NVIDIA(GPU-0):     Vision stereo.
[ 24869.065] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 560 Ti (GF110) at PCI:1:0:0 (GPU-0)
[ 24869.065] (--) NVIDIA(0): Memory: 1310720 kBytes
[ 24869.065] (--) NVIDIA(0): VideoBIOS: 70.10.61.00.62
[ 24869.065] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 24869.065] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 24869.068] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 560 Ti at PCI:1:0:0
[ 24869.068] (--) NVIDIA(0):     CRT-0
[ 24869.068] (--) NVIDIA(0):     CRT-1
[ 24869.068] (--) NVIDIA(0):     DELL U2412M (DFP-0) (connected)
[ 24869.068] (--) NVIDIA(0):     DFP-1
[ 24869.068] (--) NVIDIA(0):     DFP-2
[ 24869.068] (--) NVIDIA(0):     DFP-3
[ 24869.068] (--) NVIDIA(0):     DFP-4
[ 24869.068] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[ 24869.068] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[ 24869.068] (--) NVIDIA(0): DELL U2412M (DFP-0): 330.0 MHz maximum pixel clock
[ 24869.068] (--) NVIDIA(0): DELL U2412M (DFP-0): Internal Dual Link TMDS
[ 24869.068] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[ 24869.068] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[ 24869.068] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[ 24869.068] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[ 24869.068] (--) NVIDIA(0): DFP-3: 330.0 MHz maximum pixel clock
[ 24869.068] (--) NVIDIA(0): DFP-3: Internal Single Link TMDS
[ 24869.068] (--) NVIDIA(0): DFP-4: 480.0 MHz maximum pixel clock
[ 24869.068] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[ 24869.068] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 24869.068] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[ 24869.068] (**) NVIDIA(0):     been enabled on all display devices.)
[ 24869.069] (==) NVIDIA(0): 
[ 24869.069] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[ 24869.069] (==) NVIDIA(0):     will be used as the requested mode.
[ 24869.069] (==) NVIDIA(0): 
[ 24869.069] (II) NVIDIA(0): Validated MetaModes:
[ 24869.069] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[ 24869.069] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[ 24869.094] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[ 24869.094] (--) NVIDIA(0):     option
[ 24869.094] (--) Depth 24 pixmap format is 32 bpp
[ 24869.094] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[ 24869.094] (II) NVIDIA:     access.
[ 24869.100] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[ 24869.128] (II) Loading extension NV-GLX
[ 24869.173] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 24869.173] (==) NVIDIA(0): Backing store disabled
[ 24869.173] (==) NVIDIA(0): Silken mouse enabled
[ 24869.173] (**) NVIDIA(0): DPMS enabled
[ 24869.173] (II) Loading extension NV-CONTROL
[ 24869.173] (II) Loading extension XINERAMA
[ 24869.173] (II) Loading sub module "dri2"
[ 24869.173] (II) LoadModule: "dri2"
[ 24869.173] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 24869.173] (II) Module dri2: vendor="X.Org Foundation"
[ 24869.173]     compiled for 1.11.3, module version = 1.2.0
[ 24869.173]     ABI class: X.Org Server Extension, version 6.0
[ 24869.173] (II) NVIDIA(0): [DRI2] Setup complete
[ 24869.173] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[ 24869.173] (--) RandR disabled
[ 24869.173] (II) Initializing built-in extension Generic Event Extension
[ 24869.173] (II) Initializing built-in extension SHAPE
[ 24869.173] (II) Initializing built-in extension MIT-SHM
[ 24869.173] (II) Initializing built-in extension XInputExtension
[ 24869.173] (II) Initializing built-in extension XTEST
[ 24869.173] (II) Initializing built-in extension BIG-REQUESTS
[ 24869.173] (II) Initializing built-in extension SYNC
[ 24869.173] (II) Initializing built-in extension XKEYBOARD
[ 24869.173] (II) Initializing built-in extension XC-MISC
[ 24869.173] (II) Initializing built-in extension SECURITY
[ 24869.173] (II) Initializing built-in extension XINERAMA
[ 24869.173] (II) Initializing built-in extension XFIXES
[ 24869.173] (II) Initializing built-in extension RENDER
[ 24869.173] (II) Initializing built-in extension RANDR
[ 24869.173] (II) Initializing built-in extension COMPOSITE
[ 24869.173] (II) Initializing built-in extension DAMAGE
[ 24869.174] (II) Initializing extension GLX
[ 24869.186] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[ 24869.187] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 24869.187] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 24869.188] (II) LoadModule: "evdev"
[ 24869.188] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 24869.188] (II) Module evdev: vendor="X.Org Foundation"
[ 24869.188]     compiled for 1.11.3, module version = 2.7.0
[ 24869.188]     Module class: X.Org XInput Driver
[ 24869.188]     ABI class: X.Org XInput driver, version 16.0
[ 24869.188] (II) Using input driver 'evdev' for 'Power Button'
[ 24869.188] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 24869.188] (**) Power Button: always reports core events
[ 24869.188] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 24869.188] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 24869.188] (--) evdev: Power Button: Found keys
[ 24869.188] (II) evdev: Power Button: Configuring as keyboard
[ 24869.188] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[ 24869.188] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 24869.188] (**) Option "xkb_rules" "evdev"
[ 24869.188] (**) Option "xkb_model" "pc105"
[ 24869.188] (**) Option "xkb_layout" "gb"
[ 24869.189] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[ 24869.189] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 24869.189] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 24869.189] (II) Using input driver 'evdev' for 'Power Button'
[ 24869.189] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 24869.189] (**) Power Button: always reports core events
[ 24869.189] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 24869.189] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 24869.189] (--) evdev: Power Button: Found keys
[ 24869.189] (II) evdev: Power Button: Configuring as keyboard
[ 24869.189] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[ 24869.189] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[ 24869.189] (**) Option "xkb_rules" "evdev"
[ 24869.189] (**) Option "xkb_model" "pc105"
[ 24869.189] (**) Option "xkb_layout" "gb"
[ 24869.189] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event10)
[ 24869.189] (II) No input driver specified, ignoring this device.
[ 24869.189] (II) This device may have been added with another device file.
[ 24869.189] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event7)
[ 24869.189] (II) No input driver specified, ignoring this device.
[ 24869.189] (II) This device may have been added with another device file.
[ 24869.190] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event8)
[ 24869.190] (II) No input driver specified, ignoring this device.
[ 24869.190] (II) This device may have been added with another device file.
[ 24869.190] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event9)
[ 24869.190] (II) No input driver specified, ignoring this device.
[ 24869.190] (II) This device may have been added with another device file.
[ 24869.190] (II) config/udev: Adding input device Logitech G9x Laser Mouse (/dev/input/event2)
[ 24869.190] (**) Logitech G9x Laser Mouse: Applying InputClass "evdev pointer catchall"
[ 24869.190] (II) Using input driver 'evdev' for 'Logitech G9x Laser Mouse'
[ 24869.190] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 24869.190] (**) Logitech G9x Laser Mouse: always reports core events
[ 24869.190] (**) evdev: Logitech G9x Laser Mouse: Device: "/dev/input/event2"
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Vendor 0x46d Product 0xc066
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Found 20 mouse buttons
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Found scroll wheel(s)
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Found relative axes
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Found x and y relative axes
[ 24869.190] (II) evdev: Logitech G9x Laser Mouse: Configuring as mouse
[ 24869.190] (II) evdev: Logitech G9x Laser Mouse: Adding scrollwheel support
[ 24869.190] (**) evdev: Logitech G9x Laser Mouse: YAxisMapping: buttons 4 and 5
[ 24869.190] (**) evdev: Logitech G9x Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 24869.190] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2/event2"
[ 24869.190] (II) XINPUT: Adding extended input device "Logitech G9x Laser Mouse" (type: MOUSE, id 8)
[ 24869.190] (II) evdev: Logitech G9x Laser Mouse: initialized for relative axes.
[ 24869.190] (**) Logitech G9x Laser Mouse: (accel) keeping acceleration scheme 1
[ 24869.190] (**) Logitech G9x Laser Mouse: (accel) acceleration profile 0
[ 24869.190] (**) Logitech G9x Laser Mouse: (accel) acceleration factor: 2.000
[ 24869.190] (**) Logitech G9x Laser Mouse: (accel) acceleration threshold: 4
[ 24869.190] (II) config/udev: Adding input device Logitech G9x Laser Mouse (/dev/input/mouse0)
[ 24869.190] (II) No input driver specified, ignoring this device.
[ 24869.190] (II) This device may have been added with another device file.
[ 24869.190] (II) config/udev: Adding input device Logitech G9x Laser Mouse (/dev/input/event3)
[ 24869.190] (**) Logitech G9x Laser Mouse: Applying InputClass "evdev keyboard catchall"
[ 24869.190] (II) Using input driver 'evdev' for 'Logitech G9x Laser Mouse'
[ 24869.190] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 24869.190] (**) Logitech G9x Laser Mouse: always reports core events
[ 24869.190] (**) evdev: Logitech G9x Laser Mouse: Device: "/dev/input/event3"
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Vendor 0x46d Product 0xc066
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Found 1 mouse buttons
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Found scroll wheel(s)
[ 24869.190] (--) evdev: Logitech G9x Laser Mouse: Found relative axes
[ 24869.191] (II) evdev: Logitech G9x Laser Mouse: Forcing relative x/y axes to exist.
[ 24869.191] (--) evdev: Logitech G9x Laser Mouse: Found absolute axes
[ 24869.191] (II) evdev: Logitech G9x Laser Mouse: Forcing absolute x/y axes to exist.
[ 24869.191] (--) evdev: Logitech G9x Laser Mouse: Found keys
[ 24869.191] (II) evdev: Logitech G9x Laser Mouse: Configuring as mouse
[ 24869.191] (II) evdev: Logitech G9x Laser Mouse: Configuring as keyboard
[ 24869.191] (II) evdev: Logitech G9x Laser Mouse: Adding scrollwheel support
[ 24869.191] (**) evdev: Logitech G9x Laser Mouse: YAxisMapping: buttons 4 and 5
[ 24869.191] (**) evdev: Logitech G9x Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 24869.191] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input3/event3"
[ 24869.191] (II) XINPUT: Adding extended input device "Logitech G9x Laser Mouse" (type: KEYBOARD, id 9)
[ 24869.191] (**) Option "xkb_rules" "evdev"
[ 24869.191] (**) Option "xkb_model" "pc105"
[ 24869.191] (**) Option "xkb_layout" "gb"
[ 24869.191] (II) evdev: Logitech G9x Laser Mouse: initialized for relative axes.
[ 24869.191] (WW) evdev: Logitech G9x Laser Mouse: ignoring absolute axes.
[ 24869.191] (**) Logitech G9x Laser Mouse: (accel) keeping acceleration scheme 1
[ 24869.191] (**) Logitech G9x Laser Mouse: (accel) acceleration profile 0
[ 24869.191] (**) Logitech G9x Laser Mouse: (accel) acceleration factor: 2.000
[ 24869.191] (**) Logitech G9x Laser Mouse: (accel) acceleration threshold: 4
[ 24869.191] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event4)
[ 24869.191] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[ 24869.191] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[ 24869.191] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 24869.191] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[ 24869.191] (**) evdev: Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event4"
[ 24869.191] (--) evdev: Logitech Logitech Illuminated Keyboard: Vendor 0x46d Product 0xc318
[ 24869.191] (--) evdev: Logitech Logitech Illuminated Keyboard: Found keys
[ 24869.191] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[ 24869.191] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4/event4"
[ 24869.191] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD, id 10)
[ 24869.191] (**) Option "xkb_rules" "evdev"
[ 24869.191] (**) Option "xkb_model" "pc105"
[ 24869.191] (**) Option "xkb_layout" "gb"
[ 24869.191] (II) config/udev: Adding input device Logitech Logitech Illuminated Keyboard (/dev/input/event5)
[ 24869.191] (**) Logitech Logitech Illuminated Keyboard: Applying InputClass "evdev keyboard catchall"
[ 24869.191] (II) Using input driver 'evdev' for 'Logitech Logitech Illuminated Keyboard'
[ 24869.191] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 24869.191] (**) Logitech Logitech Illuminated Keyboard: always reports core events
[ 24869.191] (**) evdev: Logitech Logitech Illuminated Keyboard: Device: "/dev/input/event5"
[ 24869.191] (--) evdev: Logitech Logitech Illuminated Keyboard: Vendor 0x46d Product 0xc318
[ 24869.191] (--) evdev: Logitech Logitech Illuminated Keyboard: Found 1 mouse buttons
[ 24869.191] (--) evdev: Logitech Logitech Illuminated Keyboard: Found scroll wheel(s)
[ 24869.191] (--) evdev: Logitech Logitech Illuminated Keyboard: Found relative axes
[ 24869.191] (II) evdev: Logitech Logitech Illuminated Keyboard: Forcing relative x/y axes to exist.
[ 24869.192] (--) evdev: Logitech Logitech Illuminated Keyboard: Found absolute axes
[ 24869.192] (II) evdev: Logitech Logitech Illuminated Keyboard: Forcing absolute x/y axes to exist.
[ 24869.192] (--) evdev: Logitech Logitech Illuminated Keyboard: Found keys
[ 24869.192] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as mouse
[ 24869.192] (II) evdev: Logitech Logitech Illuminated Keyboard: Configuring as keyboard
[ 24869.192] (II) evdev: Logitech Logitech Illuminated Keyboard: Adding scrollwheel support
[ 24869.192] (**) evdev: Logitech Logitech Illuminated Keyboard: YAxisMapping: buttons 4 and 5
[ 24869.192] (**) evdev: Logitech Logitech Illuminated Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 24869.192] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input5/event5"
[ 24869.192] (II) XINPUT: Adding extended input device "Logitech Logitech Illuminated Keyboard" (type: KEYBOARD, id 11)
[ 24869.192] (**) Option "xkb_rules" "evdev"
[ 24869.192] (**) Option "xkb_model" "pc105"
[ 24869.192] (**) Option "xkb_layout" "gb"
[ 24869.192] (II) evdev: Logitech Logitech Illuminated Keyboard: initialized for relative axes.
[ 24869.192] (WW) evdev: Logitech Logitech Illuminated Keyboard: ignoring absolute axes.
[ 24869.192] (**) Logitech Logitech Illuminated Keyboard: (accel) keeping acceleration scheme 1
[ 24869.192] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration profile 0
[ 24869.192] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration factor: 2.000
[ 24869.192] (**) Logitech Logitech Illuminated Keyboard: (accel) acceleration threshold: 4
[ 24869.192] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event6)
[ 24869.192] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 24869.192] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[ 24869.192] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 24869.192] (**) Eee PC WMI hotkeys: always reports core events
[ 24869.192] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event6"
[ 24869.192] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[ 24869.192] (--) evdev: Eee PC WMI hotkeys: Found keys
[ 24869.192] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[ 24869.192] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input6/event6"
[ 24869.192] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 12)
[ 24869.192] (**) Option "xkb_rules" "evdev"
[ 24869.192] (**) Option "xkb_model" "pc105"
[ 24869.192] (**) Option "xkb_layout" "gb"
[ 24869.383] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[ 24869.383] (II) NVIDIA(GPU-0):     Vision stereo.
[ 24869.383] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 24869.383] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[ 24869.383] (**) NVIDIA(0):     been enabled on all display devices.)
[ 24869.432] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[ 24869.432] (II) NVIDIA(GPU-0):     Vision stereo.
[ 24869.432] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 24869.432] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[ 24869.432] (**) NVIDIA(0):     been enabled on all display devices.)
[ 24882.507] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[ 24882.507] (II) NVIDIA(GPU-0):     Vision stereo.
[ 24882.507] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 24882.507] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[ 24882.507] (**) NVIDIA(0):     been enabled on all display devices.)
[ 24882.624] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[ 24882.624] (II) NVIDIA(GPU-0):     Vision stereo.
[ 24882.624] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 24882.624] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[ 24882.624] (**) NVIDIA(0):     been enabled on all display devices.)
[ 24882.670] (II) NVIDIA(GPU-0): Display (DELL U2412M (DFP-0)) does not support NVIDIA 3D
[ 24882.670] (II) NVIDIA(GPU-0):     Vision stereo.
[ 24882.670] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 24882.670] (**) NVIDIA(0):     device DELL U2412M (DFP-0) (Using EDID frequencies has
[ 24882.670] (**) NVIDIA(0):     been enabled on all display devices.)

```I tried to start gnome_classic, but there is just a hanging black screen (with cursor). So I jumped to T1 restarted the service, GNOME3 works and so does gnome_classic_no_effects. I also re-installed the fallback_session package and the same thing is happening.

The only thing that has changed is that I upgraded nVidia drivers to 304.64 on the 12th.

Thanks.

---

