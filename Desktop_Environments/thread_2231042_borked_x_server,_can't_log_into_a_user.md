---
title: "borked x server, can't log into a user"
date: 2014-06-23
forum: Desktop Environments
---

### Post by Drone4four on 2014-06-23
I can't login into a desktop environment from ldm.  After I select my username and enter my password, the screen goes black for a few seconds and then ldm reappears.  This happens no matter which of the 8 installed window managers I select.  

It's worth noting that earlier today I tried starting another xsession with startx -- :1 .  It failed.  I am not sure if this is related to the issue I am now troubleshooting.

Here is my my /var/log/Xorg.0.log:

```
[    27.138] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    27.139] X Protocol Version 11, Revision 0
[    27.139] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    27.139] Current Operating System: Linux gnosis 3.13.0-27-generic #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 x86_64
[    27.139] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=423b52fc-fb8b-4c71-87dc-3b538f3bb801 ro quiet splash
[    27.139] Build Date: 16 April 2014  01:36:29PM
[    27.139] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    27.139] Current version of pixman: 0.30.2
[    27.139] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    27.139] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    27.139] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 22 23:41:06 2014
[    27.139] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    27.139] (==) No Layout section.  Using the first Screen section.
[    27.139] (==) No screen section available. Using defaults.
[    27.139] (**) |-->Screen "Default Screen Section" (0)
[    27.139] (**) |   |-->Monitor "<default monitor>"
[    27.139] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    27.139] (==) Automatically adding devices
[    27.139] (==) Automatically enabling devices
[    27.139] (==) Automatically adding GPU devices
[    27.139] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    27.139] 	Entry deleted from font path.
[    27.139] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    27.139] 	Entry deleted from font path.
[    27.139] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    27.139] 	Entry deleted from font path.
[    27.139] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    27.139] 	Entry deleted from font path.
[    27.139] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    27.139] 	Entry deleted from font path.
[    27.139] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    27.139] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    27.139] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    27.139] (II) Loader magic: 0x7f17b8e58d60
[    27.139] (II) Module ABI versions:
[    27.140] 	X.Org ANSI C Emulation: 0.4
[    27.140] 	X.Org Video Driver: 15.0
[    27.140] 	X.Org XInput driver : 20.0
[    27.140] 	X.Org Server Extension : 8.0
[    27.140] (II) xfree86: Adding drm device (/dev/dri/card0)
[    27.141] (--) PCI:*(0:1:0:0) 10de:1200:3842:1568 rev 161, Mem @ 0xda000000/33554432, 0xc0000000/134217728, 0xcc000000/67108864, I/O @ 0x0000bf00/128, BIOS @ 0x????????/524288
[    27.141] Initializing built-in extension Generic Event Extension
[    27.141] Initializing built-in extension SHAPE
[    27.141] Initializing built-in extension MIT-SHM
[    27.141] Initializing built-in extension XInputExtension
[    27.141] Initializing built-in extension XTEST
[    27.141] Initializing built-in extension BIG-REQUESTS
[    27.141] Initializing built-in extension SYNC
[    27.141] Initializing built-in extension XKEYBOARD
[    27.141] Initializing built-in extension XC-MISC
[    27.141] Initializing built-in extension SECURITY
[    27.141] Initializing built-in extension XINERAMA
[    27.141] Initializing built-in extension XFIXES
[    27.141] Initializing built-in extension RENDER
[    27.141] Initializing built-in extension RANDR
[    27.141] Initializing built-in extension COMPOSITE
[    27.141] Initializing built-in extension DAMAGE
[    27.141] Initializing built-in extension MIT-SCREEN-SAVER
[    27.141] Initializing built-in extension DOUBLE-BUFFER
[    27.141] Initializing built-in extension RECORD
[    27.141] Initializing built-in extension DPMS
[    27.141] Initializing built-in extension Present
[    27.141] Initializing built-in extension DRI3
[    27.141] Initializing built-in extension X-Resource
[    27.141] Initializing built-in extension XVideo
[    27.141] Initializing built-in extension XVideo-MotionCompensation
[    27.141] Initializing built-in extension SELinux
[    27.141] Initializing built-in extension XFree86-VidModeExtension
[    27.141] Initializing built-in extension XFree86-DGA
[    27.141] Initializing built-in extension XFree86-DRI
[    27.141] Initializing built-in extension DRI2
[    27.141] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    27.141] (II) "glx" will be loaded by default.
[    27.141] (WW) "xmir" is not to be loaded by default. Skipping.
[    27.141] (II) LoadModule: "glx"
[    27.142] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    27.156] (II) Module glx: vendor="NVIDIA Corporation"
[    27.156] 	compiled for 4.0.2, module version = 1.0.0
[    27.156] 	Module class: X.Org Server Extension
[    27.156] (II) NVIDIA GLX Module  331.38  Wed Jan  8 19:10:17 PST 2014
[    27.156] Loading extension GLX
[    27.156] (==) Matched nvidia as autoconfigured driver 0
[    27.156] (==) Matched nouveau as autoconfigured driver 1
[    27.156] (==) Matched nvidia as autoconfigured driver 2
[    27.156] (==) Matched nouveau as autoconfigured driver 3
[    27.156] (==) Matched modesetting as autoconfigured driver 4
[    27.156] (==) Matched fbdev as autoconfigured driver 5
[    27.156] (==) Matched vesa as autoconfigured driver 6
[    27.156] (==) Assigned the driver to the xf86ConfigLayout
[    27.156] (II) LoadModule: "nvidia"
[    27.156] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    27.157] (II) Module nvidia: vendor="NVIDIA Corporation"
[    27.157] 	compiled for 4.0.2, module version = 1.0.0
[    27.157] 	Module class: X.Org Video Driver
[    27.157] (II) LoadModule: "nouveau"
[    27.157] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    27.157] (II) Module nouveau: vendor="X.Org Foundation"
[    27.157] 	compiled for 1.15.0, module version = 1.0.10
[    27.157] 	Module class: X.Org Video Driver
[    27.157] 	ABI class: X.Org Video Driver, version 15.0
[    27.157] (II) LoadModule: "modesetting"
[    27.157] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    27.157] (II) Module modesetting: vendor="X.Org Foundation"
[    27.158] 	compiled for 1.15.0, module version = 0.8.1
[    27.158] 	Module class: X.Org Video Driver
[    27.158] 	ABI class: X.Org Video Driver, version 15.0
[    27.158] (II) LoadModule: "fbdev"
[    27.158] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    27.158] (II) Module fbdev: vendor="X.Org Foundation"
[    27.158] 	compiled for 1.15.0, module version = 0.4.4
[    27.158] 	Module class: X.Org Video Driver
[    27.158] 	ABI class: X.Org Video Driver, version 15.0
[    27.158] (II) LoadModule: "vesa"
[    27.158] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    27.158] (II) Module vesa: vendor="X.Org Foundation"
[    27.158] 	compiled for 1.15.0, module version = 2.3.3
[    27.158] 	Module class: X.Org Video Driver
[    27.158] 	ABI class: X.Org Video Driver, version 15.0
[    27.158] (II) NVIDIA dlloader X Driver  331.38  Wed Jan  8 18:51:00 PST 2014
[    27.158] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    27.158] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    27.158] (II) NOUVEAU driver for NVIDIA chipset families :
[    27.158] 	RIVA TNT        (NV04)
[    27.158] 	RIVA TNT2       (NV05)
[    27.158] 	GeForce 256     (NV10)
[    27.158] 	GeForce 2       (NV11, NV15)
[    27.158] 	GeForce 4MX     (NV17, NV18)
[    27.158] 	GeForce 3       (NV20)
[    27.158] 	GeForce 4Ti     (NV25, NV28)
[    27.158] 	GeForce FX      (NV3x)
[    27.158] 	GeForce 6       (NV4x)
[    27.158] 	GeForce 7       (G7x)
[    27.158] 	GeForce 8       (G8x)
[    27.159] 	GeForce GTX 200 (NVA0)
[    27.159] 	GeForce GTX 400 (NVC0)
[    27.159] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    27.159] (II) FBDEV: driver for framebuffer: fbdev
[    27.159] (II) VESA: driver for VESA chipsets: vesa
[    27.159] (++) using VT number 7

[    27.161] (II) Loading sub module "fb"
[    27.161] (II) LoadModule: "fb"
[    27.161] (II) Loading /usr/lib/xorg/modules/libfb.so
[    27.162] (II) Module fb: vendor="X.Org Foundation"
[    27.162] 	compiled for 1.15.1, module version = 1.0.0
[    27.162] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    27.162] (WW) Unresolved symbol: fbGetGCPrivateKey
[    27.162] (II) Loading sub module "wfb"
[    27.162] (II) LoadModule: "wfb"
[    27.162] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    27.162] (II) Module wfb: vendor="X.Org Foundation"
[    27.162] 	compiled for 1.15.1, module version = 1.0.0
[    27.162] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    27.162] (II) Loading sub module "ramdac"
[    27.162] (II) LoadModule: "ramdac"
[    27.162] (II) Module "ramdac" already built-in
[    27.162] (WW) Falling back to old probe method for modesetting
[    27.162] (WW) Falling back to old probe method for fbdev
[    27.162] (II) Loading sub module "fbdevhw"
[    27.162] (II) LoadModule: "fbdevhw"
[    27.162] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    27.162] (II) Module fbdevhw: vendor="X.Org Foundation"
[    27.163] 	compiled for 1.15.1, module version = 0.0.2
[    27.163] 	ABI class: X.Org Video Driver, version 15.0
[    27.163] (EE) open /dev/fb0: No such file or directory
[    27.163] (WW) Falling back to old probe method for vesa
[    27.163] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    27.163] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    27.163] (==) NVIDIA(0): RGB weight 888
[    27.163] (==) NVIDIA(0): Default visual is TrueColor
[    27.163] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    27.163] (**) NVIDIA(0): Enabling 2D acceleration
[    27.547] (II) NVIDIA(0): Display (Samsung SyncMaster (DFP-0)) does not support NVIDIA
[    27.547] (II) NVIDIA(0):     3D Vision stereo.
[    27.547] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[    27.548] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 560 Ti (GF114) at PCI:1:0:0 (GPU-0)
[    27.548] (--) NVIDIA(0): Memory: 2097152 kBytes
[    27.548] (--) NVIDIA(0): VideoBIOS: 70.24.21.00.62
[    27.548] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    27.552] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 560 Ti at PCI:1:0:0
[    27.552] (--) NVIDIA(0):     CRT-0
[    27.552] (--) NVIDIA(0):     CRT-1
[    27.552] (--) NVIDIA(0):     Samsung SyncMaster (DFP-0) (boot, connected)
[    27.552] (--) NVIDIA(0):     DFP-1
[    27.552] (--) NVIDIA(0):     DFP-2
[    27.552] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    27.552] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    27.552] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
[    27.553] (--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
[    27.553] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    27.553] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock
[    27.553] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[    27.553] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[    27.553] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    27.553] (**) NVIDIA(0):     device Samsung SyncMaster (DFP-0) (Using EDID frequencies
[    27.553] (**) NVIDIA(0):     has been enabled on all display devices.)
[    27.554] (==) NVIDIA(0): 
[    27.554] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    27.554] (==) NVIDIA(0):     will be used as the requested mode.
[    27.554] (==) NVIDIA(0): 
[    27.554] (II) NVIDIA(0): Validated MetaModes:
[    27.554] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select"
[    27.554] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    27.579] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    27.579] (--) NVIDIA(0):     option
[    27.579] (II) UnloadModule: "nouveau"
[    27.579] (II) Unloading nouveau
[    27.579] (II) UnloadModule: "modesetting"
[    27.579] (II) Unloading modesetting
[    27.579] (II) UnloadModule: "fbdev"
[    27.579] (II) Unloading fbdev
[    27.579] (II) UnloadSubModule: "fbdevhw"
[    27.579] (II) Unloading fbdevhw
[    27.579] (II) UnloadModule: "vesa"
[    27.579] (II) Unloading vesa
[    27.579] (--) Depth 24 pixmap format is 32 bpp
[    27.579] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    27.579] (II) NVIDIA:     access.
[    27.587] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select"
[    27.629] Loading extension NV-GLX
[    27.675] (==) NVIDIA(0): Disabling shared memory pixmaps
[    27.675] (==) NVIDIA(0): Backing store enabled
[    27.675] (==) NVIDIA(0): Silken mouse enabled
[    27.675] (==) NVIDIA(0): DPMS enabled
[    27.675] Loading extension NV-CONTROL
[    27.675] Loading extension XINERAMA
[    27.675] (II) Loading sub module "dri2"
[    27.675] (II) LoadModule: "dri2"
[    27.675] (II) Module "dri2" already built-in
[    27.675] (II) NVIDIA(0): [DRI2] Setup complete
[    27.675] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    27.675] (--) RandR disabled
[    27.679] (II) SELinux: Disabled on system
[    27.680] (II) Initializing extension GLX
[    27.696] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.698] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    27.698] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.698] (II) LoadModule: "evdev"
[    27.698] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.698] (II) Module evdev: vendor="X.Org Foundation"
[    27.698] 	compiled for 1.15.0, module version = 2.8.2
[    27.698] 	Module class: X.Org XInput Driver
[    27.698] 	ABI class: X.Org XInput driver, version 20.0
[    27.699] (II) Using input driver 'evdev' for 'Power Button'
[    27.699] (**) Power Button: always reports core events
[    27.699] (**) evdev: Power Button: Device: "/dev/input/event1"
[    27.699] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.699] (--) evdev: Power Button: Found keys
[    27.699] (II) evdev: Power Button: Configuring as keyboard
[    27.699] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    27.699] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.699] (**) Option "xkb_rules" "evdev"
[    27.699] (**) Option "xkb_model" "pc105"
[    27.699] (**) Option "xkb_layout" "us"
[    27.699] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    27.699] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.699] (II) Using input driver 'evdev' for 'Power Button'
[    27.699] (**) Power Button: always reports core events
[    27.699] (**) evdev: Power Button: Device: "/dev/input/event0"
[    27.699] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.699] (--) evdev: Power Button: Found keys
[    27.699] (II) evdev: Power Button: Configuring as keyboard
[    27.699] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    27.699] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    27.699] (**) Option "xkb_rules" "evdev"
[    27.699] (**) Option "xkb_model" "pc105"
[    27.699] (**) Option "xkb_layout" "us"
[    27.699] (II) config/udev: Adding drm device (/dev/dri/card0)
[    27.699] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    27.700] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event13)
[    27.700] (II) No input driver specified, ignoring this device.
[    27.700] (II) This device may have been added with another device file.
[    27.700] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event12)
[    27.700] (II) No input driver specified, ignoring this device.
[    27.700] (II) This device may have been added with another device file.
[    27.700] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event11)
[    27.700] (II) No input driver specified, ignoring this device.
[    27.700] (II) This device may have been added with another device file.
[    27.700] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event10)
[    27.700] (II) No input driver specified, ignoring this device.
[    27.700] (II) This device may have been added with another device file.
[    27.701] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event2)
[    27.701] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    27.701] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    27.701] (**) Dell Dell USB Keyboard: always reports core events
[    27.701] (**) evdev: Dell Dell USB Keyboard: Device: "/dev/input/event2"
[    27.701] (--) evdev: Dell Dell USB Keyboard: Vendor 0x413c Product 0x2105
[    27.701] (--) evdev: Dell Dell USB Keyboard: Found keys
[    27.701] (II) evdev: Dell Dell USB Keyboard: Configuring as keyboard
[    27.701] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5/event2"
[    27.701] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD, id 8)
[    27.701] (**) Option "xkb_rules" "evdev"
[    27.701] (**) Option "xkb_model" "pc105"
[    27.701] (**) Option "xkb_layout" "us"
[    27.701] (II) config/udev: Adding input device C-Media Electronics Inc.       USB PnP Sound Device           (/dev/input/event3)
[    27.701] (**) C-Media Electronics Inc.       USB PnP Sound Device          : Applying InputClass "evdev keyboard catchall"
[    27.701] (II) Using input driver 'evdev' for 'C-Media Electronics Inc.       USB PnP Sound Device          '
[    27.701] (**) C-Media Electronics Inc.       USB PnP Sound Device          : always reports core events
[    27.701] (**) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : Device: "/dev/input/event3"
[    27.701] (--) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : Vendor 0xd8c Product 0x13c
[    27.701] (--) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : Found 1 mouse buttons
[    27.701] (--) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : Found keys
[    27.701] (II) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : Forcing relative x/y axes to exist.
[    27.701] (II) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : Configuring as mouse
[    27.701] (II) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : Configuring as keyboard
[    27.702] (**) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : YAxisMapping: buttons 4 and 5
[    27.702] (**) evdev: C-Media Electronics Inc.       USB PnP Sound Device          : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.702] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.3/input/input6/event3"
[    27.702] (II) XINPUT: Adding extended input device "C-Media Electronics Inc.       USB PnP Sound Device          " (type: KEYBOARD, id 9)
[    27.702] (**) Option "xkb_rules" "evdev"
[    27.702] (**) Option "xkb_model" "pc105"
[    27.702] (**) Option "xkb_layout" "us"
[    27.702] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[    27.702] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    27.702] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    27.702] (**) USB Optical Mouse: always reports core events
[    27.702] (**) evdev: USB Optical Mouse: Device: "/dev/input/event4"
[    27.702] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d22
[    27.702] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    27.702] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    27.702] (--) evdev: USB Optical Mouse: Found relative axes
[    27.702] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    27.702] (II) evdev: USB Optical Mouse: Configuring as mouse
[    27.702] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    27.702] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    27.702] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.702] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input7/event4"
[    27.702] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 10)
[    27.702] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    27.702] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    27.702] (**) USB Optical Mouse: (accel) acceleration profile 0
[    27.702] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    27.702] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    27.703] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    27.703] (II) No input driver specified, ignoring this device.
[    27.703] (II) This device may have been added with another device file.
[    27.703] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event7)
[    27.703] (II) No input driver specified, ignoring this device.
[    27.703] (II) This device may have been added with another device file.
[    27.703] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event6)
[    27.703] (II) No input driver specified, ignoring this device.
[    27.703] (II) This device may have been added with another device file.
[    27.703] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event5)
[    27.703] (II) No input driver specified, ignoring this device.
[    27.703] (II) This device may have been added with another device file.
[    27.704] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event9)
[    27.704] (II) No input driver specified, ignoring this device.
[    27.704] (II) This device may have been added with another device file.
[    27.704] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event8)
[    27.704] (II) No input driver specified, ignoring this device.
[    27.704] (II) This device may have been added with another device file.

```
What is preventing me from logging into an xsession?

