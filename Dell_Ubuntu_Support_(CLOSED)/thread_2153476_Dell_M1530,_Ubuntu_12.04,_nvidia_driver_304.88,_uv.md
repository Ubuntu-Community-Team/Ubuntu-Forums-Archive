---
title: "Dell M1530, Ubuntu 12.04, nvidia driver 304.88, uvesafb - unable to change resolution"
date: 2013-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kkkkdddd on 2013-06-11
I have Dell M1530 with GeForce 8600M GT.
I have installed Ubuntu 12.04 and binary driver from nvidia-current-updates (version 304.88).
I also use uvesafb framebuffer.

My native screen resolution is 1440x900 and it works perfectly fine.
The problem is, I can not use other resolutions (i.e. 640x480).
First of all, nvidia-settings didn't allow my to change resolution to anything else than 1440x900.
So I added: "Option	"ModeValidation" "AllowNonEdidModes"
to xorg.conf

Now I can change resolution with nvidia-settings or "xrandr --output LVDS-0 --mode 640x480 --rate 60" but when I do that, my screen becomes to be completely corrupted (it gets white with vertical lines, after a while it becomes purple).
When I change to different resolution, for example 1024x768, it is also corrupted (with 1024x768 I see 4 overlapping desktops).
 

$ cat /etc/X11/xorg.conf

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option	"ModeValidation" "AllowNonEdidModes"
EndSection

```

$ cat /etc/modprobe.d/uvesafb.conf
```
options uvesafb mode_option=1440x900-24 scroll=ywrap

```

$ cat /sys/devices/virtual/graphics/fbcon/subsystem/fb0/modes
```
U:1440x900p-59
V:1024x768p-85
V:1024x768p-75
V:1024x768p-70
V:1024x768p-60
V:1024x768i-43
V:800x600p-85
V:800x600p-75
V:800x600p-72
V:800x600p-60
V:800x600p-56
V:640x480p-85
V:640x480p-75
V:640x480p-72
V:640x480p-60
V:640x400p-85
U:1440x900p-59
U:768x480p-60
U:1280x800p-60
U:320x240p-60
U:320x400p-59
U:320x200p-59
U:1024x768p-60
U:800x600p-59
U:640x480p-60
U:640x400p-59
```

cat /sys/bus/platform/drivers/uvesafb/uvesafb.0/vbe_modes
```

