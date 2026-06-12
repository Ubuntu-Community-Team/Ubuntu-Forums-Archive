---
title: "can not start GUI"
date: 2017-07-24
forum: Desktop Environments
---

### Post by vanili on 2017-07-24
Hi all,

after installing xen-hypervisor-amd64 and booting xen kernal GUI does not want to start. In fact Xen did not want to start at all before I added nomodeset option to the grub, after it starts but without GUI. 

Xorg.log
```
[   148.112] Kernel command line: placeholder root=UUID=91d6a877-ee7c-4671-bfa3-6dc1fe487de7 ro quiet splash nomodeset
[   148.112] Build Date: 28 March 2017  06:16:52AM
[   148.112] xorg-server 2:1.19.3-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[   148.113] Current version of pixman: 0.34.0
[   148.113]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   148.113] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   148.113] (==) Log file: "/home/epitt/.local/share/xorg/Xorg.0.log", Time: Mon Jul 24 13:45:16 2017
[   148.114] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   148.114] (==) No Layout section.  Using the first Screen section.
[   148.114] (==) No screen section available. Using defaults.
[   148.114] (**) |-->Screen "Default Screen Section" (0)
[   148.114] (**) |   |-->Monitor "<default monitor>"
[   148.114] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   148.114] (==) Automatically adding devices
[   148.114] (==) Automatically enabling devices
[   148.114] (==) Automatically adding GPU devices
[   148.114] (==) Automatically binding GPU devices
[   148.114] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   148.114] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   148.114]     Entry deleted from font path.
[   148.114] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   148.115]     Entry deleted from font path.
[   148.115] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   148.115]     Entry deleted from font path.
[   148.115] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   148.115]     Entry deleted from font path.
[   148.115] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   148.115]     Entry deleted from font path.
[   148.115] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   148.115] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   148.115] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   148.115] (II) Loader magic: 0x55e12552d020
[   148.115] (II) Module ABI versions:
[   148.115]     X.Org ANSI C Emulation: 0.4
[   148.115]     X.Org Video Driver: 23.0
[   148.115]     X.Org XInput driver : 24.1
[   148.115]     X.Org Server Extension : 10.0
[   148.116] (++) using VT number 1

[   148.119] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_31
[   148.122] (--) PCI:*(0:0:2:0) 8086:2e12:17aa:3047 rev 3, Mem @ 0xfc000000/4194304, 0xe0000000/268435456, I/O @ 0x00001c70/8, BIOS @ 0x????????/131072
[   148.122] (--) PCI: (0:0:2:1) 8086:2e13:17aa:3047 rev 3, Mem @ 0xfc400000/1048576
[   148.122] (II) LoadModule: "glx"
[   148.123] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   148.125] (II) Module glx: vendor="X.Org Foundation"
[   148.125]     compiled for 1.19.3, module version = 1.0.0
[   148.125]     ABI class: X.Org Server Extension, version 10.0
[   148.125] (==) Matched modesetting as autoconfigured driver 0
[   148.125] (==) Matched fbdev as autoconfigured driver 1
[   148.125] (==) Matched vesa as autoconfigured driver 2
[   148.125] (==) Assigned the driver to the xf86ConfigLayout
[   148.125] (II) LoadModule: "modesetting"
[   148.125] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   148.125] (II) Module modesetting: vendor="X.Org Foundation"
[   148.125]     compiled for 1.19.3, module version = 1.19.3
[   148.125]     Module class: X.Org Video Driver
[   148.125]     ABI class: X.Org Video Driver, version 23.0
[   148.126] (II) LoadModule: "fbdev"
[   148.126] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   148.126] (II) Module fbdev: vendor="X.Org Foundation"
[   148.126]     compiled for 1.19.3, module version = 0.4.4
[   148.126]     Module class: X.Org Video Driver
[   148.126]     ABI class: X.Org Video Driver, version 23.0
[   148.126] (II) LoadModule: "vesa"
[   148.126] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   148.126] (II) Module vesa: vendor="X.Org Foundation"
[   148.126]     compiled for 1.19.3, module version = 2.3.4
[   148.126]     Module class: X.Org Video Driver
[   148.126]     ABI class: X.Org Video Driver, version 23.0
[   148.126] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   148.126] (II) FBDEV: driver for framebuffer: fbdev
[   148.126] (II) VESA: driver for VESA chipsets: vesa
[   148.127] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[   148.127] (EE) open /dev/dri/card0: No such file or directory
[   148.127] (WW) Falling back to old probe method for modesetting
[   148.127] (EE) open /dev/dri/card0: No such file or directory
[   148.127] (II) Loading sub module "fbdevhw"
[   148.127] (II) LoadModule: "fbdevhw"
[   148.127] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   148.127] (II) Module fbdevhw: vendor="X.Org Foundation"
[   148.127]     compiled for 1.19.3, module version = 0.0.2
[   148.127]     ABI class: X.Org Video Driver, version 23.0
[   148.127] (EE) open /dev/fb0: No such file or directory
[   148.127] (WW) Falling back to old probe method for fbdev
[   148.127] (II) Loading sub module "fbdevhw"
[   148.127] (II) LoadModule: "fbdevhw"
[   148.127] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   148.127] (II) Module fbdevhw: vendor="X.Org Foundation"
[   148.127]     compiled for 1.19.3, module version = 0.0.2
[   148.127]     ABI class: X.Org Video Driver, version 23.0
[   148.127] (EE) open /dev/fb0: No such file or directory
[   148.127] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[   148.127] (EE) Screen 0 deleted because of no matching config section.
[   148.127] (II) UnloadModule: "modesetting"
[   148.127] (EE) Screen 0 deleted because of no matching config section.
[   148.127] (II) UnloadModule: "fbdev"
[   148.127] (II) UnloadSubModule: "fbdevhw"
[   148.127] (II) Loading sub module "vbe"
[   148.127] (II) LoadModule: "vbe"
[   148.128] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   148.128] (II) Module vbe: vendor="X.Org Foundation"
[   148.128]     compiled for 1.19.3, module version = 1.1.0
[   148.128]     ABI class: X.Org Video Driver, version 23.0
[   148.128] (II) Loading sub module "int10"
[   148.128] (II) LoadModule: "int10"
[   148.128] (II) Loading /usr/lib/xorg/modules/libint10.so
[   148.128] (II) Module int10: vendor="X.Org Foundation"
[   148.128]     compiled for 1.19.3, module version = 1.0.0
[   148.128]     ABI class: X.Org Video Driver, version 23.0
[   148.128] (II) VESA(0): initializing int10
[   148.128] (EE) VESA(0): Cannot read int vect
[   148.128] (II) UnloadModule: "vesa"
[   148.128] (II) UnloadSubModule: "int10"
[   148.129] (II) Unloading int10
[   148.129] (II) UnloadSubModule: "vbe"
[   148.129] (II) Unloading vbe
[   148.129] (EE) Screen(s) found, but none have a usable configuration.
[   148.129] (EE) 
Fatal server error:
[   148.129] (EE) no screens found(EE) 
[   148.129] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   148.129] (EE) Please also check the log file at "/home/epitt/.local/share/xorg/Xorg.0.log" for additional information.
[   148.129] (EE) 
[   148.130] (EE) Server terminated with error (1). Closing log file.
```

I already tried startx and X -configure, it gave no result...

Any other option to try?

Thanks in advance

---

