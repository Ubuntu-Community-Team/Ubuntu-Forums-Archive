---
title: "startx brings up a black screen with cursor only [Ubuntu 14.04 Server]"
date: 2016-03-11
forum: Desktop Environments
---

### Post by martin_jones3 on 2016-03-11
Hi - I just installed Virtualbox on my Windows 10 PC, then Ubuntu Server 14.04. I installed Gnome core, using:

```
sudo apt-get install xorg gnome-core gnome-system-tools gnome-app-install
```

but when i run "startx" or boot the server up from Virtualbox I'm getting a black screen with just a cursor... /var/log/Xorg.1.log posted below.

```
[   227.911] X.Org X Server 1.15.1
Release Date: 2014-04-13
[   227.911] X Protocol Version 11, Revision 0
[   227.911] Build Operating System: Linux 3.2.0-75-generic i686 Ubuntu
[   227.911] Current Operating System: Linux casperhost 4.2.0-27-generic #32~14.04.1-Ubuntu SMP Fri Jan 22 15:32:27 UTC 2016 i686
[   227.911] Kernel command line: BOOT_IMAGE=/vmlinuz-4.2.0-27-generic root=/dev/mapper/casperhost--vg-root ro
[   227.912] Build Date: 12 February 2015  02:49:46PM
[   227.912] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[   227.912] Current version of pixman: 0.30.2
[   227.912] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   227.912] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   227.913] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 11 12:14:07 2016
[   227.915] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   227.916] (==) No Layout section.  Using the first Screen section.
[   227.917] (==) No screen section available. Using defaults.
[   227.917] (**) |-->Screen "Default Screen Section" (0)
[   227.917] (**) |   |-->Monitor "<default monitor>"
[   227.917] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   227.918] (==) Automatically adding devices
[   227.918] (==) Automatically enabling devices
[   227.918] (==) Automatically adding GPU devices
[   227.919] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   227.919] 	Entry deleted from font path.
[   227.919] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   227.919] 	Entry deleted from font path.
[   227.919] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   227.919] 	Entry deleted from font path.
[   227.919] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   227.919] 	Entry deleted from font path.
[   227.919] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   227.919] 	Entry deleted from font path.
[   227.920] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   227.920] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   227.920] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   227.920] (II) Loader magic: 0x802c06c0
[   227.920] (II) Module ABI versions:
[   227.920] 	X.Org ANSI C Emulation: 0.4
[   227.920] 	X.Org Video Driver: 15.0
[   227.920] 	X.Org XInput driver : 20.0
[   227.920] 	X.Org Server Extension : 8.0
[   227.922] (II) xfree86: Adding drm device (/dev/dri/card0)
[   227.933] (--) PCI:*(0:0:2:0) 80ee:beef:0000:0000 rev 0, Mem @ 0xe0000000/16777216
[   227.934] Initializing built-in extension Generic Event Extension
[   227.934] Initializing built-in extension SHAPE
[   227.934] Initializing built-in extension MIT-SHM
[   227.934] Initializing built-in extension XInputExtension
[   227.934] Initializing built-in extension XTEST
[   227.934] Initializing built-in extension BIG-REQUESTS
[   227.934] Initializing built-in extension SYNC
[   227.934] Initializing built-in extension XKEYBOARD
[   227.934] Initializing built-in extension XC-MISC
[   227.934] Initializing built-in extension SECURITY
[   227.935] Initializing built-in extension XINERAMA
[   227.935] Initializing built-in extension XFIXES
[   227.935] Initializing built-in extension RENDER
[   227.935] Initializing built-in extension RANDR
[   227.935] Initializing built-in extension COMPOSITE
[   227.935] Initializing built-in extension DAMAGE
[   227.935] Initializing built-in extension MIT-SCREEN-SAVER
[   227.935] Initializing built-in extension DOUBLE-BUFFER
[   227.935] Initializing built-in extension RECORD
[   227.935] Initializing built-in extension DPMS
[   227.936] Initializing built-in extension Present
[   227.936] Initializing built-in extension DRI3
[   227.936] Initializing built-in extension X-Resource
[   227.936] Initializing built-in extension XVideo
[   227.936] Initializing built-in extension XVideo-MotionCompensation
[   227.936] Initializing built-in extension SELinux
[   227.936] Initializing built-in extension XFree86-VidModeExtension
[   227.937] Initializing built-in extension XFree86-DGA
[   227.937] Initializing built-in extension XFree86-DRI
[   227.937] Initializing built-in extension DRI2
[   227.937] (II) LoadModule: "glx"
[   227.938] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   227.947] (II) Module glx: vendor="X.Org Foundation"
[   227.948] 	compiled for 1.15.1, module version = 1.0.0
[   227.948] 	ABI class: X.Org Server Extension, version 8.0
[   227.948] (==) AIGLX enabled
[   227.949] Loading extension GLX
[   227.949] (==) Matched vboxvideo as autoconfigured driver 0
[   227.949] (==) Matched vboxvideo as autoconfigured driver 1
[   227.949] (==) Matched modesetting as autoconfigured driver 2
[   227.949] (==) Matched fbdev as autoconfigured driver 3
[   227.949] (==) Matched vesa as autoconfigured driver 4
[   227.949] (==) Assigned the driver to the xf86ConfigLayout
[   227.949] (II) LoadModule: "vboxvideo"
[   227.950] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
[   227.951] (II) Module vboxvideo: vendor="Oracle Corporation"
[   227.951] 	compiled for 1.15.0, module version = 1.0.1
[   227.951] 	Module class: X.Org Video Driver
[   227.951] 	ABI class: X.Org Video Driver, version 15.0
[   227.951] (**) Load address of symbol "VBOXVIDEO" is 0xb7075060
[   227.951] (II) LoadModule: "modesetting"
[   227.953] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   227.953] (II) Module modesetting: vendor="X.Org Foundation"
[   227.954] 	compiled for 1.15.0, module version = 0.8.1
[   227.954] 	Module class: X.Org Video Driver
[   227.954] 	ABI class: X.Org Video Driver, version 15.0
[   227.954] (II) LoadModule: "fbdev"
[   227.954] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   227.955] (II) Module fbdev: vendor="X.Org Foundation"
[   227.955] 	compiled for 1.15.0, module version = 0.4.4
[   227.955] 	Module class: X.Org Video Driver
[   227.955] 	ABI class: X.Org Video Driver, version 15.0
[   227.955] (II) LoadModule: "vesa"
[   227.956] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   227.957] (II) Module vesa: vendor="X.Org Foundation"
[   227.957] 	compiled for 1.15.0, module version = 2.3.3
[   227.957] 	Module class: X.Org Video Driver
[   227.957] 	ABI class: X.Org Video Driver, version 15.0
[   227.958] (II) VBoxVideo: guest driver for VirtualBox: vbox
[   227.958] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   227.960] (II) FBDEV: driver for framebuffer: fbdev
[   227.960] (II) VESA: driver for VESA chipsets: vesa
[   227.960] (++) using VT number 7


[   227.962] (WW) Falling back to old probe method for modesetting
[   227.962] (WW) Falling back to old probe method for fbdev
[   227.962] (II) Loading sub module "fbdevhw"
[   227.962] (II) LoadModule: "fbdevhw"
[   227.963] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   227.963] (II) Module fbdevhw: vendor="X.Org Foundation"
[   227.963] 	compiled for 1.15.1, module version = 0.0.2
[   227.963] 	ABI class: X.Org Video Driver, version 15.0
[   227.964] (WW) Falling back to old probe method for vesa
[   227.965] (II) VBoxVideo(0): VirtualBox guest additions video driver version 5.0.16r105871
[   227.965] (II) Loading sub module "ramdac"
[   227.965] (II) LoadModule: "ramdac"
[   227.965] (II) Module "ramdac" already built-in
[   227.965] (II) Loading sub module "fb"
[   227.965] (II) LoadModule: "fb"
[   227.965] (II) Loading /usr/lib/xorg/modules/libfb.so
[   227.966] (II) Module fb: vendor="X.Org Foundation"
[   227.966] 	compiled for 1.15.1, module version = 1.0.0
[   227.966] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   227.966] (II) Loading sub module "shadowfb"
[   227.966] (II) LoadModule: "shadowfb"
[   227.967] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   227.967] (II) Module shadowfb: vendor="X.Org Foundation"
[   227.968] 	compiled for 1.15.1, module version = 1.0.0
[   227.968] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   227.968] (II) Loading sub module "vgahw"
[   227.968] (II) LoadModule: "vgahw"
[   227.969] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   227.971] (II) Module vgahw: vendor="X.Org Foundation"
[   227.971] 	compiled for 1.15.1, module version = 0.1.0
[   227.972] 	ABI class: X.Org Video Driver, version 15.0
[   227.972] (II) Loading sub module "dri2"
[   227.972] (II) LoadModule: "dri2"
[   227.972] (II) Module "dri2" already built-in
[   227.973] (II) VBoxVideo(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   227.973] (==) VBoxVideo(0): Depth 24, (--) framebuffer bpp 32
[   227.973] (--) VBoxVideo(0): Virtual size is 32766x32766 (pitch 32766)
[   227.973] (**) VBoxVideo(0):  Built-in mode "800x600": 29.3 MHz (scaled from 0.0 MHz), 36.4 kHz, 60.0 Hz
[   227.973] (II) VBoxVideo(0): Modeline "800x600"x0.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz b)
[   227.973] (**) VBoxVideo(0):  Built-in mode "800x600": 29.3 MHz (scaled from 0.0 MHz), 36.4 kHz, 60.0 Hz
[   227.973] (II) VBoxVideo(0): Modeline "800x600"x0.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz b)
[   227.974] (II) VBoxVideo(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[   227.974] (==) VBoxVideo(0): RGB weight 888
[   227.974] (==) VBoxVideo(0): Default visual is TrueColor
[   227.974] (==) VBoxVideo(0): Using gamma correction (1.0, 1.0, 1.0)
[   227.974] (==) VBoxVideo(0): DPI set to (96, 96)
[   227.974] (II) UnloadModule: "modesetting"
[   227.974] (II) Unloading modesetting
[   227.975] (II) UnloadModule: "fbdev"
[   227.975] (II) Unloading fbdev
[   227.975] (II) UnloadSubModule: "fbdevhw"
[   227.975] (II) Unloading fbdevhw
[   227.975] (II) UnloadModule: "vesa"
[   227.976] (II) Unloading vesa
[   227.976] (--) Depth 24 pixmap format is 32 bpp
[   227.983] (II) VBoxVideo(0): [DRI2] Setup complete
[   227.984] (II) VBoxVideo(0): [DRI2]   DRI driver: vboxvideo
[   227.985] (II) VBoxVideo(0): Requested monitor count: 1
[   227.986] (II) VBoxVideo(0): Output VGA-0 has no monitor section
[   227.986] (II) VBoxVideo(0): Output VGA-0 has no monitor section
[   227.986] (II) VBoxVideo(0): Printing probed modes for output VGA-0
[   227.986] (II) VBoxVideo(0): Modeline "800x600"x60.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz Pb)
[   227.986] (II) VBoxVideo(0): Modeline "2560x1600"x60.0  247.26  2560 2562 2564 2566  1600 1602 1604 1606 (96.4 kHz b)
[   227.986] (II) VBoxVideo(0): Modeline "2560x1440"x60.0  222.63  2560 2562 2564 2566  1440 1442 1444 1446 (86.8 kHz b)
[   227.986] (II) VBoxVideo(0): Modeline "2048x1536"x60.0  190.04  2048 2050 2052 2054  1536 1538 1540 1542 (92.5 kHz b)
[   227.987] (II) VBoxVideo(0): Modeline "1920x1600"x60.0  185.59  1920 1922 1924 1926  1600 1602 1604 1606 (96.4 kHz b)
[   227.987] (II) VBoxVideo(0): Modeline "1920x1080"x60.0  125.50  1920 1922 1924 1926  1080 1082 1084 1086 (65.2 kHz b)
[   227.987] (II) VBoxVideo(0): Modeline "1600x1200"x60.0  116.21  1600 1602 1604 1606  1200 1202 1204 1206 (72.4 kHz b)
[   227.987] (II) VBoxVideo(0): Modeline "1680x1050"x60.0  106.82  1680 1682 1684 1686  1050 1052 1054 1056 (63.4 kHz b)
[   227.987] (II) VBoxVideo(0): Modeline "1400x1050"x60.0   89.08  1400 1402 1404 1406  1050 1052 1054 1056 (63.4 kHz b)
[   227.987] (II) VBoxVideo(0): Modeline "1280x1024"x60.0   79.47  1280 1282 1284 1286  1024 1026 1028 1030 (61.8 kHz b)
[   227.987] (II) VBoxVideo(0): Modeline "1024x768"x60.0   47.83  1024 1026 1028 1030  768 770 772 774 (46.4 kHz b)
[   227.987] (II) VBoxVideo(0): Modeline "800x600"x60.0   29.31  800 802 804 806  600 602 604 606 (36.4 kHz b)
[   227.988] (II) VBoxVideo(0): Modeline "640x480"x60.0   18.84  640 642 644 646  480 482 484 486 (29.2 kHz b)
[   227.988] (II) VBoxVideo(0): Output VGA-0 connected
[   227.988] (II) VBoxVideo(0): Using exact sizes for initial modes
[   227.988] (II) VBoxVideo(0): Output VGA-0 using initial mode 800x600
[   227.989] (II) VBoxVideo(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   227.989] (II) VBoxVideo(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   227.990] (==) VBoxVideo(0): DPMS enabled
[   227.990] (--) RandR disabled
[   228.006] (II) SELinux: Disabled on system
[   228.014] (II) Next line is added to allow vboxvideo_drv.so to appear as whitelisted driver
[   228.014] (II) The file referenced, is *NOT* loaded
[   228.014] (II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
[   228.014] (EE) AIGLX error: vboxvideo does not export required DRI extension
[   228.015] (EE) AIGLX: reverting to software rendering
[   228.067] (II) AIGLX: Loaded and initialized swrast
[   228.068] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   228.069] (II) VBoxVideo(0): Setting screen physical size to 211 x 158
[   228.114] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   228.140] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   228.141] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   228.141] (II) LoadModule: "evdev"
[   228.142] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   228.143] (II) Module evdev: vendor="X.Org Foundation"
[   228.143] 	compiled for 1.15.0, module version = 2.8.2
[   228.143] 	Module class: X.Org XInput Driver
[   228.143] 	ABI class: X.Org XInput driver, version 20.0
[   228.143] (II) Using input driver 'evdev' for 'Power Button'
[   228.143] (**) Power Button: always reports core events
[   228.143] (**) evdev: Power Button: Device: "/dev/input/event0"
[   228.143] (--) evdev: Power Button: Vendor 0 Product 0x1
[   228.144] (--) evdev: Power Button: Found keys
[   228.144] (II) evdev: Power Button: Configuring as keyboard
[   228.144] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0/event0"
[   228.144] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   228.144] (**) Option "xkb_rules" "evdev"
[   228.144] (**) Option "xkb_model" "pc105"
[   228.145] (**) Option "xkb_layout" "us"
[   228.145] (**) Option "xkb_variant" "intl"
[   228.149] (II) XKB: reuse xkmfile /var/lib/xkb/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[   228.153] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[   228.154] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   228.154] (II) Using input driver 'evdev' for 'Sleep Button'
[   228.154] (**) Sleep Button: always reports core events
[   228.154] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[   228.154] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   228.154] (--) evdev: Sleep Button: Found keys
[   228.155] (II) evdev: Sleep Button: Configuring as keyboard
[   228.155] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSLPBN:00/input/input1/event1"
[   228.155] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 7)
[   228.155] (**) Option "xkb_rules" "evdev"
[   228.155] (**) Option "xkb_model" "pc105"
[   228.155] (**) Option "xkb_layout" "us"
[   228.155] (**) Option "xkb_variant" "intl"
[   228.157] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[   228.158] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[   228.158] (II) Using input driver 'evdev' for 'Video Bus'
[   228.158] (**) Video Bus: always reports core events
[   228.158] (**) evdev: Video Bus: Device: "/dev/input/event5"
[   228.158] (--) evdev: Video Bus: Vendor 0 Product 0x6
[   228.158] (--) evdev: Video Bus: Found keys
[   228.158] (II) evdev: Video Bus: Configuring as keyboard
[   228.158] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input6/event5"
[   228.158] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[   228.158] (**) Option "xkb_rules" "evdev"
[   228.159] (**) Option "xkb_model" "pc105"
[   228.159] (**) Option "xkb_layout" "us"
[   228.159] (**) Option "xkb_variant" "intl"
[   228.160] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[   228.160] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[   228.162] (II) config/udev: Adding input device VirtualBox mouse integration (/dev/input/event6)
[   228.162] (**) VirtualBox mouse integration: Applying InputClass "evdev pointer catchall"
[   228.162] (II) Using input driver 'evdev' for 'VirtualBox mouse integration'
[   228.162] (**) VirtualBox mouse integration: always reports core events
[   228.162] (**) evdev: VirtualBox mouse integration: Device: "/dev/input/event6"
[   228.162] (--) evdev: VirtualBox mouse integration: Vendor 0x80ee Product 0xcafe
[   228.163] (--) evdev: VirtualBox mouse integration: Found 1 mouse buttons
[   228.163] (--) evdev: VirtualBox mouse integration: Found absolute axes
[   228.163] (--) evdev: VirtualBox mouse integration: Found x and y absolute axes
[   228.163] (--) evdev: VirtualBox mouse integration: Found absolute touchscreen
[   228.163] (II) evdev: VirtualBox mouse integration: Configuring as touchscreen
[   228.163] (**) evdev: VirtualBox mouse integration: YAxisMapping: buttons 4 and 5
[   228.163] (**) evdev: VirtualBox mouse integration: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   228.163] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/input/input7/event6"
[   228.163] (II) XINPUT: Adding extended input device "VirtualBox mouse integration" (type: TOUCHSCREEN, id 9)
[   228.164] (II) evdev: VirtualBox mouse integration: initialized for absolute axes.
[   228.166] (**) VirtualBox mouse integration: (accel) keeping acceleration scheme 1
[   228.166] (**) VirtualBox mouse integration: (accel) acceleration profile 0
[   228.166] (**) VirtualBox mouse integration: (accel) acceleration factor: 2.000
[   228.166] (**) VirtualBox mouse integration: (accel) acceleration threshold: 4
[   228.167] (II) config/udev: Adding input device VirtualBox mouse integration (/dev/input/js1)
[   228.168] (II) No input driver specified, ignoring this device.
[   228.168] (II) This device may have been added with another device file.
[   228.169] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/event4)
[   228.169] (**) VirtualBox USB Tablet: Applying InputClass "evdev pointer catchall"
[   228.169] (II) Using input driver 'evdev' for 'VirtualBox USB Tablet'
[   228.170] (**) VirtualBox USB Tablet: always reports core events
[   228.170] (**) evdev: VirtualBox USB Tablet: Device: "/dev/input/event4"
[   228.229] (--) evdev: VirtualBox USB Tablet: Vendor 0x80ee Product 0x21
[   228.230] (--) evdev: VirtualBox USB Tablet: Found 9 mouse buttons
[   228.231] (--) evdev: VirtualBox USB Tablet: Found scroll wheel(s)
[   228.231] (--) evdev: VirtualBox USB Tablet: Found relative axes
[   228.231] (--) evdev: VirtualBox USB Tablet: Found absolute axes
[   228.231] (--) evdev: VirtualBox USB Tablet: Found x and y absolute axes
[   228.231] (--) evdev: VirtualBox USB Tablet: Found absolute touchscreen
[   228.231] (II) evdev: VirtualBox USB Tablet: Configuring as touchscreen
[   228.232] (II) evdev: VirtualBox USB Tablet: Adding scrollwheel support
[   228.232] (**) evdev: VirtualBox USB Tablet: YAxisMapping: buttons 4 and 5
[   228.232] (**) evdev: VirtualBox USB Tablet: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   228.232] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:06.0/usb1/1-1/1-1:1.0/0003:80EE:0021.0001/input/input5/event4"
[   228.233] (II) XINPUT: Adding extended input device "VirtualBox USB Tablet" (type: TOUCHSCREEN, id 10)
[   228.233] (WW) evdev: VirtualBox USB Tablet: touchpads, tablets and touchscreens ignore relative axes.
[   228.233] (II) evdev: VirtualBox USB Tablet: initialized for absolute axes.
[   228.234] (**) VirtualBox USB Tablet: (accel) keeping acceleration scheme 1
[   228.234] (**) VirtualBox USB Tablet: (accel) acceleration profile 0
[   228.235] (**) VirtualBox USB Tablet: (accel) acceleration factor: 2.000
[   228.237] (**) VirtualBox USB Tablet: (accel) acceleration threshold: 4
[   228.250] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/js0)
[   228.251] (II) No input driver specified, ignoring this device.
[   228.253] (II) This device may have been added with another device file.
[   228.255] (II) config/udev: Adding input device VirtualBox USB Tablet (/dev/input/mouse1)
[   228.255] (II) No input driver specified, ignoring this device.
[   228.257] (II) This device may have been added with another device file.
[   228.265] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   228.267] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   228.267] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   228.269] (**) AT Translated Set 2 keyboard: always reports core events
[   228.269] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   228.270] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   228.271] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   228.271] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   228.274] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   228.275] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[   228.281] (**) Option "xkb_rules" "evdev"
[   228.283] (**) Option "xkb_model" "pc105"
[   228.284] (**) Option "xkb_layout" "us"
[   228.285] (**) Option "xkb_variant" "intl"
[   228.293] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event3)
[   228.294] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[   228.295] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[   228.295] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[   228.295] (**) evdev: ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event3"
[   228.296] (--) evdev: ImExPS/2 Generic Explorer Mouse: Vendor 0x2 Product 0x6
[   228.297] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[   228.297] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[   228.298] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found relative axes
[   228.298] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[   228.298] (II) evdev: ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[   228.298] (II) evdev: ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[   228.299] (**) evdev: ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[   228.299] (**) evdev: ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   228.299] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input4/event3"
[   228.300] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE, id 12)
[   228.301] (II) evdev: ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[   228.301] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[   228.301] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[   228.302] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[   228.302] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[   228.305] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[   228.306] (II) No input driver specified, ignoring this device.
[   228.307] (II) This device may have been added with another device file.
[   231.836] (II) XKB: reuse xkmfile /var/lib/xkb/server-A5431D4A34463C892C9E905E2E421B30A3CC30DD.xkm
[   232.126] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[   232.160] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[   232.185] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[   232.359] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[   232.382] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[   232.405] (II) XKB: reuse xkmfile /var/lib/xkb/server-5ABD7681B17F87CA1AF9A3B09827D995002CEEFE.xkm
[   233.399] (II) XKB: reuse xkmfile /var/lib/xkb/server-3DA2CB64A782496C0B986EAFE8E005C5766EF3CA.xkm
[   234.193] (II) XKB: reuse xkmfile /var/lib/xkb/server-3DA2CB64A782496C0B986EAFE8E005C5766EF3CA.xkm
[   234.428] (II) XKB: reuse xkmfile /var/lib/xkb/server-3DA2CB64A782496C0B986EAFE8E005C5766EF3CA.xkm
[   234.667] (II) XKB: reuse xkmfile /var/lib/xkb/server-3DA2CB64A782496C0B986EAFE8E005C5766EF3CA.xkm
[   234.806] (II) XKB: reuse xkmfile /var/lib/xkb/server-3DA2CB64A782496C0B986EAFE8E005C5766EF3CA.xkm
[   234.925] (II) XKB: reuse xkmfile /var/lib/xkb/server-3DA2CB64A782496C0B986EAFE8E005C5766EF3CA.xkm
[   235.082] (II) XKB: reuse xkmfile /var/lib/xkb/server-3DA2CB64A782496C0B986EAFE8E005C5766EF3CA.xkm



```

I think it must be something to do with my graphics driver but i can't tell. Anyone have any idea what I'm missing?

---

### Post by v3.xx on 2016-03-11
I have not tried gnome-core, but what you have looks good to me.

Have you tried xinitrc?

[https://wiki.archlinux.org/index.php/xinitrc#Making_a_DE.2FWM_choice](https://wiki.archlinux.org/index.php/xinitrc#Making_a_DE.2FWM_choice)

And this could be video related, onboard server graphics are poor.

---

