---
title: "Booting into ttyl - Inspiron 1525"
date: 2011-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by THE_An0mOLy! on 2011-02-15
Edit - solved by a complete reinstall of ubuntu + then using compiz fusion ;D


Okay so I've tried searching and reading through a billion and one different threads about this problem/similar problems and have yet to find a working solution.

I'm new to linux, running ubuntu 10.10 on an inspiron 1525 and things were going great until I tried to install a custom login screen. After many various attempts using Gtweak, Ubuntu tweak I have successfully managed to change some sort of graphics setting resulting in only being able to boot into the ttyl CLI.

I can boot into failsafeX mode and everything works perfectly but it's a pain doing it everytime and a fix would be nice :D Preferably one that doesn't involve a clean install >_>

The main three errors I can pick out are:

open /dev/fb0: no such file or directory - ubuntu

intel(0): No kernel modesetting driver detected

Screen(s) found, but none havea usable configuration

Here is my Xorg.0.log file:
> [    49.870] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    49.870] X Protocol Version 11, Revision 0
[    49.870] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    49.870] Current Operating System: Linux nom-Inspiron-1525  2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686
[    49.871] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-25-generic root=UUID=5bc628dc-9591-4a56-b2e8-b2455fa48fee ro quiet splash nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
[    49.871] Build Date: 09 January 2011  12:14:58PM
[    49.871] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    49.871] Current version of pixman: 0.18.4
[    49.871]     Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
[    49.871] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    49.872] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 15 20:45:55 2011
[    49.872] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    49.872] (==) No Layout section.  Using the first Screen section.
[    49.872] (==) No screen section available. Using defaults.
[    49.872] (**) |-->Screen "Default Screen Section" (0)
[    49.872] (**) |   |-->Monitor "<default monitor>"
[    49.873] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    49.873] (==) Automatically adding devices
[    49.873] (==) Automatically enabling devices
[    49.873] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    49.873]     Entry deleted from font path.
[    49.873] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    49.873] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    49.873] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    49.873] (II) Loader magic: 0x81f9b00
[    49.873] (II) Module ABI versions:
[    49.873]     X.Org ANSI C Emulation: 0.4
[    49.873]     X.Org Video Driver: 8.0
[    49.873]     X.Org XInput driver : 11.0
[    49.873]     X.Org Server Extension : 4.0
[    49.875] (--) PCI:*(0:0:2:0) 8086:2a02:1028:022f rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000eff8/8
[    49.875] (--) PCI: (0:0:2:1) 8086:2a03:1028:022f rev 12, Mem @ 0xfeb00000/1048576
[    49.875] (II) Open ACPI successful (/var/run/acpid.socket)
[    49.875] (II) LoadModule: "extmod"
[    49.876] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    49.876] (II) Module extmod: vendor="X.Org Foundation"
[    49.876]     compiled for 1.9.0, module version = 1.0.0
[    49.876]     Module class: X.Org Server Extension
[    49.876]     ABI class: X.Org Server Extension, version 4.0
[    49.876] (II) Loading extension MIT-SCREEN-SAVER
[    49.876] (II) Loading extension XFree86-VidModeExtension
[    49.876] (II) Loading extension XFree86-DGA
[    49.876] (II) Loading extension DPMS
[    49.876] (II) Loading extension XVideo
[    49.876] (II) Loading extension XVideo-MotionCompensation
[    49.876] (II) Loading extension X-Resource
[    49.876] (II) LoadModule: "dbe"
[    49.877] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    49.877] (II) Module dbe: vendor="X.Org Foundation"
[    49.877]     compiled for 1.9.0, module version = 1.0.0
[    49.877]     Module class: X.Org Server Extension
[    49.877]     ABI class: X.Org Server Extension, version 4.0
[    49.877] (II) Loading extension DOUBLE-BUFFER
[    49.877] (II) LoadModule: "glx"
[    49.878] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    49.878] (II) Module glx: vendor="X.Org Foundation"
[    49.878]     compiled for 1.9.0, module version = 1.0.0
[    49.878]     ABI class: X.Org Server Extension, version 4.0
[    49.878] (==) AIGLX enabled
[    49.878] (II) Loading extension GLX
[    49.878] (II) LoadModule: "record"
[    49.878] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    49.879] (II) Module record: vendor="X.Org Foundation"
[    49.879]     compiled for 1.9.0, module version = 1.13.0
[    49.879]     Module class: X.Org Server Extension
[    49.879]     ABI class: X.Org Server Extension, version 4.0
[    49.879] (II) Loading extension RECORD
[    49.879] (II) LoadModule: "dri"
[    49.879] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    49.880] (II) Module dri: vendor="X.Org Foundation"
[    49.880]     compiled for 1.9.0, module version = 1.0.0
[    49.880]     ABI class: X.Org Server Extension, version 4.0
[    49.880] (II) Loading extension XFree86-DRI
[    49.880] (II) LoadModule: "dri2"
[    49.880] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    49.880] (II) Module dri2: vendor="X.Org Foundation"
[    49.880]     compiled for 1.9.0, module version = 1.2.0
[    49.880]     ABI class: X.Org Server Extension, version 4.0
[    49.880] (II) Loading extension DRI2
[    49.880] (==) Matched intel as autoconfigured driver 0
[    49.880] (==) Matched vesa as autoconfigured driver 1
[    49.880] (==) Matched fbdev as autoconfigured driver 2
[    49.880] (==) Assigned the driver to the xf86ConfigLayout
[    49.880] (II) LoadModule: "intel"
[    49.881] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    49.881] (II) Module intel: vendor="X.Org Foundation"
[    49.881]     compiled for 1.9.0, module version = 2.12.0
[    49.881]     Module class: X.Org Video Driver
[    49.881]     ABI class: X.Org Video Driver, version 8.0
[    49.881] (II) LoadModule: "vesa"
[    49.882] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    49.882] (II) Module vesa: vendor="X.Org Foundation"
[    49.882]     compiled for 1.8.99.905, module version = 2.3.0
[    49.882]     Module class: X.Org Video Driver
[    49.882]     ABI class: X.Org Video Driver, version 8.0
[    49.882] (II) LoadModule: "fbdev"
[    49.882] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    49.882] (II) Module fbdev: vendor="X.Org Foundation"
[    49.882]     compiled for 1.8.99.905, module version = 0.4.2
[    49.882]     ABI class: X.Org Video Driver, version 8.0
[    49.882] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[    49.883] (II) VESA: driver for VESA chipsets: vesa
[    49.883] (II) FBDEV: driver for framebuffer: fbdev
[    49.883] (--) using VT number 8

[    49.888] (WW) Falling back to old probe method for vesa
[    49.888] (WW) Falling back to old probe method for fbdev
[    49.888] (II) Loading sub module "fbdevhw"
[    49.888] (II) LoadModule: "fbdevhw"
[    49.889] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    49.889] (II) Module fbdevhw: vendor="X.Org Foundation"
[    49.889]     compiled for 1.9.0, module version = 0.0.2
[    49.889]     ABI class: X.Org Video Driver, version 8.0
[    49.893] (EE) intel(0): No kernel modesetting driver detected.
[    49.893] (II) UnloadModule: "intel"
[    49.893] (EE) Screen(s) found, but none have a usable configuration.
[    49.893] 
Fatal server error:
[    49.893] no screens found
[    49.893] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 
[    49.893] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    49.893] 
[    50.034]  ddxSigGiveUp: Closing log

Any help would be greatly appreciated :D

---

