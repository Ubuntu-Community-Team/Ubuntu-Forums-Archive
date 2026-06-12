---
title: "Some Xorg problems..."
date: 2011-10-28
forum: Desktop Environments
---

### Post by Aurauxis on 2011-10-28
I have an Ubuntu 10.10 installation on an external 500 GB. I installed it on an external hard drive with the intention do boot it from other desktops. But when the time to use it somewhere else came I got a xorg fatal error: No screens found. After messing around, I would sometimes get fatal error: Screens found but none have a usable configuration or something. I know it is just a quick fix but I seem to be the only one with the problem. All help greatly appreciated.

Before you ask...

Config
```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
    SubSection "Display"
        Virtual    3280 1200
    EndSubSection
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

```Log...
```

[    21.034] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    21.034] X Protocol Version 11, Revision 0
[    21.034] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[    21.034] Current Operating System: Linux Snow-Leopard 2.6.35-30-generic #60-Ubuntu SMP Mon Sep 19 20:45:08 UTC 2011 i686
[    21.034] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-30-generic root=UUID=b1f4fc87-b02b-4e95-8897-d71ecd526f11 ro splash vga=771 quiet quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
[    21.034] Build Date: 09 January 2011  12:14:58PM
[    21.035] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    21.035] Current version of pixman: 0.18.4
[    21.035]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    21.035] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.035] (==) Log file: "/var/log/Xorg.5.log", Time: Sat Oct 15 20:34:22 2011
[    21.035] (==) Using config file: "/etc/X11/xorg.conf"
[    21.035] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.036] (==) No Layout section.  Using the first Screen section.
[    21.036] (**) |-->Screen "Default Screen" (0)
[    21.036] (**) |   |-->Monitor "<default monitor>"
[    21.037] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    21.037] (**) |   |-->Device "Default Device"
[    21.037] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    21.037] (==) Automatically adding devices
[    21.037] (==) Automatically enabling devices
[    21.037] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.037]     Entry deleted from font path.
[    21.037] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    21.037] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.037] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    21.037] (II) Loader magic: 0x81f9b00
[    21.038] (II) Module ABI versions:
[    21.038]     X.Org ANSI C Emulation: 0.4
[    21.038]     X.Org Video Driver: 8.0
[    21.038]     X.Org XInput driver : 11.0
[    21.038]     X.Org Server Extension : 4.0
[    21.039] (--) PCI:*(0:0:2:0) 8086:a011:1179:ff30 rev 0, Mem @ 0xf0200000/524288, 0xd0000000/268435456, 0xf0000000/1048576, I/O @ 0x000018d0/8
[    21.039] (--) PCI: (0:0:2:1) 8086:a012:1179:ff30 rev 0, Mem @ 0xf0280000/524288
[    21.040] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.040] (II) "extmod" will be loaded by default.
[    21.040] (II) "dbe" will be loaded by default.
[    21.040] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    21.040] (II) "record" will be loaded by default.
[    21.040] (II) "dri" will be loaded by default.
[    21.040] (II) "dri2" will be loaded by default.
[    21.040] (II) LoadModule: "glx"
[    21.041] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    21.042] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    21.042]     compiled for 7.6.0, module version = 1.0.0
[    21.042] (II) Loading extension GLX
[    21.042] (II) LoadModule: "extmod"
[    21.043] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.043] (II) Module extmod: vendor="X.Org Foundation"
[    21.043]     compiled for 1.9.0, module version = 1.0.0
[    21.043]     Module class: X.Org Server Extension
[    21.043]     ABI class: X.Org Server Extension, version 4.0
[    21.043] (II) Loading extension MIT-SCREEN-SAVER
[    21.043] (II) Loading extension XFree86-VidModeExtension
[    21.043] (II) Loading extension XFree86-DGA
[    21.044] (II) Loading extension DPMS
[    21.044] (II) Loading extension XVideo
[    21.044] (II) Loading extension XVideo-MotionCompensation
[    21.044] (II) Loading extension X-Resource
[    21.044] (II) LoadModule: "dbe"
[    21.044] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.045] (II) Module dbe: vendor="X.Org Foundation"
[    21.045]     compiled for 1.9.0, module version = 1.0.0
[    21.045]     Module class: X.Org Server Extension
[    21.045]     ABI class: X.Org Server Extension, version 4.0
[    21.045] (II) Loading extension DOUBLE-BUFFER
[    21.045] (II) LoadModule: "record"
[    21.046] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.046] (II) Module record: vendor="X.Org Foundation"
[    21.046]     compiled for 1.9.0, module version = 1.13.0
[    21.046]     Module class: X.Org Server Extension
[    21.046]     ABI class: X.Org Server Extension, version 4.0
[    21.046] (II) Loading extension RECORD
[    21.046] (II) LoadModule: "dri"
[    21.047] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.047] (II) Module dri: vendor="X.Org Foundation"
[    21.047]     compiled for 1.9.0, module version = 1.0.0
[    21.047]     ABI class: X.Org Server Extension, version 4.0
[    21.047] (II) Loading extension XFree86-DRI
[    21.047] (II) LoadModule: "dri2"
[    21.048] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.048] (II) Module dri2: vendor="X.Org Foundation"
[    21.048]     compiled for 1.9.0, module version = 1.2.0
[    21.048]     ABI class: X.Org Server Extension, version 4.0
[    21.049] (II) Loading extension DRI2
[    21.049] (II) LoadModule: "fglrx"
[    21.049] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    21.104] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    21.104]     compiled for 1.4.99.906, module version = 8.78.30
[    21.105]     Module class: X.Org Video Driver
[    21.105] (II) Loading sub module "fglrxdrm"
[    21.105] (II) LoadModule: "fglrxdrm"
[    21.106] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    21.106] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    21.106]     compiled for 1.8.99.905, module version = 8.78.30
[    21.106] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    21.106] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    21.106] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:30:49
[    21.107] (--) using VT number 8

[    21.109] (WW) Falling back to old probe method for fglrx
[    21.109] (EE) No supported AMD display adapters were found
[    21.109] (EE) No devices detected.
[    21.109] 
Fatal server error:
[    21.109] no screens found
[    21.109] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    21.109] Please also check the log file at "/var/log/Xorg.5.log" for additional information.
[    21.110] 

```

