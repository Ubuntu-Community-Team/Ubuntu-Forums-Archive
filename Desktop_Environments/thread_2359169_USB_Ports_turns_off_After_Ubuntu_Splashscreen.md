---
title: "USB Ports turns off After Ubuntu Splashscreen"
date: 2017-04-21
forum: Desktop Environments
---

### Post by jonathangrice on 2017-04-21
I am developing on an AllWinner A20. It was an Android Smart TV Player with a YBKJ_A20 board. (Everyone has to start somewhere.)

This board works well with Linux distributions for the Cubietruck (Cubieboard 3). Lubuntu for Cubietruck ([cb-a20-lubuntu-desktop-card-v105.img.gz]("http://dl.cubieboard.org/software/a20-cubieboard/lubuntu/")) works flawlessly. USB, NIC, sound, video. Only thing that doesn't work is the onboard Realtek rtl8188etv wifi/bluetooth module, I've yet to compile the rtl8188eu module/driver for linux 4.4.55.

I have successfully built a bootable SD Card with, uBoot and Linux Kernel 4.4.55 compiled by [Robert Sperling]("https://www.robert-sperling.de/en/mainline-kernel-for-cubietruck/") and Ubuntu 16.04 Base, [ubuntu-base-16.04.1-base-armhf]("http://cdimage.ubuntu.com/ubuntu-base/releases/16.04/release/").

I used chroot to install various packages and added a user to log in.

The SD Card booted to the prompt and I was able to log in using the user and password that I set up using a USB keyboard that was attached to one of the two USB ports on the board.

I then proceeded to install LXDE and that's where things went wrong. I used apt-get to install lxde, xinit, and xorg. The device still boots and it displays the Ubuntu splash screen, however, after the splash screen appears, the USB keyboard does not work and the screen hangs. I have researched every possible solution to no avail. I can apt-get remove lxde xinit xorg through chroot and regain the USB keyboard.

One possible solution was to try a USB HUB. Nope. When the Ubuntu Splash Screen loads, the light on the USB HUB goes out.
Another solution was to add "quiet splash" to the environment variables for uBoot. Same result, no USB after the Ubuntu screen.

I don't understand why USB doesn't work when I install lxde. There has to be a configuration that I haven't come across to prevent the desktop environment from turning off USB.

Any help would be greatly appreciated.

---

### Post by jonathangrice on 2017-04-26
Update: After further research, I have found many people with the same  problem. The OP is hijacked on each occurrence and is directed towards  something to do with video drivers.
I have not seen a definite resolution to this problem.

As I have absolutely no keyboard or mouse control after booting the SD Card, I have to power down, remove the card and chroot to access any logs that are available from the system. 