---

### Post by Bucky Ball on 2014-06-23
To fix this I installed lightdm-gtk-greeter. You may want to install a greeter or check if one is installed already. If it is, that is obviously not your problem, but it worked for me just yesterday. 

You could also try deleting the sessions cache and having another go. 

```
sudo rm -rf .cache/sessions
```

Run that in a terminal then reboot. Any better?

---

### Post by Drone4four on 2014-06-23
When I went to install lightdm-gtk-greeter, aptitude told me that it was already installed to the latest version.  I then proceeded to rename ~/.cache/sessions.  That didn't help.  So I Googled 'reconfigure lightdm' and came across some offcial Ubuntu wiki docs somewhere.  I booted Ubuntu, switched to a VT, stopped lightdm, entered, 'sudo dpkg-reconfigure lightdm' and selected gdm.  I started gdm and presto, I was able to start my xsessions again.  I would prefer to use lightdm because its faster to load, but since it doesn't allow me to load an xsession, I am stuck with a slightly slower (but at least functional) gdm.

---

### Post by Bucky Ball on 2014-06-23
I suggested you delete it completely with this,

sudo rm -rf .cache/sessions

... not rename it, although that should have the same effect. I would try deleting it, though, as I suggested.

---

### Post by bapoumba on 2014-06-24
Would you be running out of space ?
```
df -h
df -i
```