640x400-8, 0x0100
640x480-8, 0x0101
800x600-8, 0x0103
1024x768-8, 0x0105
320x200-16, 0x010e
320x200-32, 0x010f
640x480-16, 0x0111
640x480-32, 0x0112
800x600-16, 0x0114
800x600-32, 0x0115
1024x768-16, 0x0117
1024x768-32, 0x0118
320x200-8, 0x0130
320x400-8, 0x0131
320x400-16, 0x0132
320x400-32, 0x0133
320x240-8, 0x0134
320x240-16, 0x0135
320x240-32, 0x0136
640x400-16, 0x013d
640x400-32, 0x013e
1280x800-8, 0x0160
1280x800-32, 0x0161
768x480-8, 0x0162
1440x900-8, 0x0164
1440x900-32, 0x0165
```

$ cat /var/log/Xorg.0.log
```
[    37.822] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[    37.822] X Protocol Version 11, Revision 0
[    37.822] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    37.822] Current Operating System: Linux krzysztof 3.2.0-45-generic #70-Ubuntu SMP Wed May 29 20:11:31 UTC 2013 i686
[    37.822] Kernel command line: root=UUID=d24f1fb6-98ff-4e5c-9dcf-d523acf3c5e3 ro quiet splash 
[    37.822] Build Date: 11 April 2013  01:04:30PM
[    37.822] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[    37.822] Current version of pixman: 0.24.4
[    37.822] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    37.822] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    37.822] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 11 09:03:21 2013
[    37.822] (==) Using config file: "/etc/X11/xorg.conf"
[    37.822] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    37.823] (==) No Layout section.  Using the first Screen section.
[    37.823] (**) |-->Screen "Default Screen" (0)
[    37.823] (**) |   |-->Monitor "Configured Monitor"
[    37.823] (**) |   |-->Device "Configured Video Device"
[    37.823] (==) Automatically adding devices
[    37.823] (==) Automatically enabling devices
[    37.823] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    37.823] 	Entry deleted from font path.
[    37.823] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    37.823] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    37.823] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    37.823] (II) Loader magic: 0x6575a0
[    37.823] (II) Module ABI versions:
[    37.823] 	X.Org ANSI C Emulation: 0.4
[    37.823] 	X.Org Video Driver: 11.0
[    37.823] 	X.Org XInput driver : 16.0
[    37.823] 	X.Org Server Extension : 6.0
[    37.824] (--) PCI:*(0:1:0:0) 10de:0407:1028:022e rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
[    37.824] (II) Open ACPI successful (/var/run/acpid.socket)
[    37.824] (II) "extmod" will be loaded by default.
[    37.824] (II) "dbe" will be loaded by default.
[    37.824] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    37.824] (II) "record" will be loaded by default.
[    37.824] (II) "dri" will be loaded by default.
[    37.824] (II) "dri2" will be loaded by default.
[    37.824] (II) LoadModule: "glx"
[    37.825] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    37.854] (II) Module glx: vendor="NVIDIA Corporation"
[    37.854] 	compiled for 4.0.2, module version = 1.0.0
[    37.854] 	Module class: X.Org Server Extension
[    37.854] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:51:59 PDT 2013
[    37.854] (II) Loading extension GLX
[    37.854] (II) LoadModule: "extmod"
[    37.868] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    37.868] (II) Module extmod: vendor="X.Org Foundation"
[    37.868] 	compiled for 1.11.3, module version = 1.0.0
[    37.868] 	Module class: X.Org Server Extension
[    37.868] 	ABI class: X.Org Server Extension, version 6.0
[    37.868] (II) Loading extension MIT-SCREEN-SAVER
[    37.868] (II) Loading extension XFree86-VidModeExtension
[    37.868] (II) Loading extension XFree86-DGA
[    37.868] (II) Loading extension DPMS
[    37.868] (II) Loading extension XVideo
[    37.869] (II) Loading extension XVideo-MotionCompensation
[    37.869] (II) Loading extension X-Resource
[    37.869] (II) LoadModule: "dbe"
[    37.869] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    37.869] (II) Module dbe: vendor="X.Org Foundation"
[    37.869] 	compiled for 1.11.3, module version = 1.0.0
[    37.869] 	Module class: X.Org Server Extension
[    37.869] 	ABI class: X.Org Server Extension, version 6.0
[    37.869] (II) Loading extension DOUBLE-BUFFER
[    37.869] (II) LoadModule: "record"
[    37.869] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    37.869] (II) Module record: vendor="X.Org Foundation"
[    37.869] 	compiled for 1.11.3, module version = 1.13.0
[    37.869] 	Module class: X.Org Server Extension
[    37.869] 	ABI class: X.Org Server Extension, version 6.0
[    37.869] (II) Loading extension RECORD
[    37.869] (II) LoadModule: "dri"
[    37.870] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    37.870] (II) Module dri: vendor="X.Org Foundation"
[    37.870] 	compiled for 1.11.3, module version = 1.0.0
[    37.870] 	ABI class: X.Org Server Extension, version 6.0
[    37.870] (II) Loading extension XFree86-DRI
[    37.870] (II) LoadModule: "dri2"
[    37.870] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    37.870] (II) Module dri2: vendor="X.Org Foundation"
[    37.870] 	compiled for 1.11.3, module version = 1.2.0
[    37.870] 	ABI class: X.Org Server Extension, version 6.0
[    37.870] (II) Loading extension DRI2
[    37.870] (II) LoadModule: "nvidia"
[    37.870] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    37.871] (II) Module nvidia: vendor="NVIDIA Corporation"
[    37.871] 	compiled for 4.0.2, module version = 1.0.0
[    37.871] 	Module class: X.Org Video Driver
[    37.871] (II) NVIDIA dlloader X Driver  304.88  Wed Mar 27 14:32:42 PDT 2013
[    37.871] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    37.871] (++) using VT number 7