The Xorg log is as follows.
```
[    11.351] (--) Log file renamed from "/var/log/Xorg.pid-296.log" to "/var/log/Xorg.0.log"
[    11.356] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    11.356] X Protocol Version 11, Revision 0
[    11.356] Build Operating System: Linux 4.4.0-45-generic armv7l Ubuntu
[    11.356] Current Operating System: Linux sunxi 4.4.55 #33 SMP Tue Mar 21 23:10:42 CET 2017 armv7l
[    11.356] Kernel command line: console=ttyS0,115200 earlyprintk root=/dev/mmcblk0p2 rootwait rw panic=10
[    11.356] Build Date: 02 November 2016  10:05:15PM
[    11.356] xorg-server 2:1.18.4-0ubuntu0.2 (For technical support please see http://www.ubuntu.com/support) 
[    11.356] Current version of pixman: 0.33.6
[    11.356]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    11.356] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.357] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 11 10:28:06 2016
[    11.379] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.389] (==) No Layout section.  Using the first Screen section.
[    11.389] (==) No screen section available. Using defaults.
[    11.389] (**) |-->Screen "Default Screen Section" (0)
[    11.389] (**) |   |-->Monitor "<default monitor>"
[    11.390] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    11.390] (==) Automatically adding devices
[    11.390] (==) Automatically enabling devices
[    11.390] (==) Automatically adding GPU devices
[    11.390] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    11.413] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.413]     Entry deleted from font path.
[    11.413] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.414]     Entry deleted from font path.
[    11.414] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.414]     Entry deleted from font path.
[    11.415] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.415]     Entry deleted from font path.
[    11.415] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.415]     Entry deleted from font path.
[    11.415] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    11.415] (==) ModulePath set to "/usr/lib/arm-linux-gnueabihf/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.415] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.415] (II) Loader magic: 0x7f791f70
[    11.415] (II) Module ABI versions:
[    11.415]     X.Org ANSI C Emulation: 0.4
[    11.415]     X.Org Video Driver: 20.0
[    11.415]     X.Org XInput driver : 22.1
[    11.415]     X.Org Server Extension : 9.0
[    11.418] (++) using VT number 7

[    11.418] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    11.419] (II) no primary bus or device found
[    11.419] (II) LoadModule: "glx"
[    11.439] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.528] (II) Module glx: vendor="X.Org Foundation"
[    11.528]     compiled for 1.18.4, module version = 1.0.0
[    11.528]     ABI class: X.Org Server Extension, version 9.0
[    11.528] (==) AIGLX enabled
[    11.529] (==) Matched modesetting as autoconfigured driver 0
[    11.529] (==) Matched fbdev as autoconfigured driver 1
[    11.529] (==) Assigned the driver to the xf86ConfigLayout
[    11.529] (II) LoadModule: "modesetting"
[    11.531] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    11.535] (II) Module modesetting: vendor="X.Org Foundation"
[    11.535]     compiled for 1.18.4, module version = 1.18.4
[    11.535]     Module class: X.Org Video Driver
[    11.535]     ABI class: X.Org Video Driver, version 20.0
[    11.535] (II) LoadModule: "fbdev"
[    11.537] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.539] (II) Module fbdev: vendor="X.Org Foundation"
[    11.539]     compiled for 1.18.1, module version = 0.4.4
[    11.539]     Module class: X.Org Video Driver
[    11.539]     ABI class: X.Org Video Driver, version 20.0
[    11.539] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    11.540] (II) FBDEV: driver for framebuffer: fbdev
[    11.570] (WW) Falling back to old probe method for modesetting
[    11.570] (EE) open /dev/dri/card0: No such file or directory
[    11.570] (WW) Falling back to old probe method for fbdev
[    11.570] (II) Loading sub module "fbdevhw"
[    11.571] (II) LoadModule: "fbdevhw"
[    11.571] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.577] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.577]     compiled for 1.18.4, module version = 0.0.2
[    11.577]     ABI class: X.Org Video Driver, version 20.0
[    11.578] (II) FBDEV(0): using default device
[    11.578] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[    11.578] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    11.578] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    11.578] (==) FBDEV(0): RGB weight 888
[    11.578] (==) FBDEV(0): Default visual is TrueColor
[    11.578] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    11.578] (II) FBDEV(0): hardware: simple (video memory: 5625kB)
[    11.578] (II) FBDEV(0): checking modes against framebuffer device...
[    11.578] (II) FBDEV(0): checking modes against monitor...
[    11.578] (--) FBDEV(0): Virtual size is 1600x900 (pitch 1600)
[    11.578] (**) FBDEV(0):  Built-in mode "current"
[    11.579] (==) FBDEV(0): DPI set to (96, 96)
[    11.579] (II) Loading sub module "fb"
[    11.579] (II) LoadModule: "fb"
[    11.579] (II) Loading /usr/lib/xorg/modules/libfb.so
[    11.585] (II) Module fb: vendor="X.Org Foundation"
[    11.585]     compiled for 1.18.4, module version = 1.0.0
[    11.585]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.585] (**) FBDEV(0): using shadow framebuffer
[    11.585] (II) Loading sub module "shadow"
[    11.585] (II) LoadModule: "shadow"
[    11.586] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    11.590] (II) Module shadow: vendor="X.Org Foundation"
[    11.590]     compiled for 1.18.4, module version = 1.1.0
[    11.590]     ABI class: X.Org ANSI C Emulation, version 0.4
[    11.590] (II) UnloadModule: "modesetting"
[    11.590] (II) Unloading modesetting
[    11.590] (==) Depth 24 pixmap format is 32 bpp
[    11.591] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    11.604] (==) FBDEV(0): Backing store enabled
[    11.608] (==) FBDEV(0): DPMS enabled
[    11.608] (==) RandR enabled
[    11.641] (II) SELinux: Disabled on system
[    11.646] (II) AIGLX: Screen 0 is not DRI2 capable
[    11.646] (EE) AIGLX: reverting to software rendering
[    12.754] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    12.758] (II) AIGLX: Loaded and initialized swrast
[    12.758] (II) GLX: Initialized DRISWRAST GL provider for screen 0
```


Any help would be greatly appreciated.

---