---

### Post by Drone4four on 2014-07-03
**Bucky Ball**:  I appreciate your suggestion.  Given that now gdm works for my purposes, I am now not going to try something to fix my previous broken lightdm configuration. But cheers all the same.  Maybe if gdm breaks, I will try to get lightdm working by deleting ~/.cache/sessions rather than moving it.

**bapoumba** said:
> Would you be running out of space ?
```
df -h
df -i
```

Here is the output of those two commands:

```
~ $ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        96G   55G   37G  61% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.9G  4.0K  7.9G   1% /dev
tmpfs           1.6G  1.5M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.9G  205M  7.7G   3% /run/shm
none            100M   96K  100M   1% /run/user
/dev/sda1       961G  192G  770G  20% /media/gnull/data
/dev/sda2       889G  331G  514G  40% /media/gnull/VMs
~ $ df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
/dev/sdb1        6406144 810765   5595379   13% /
none             2054152      2   2054150    1% /sys/fs/cgroup
udev             2050498    567   2049931    1% /dev
tmpfs            2054152    608   2053544    1% /run
none             2054152      4   2054148    1% /run/lock
none             2054152    257   2053895    1% /run/shm
none             2054152     49   2054103    1% /run/user
/dev/sda1      806678528  37585 806640943    1% /media/gnull/data
/dev/sda2       59170816 657221  58513595    2% /media/gnull/VMs
~ $ 
```

Given that my issue is now solved, I'd like to thank **bapoumba** and **Bucky Ball** for their helpful suggestions

---

### Post by bapoumba on 2014-07-04
Thanks Drone4four. Sometimes, being bounced back at the login page is a symptom of running out of space. But that was not the case here :)

---

