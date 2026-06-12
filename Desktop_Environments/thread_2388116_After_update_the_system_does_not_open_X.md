---
title: "After update the system does not open X"
date: 2018-03-28
forum: Desktop Environments
---

### Post by danielsender on 2018-03-28
I have a Dell M90 with 16.04-4 installed. Everything was OK until the last update. Now when I boot, the NVidia screen blinks a few times and it never goes to the grub menu nor the graphic interface. I can get to the console with Ctrl+Alt+F1 and log on. So just in case I reinstalled lightdm and ubuntu-desktop but it didn't change anything. I also installed gdm to see if there was something wrong with lightdm but the situation didn't change. When I do a ps I see that gdm3 is running. I also typed "sudo startx" and a graphic interface opened that looked like xfce4 but when I clicked anywhere I got no response.

I will appreciate any help.

---

### Post by ank2 on 2018-03-28
Was it an LTS?

Try startx as user (don't use sudo, log in on a TTY as user).

Anyway I had this on an upgrade a few years ago too and couldn't figure out whats wrong. I ended up installing the new version over the old version and was able to salvage user settings.

---

### Post by danielsender on 2018-03-28
Yes, 16.04 is LTS

I tried startx without the sudo and it doesn't do anything.

---

### Post by ank2 on 2018-03-28
Cannot help here because I ran into the same problems after a (not LTS) update. I hope others here can give you a hand.

If not and it's a lost cause, try installing the new version (from DVD or USB stick) over the old version without formatting the partition. With some luck you get your old system back.

---

### Post by again? on 2018-03-28
If you ran startx with sudo, your ~/.Xauthority file may no longer belong to you and you won't be able to login to an X session.
Try removing...
```
sudo rm ~/.Xauthority
```

At this stage I would run an update (any errors?)
```
sudo apt update && sudo apt upgrade
```

and reboot.

---

### Post by danielsender on 2018-03-29
This is what I get when I type 'startx' (not as sudo):
```
X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
Current Operating System: Linux Beethoven 4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:23:04 UTC 2018 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-116-generic root=UUID=8f168b62-07d0-4622-b463-a170e07fc9c5 ro quiet splash
Build Date: 13 October 2017  01:57:05PM
xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support)
Current version of pixman: 0.33.6
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 28 21:43:45 2018
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
xinit: connection to X server lost
waiting for X server to shut down (II) Server terminated successfully (0). Closing log file.                                                                       

```

I'm also attaching the Xorg.0.log file.

```

[    59.012] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    59.012] X Protocol Version 11, Revision 0
[    59.013] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    59.013] Current Operating System: Linux Beethoven 4.4.0-116-generic #140-Ubuntu SMP Mon Feb 12 21:23:04 UTC 2018 x86_64
[    59.013] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-116-generic root=UUID=8f168b62-07d0-4622-b463-a170e07fc9c5 ro quiet splash
[    59.013] Build Date: 13 October 2017  01:57:05PM
[    59.013] xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
[    59.013] Current version of pixman: 0.33.6
[    59.013] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    59.014] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    59.014] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 28 23:18:01 2018
[    59.015] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    59.015] (==) No Layout section.  Using the first Screen section.
[    59.015] (==) No screen section available. Using defaults.
[    59.015] (**) |-->Screen "Default Screen Section" (0)
[    59.015] (**) |   |-->Monitor "<default monitor>"
[    59.015] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    59.015] (==) Automatically adding devices
[    59.015] (==) Automatically enabling devices
[    59.015] (==) Automatically adding GPU devices
[    59.015] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    59.015] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    59.015] 	Entry deleted from font path.
[    59.015] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    59.015] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    59.015] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    59.015] (II) Loader magic: 0x55cb5091adc0
[    59.015] (II) Module ABI versions:
[    59.015] 	X.Org ANSI C Emulation: 0.4
[    59.015] 	X.Org Video Driver: 20.0
[    59.015] 	X.Org XInput driver : 22.1
[    59.015] 	X.Org Server Extension : 9.0
[    59.016] (++) using VT number 1

[    59.022] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_32
[    59.023] (II) xfree86: Adding drm device (/dev/dri/card0)
[    59.023] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 8 paused 0
[    59.025] (--) PCI:*(0:1:0:0) 10de:029a:1028:019b rev 161, Mem @ 0xed000000/16777216, 0xd0000000/268435456, 0xee000000/16777216, I/O @ 0x0000ef00/128, BIOS @ 0x????????/131072
[    59.025] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    59.025] (II) "glx" will be loaded by default.
[    59.025] (II) LoadModule: "glx"
[    59.026] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    59.043] (II) Module glx: vendor="NVIDIA Corporation"
[    59.043] 	compiled for 4.0.2, module version = 1.0.0
[    59.043] 	Module class: X.Org Server Extension
[    59.043] (II) NVIDIA GLX Module  304.135  Tue Jan 17 15:46:50 PST 2017
[    59.043] (==) Matched nvidia as autoconfigured driver 0
[    59.043] (==) Matched nouveau as autoconfigured driver 1
[    59.043] (==) Matched nvidia as autoconfigured driver 2
[    59.043] (==) Matched nouveau as autoconfigured driver 3
[    59.043] (==) Matched modesetting as autoconfigured driver 4
[    59.043] (==) Matched fbdev as autoconfigured driver 5
[    59.043] (==) Matched vesa as autoconfigured driver 6
[    59.043] (==) Assigned the driver to the xf86ConfigLayout
[    59.043] (II) LoadModule: "nvidia"
[    59.043] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    59.044] (II) Module nvidia: vendor="NVIDIA Corporation"
[    59.044] 	compiled for 4.0.2, module version = 1.0.0
[    59.044] 	Module class: X.Org Video Driver
[    59.044] (II) LoadModule: "nouveau"
[    59.045] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    59.045] (II) Module nouveau: vendor="X.Org Foundation"
[    59.045] 	compiled for 1.18.1, module version = 1.0.12
[    59.045] 	Module class: X.Org Video Driver
[    59.045] 	ABI class: X.Org Video Driver, version 20.0
[    59.045] (II) LoadModule: "modesetting"
[    59.045] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    59.045] (II) Module modesetting: vendor="X.Org Foundation"
[    59.045] 	compiled for 1.18.4, module version = 1.18.4
[    59.045] 	Module class: X.Org Video Driver
[    59.045] 	ABI class: X.Org Video Driver, version 20.0
[    59.045] (II) LoadModule: "fbdev"
[    59.046] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    59.046] (II) Module fbdev: vendor="X.Org Foundation"
[    59.046] 	compiled for 1.18.1, module version = 0.4.4
[    59.046] 	Module class: X.Org Video Driver
[    59.046] 	ABI class: X.Org Video Driver, version 20.0
[    59.046] (II) LoadModule: "vesa"
[    59.046] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    59.046] (II) Module vesa: vendor="X.Org Foundation"
[    59.046] 	compiled for 1.18.1, module version = 2.3.4
[    59.046] 	Module class: X.Org Video Driver
[    59.046] 	ABI class: X.Org Video Driver, version 20.0
[    59.046] (II) NVIDIA dlloader X Driver  304.135  Tue Jan 17 15:28:00 PST 2017
[    59.046] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    59.046] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    59.046] (II) NOUVEAU driver for NVIDIA chipset families :
[    59.046] 	RIVA TNT        (NV04)
[    59.046] 	RIVA TNT2       (NV05)
[    59.046] 	GeForce 256     (NV10)
[    59.046] 	GeForce 2       (NV11, NV15)
[    59.046] 	GeForce 4MX     (NV17, NV18)
[    59.046] 	GeForce 3       (NV20)
[    59.046] 	GeForce 4Ti     (NV25, NV28)
[    59.046] 	GeForce FX      (NV3x)
[    59.046] 	GeForce 6       (NV4x)
[    59.046] 	GeForce 7       (G7x)
[    59.046] 	GeForce 8       (G8x)
[    59.046] 	GeForce GTX 200 (NVA0)
[    59.046] 	GeForce GTX 400 (NVC0)
[    59.046] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    59.046] (II) FBDEV: driver for framebuffer: fbdev
[    59.047] (II) VESA: driver for VESA chipsets: vesa
[    59.047] (II) Loading sub module "fb"
[    59.047] (II) LoadModule: "fb"
[    59.047] (II) Loading /usr/lib/xorg/modules/libfb.so
[    59.047] (II) Module fb: vendor="X.Org Foundation"
[    59.047] 	compiled for 1.18.4, module version = 1.0.0
[    59.047] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    59.047] (II) Loading sub module "wfb"
[    59.047] (II) LoadModule: "wfb"
[    59.047] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    59.047] (II) Module wfb: vendor="X.Org Foundation"
[    59.047] 	compiled for 1.18.4, module version = 1.0.0
[    59.047] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    59.047] (II) Loading sub module "ramdac"
[    59.047] (II) LoadModule: "ramdac"
[    59.047] (II) Module "ramdac" already built-in
[    59.048] (WW) Falling back to old probe method for modesetting
[    59.048] (WW) Falling back to old probe method for fbdev
[    59.048] (II) Loading sub module "fbdevhw"
[    59.048] (II) LoadModule: "fbdevhw"
[    59.048] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    59.048] (II) Module fbdevhw: vendor="X.Org Foundation"
[    59.048] 	compiled for 1.18.4, module version = 0.0.2
[    59.048] 	ABI class: X.Org Video Driver, version 20.0
[    59.048] (EE) open /dev/fb0: No such file or directory
[    59.048] (WW) Falling back to old probe method for vesa
[    59.048] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    59.048] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    59.048] (==) NVIDIA(0): RGB weight 888
[    59.048] (==) NVIDIA(0): Default visual is TrueColor
[    59.048] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    59.048] (**) NVIDIA(0): Enabling 2D acceleration
[    59.718] (II) NVIDIA(GPU-0): Display (Seiko/Epson (DFP-0)) does not support NVIDIA 3D
[    59.718] (II) NVIDIA(GPU-0):     Vision stereo.
[    59.780] (II) NVIDIA(GPU-0): Display (HP LP2465 (DFP-1)) does not support NVIDIA 3D Vision
[    59.780] (II) NVIDIA(GPU-0):     stereo.
[    59.782] (II) NVIDIA(0): NVIDIA GPU Quadro FX 2500M (G71GL) at PCI:1:0:0 (GPU-0)
[    59.782] (--) NVIDIA(0): Memory: 524288 kBytes
[    59.782] (--) NVIDIA(0): VideoBIOS: 05.71.22.28.04
[    59.782] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    59.782] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    59.782] (--) NVIDIA(0): Valid display device(s) on Quadro FX 2500M at PCI:1:0:0
[    59.782] (--) NVIDIA(0):     CRT-0
[    59.782] (--) NVIDIA(0):     TV-0
[    59.782] (--) NVIDIA(0):     Seiko/Epson (DFP-0) (connected)
[    59.782] (--) NVIDIA(0):     HP LP2465 (DFP-1) (connected)
[    59.782] (--) NVIDIA(0):     DFP-2
[    59.782] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    59.782] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    59.782] (--) NVIDIA(0): TV encoder: Unknown
[    59.782] (--) NVIDIA(0): Seiko/Epson (DFP-0): 330.0 MHz maximum pixel clock
[    59.782] (--) NVIDIA(0): Seiko/Epson (DFP-0): Internal Dual Link LVDS
[    59.782] (--) NVIDIA(0): HP LP2465 (DFP-1): 165.0 MHz maximum pixel clock
[    59.782] (--) NVIDIA(0): HP LP2465 (DFP-1): Internal Single Link TMDS
[    59.782] (--) NVIDIA(0): DFP-2: 165.0 MHz maximum pixel clock
[    59.782] (--) NVIDIA(0): DFP-2: Internal Single Link TMDS
[    59.782] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    59.782] (**) NVIDIA(0):     device Seiko/Epson (DFP-0) (Using EDID frequencies has
[    59.782] (**) NVIDIA(0):     been enabled on all display devices.)
[    59.782] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    59.782] (**) NVIDIA(0):     device HP LP2465 (DFP-1) (Using EDID frequencies has been
[    59.782] (**) NVIDIA(0):     enabled on all display devices.)
[    59.782] (==) NVIDIA(0): 
[    59.782] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    59.782] (==) NVIDIA(0):     will be used as the requested mode.
[    59.782] (==) NVIDIA(0): 
[    59.782] (II) NVIDIA(0): Validated MetaModes:
[    59.782] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[    59.782] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 1200
[    59.783] (WW) NVIDIA(0): Unable to support custom viewPortOut 1920 x 1080 +0 +60
[    59.783] (WW) NVIDIA(0): Unable to support custom viewPortOut 1600 x 1200 +160 +0
[    59.783] (WW) NVIDIA(0): Unable to support custom viewPortOut 1500 x 1200 +210 +0
[    59.784] (WW) NVIDIA(0): Unable to support custom viewPortOut 1920 x 1080 +0 +60
[    59.784] (WW) NVIDIA(0): Unable to support custom viewPortOut 1600 x 1200 +160 +0
[    59.784] (WW) NVIDIA(0): Unable to support custom viewPortOut 1600 x 1200 +160 +0
[    59.784] (WW) NVIDIA(0): Unable to support custom viewPortOut 1600 x 1200 +160 +0
[    59.784] (--) NVIDIA(0): DPI set to (131, 132); computed from "UseEdidDpi" X config
[    59.784] (--) NVIDIA(0):     option
[    59.784] (WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
[    59.784] (WW) NVIDIA(0):     UBB.
[    59.784] (II) UnloadModule: "nouveau"
[    59.784] (II) Unloading nouveau
[    59.784] (II) UnloadModule: "modesetting"
[    59.785] (II) Unloading modesetting
[    59.785] (II) UnloadModule: "fbdev"
[    59.785] (II) Unloading fbdev
[    59.785] (II) UnloadSubModule: "fbdevhw"
[    59.785] (II) Unloading fbdevhw
[    59.785] (II) UnloadModule: "vesa"
[    59.785] (II) Unloading vesa
[    59.785] (--) Depth 24 pixmap format is 32 bpp
[    59.798] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select"
[    59.993] (==) NVIDIA(0): Disabling shared memory pixmaps
[    59.993] (==) NVIDIA(0): Backing store enabled
[    59.993] (==) NVIDIA(0): Silken mouse enabled
[    59.994] (==) NVIDIA(0): DPMS enabled
[    59.994] (II) Loading sub module "dri2"
[    59.994] (II) LoadModule: "dri2"
[    59.994] (II) Module "dri2" already built-in
[    59.994] (II) NVIDIA(0): [DRI2] Setup complete
[    59.994] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    59.994] (--) RandR disabled
[    59.999] (II) SELinux: Disabled on system
[    60.000] (II) Initializing extension GLX
[    60.000] (II) Indirect GLX disabled.(II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    60.132] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    60.132] (II) LoadModule: "evdev"
[    60.133] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    60.133] (II) Module evdev: vendor="X.Org Foundation"
[    60.133] 	compiled for 1.18.1, module version = 2.10.1
[    60.133] 	Module class: X.Org XInput Driver
[    60.133] 	ABI class: X.Org XInput driver, version 22.1
[    60.134] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 30 paused 0
[    60.134] (II) Using input driver 'evdev' for 'Video Bus'
[    60.134] (**) Video Bus: always reports core events
[    60.134] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    60.134] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    60.134] (--) evdev: Video Bus: Found keys
[    60.134] (II) evdev: Video Bus: Configuring as keyboard
[    60.134] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:2a/LNXVIDEO:00/input/input5/event4"
[    60.134] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    60.134] (**) Option "xkb_rules" "evdev"
[    60.134] (**) Option "xkb_model" "pc105"
[    60.134] (**) Option "xkb_layout" "us"
[    60.135] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    60.135] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    60.135] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 31 paused 0
[    60.135] (II) Using input driver 'evdev' for 'Power Button'
[    60.135] (**) Power Button: always reports core events
[    60.135] (**) evdev: Power Button: Device: "/dev/input/event1"
[    60.135] (--) evdev: Power Button: Vendor 0 Product 0x1
[    60.135] (--) evdev: Power Button: Found keys
[    60.135] (II) evdev: Power Button: Configuring as keyboard
[    60.135] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    60.135] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    60.136] (**) Option "xkb_rules" "evdev"
[    60.136] (**) Option "xkb_model" "pc105"
[    60.136] (**) Option "xkb_layout" "us"
[    60.136] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    60.136] (II) No input driver specified, ignoring this device.
[    60.136] (II) This device may have been added with another device file.
[    60.137] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    60.137] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    60.137] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 32 paused 0
[    60.137] (II) Using input driver 'evdev' for 'Sleep Button'
[    60.137] (**) Sleep Button: always reports core events
[    60.137] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    60.138] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    60.138] (--) evdev: Sleep Button: Found keys
[    60.138] (II) evdev: Sleep Button: Configuring as keyboard
[    60.138] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    60.138] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    60.138] (**) Option "xkb_rules" "evdev"
[    60.138] (**) Option "xkb_model" "pc105"
[    60.138] (**) Option "xkb_layout" "us"
[    60.138] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[    60.138] (II) No input driver specified, ignoring this device.
[    60.138] (II) This device may have been added with another device file.
[    60.139] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event8)
[    60.139] (II) No input driver specified, ignoring this device.
[    60.139] (II) This device may have been added with another device file.
[    60.140] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
[    60.140] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    60.140] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 33 paused 0
[    60.140] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    60.140] (**) Logitech USB Receiver: always reports core events
[    60.140] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event6"
[    60.140] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc505
[    60.140] (--) evdev: Logitech USB Receiver: Found keys
[    60.140] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    60.140] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/0003:046D:C505.0001/input/input7/event6"
[    60.140] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 9)
[    60.140] (**) Option "xkb_rules" "evdev"
[    60.140] (**) Option "xkb_model" "pc105"
[    60.140] (**) Option "xkb_layout" "us"
[    60.141] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event7)
[    60.141] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    60.142] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    60.142] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 34 paused 0
[    60.142] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    60.142] (**) Logitech USB Receiver: always reports core events
[    60.142] (**) evdev: Logitech USB Receiver: Device: "/dev/input/event7"
[    60.142] (--) evdev: Logitech USB Receiver: Vendor 0x46d Product 0xc505
[    60.142] (--) evdev: Logitech USB Receiver: Found 20 mouse buttons
[    60.142] (--) evdev: Logitech USB Receiver: Found scroll wheel(s)
[    60.142] (--) evdev: Logitech USB Receiver: Found relative axes
[    60.142] (--) evdev: Logitech USB Receiver: Found x and y relative axes
[    60.142] (--) evdev: Logitech USB Receiver: Found keys
[    60.142] (II) evdev: Logitech USB Receiver: Configuring as mouse
[    60.142] (II) evdev: Logitech USB Receiver: Configuring as keyboard
[    60.142] (II) evdev: Logitech USB Receiver: Adding scrollwheel support
[    60.142] (**) evdev: Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    60.142] (**) evdev: Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    60.142] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.1/0003:046D:C505.0002/input/input8/event7"
[    60.142] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD, id 10)
[    60.142] (**) Option "xkb_rules" "evdev"
[    60.142] (**) Option "xkb_model" "pc105"
[    60.142] (**) Option "xkb_layout" "us"
[    60.143] (II) evdev: Logitech USB Receiver: initialized for relative axes.
[    60.143] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    60.143] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    60.143] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    60.143] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    60.144] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
[    60.144] (II) No input driver specified, ignoring this device.
[    60.144] (II) This device may have been added with another device file.
[    60.144] (II) config/udev: Adding input device UVC Camera (046d:081a) (/dev/input/event11)
[    60.144] (**) UVC Camera (046d:081a): Applying InputClass "evdev keyboard catchall"
[    60.145] (II) systemd-logind: got fd for /dev/input/event11 13:75 fd 35 paused 0
[    60.145] (II) Using input driver 'evdev' for 'UVC Camera (046d:081a)'
[    60.145] (**) UVC Camera (046d:081a): always reports core events
[    60.145] (**) evdev: UVC Camera (046d:081a): Device: "/dev/input/event11"
[    60.145] (--) evdev: UVC Camera (046d:081a): Vendor 0x46d Product 0x81a
[    60.145] (--) evdev: UVC Camera (046d:081a): Found keys
[    60.145] (II) evdev: UVC Camera (046d:081a): Configuring as keyboard
[    60.145] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input12/event11"
[    60.145] (II) XINPUT: Adding extended input device "UVC Camera (046d:081a)" (type: KEYBOARD, id 11)
[    60.145] (**) Option "xkb_rules" "evdev"
[    60.145] (**) Option "xkb_model" "pc105"
[    60.145] (**) Option "xkb_layout" "us"
[    60.146] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    60.146] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    60.146] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 36 paused 0
[    60.146] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    60.146] (**) AT Translated Set 2 keyboard: always reports core events
[    60.146] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    60.146] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    60.146] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    60.146] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    60.146] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    60.146] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    60.146] (**) Option "xkb_rules" "evdev"
[    60.146] (**) Option "xkb_model" "pc105"
[    60.146] (**) Option "xkb_layout" "us"
[    60.147] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    60.147] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    60.147] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    60.147] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    60.147] (II) LoadModule: "synaptics"
[    60.148] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    60.148] (II) Module synaptics: vendor="X.Org Foundation"
[    60.148] 	compiled for 1.18.1, module version = 1.8.2
[    60.148] 	Module class: X.Org XInput Driver
[    60.148] 	ABI class: X.Org XInput driver, version 22.1
[    60.148] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 37 paused 0
[    60.148] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    60.148] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    60.148] (**) Option "Device" "/dev/input/event5"
[    60.176] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472 (res 65)
[    60.176] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448 (res 102)
[    60.176] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    60.176] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    60.176] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
[    60.176] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    60.176] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    60.176] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    60.176] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event5"
[    60.176] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    60.176] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    60.176] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    60.176] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.040
[    60.176] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    60.176] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    60.176] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    60.176] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    60.176] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    60.177] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    60.177] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    60.180] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)
[    60.180] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    60.181] (II) systemd-logind: got fd for /dev/input/event10 13:74 fd 38 paused 0
[    60.181] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    60.181] (**) Dell WMI hotkeys: always reports core events
[    60.181] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event10"
[    60.181] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    60.181] (--) evdev: Dell WMI hotkeys: Found keys
[    60.181] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    60.181] (**) Option "config_info" "udev:/sys/devices/virtual/input/input11/event10"
[    60.181] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    60.181] (**) Option "xkb_rules" "evdev"
[    60.181] (**) Option "xkb_model" "pc105"
[    60.181] (**) Option "xkb_layout" "us"
[    62.028] (II) evdev: Dell WMI hotkeys: Close
[    62.028] (II) UnloadModule: "evdev"
[    62.028] (II) systemd-logind: releasing fd for 13:74
[    62.044] (II) UnloadModule: "synaptics"
[    62.044] (II) systemd-logind: releasing fd for 13:69
[    62.072] (II) evdev: AT Translated Set 2 keyboard: Close
[    62.072] (II) UnloadModule: "evdev"
[    62.072] (II) systemd-logind: releasing fd for 13:67
[    62.084] (II) evdev: UVC Camera (046d:081a): Close
[    62.084] (II) UnloadModule: "evdev"
[    62.084] (II) systemd-logind: releasing fd for 13:75
[    62.108] (II) evdev: Logitech USB Receiver: Close
[    62.108] (II) UnloadModule: "evdev"
[    62.108] (II) systemd-logind: releasing fd for 13:71
[    62.120] (II) evdev: Logitech USB Receiver: Close
[    62.120] (II) UnloadModule: "evdev"
[    62.120] (II) systemd-logind: releasing fd for 13:70
[    62.132] (II) evdev: Sleep Button: Close
[    62.132] (II) UnloadModule: "evdev"
[    62.132] (II) systemd-logind: releasing fd for 13:66
[    62.144] (II) evdev: Power Button: Close
[    62.144] (II) UnloadModule: "evdev"
[    62.144] (II) systemd-logind: releasing fd for 13:65
[    62.156] (II) evdev: Video Bus: Close
[    62.156] (II) UnloadModule: "evdev"
[    62.156] (II) systemd-logind: releasing fd for 13:68
[    62.282] (II) Server terminated successfully (0). Closing log file.

```

---

### Post by again? on 2018-03-29
I believe startx no longer works because of the use of systemd.
Try 
```
systemctl start lightdm
```

No luck....
If your system is having problems with graphics display I would remove the nvidia proprietary drivers which will revert you to nouveau.
```
sudo apt purge nvidia*
sudo reboot
```

---

### Post by springshades on 2018-03-29
That 4.4.0-116 kernel is DEATH to many systems. It's shocking that they allowed it to be released.

The next time you boot, try using an older kernel and see if it fixes SOME of your issues. For whatever reason, after installing the update some of the issues have been permanent on multiple systems even if you aren't running the kernel that is responsible for it. So even if reverting to an older kernel doesn't fix everything, if it causes improvements it's still the likely culprit.

See:

[https://bugs.launchpad.net/ubuntu/+source/gcc-4.8/+bug/1750937](https://bugs.launchpad.net/ubuntu/+source/gcc-4.8/+bug/1750937)

And you'll find a bunch of other bugs related to that kernel if you google around.

Some people have managed to fix the issues by purging and reinstalling the kernel.

1) Boot with an older kernel.

2) Purge 116:

