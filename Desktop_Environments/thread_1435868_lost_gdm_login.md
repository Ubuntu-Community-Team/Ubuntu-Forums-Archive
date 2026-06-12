---
title: "lost gdm login"
date: 2010-03-22
forum: Desktop Environments
---

### Post by spec o spec on 2010-03-22
alsodear geeks,
last day i installed few gdm login windows,usplash thems,gtk thems in my ubuntu 9.10 .
all these installation files were .deb.
and i installed all together using```
 dpkg -i *.deb
```but after i restarted my computer  i am not getting the gdm login screen,instead i only get command line interface.
i tried ```
sudo dpkg-reconfigure -phigh xserver-xorg


```but it doesnt work
.when i press alt+ctrl+f7 i am getting a blank screen with a cursur blinking at the top.
also tried dpkg-reconfigure gdm


pls help me

---

### Post by dusdus on 2010-03-22
Just to be curious, why didn't you use 
```

sudo apt-get install gdm

```

because dpkg -i doesn't check all of it's depencies iirc.

Did it ever work, or is this the first time you're trying gdm?
If you use "top", does it show any Xorg process?

anyway, my suggestion is to try and remove the package gdm
```

dpkg --remove gdm

```

and reinstall it, using apt-get.

---

### Post by spec o spec on 2010-03-22
i would have if i had a working internet connection,](*,)](*,)

if there is no other ways i am going to install remastered ubuntu 9.10 :D

---

### Post by dusdus on 2010-03-22
Are you using the LiveCD?

check if the cd is added to your /etc/apt/sources.list

```

sudo apt-cdrom add
sudo apt-get update

```

and then the rest

---

### Post by spec o spec on 2010-03-23
oh thanks i havent;) even thought about it/
what if i is a poblem with display driver ?how should i configue it>?

---

### Post by dusdus on 2010-03-23
depends on what video card you use
xorg does it mostly automatically, but in some cases you need to manually install and configure the driver.

test it first, because the LiveCD works, I don't think it's a problem related to your graphics card

---

### Post by spec o spec on 2010-03-27
**additional information** on my problem

here is my xorg log



X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-24-xen i686 Ubuntu
Current Operating System: Linux spec-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 26 March 2009  03:47:28PM
xorg-server 2:1.5.2-2ubuntu3.1+ppa2 (buildd@rothera.buildd) 
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 27 13:53:05 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 8

(--) PCI:*(0@0:2:0) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0x91000000/0, 0x80000000/0, I/O @ 0x000030b0/0
(--) PCI: (0@0:2:1) Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller rev 3, Mem @ 0x91100000/0
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.5.2, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.5.2, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.6.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(EE) module ABI major version (5) doesn't match the server's version (4)
(II) UnloadModule: "intel"
(II) Unloading /usr/lib/xorg/modules/drivers//intel_drv.so
(EE) Failed to load module "intel" (module requirement mismatch, 0)
(EE) No drivers available.

Fatal server error:
no screens found

---

### Post by spec o spec on 2010-03-27
here is my x.conf file
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