[    37.871] (II) Loading sub module "fb"
[    37.871] (II) LoadModule: "fb"
[    37.872] (II) Loading /usr/lib/xorg/modules/libfb.so
[    37.872] (II) Module fb: vendor="X.Org Foundation"
[    37.872] 	compiled for 1.11.3, module version = 1.0.0
[    37.872] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    37.872] (II) Loading sub module "wfb"
[    37.872] (II) LoadModule: "wfb"
[    37.872] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    37.872] (II) Module wfb: vendor="X.Org Foundation"
[    37.872] 	compiled for 1.11.3, module version = 1.0.0
[    37.872] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    37.872] (II) Loading sub module "ramdac"
[    37.872] (II) LoadModule: "ramdac"
[    37.872] (II) Module "ramdac" already built-in
[    37.872] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    37.873] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    37.873] (II) Loading /usr/lib/xorg/modules/libfb.so
[    37.873] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    37.873] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    37.873] (==) NVIDIA(0): RGB weight 888
[    37.873] (==) NVIDIA(0): Default visual is TrueColor
[    37.873] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    37.873] (**) NVIDIA(0): Option "NoLogo" "True"
[    37.873] (**) NVIDIA(0): Option "ModeValidation" "AllowNonEdidModes"
[    37.873] (**) NVIDIA(0): Enabling 2D acceleration
[    38.991] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[    38.991] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    38.999] (II) NVIDIA(0): NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)
[    38.999] (--) NVIDIA(0): Memory: 524288 kBytes
[    38.999] (--) NVIDIA(0): VideoBIOS: 60.84.5e.00.08
[    38.999] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    38.999] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    39.005] (--) NVIDIA(0): Valid display device(s) on GeForce 8600M GT at PCI:1:0:0
[    39.005] (--) NVIDIA(0):     CRT-0
[    39.005] (--) NVIDIA(0):     TV-0
[    39.005] (--) NVIDIA(0):     AU Optronics Corporation (DFP-0) (connected)
[    39.005] (--) NVIDIA(0):     DFP-1
[    39.005] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    39.005] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    39.005] (--) NVIDIA(0): TV encoder: Unknown
[    39.005] (--) NVIDIA(0): AU Optronics Corporation (DFP-0): 330.0 MHz maximum pixel clock
[    39.005] (--) NVIDIA(0): AU Optronics Corporation (DFP-0): Internal Dual Link LVDS
[    39.005] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    39.005] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    39.005] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    39.005] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[    39.005] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    39.005] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[    39.005] (II) NVIDIA(0):     (DFP-0):
[    39.005] (II) NVIDIA(0):     AllowNonEdidModes
[    39.018] (==) NVIDIA(0): 
[    39.018] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    39.018] (==) NVIDIA(0):     will be used as the requested mode.
[    39.018] (==) NVIDIA(0): 
[    39.018] (II) NVIDIA(0): Validated MetaModes:
[    39.018] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[    39.018] (II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
[    40.040] (--) NVIDIA(0): DPI set to (110, 108); computed from "UseEdidDpi" X config
[    40.040] (--) NVIDIA(0):     option
[    40.040] (--) Depth 24 pixmap format is 32 bpp
[    40.040] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    40.058] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[    40.340] (II) Loading extension NV-GLX
[    40.381] (==) NVIDIA(0): Disabling shared memory pixmaps
[    40.381] (==) NVIDIA(0): Backing store disabled
[    40.381] (==) NVIDIA(0): Silken mouse enabled
[    40.381] (==) NVIDIA(0): DPMS enabled
[    40.381] (II) Loading extension NV-CONTROL
[    40.382] (II) Loading extension XINERAMA
[    40.382] (II) Loading sub module "dri2"
[    40.382] (II) LoadModule: "dri2"
[    40.382] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    40.382] (II) Module dri2: vendor="X.Org Foundation"
[    40.382] 	compiled for 1.11.3, module version = 1.2.0
[    40.382] 	ABI class: X.Org Server Extension, version 6.0
[    40.382] (II) NVIDIA(0): [DRI2] Setup complete
[    40.382] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    40.382] (--) RandR disabled
[    40.382] (II) Initializing built-in extension Generic Event Extension
[    40.382] (II) Initializing built-in extension SHAPE
[    40.382] (II) Initializing built-in extension MIT-SHM
[    40.382] (II) Initializing built-in extension XInputExtension
[    40.382] (II) Initializing built-in extension XTEST
[    40.382] (II) Initializing built-in extension BIG-REQUESTS
[    40.382] (II) Initializing built-in extension SYNC
[    40.382] (II) Initializing built-in extension XKEYBOARD
[    40.382] (II) Initializing built-in extension XC-MISC
[    40.382] (II) Initializing built-in extension SECURITY
[    40.382] (II) Initializing built-in extension XINERAMA
[    40.382] (II) Initializing built-in extension XFIXES
[    40.382] (II) Initializing built-in extension RENDER
[    40.382] (II) Initializing built-in extension RANDR
[    40.382] (II) Initializing built-in extension COMPOSITE
[    40.382] (II) Initializing built-in extension DAMAGE
[    40.382] (II) Initializing extension GLX
[    40.415] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    40.418] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    40.418] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    40.418] (II) LoadModule: "evdev"
[    40.418] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.418] (II) Module evdev: vendor="X.Org Foundation"
[    40.418] 	compiled for 1.11.3, module version = 2.7.0
[    40.418] 	Module class: X.Org XInput Driver
[    40.418] 	ABI class: X.Org XInput driver, version 16.0
[    40.419] (II) Using input driver 'evdev' for 'Video Bus'
[    40.419] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.419] (**) Video Bus: always reports core events
[    40.419] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    40.419] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    40.419] (--) evdev: Video Bus: Found keys
[    40.419] (II) evdev: Video Bus: Configuring as keyboard
[    40.419] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:2d/LNXVIDEO:00/input/input4/event4"
[    40.419] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    40.419] (**) Option "xkb_rules" "evdev"
[    40.419] (**) Option "xkb_model" "pc105"
[    40.419] (**) Option "xkb_layout" "pl"
[    40.421] (II) XKB: reuse xkmfile /var/lib/xkb/server-61818C6B46DD4F01AE1F641F27B555591612208F.xkm
[    40.421] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    40.422] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    40.422] (II) Using input driver 'evdev' for 'Power Button'
[    40.422] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.422] (**) Power Button: always reports core events
[    40.422] (**) evdev: Power Button: Device: "/dev/input/event1"
[    40.422] (--) evdev: Power Button: Vendor 0 Product 0x1
[    40.422] (--) evdev: Power Button: Found keys
[    40.422] (II) evdev: Power Button: Configuring as keyboard
[    40.422] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    40.422] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    40.422] (**) Option "xkb_rules" "evdev"
[    40.422] (**) Option "xkb_model" "pc105"
[    40.422] (**) Option "xkb_layout" "pl"
[    40.422] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    40.422] (II) No input driver specified, ignoring this device.
[    40.422] (II) This device may have been added with another device file.
[    40.422] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    40.422] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    40.422] (II) Using input driver 'evdev' for 'Sleep Button'
[    40.422] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.422] (**) Sleep Button: always reports core events
[    40.423] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    40.423] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    40.423] (--) evdev: Sleep Button: Found keys
[    40.423] (II) evdev: Sleep Button: Configuring as keyboard
[    40.423] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    40.423] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    40.423] (**) Option "xkb_rules" "evdev"
[    40.423] (**) Option "xkb_model" "pc105"
[    40.423] (**) Option "xkb_layout" "pl"
[    40.423] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    40.423] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    40.423] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    40.423] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.423] (**) Logitech USB Receiver: always reports core events
[    40.423] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event5"
[    40.423] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[    40.423] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    40.423] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    40.423] (--) evdev: Logitech USB Receiver: Found relative axes
[    40.423] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    40.423] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    40.423] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    40.423] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    40.423] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    40.423] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.0/input/input5/event5"
[    40.423] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE, id 9)
[    40.424] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    40.424] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    40.424] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    40.424] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    40.424] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    40.424] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    40.424] (II) No input driver specified, ignoring this device.
[    40.424] (II) This device may have been added with another device file.
[    40.424] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    40.424] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    40.424] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    40.424] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.424] (**) Logitech USB Receiver: always reports core events
[    40.424] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event6"
[    40.424] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc52f
[    40.424] (--) evdev: Logitech USB Receiver: Found 1 mouse buttons
[    40.424] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    40.424] (--) evdev: Logitech USB Receiver: Found relative axes
[    40.424] (II) evdev: Logitech USB Receiver: Forcing relative x/y axes to exist.
[    40.424] (--) evdev: Logitech USB Receiver: Found absolute axes
[    40.424] (II) evdev: Logitech USB Receiver: Forcing absolute x/y axes to exist.
[    40.424] (--) evdev: Logitech USB Receiver: Found keys
[    40.425] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    40.425] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    40.425] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    40.425] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    40.425] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    40.425] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.1/input/input6/event6"
[    40.425] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[    40.425] (**) Option "xkb_rules" "evdev"
[    40.425] (**) Option "xkb_model" "pc105"
[    40.425] (**) Option "xkb_layout" "pl"
[    40.425] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    40.425] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
[    40.425] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    40.425] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    40.425] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    40.425] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    40.425] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    40.425] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    40.425] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    40.425] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.425] (**) AT Translated Set 2 keyboard: always reports core events
[    40.425] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    40.425] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    40.425] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    40.425] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    40.425] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    40.426] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    40.426] (**) Option "xkb_rules" "evdev"
[    40.426] (**) Option "xkb_model" "pc105"
[    40.426] (**) Option "xkb_layout" "pl"
[    40.426] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/event8)
[    40.426] (**) PS/2 Mouse: Applying InputClass "evdev pointer catchall"
[    40.426] (II) Using input driver 'evdev' for 'PS/2 Mouse'
[    40.426] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.426] (**) PS/2 Mouse: always reports core events
[    40.426] (**) evdev: PS/2 Mouse: Device: "/dev/input/event8"
[    40.426] (--) evdev: PS/2 Mouse: Vendor 0x2 Product 0x8
[    40.426] (--) evdev: PS/2 Mouse: Found 3 mouse buttons
[    40.426] (--) evdev: PS/2 Mouse: Found relative axes
[    40.426] (--) evdev: PS/2 Mouse: Found x and y relative axes
[    40.426] (II) evdev: PS/2 Mouse: Configuring as mouse
[    40.426] (**) evdev: PS/2 Mouse: YAxisMapping: buttons 4 and 5
[    40.426] (**) evdev: PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    40.426] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    40.426] (II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE, id 12)
[    40.426] (II) evdev: PS/2 Mouse: initialized for relative axes.
[    40.426] (**) PS/2 Mouse: (accel) keeping acceleration scheme 1
[    40.426] (**) PS/2 Mouse: (accel) acceleration profile 0
[    40.426] (**) PS/2 Mouse: (accel) acceleration factor: 2.000
[    40.426] (**) PS/2 Mouse: (accel) acceleration threshold: 4
[    40.427] (II) config/udev: Adding input device PS/2 Mouse (/dev/input/mouse1)
[    40.427] (II) No input driver specified, ignoring this device.
[    40.427] (II) This device may have been added with another device file.
[    40.427] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/event9)
[    40.427] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "evdev touchpad catchall"
[    40.427] (**) AlpsPS/2 ALPS GlidePoint: Applying InputClass "touchpad catchall"
[    40.427] (II) LoadModule: "synaptics"
[    40.427] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    40.427] (II) Module synaptics: vendor="X.Org Foundation"
[    40.427] 	compiled for 1.11.3, module version = 1.6.2
[    40.427] 	Module class: X.Org XInput Driver
[    40.427] 	ABI class: X.Org XInput driver, version 16.0
[    40.427] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS GlidePoint'
[    40.427] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    40.427] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    40.427] (**) Option "Device" "/dev/input/event9"
[    40.432] (--) synaptics: AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
[    40.432] (--) synaptics: AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
[    40.432] (--) synaptics: AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
[    40.432] (II) synaptics: AlpsPS/2 ALPS GlidePoint: device does not report finger width.
[    40.432] (--) synaptics: AlpsPS/2 ALPS GlidePoint: buttons: left right middle
[    40.432] (--) synaptics: AlpsPS/2 ALPS GlidePoint: Vendor 0x2 Product 0x8
[    40.432] (--) synaptics: AlpsPS/2 ALPS GlidePoint: invalid finger width range.  defaulting to 0 - 15
[    40.432] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    40.432] (**) AlpsPS/2 ALPS GlidePoint: always reports core events
[    40.436] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    40.436] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD, id 13)
[    40.436] (**) synaptics: AlpsPS/2 ALPS GlidePoint: (accel) MinSpeed is now constant deceleration 2.5
[    40.436] (**) synaptics: AlpsPS/2 ALPS GlidePoint: MaxSpeed is now 1.75
[    40.436] (**) synaptics: AlpsPS/2 ALPS GlidePoint: AccelFactor is now 0.156
[    40.436] (**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    40.436] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration profile 1
[    40.436] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    40.436] (**) AlpsPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    40.436] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[    40.436] (II) config/udev: Adding input device AlpsPS/2 ALPS GlidePoint (/dev/input/mouse2)
[    40.436] (**) AlpsPS/2 ALPS GlidePoint: Ignoring device from InputClass "touchpad ignore duplicates"
[    40.438] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event7)
[    40.438] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    40.438] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    40.438] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    40.438] (**) Dell WMI hotkeys: always reports core events
[    40.438] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event7"
[    40.438] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    40.438] (--) evdev: Dell WMI hotkeys: Found keys
[    40.438] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    40.438] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    40.438] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    40.438] (**) Option "xkb_rules" "evdev"
[    40.438] (**) Option "xkb_model" "pc105"
[    40.438] (**) Option "xkb_layout" "pl"
[    46.457] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[    46.457] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    46.457] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    46.457] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[    46.457] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    46.457] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[    46.457] (II) NVIDIA(0):     (DFP-0):
[    46.457] (II) NVIDIA(0):     AllowNonEdidModes
[    47.405] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[    47.533] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    47.533] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    47.533] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[    47.533] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    47.533] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[    47.533] (II) NVIDIA(0):     (DFP-0):
[    47.533] (II) NVIDIA(0):     AllowNonEdidModes
[    47.940] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[    47.940] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    47.940] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    47.940] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[    47.940] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    47.940] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[    47.940] (II) NVIDIA(0):     (DFP-0):
[    47.940] (II) NVIDIA(0):     AllowNonEdidModes
[    66.152] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    68.611] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[    68.611] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[    68.685] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    68.685] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[    68.685] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    68.685] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[    68.685] (II) NVIDIA(0):     (DFP-0):
[    68.685] (II) NVIDIA(0):     AllowNonEdidModes
[   666.357] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[   666.357] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[   666.357] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[   666.357] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[   666.357] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[   666.357] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[   666.357] (II) NVIDIA(0):     (DFP-0):
[   666.357] (II) NVIDIA(0):     AllowNonEdidModes
[  2461.889] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  2461.889] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  2461.889] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2461.889] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  2461.889] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  2461.889] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  2461.889] (II) NVIDIA(0):     (DFP-0):
[  2461.889] (II) NVIDIA(0):     AllowNonEdidModes
[  2467.385] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  2467.385] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  2467.385] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2467.385] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  2467.385] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  2467.385] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  2467.385] (II) NVIDIA(0):     (DFP-0):
[  2467.385] (II) NVIDIA(0):     AllowNonEdidModes
[  2500.853] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  2500.853] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  2500.853] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2500.853] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  2500.853] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  2500.853] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  2500.853] (II) NVIDIA(0):     (DFP-0):
[  2500.854] (II) NVIDIA(0):     AllowNonEdidModes
[  2502.229] (II) NVIDIA(0): Setting mode "NULL"
[  2502.382] (II) NVIDIA(0): Setting mode "LVDS-0: 1024x768 @1024x768 +0+0"
[  2521.650] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  2521.650] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  2521.650] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2521.650] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  2521.650] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  2521.650] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  2521.650] (II) NVIDIA(0):     (DFP-0):
[  2521.650] (II) NVIDIA(0):     AllowNonEdidModes
[  2522.862] (II) NVIDIA(0): Setting mode "NULL"
[  2522.979] (II) NVIDIA(0): Setting mode "LVDS-0: 640x480 @640x480 +0+0"
[  2540.346] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  2540.346] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  2540.346] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2540.346] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  2540.346] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  2540.346] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  2540.346] (II) NVIDIA(0):     (DFP-0):
[  2540.346] (II) NVIDIA(0):     AllowNonEdidModes
[  2541.593] (II) NVIDIA(0): Setting mode "LVDS-0: 1024x768 @1024x768 +0+0"
[  2557.273] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  2557.273] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  2557.274] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  2557.274] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  2557.274] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  2557.274] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  2557.274] (II) NVIDIA(0):     (DFP-0):
[  2557.274] (II) NVIDIA(0):     AllowNonEdidModes
[  2558.578] (II) NVIDIA(0): Setting mode "LVDS-0: nvidia-auto-select @1440x900 +0+0"
[  5050.856] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  5050.856] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  5050.856] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  5050.856] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  5050.856] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  5050.856] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  5050.856] (II) NVIDIA(0):     (DFP-0):
[  5050.856] (II) NVIDIA(0):     AllowNonEdidModes
[  6032.954] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  6032.954] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  6032.954] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6032.954] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  6032.954] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  6032.954] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  6032.954] (II) NVIDIA(0):     (DFP-0):
[  6032.954] (II) NVIDIA(0):     AllowNonEdidModes
[  6043.017] (II) Open ACPI successful (/var/run/acpid.socket)
[  6043.287] (II) NVIDIA(0): Setting mode "LVDS-0: nvidia-auto-select @1440x900 +0+0"
[  6044.659] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
[  6044.666] (II) config/udev: Adding input device Laptop Integrated Webcam (/dev/input/event10)
[  6044.666] (**) Laptop Integrated Webcam: Applying InputClass "evdev keyboard catchall"
[  6044.666] (II) Using input driver 'evdev' for 'Laptop Integrated Webcam'
[  6044.666] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  6044.666] (**) Laptop Integrated Webcam: always reports core events
[  6044.666] (**) evdev: Laptop Integrated Webcam: Device: "/dev/input/event10"
[  6044.666] (--) evdev: Laptop Integrated Webcam: Vendor 0x5a9 Product 0x2640
[  6044.666] (--) evdev: Laptop Integrated Webcam: Found keys
[  6044.666] (II) evdev: Laptop Integrated Webcam: Configuring as keyboard
[  6044.666] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0/input/input10/event10"
[  6044.666] (II) XINPUT: Adding extended input device "Laptop Integrated Webcam" (type: KEYBOARD, id 15)
[  6044.666] (**) Option "xkb_rules" "evdev"
[  6044.666] (**) Option "xkb_model" "pc105"
[  6044.666] (**) Option "xkb_layout" "pl"
[  6045.385] (II) NVIDIA(GPU-0): Display (AU Optronics Corporation (DFP-0)) does not support
[  6045.386] (II) NVIDIA(GPU-0):     NVIDIA 3D Vision stereo.
[  6045.386] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[  6045.386] (**) NVIDIA(0):     device AU Optronics Corporation (DFP-0) (Using EDID
[  6045.386] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[  6045.386] (II) NVIDIA(0): Mode Validation Overrides for AU Optronics Corporation
[  6045.386] (II) NVIDIA(0):     (DFP-0):
[  6045.386] (II) NVIDIA(0):     AllowNonEdidModes
[  6068.984] (II) Open ACPI successful (/var/run/acpid.socket)
[  6069.288] (II) NVIDIA(0): Setting mode "LVDS-0: nvidia-auto-select @1440x900 +0+0"
[  6070.667] (--) synaptics: AlpsPS/2 ALPS GlidePoint: touchpad found
```

Could you help me?
In Ubuntu 10.04 I could change resolution without a problem.
The same problem is with both Unity and KDE.

---

### Post by kkkkdddd on 2013-06-12
I have today tried the following, but to no avail:
-use KDE instead of Unity
-disable framebuffor by specifying vga=0x365 boot option

---