sudo apt-get purge linux-headers-4.4.0-116 linux-headers-4.4.0-116-generic

3) Reboot again (this may or may not be strictly necessary).

4) Reinstall the kernel:

sudo apt-get install linux-generic-lts-xenial

5) Reboot again to the -116 kernel.

For me, all of my machines (most of them are running Kubuntu or KDE desktop on top of something else) have needed to be updated to the hardware enablement stack to fully fix things.

1) sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04

2) reboot

The combination of that kernel and the LTS version of X must not play nicely on certain systems.


EDIT: Some further details. Some symptoms on my machines were that glxinfo couldn't even detect which nvidia card I was driving on one machine. It also caused major graphical issues (completely unusable desktop) on both an Intel graphics machine and inside of a virtual machine.

---

### Post by danielsender on 2018-03-29
My problem about booting from a different kernel is that I'm not even presented with the grub screen to make my choice. Is there a way to do it under that condition?

---

### Post by danielsender on 2018-03-29
I booted with the live CD and after mounting /dev, /proc and /sys under /mnt I did a chroot. So I ran the purging of 4.4.0-116 which apparently was successful. I rebooted the machine and the situation didn't change!!! Typing from the console the 'uname -a' it said that I was running 4.4.0-116!!! So it wasn't purged after all or am I missing something here?

---

### Post by danielsender on 2018-03-30
I just found out that my other machine, a Dell Latitude E6430, also running 16.04 was subject to the destroying features of kernel 4.4.0-116. I followed Springshades' instructions but the problem was still there. I decided to purge the Nvidia drivers and use Nouveau instead. That did the trick but only on the M90, the Latitude still refuse to boot normally. An option that is presented is to view the journalctl which is uploaded to [https://paste.ubuntu.com/p/Q4yzyQbVmx/](https://paste.ubuntu.com/p/Q4yzyQbVmx/)

Many thanks in advance.

---

### Post by danielsender on 2018-03-30
I think I fixed the Latitude. At the attempted boots I could see the message:

*ERROR* uncleared PCH fifo underrun on PCH transcoder A
and
*ERROR* PCH transcoder A FIFO underrun

I found a similar case in [https://askubuntu.com/questions/840496/startup-error-uncleared-pch-fifo-underrun-on-pch-transcoder](https://askubuntu.com/questions/840496/startup-error-uncleared-pch-fifo-underrun-on-pch-transcoder) that suggests to run fsck, which I had to do it with the live CD, and it worked!

I don't know if that problem was caused by 4.4.0-116, but in any case is something to take into account.

Thanks guys.

---