---

### Post by Aurauxis on 2011-10-29
Cookies.

---

### Post by typhoon_tip on 2011-10-29
That's very easy, you have installed an ATI proprietary driver, making that install start only on a Desktop or Laptop that has ATI video card of any sort. To fix the issue, start Ubuntu into the original PC that you used with ATI video card, and run the following commands (ALL of them):

```
$ sudo sh /usr/share/ati/fglrx-uninstall.sh *(if you get "Command not found", it doesn't matter !)*
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Restart to make sure the PC starts, and ignore if it asks you to install any proprietary video driver.

---

### Post by Aurauxis on 2011-10-29
But doing so would render the graphics card useless... :(

---

### Post by typhoon_tip on 2011-10-29
> **Aurauxis said:**
> But doing so would render the graphics card useless... :(

Possible. I would suggest you to go for Ubuntu 11.10, which supports 2D acceleration and 3D on the stock ATI driver, you don't need to use fglrx unless you play games with heavy requirements (games also work on stock drivers, albeit frame rate is a bit slow). Give it a try if you have another HD, do a fresh install of 11.10 and try it out with stock driver and bring it to other desktops as well. ;)

---

### Post by Aurauxis on 2011-10-30
Please... no Unity for me... yet. 11.10 is probably great but for me, Maverick is just perfect. I don't want to bother with the upgrade.       
Also, I have a few other problems, maybe you could help me out. First, I was preforming an update one that included a kernel update. It froze while generating a grub menu... looking for initrd kind of thing. So I had to kill the process. I restarted and did a partial upgrade but it froze again. I think it is because I have a faulty OS on the harddrive and thats where it freezes. I don't need even need those OSs on the grub menu, any way I could bypass them? And second, [http://ubuntuforums.org/showthread.php?t=1832914](http://ubuntuforums.org/showthread.php?t=1832914)  
I feel ignored...

---

### Post by Aurauxis on 2011-10-30
I there any way I could have multiple configs? Like one with driver and one without. I know it has the potential.

---

### Post by Aurauxis on 2011-11-04
Nobody?

---

