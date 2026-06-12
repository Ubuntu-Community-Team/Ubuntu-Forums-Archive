---
title: "can't get the right resolution"
date: 2013-10-22
forum: Desktop Environments
---

### Post by danielsender on 2013-10-22
The problem I'm having actually consists in two parts. I had a perfectly running 13.04 system on my Dell M50 laptop, that has an nvidia GeForce graphic card. The other day I decided to upgrade to 13.10, process that went well. However at the step of rebooting the machine it would do it coming out with an error that I already posted in the update/upgrade forum ( [http://ubuntuforums.org/showthread.php?t=2181785&page=2&p=12823645#post12823645](http://ubuntuforums.org/showthread.php?t=2181785&page=2&p=12823645#post12823645) ). On the other hand, I booted an older kernel without problems. Going back to the new kernel and thinking that it was a initramfs issue I ran 'update-initramfs -c -k all'. That didn't do it, and furthermore it did something that prevented me from booting from the old kernel either. So I re-installed grub, and that again allow me to boot the older kernels (but not the new one). But the problem now is that when booting from these old kernels the maximum resolution is 1024x768 instead of what my screen is 1600x1200. I don't have any /etc/X11/xorg.conf file on the system. I know that I can perhaps fix it with xrandr on an user by user basis, but I would also like to know where in the system there is a "knob" that can revert the system to its previous operating condition.

Daniel

---

### Post by danielsender on 2013-10-23
> **danielsender said:**
> The problem I'm having actually consists in two parts. I had a perfectly running 13.04 system on my Dell M50 laptop, that has an nvidia GeForce graphic card. The other day I decided to upgrade to 13.10, process that went well. However at the step of rebooting the machine it would do it coming out with an error that I already posted in the update/upgrade forum ( [http://ubuntuforums.org/showthread.php?t=2181785&page=2&p=12823645#post12823645](http://ubuntuforums.org/showthread.php?t=2181785&page=2&p=12823645#post12823645) ). On the other hand, I booted an older kernel without problems. Going back to the new kernel and thinking that it was a initramfs issue I ran 'update-initramfs -c -k all'. That didn't do it, and furthermore it did something that prevented me from booting from the old kernel either. So I re-installed grub, and that again allow me to boot the older kernels (but not the new one). But the problem now is that when booting from these old kernels the maximum resolution is 1024x768 instead of what my screen is 1600x1200. I don't have any /etc/X11/xorg.conf file on the system. I know that I can perhaps fix it with xrandr on an user by user basis, but I would also like to know where in the system there is a "knob" that can revert the system to its previous operating condition.

Daniel

I suspect that is something related to not being able to load the nouveau driver and using the vesa driver. I can't decypher the Xorg.0.log file, can someone help me?
```
[    38.262]
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    38.262] X Protocol Version 11, Revision 0
[    38.262] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    38.262] Current Operating System: Linux kidhug 3.9.0-030900rc6-generic #201304080035 SMP Mon Apr 8 04:44:54 UTC 2013 i686
[    38.262] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.9.0-030900rc6-generic root=UUID=67e485e0-aa01-44ad-b18f-48462d9c906e ro quiet splash vt.handoff=7
[    38.262] Build Date: 15 October 2013  09:23:29AM
[    38.262] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support)
[    38.262] Current version of pixman: 0.30.2
[    38.262]    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    38.262] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.262] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 22 22:16:05 2013
[    38.289] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    38.290] (==) No Layout section.  Using the first Screen section.
[    38.290] (==) No screen section available. Using defaults.
[    38.290] (**) |-->Screen "Default Screen Section" (0)
[    38.290] (**) |   |-->Monitor "<default monitor>"
[    38.290] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    38.290] (==) Automatically adding devices
[    38.290] (==) Automatically enabling devices
[    38.290] (==) Automatically adding GPU devices
[    38.290] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.290]    Entry deleted from font path.
[    38.290] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.290]    Entry deleted from font path.
[    38.290] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.290]    Entry deleted from font path.
[    38.291] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.291]    Entry deleted from font path.
[    38.291] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.291]    Entry deleted from font path.
[    38.291] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    38.291] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    38.291] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    38.291] (II) Loader magic: 0xb77936a0
[    38.291] (II) Module ABI versions:
[    38.291]    X.Org ANSI C Emulation: 0.4
[    38.291]    X.Org Video Driver: 14.1
[    38.291]    X.Org XInput driver : 19.1
[    38.291]    X.Org Server Extension : 7.0
[    38.306] (--) PCI:*(0:1:0:0) 10de:017c:1028:00d5 rev 163, Mem @ 0xfc000000/16777216, 0xe0000000/134217728, 0xdff80000/524288, BIOS @ 0x????????/131072
[    38.321] (II) Open ACPI successful (/var/run/acpid.socket)
[    38.321] Initializing built-in extension Generic Event Extension
[    38.321] Initializing built-in extension SHAPE
[    38.321] Initializing built-in extension MIT-SHM
[    38.321] Initializing built-in extension XInputExtension
[    38.321] Initializing built-in extension XTEST
[    38.321] Initializing built-in extension BIG-REQUESTS
[    38.321] Initializing built-in extension SYNC
[    38.321] Initializing built-in extension XKEYBOARD
[    38.321] Initializing built-in extension XC-MISC
[    38.321] Initializing built-in extension SECURITY
[    38.321] Initializing built-in extension XINERAMA
[    38.321] Initializing built-in extension XFIXES
[    38.321] Initializing built-in extension RENDER
[    38.321] Initializing built-in extension RANDR
[    38.322] Initializing built-in extension COMPOSITE
[    38.322] Initializing built-in extension DAMAGE
[    38.322] Initializing built-in extension MIT-SCREEN-SAVER
[    38.322] Initializing built-in extension DOUBLE-BUFFER
[    38.328] Initializing built-in extension RECORD
[    38.328] Initializing built-in extension DPMS
[    38.328] Initializing built-in extension X-Resource
[    38.328] Initializing built-in extension XVideo
[    38.328] Initializing built-in extension XVideo-MotionCompensation
[    38.328] Initializing built-in extension SELinux
[    38.328] Initializing built-in extension XFree86-VidModeExtension
[    38.328] Initializing built-in extension XFree86-DGA
[    38.328] Initializing built-in extension XFree86-DRI
[    38.328] Initializing built-in extension DRI2
[    38.328] (II) "glx" will be loaded by default.
[    38.328] (WW) "xmir" is not to be loaded by default. Skipping.
[    38.328] (II) LoadModule: "dri2"
[    38.329] (II) Module "dri2" already built-in
[    38.329] (II) LoadModule: "glamoregl"
[    38.391] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    39.061] (II) Module glamoregl: vendor="X.Org Foundation"
[    39.061]    compiled for 1.14.2.901, module version = 0.5.1
[    39.061]    ABI class: X.Org ANSI C Emulation, version 0.4
[    39.061] (II) LoadModule: "glx"
[    39.062] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    39.062] (II) Module glx: vendor="X.Org Foundation"
[    39.062]    compiled for 1.14.3, module version = 1.0.0
[    39.062]    ABI class: X.Org Server Extension, version 7.0
[    39.062] (==) AIGLX enabled
[    39.062] Loading extension GLX
[    39.062] (==) Matched nvidia as autoconfigured driver 0
[    39.062] (==) Matched nouveau as autoconfigured driver 1
[    39.062] (==) Matched vesa as autoconfigured driver 2
[    39.062] (==) Matched modesetting as autoconfigured driver 3
[    39.062] (==) Matched fbdev as autoconfigured driver 4
[    39.062] (==) Assigned the driver to the xf86ConfigLayout
[    39.062] (II) LoadModule: "nvidia"
[    39.082] (WW) Warning, couldn't open module nvidia
[    39.082] (II) UnloadModule: "nvidia"
[    39.082] (II) Unloading nvidia
[    39.082] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    39.082] (II) LoadModule: "nouveau"
[    39.082] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    39.118] (II) Module nouveau: vendor="X.Org Foundation"
[    39.118]    compiled for 1.14.2.901, module version = 1.0.9
[    39.118]    Module class: X.Org Video Driver
[    39.118]    ABI class: X.Org Video Driver, version 14.1
[    39.118] (II) LoadModule: "vesa"
[    39.119] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    39.119] (II) Module vesa: vendor="X.Org Foundation"
[    39.119]    compiled for 1.14.1, module version = 2.3.2
[    39.119]    Module class: X.Org Video Driver
[    39.119]    ABI class: X.Org Video Driver, version 14.1
[    39.119] (II) LoadModule: "modesetting"
[    39.120] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    39.120] (II) Module modesetting: vendor="X.Org Foundation"
[    39.120]    compiled for 1.14.1, module version = 0.8.0
[    39.120]    Module class: X.Org Video Driver
[    39.120]    ABI class: X.Org Video Driver, version 14.1
[    39.120] (II) LoadModule: "fbdev"
[    39.121] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    39.121] (II) Module fbdev: vendor="X.Org Foundation"
[    39.121]    compiled for 1.14.1, module version = 0.4.3
[    39.121]    Module class: X.Org Video Driver
[    39.121]    ABI class: X.Org Video Driver, version 14.1
[    39.121] (==) Matched nvidia as autoconfigured driver 0
[    39.121] (==) Matched nouveau as autoconfigured driver 1
[    39.121] (==) Matched vesa as autoconfigured driver 2
[    39.121] (==) Matched modesetting as autoconfigured driver 3
[    39.121] (==) Matched fbdev as autoconfigured driver 4
[    39.121] (==) Assigned the driver to the xf86ConfigLayout
[    39.121] (II) LoadModule: "nvidia"
[    39.122] (WW) Warning, couldn't open module nvidia
[    39.122] (II) UnloadModule: "nvidia"
[    39.122] (II) Unloading nvidia
[    39.122] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    39.122] (II) LoadModule: "nouveau"
[    39.123] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    39.123] (II) Module nouveau: vendor="X.Org Foundation"
[    39.123]    compiled for 1.14.2.901, module version = 1.0.9
[    39.123]    Module class: X.Org Video Driver
[    39.123]    ABI class: X.Org Video Driver, version 14.1
[    39.123] (II) UnloadModule: "nouveau"
[    39.123] (II) Unloading nouveau
[    39.123] (II) Failed to load module "nouveau" (already loaded, 0)
[    39.123] (II) LoadModule: "vesa"
[    39.156] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    39.156] (II) Module vesa: vendor="X.Org Foundation"
[    39.156]    compiled for 1.14.1, module version = 2.3.2
[    39.156]    Module class: X.Org Video Driver
[    39.156]    ABI class: X.Org Video Driver, version 14.1
[    39.156] (II) UnloadModule: "vesa"
[    39.156] (II) Unloading vesa
[    39.156] (II) Failed to load module "vesa" (already loaded, 0)
[    39.156] (II) LoadModule: "modesetting"
[    39.157] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    39.157] (II) Module modesetting: vendor="X.Org Foundation"
[    39.157]    compiled for 1.14.1, module version = 0.8.0
[    39.157]    Module class: X.Org Video Driver
[    39.157]    ABI class: X.Org Video Driver, version 14.1
[    39.157] (II) UnloadModule: "modesetting"
[    39.157] (II) Unloading modesetting
[    39.157] (II) Failed to load module "modesetting" (already loaded, 0)
[    39.157] (II) LoadModule: "fbdev"
[    39.158] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    39.158] (II) Module fbdev: vendor="X.Org Foundation"
[    39.158]    compiled for 1.14.1, module version = 0.4.3
[    39.158]    Module class: X.Org Video Driver
[    39.158]    ABI class: X.Org Video Driver, version 14.1
[    39.158] (II) UnloadModule: "fbdev"
[    39.158] (II) Unloading fbdev
[    39.158] (II) Failed to load module "fbdev" (already loaded, 0)
[    39.158] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[    39.158] (II) NOUVEAU driver for NVIDIA chipset families :
[    39.158]    RIVA TNT        (NV04)
[    39.158]    RIVA TNT2       (NV05)
[    39.158]    GeForce 256     (NV10)
[    39.158]    GeForce 2       (NV11, NV15)
[    39.158]    GeForce 4MX     (NV17, NV18)
[    39.158]    GeForce 3       (NV20)
[    39.158]    GeForce 4Ti     (NV25, NV28)
[    39.158]    GeForce FX      (NV3x)
[    39.158]    GeForce 6       (NV4x)
[    39.158]    GeForce 7       (G7x)
[    39.159]    GeForce 8       (G8x)
[    39.159]    GeForce GTX 200 (NVA0)
[    39.159]    GeForce GTX 400 (NVC0)
[    39.159] (II) VESA: driver for VESA chipsets: vesa
[    39.159] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    39.159] (II) FBDEV: driver for framebuffer: fbdev
[    39.159] (++) using VT number 7

[    39.159] (EE) [drm] KMS not enabled
[    39.159] (EE) [drm] KMS not enabled
[    39.159] (WW) Falling back to old probe method for modesetting
[    39.160] (EE) open /dev/dri/card0: No such file or directory
[    39.160] (EE) open /dev/dri/card0: No such file or directory
[    39.160] (WW) Falling back to old probe method for fbdev
[    39.160] (II) Loading sub module "fbdevhw"
[    39.160] (II) LoadModule: "fbdevhw"
[    39.160] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    39.161] (II) Module fbdevhw: vendor="X.Org Foundation"
[    39.161]    compiled for 1.14.3, module version = 0.0.2
[    39.161]    ABI class: X.Org Video Driver, version 14.1
[    39.161] (EE) open /dev/fb0: No such file or directory
[    39.161] (II) Loading sub module "vbe"
[    39.161] (II) LoadModule: "vbe"
[    39.161] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    39.162] (II) Module vbe: vendor="X.Org Foundation"
[    39.162]    compiled for 1.14.3, module version = 1.1.0
[    39.162]    ABI class: X.Org Video Driver, version 14.1
[    39.162] (II) Loading sub module "int10"
[    39.162] (II) LoadModule: "int10"
[    39.163] (II) Loading /usr/lib/xorg/modules/libint10.so
[    39.163] (II) Module int10: vendor="X.Org Foundation"
[    39.176]    compiled for 1.14.3, module version = 1.0.0
[    39.176]    ABI class: X.Org Video Driver, version 14.1
[    39.176] (II) VESA(0): initializing int10
[    39.177] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    39.266] (II) VESA(0): VESA BIOS detected
[    39.266] (II) VESA(0): VESA VBE Version 3.0
[    39.266] (II) VESA(0): VESA VBE Total Mem: 65536 kB
[    39.266] (II) VESA(0): VESA VBE OEM: NVidia
[    39.266] (II) VESA(0): VESA VBE OEM Software Rev: 4.23
[    39.266] (II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
[    39.266] (II) VESA(0): VESA VBE OEM Product: NV17 () Board
[    39.266] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A2
[    39.526] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    39.526] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    39.526] (==) VESA(0): RGB weight 888
[    39.526] (==) VESA(0): Default visual is TrueColor
[    39.526] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    39.526] (II) Loading sub module "ddc"
[    39.526] (II) LoadModule: "ddc"
[    39.526] (II) Module "ddc" already built-in
[    39.779] (II) VESA(0): VESA VBE DDC supported
[    39.779] (II) VESA(0): VESA VBE DDC Level 2
[    39.779] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    40.290] (II) VESA(0): VESA VBE DDC read successfully
[    40.291] (II) VESA(0): Manufacturer: DEL  Model: a002  Serial#: 808993100
[    40.291] (II) VESA(0): Year: 2003  Week: 35
[    40.291] (II) VESA(0): EDID Version: 1.3
[    40.291] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    40.291] (II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
[    40.291] (II) VESA(0): Max Image Size [cm]: horiz.: 41  vert.: 31
[    40.291] (II) VESA(0): Gamma: 2.50
[    40.291] (II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    40.291] (II) VESA(0): First detailed timing is preferred mode
[    40.291] (II) VESA(0): redX: 0.630 redY: 0.340   greenX: 0.300 greenY: 0.590
[    40.291] (II) VESA(0): blueX: 0.149 blueY: 0.109   whiteX: 0.312 whiteY: 0.328
[    40.291] (II) VESA(0): Supported established timings:
[    40.291] (II) VESA(0): 720x400@70Hz
[    40.291] (II) VESA(0): 640x480@60Hz
[    40.291] (II) VESA(0): 640x480@75Hz
[    40.291] (II) VESA(0): 800x600@60Hz
[    40.291] (II) VESA(0): 800x600@75Hz
[    40.291] (II) VESA(0): 1024x768@60Hz
[    40.291] (II) VESA(0): 1024x768@75Hz
[    40.291] (II) VESA(0): 1280x1024@75Hz
[    40.291] (II) VESA(0): Manufacturer's mask: 0
[    40.291] (II) VESA(0): Supported standard timings:
[    40.291] (II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    40.291] (II) VESA(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    40.291] (II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    40.291] (II) VESA(0): Supported detailed timing:
[    40.291] (II) VESA(0): clock: 162.0 MHz   Image Size:  367 x 275 mm
[    40.291] (II) VESA(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
[    40.291] (II) VESA(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
[    40.291] (II) VESA(0): Serial No: 9E24938S08AL0
[    40.291] (II) VESA(0): Monitor name: DELL 2000FP
[    40.291] (II) VESA(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 165 MHz
[    40.291] (II) VESA(0): EDID (in hex):
[    40.318] (II) VESA(0):  00ffffffffffff0010ac02a04c413830
[    40.318] (II) VESA(0):  230d01030e291f96ea4c40a1574c9726
[    40.318] (II) VESA(0):  1c5054a54b008180a940714f01010101
[    40.318] (II) VESA(0):  010101010101483f403062b0324040c0
[    40.318] (II) VESA(0):  13006f131100001e000000ff00394532
[    40.318] (II) VESA(0):  34393338533038414c30000000fc0044
[    40.318] (II) VESA(0):  454c4c203230303046500a20000000fd
[    40.318] (II) VESA(0):  00384c1f5010000a20202020202000f1
[    40.318] (II) VESA(0): EDID vendor "DEL", prod id 40962
[    40.318] (II) VESA(0): Using EDID range info for horizontal sync
[    40.318] (II) VESA(0): Using EDID range info for vertical refresh
[    40.318] (II) VESA(0): Printing DDC gathered Modelines:
[    40.318] (II) VESA(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz eP)
[    40.318] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.318] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    40.318] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    40.318] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    40.318] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    40.319] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    40.319] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.319] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    40.319] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    40.319] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    40.319] (II) VESA(0): Searching for matching VESA mode(s):
[    40.333] Mode: 100 (640x400)
[    40.333]    ModeAttributes: 0x39f
[    40.333]    WinAAttributes: 0x7
[    40.333]    WinBAttributes: 0x0
[    40.333]    WinGranularity: 64
[    40.333]    WinSize: 64
[    40.333]    WinASegment: 0xa000
[    40.333]    WinBSegment: 0x0
[    40.333]    WinFuncPtr: 0xc000a4ae
[    40.333]    BytesPerScanline: 640
[    40.333]    XResolution: 640
[    40.333]    YResolution: 400
[    40.333]    XCharSize: 8
[    40.333]    YCharSize: 16
[    40.333]    NumberOfPlanes: 1
[    40.333]    BitsPerPixel: 8
[    40.333]    NumberOfBanks: 1
[    40.333]    MemoryModel: 4
[    40.333]    BankSize: 0
[    40.333]    NumberOfImages: 14
[    40.333]    RedMaskSize: 0
[    40.333]    RedFieldPosition: 0
[    40.333]    GreenMaskSize: 0
[    40.333]    GreenFieldPosition: 0
[    40.333]    BlueMaskSize: 0
[    40.333]    BlueFieldPosition: 0
[    40.333]    RsvdMaskSize: 0
[    40.333]    RsvdFieldPosition: 0
[    40.333]    DirectColorModeInfo: 0
[    40.333]    PhysBasePtr: 0xe0000000
[    40.333]    LinBytesPerScanLine: 640
[    40.333]    BnkNumberOfImagePages: 14
[    40.333]    LinNumberOfImagePages: 14
[    40.333]    LinRedMaskSize: 0
[    40.333]    LinRedFieldPosition: 0
[    40.333]    LinGreenMaskSize: 0
[    40.333]    LinGreenFieldPosition: 0
[    40.333]    LinBlueMaskSize: 0
[    40.333]    LinBlueFieldPosition: 0
[    40.333]    LinRsvdMaskSize: 0
[    40.333]    LinRsvdFieldPosition: 0
[    40.333]    MaxPixelClock: 229500000
[    40.334] Mode: 101 (640x480)
[    40.334]    ModeAttributes: 0x39f
[    40.334]    WinAAttributes: 0x7
[    40.334]    WinBAttributes: 0x0
[    40.334]    WinGranularity: 64
[    40.334]    WinSize: 64
[    40.334]    WinASegment: 0xa000
[    40.334]    WinBSegment: 0x0
[    40.334]    WinFuncPtr: 0xc000a4ae
[    40.334]    BytesPerScanline: 640
[    40.334]    XResolution: 640
[    40.335]    YResolution: 480
[    40.335]    XCharSize: 8
[    40.335]    YCharSize: 16
[    40.335]    NumberOfPlanes: 1
[    40.335]    BitsPerPixel: 8
[    40.335]    NumberOfBanks: 1
[    40.335]    MemoryModel: 4
[    40.335]    BankSize: 0
[    40.335]    NumberOfImages: 10
[    40.335]    RedMaskSize: 0
[    40.335]    RedFieldPosition: 0
[    40.335]    GreenMaskSize: 0
[    40.335]    GreenFieldPosition: 0
[    40.335]    BlueMaskSize: 0
[    40.335]    BlueFieldPosition: 0
[    40.335]    RsvdMaskSize: 0
[    40.335]    RsvdFieldPosition: 0
[    40.335]    DirectColorModeInfo: 0
[    40.335]    PhysBasePtr: 0xe0000000
[    40.335]    LinBytesPerScanLine: 640
[    40.335]    BnkNumberOfImagePages: 10
[    40.335]    LinNumberOfImagePages: 10
[    40.335]    LinRedMaskSize: 0
[    40.335]    LinRedMaskSize: 0
[    40.335]    LinRedFieldPosition: 0
[    40.335]    LinGreenMaskSize: 0
[    40.335]    LinGreenFieldPosition: 0
[    40.335]    LinBlueMaskSize: 0
[    40.335]    LinBlueFieldPosition: 0
[    40.335]    LinRsvdMaskSize: 0
[    40.335]    LinRsvdFieldPosition: 0
[    40.335]    MaxPixelClock: 229500000
[    40.358] Mode: 102 (800x600)
[    40.358]    ModeAttributes: 0x31f
[    40.358]    WinAAttributes: 0x7
[    40.358]    WinBAttributes: 0x0
[    40.358]    WinGranularity: 64
[    40.358]    WinSize: 64
[    40.358]    WinASegment: 0xa000
[    40.358]    WinBSegment: 0x0
[    40.358]    WinFuncPtr: 0xc000a4ae
[    40.358]    BytesPerScanline: 100
[    40.358]    XResolution: 800
[    40.358]    YResolution: 600
[    40.358]    XCharSize: 8
[    40.358]    YCharSize: 16
[    40.358]    NumberOfPlanes: 4
[    40.358]    BitsPerPixel: 4
[    40.358]    NumberOfBanks: 1
[    40.358]    MemoryModel: 3
[    40.358]    BankSize: 0
[    40.358]    NumberOfImages: 14
[    40.358]    RedMaskSize: 0
[    40.358]    RedFieldPosition: 0
[    40.358]    GreenMaskSize: 0
[    40.358]    GreenFieldPosition: 0
[    40.358]    BlueMaskSize: 0
[    40.358]    BlueFieldPosition: 0
[    40.358]    RsvdMaskSize: 0
[    40.358]    RsvdFieldPosition: 0
[    40.358]    DirectColorModeInfo: 0
[    40.358]    PhysBasePtr: 0x0
[    40.358]    LinBytesPerScanLine: 100
[    40.359]    BnkNumberOfImagePages: 14
[    40.359]    LinNumberOfImagePages: 14
[    40.359]    LinRedMaskSize: 0
[    40.359]    LinRedFieldPosition: 0
[    40.359]    LinGreenMaskSize: 0
[    40.359]    LinGreenFieldPosition: 0
[    40.359]    LinBlueMaskSize: 0
[    40.359]    LinBlueFieldPosition: 0
[    40.359]    LinRsvdMaskSize: 0
[    40.359]    LinRsvdFieldPosition: 0
[    40.359]    MaxPixelClock: 108500000
[    40.359] Mode: 103 (800x600)
[    40.372]    ModeAttributes: 0x39f
[    40.372]    WinAAttributes: 0x7
[    40.372]    WinBAttributes: 0x0
[    40.372]    WinGranularity: 64
[    40.372]    WinSize: 64
[    40.372]    WinASegment: 0xa000
[    40.372]    WinBSegment: 0x0
[    40.372]    WinFuncPtr: 0xc000a4ae
[    40.372]    BytesPerScanline: 800
[    40.372]    XResolution: 800
[    40.372]    YResolution: 600
[    40.372]    XCharSize: 8
[    40.372]    YCharSize: 16
[    40.372]    NumberOfPlanes: 1
[    40.372]    BitsPerPixel: 8
[    40.372]    NumberOfBanks: 1
[    40.372]    MemoryModel: 4
[    40.372]    BankSize: 0
[    40.372]    NumberOfImages: 6
[    40.372]    RedMaskSize: 0
[    40.372]    RedFieldPosition: 0
[    40.372]    GreenMaskSize: 0
[    40.372]    GreenFieldPosition: 0
[    40.372]    BlueMaskSize: 0
[    40.372]    BlueFieldPosition: 0
[    40.372]    RsvdMaskSize: 0
[    40.372]    RsvdFieldPosition: 0
[    40.373]    DirectColorModeInfo: 0
[    40.373]    PhysBasePtr: 0xe0000000
[    40.373]    LinBytesPerScanLine: 800
[    40.373]    BnkNumberOfImagePages: 6
[    40.373]    LinNumberOfImagePages: 6
[    40.373]    LinRedMaskSize: 0
[    40.373]    LinRedFieldPosition: 0
[    40.373]    LinGreenMaskSize: 0
[    40.373]    LinGreenFieldPosition: 0
[    40.373]    LinBlueMaskSize: 0
[    40.373]    LinBlueFieldPosition: 0
[    40.373]    LinRsvdMaskSize: 0
[    40.373]    LinRsvdFieldPosition: 0
[    40.373]    MaxPixelClock: 229500000
[    40.374] Mode: 104 (1024x768)
[    40.374]    ModeAttributes: 0x31f
[    40.374]    WinAAttributes: 0x7
[    40.374]    WinBAttributes: 0x0
[    40.374]    WinGranularity: 64
[    40.374]    WinSize: 64
[    40.374]    WinASegment: 0xa000
[    40.374]    WinBSegment: 0x0
[    40.374]    WinFuncPtr: 0xc000a4ae
[    40.374]    BytesPerScanline: 128
[    40.374]    XResolution: 1024
[    40.374]    YResolution: 768
[    40.374]    XCharSize: 8
[    40.374]    YCharSize: 16
[    40.374]    NumberOfPlanes: 4
[    40.374]    BitsPerPixel: 4
[    40.374]    NumberOfBanks: 1
[    40.374]    MemoryModel: 3
[    40.374]    BankSize: 0
[    40.374]    NumberOfImages: 6
[    40.374]    RedMaskSize: 0
[    40.374]    RedFieldPosition: 0
[    40.374]    BlueMaskSize: 0
[    40.374]    BlueFieldPosition: 0
[    40.374]    RsvdMaskSize: 0
[    40.374]    RsvdFieldPosition: 0
[    40.374]    DirectColorModeInfo: 0
[    40.374]    PhysBasePtr: 0x0
[    40.374]    LinBytesPerScanLine: 128
[    40.374]    BnkNumberOfImagePages: 6
[    40.374]    LinNumberOfImagePages: 6
[    40.374]    LinRedMaskSize: 0
[    40.374]    LinRedFieldPosition: 0
[    40.374]    LinGreenMaskSize: 0
[    40.374]    LinGreenFieldPosition: 0
[    40.374]    LinBlueMaskSize: 0
[    40.374]    LinBlueFieldPosition: 0
[    40.374]    LinRsvdMaskSize: 0
[    40.374]    LinRsvdFieldPosition: 0
[    40.375]    MaxPixelClock: 108500000
[    40.375] Mode: 105 (1024x768)
[    40.375]    ModeAttributes: 0x39f
[    40.375]    WinAAttributes: 0x7
[    40.375]    WinBAttributes: 0x0
[    40.375]    WinGranularity: 64
[    40.375]    WinSize: 64
[    40.375]    WinASegment: 0xa000
[    40.375]    WinBSegment: 0x0
[    40.375]    WinFuncPtr: 0xc000a4ae
[    40.375]    BytesPerScanline: 1024
[    40.375]    XResolution: 1024
[    40.406]    YResolution: 768
[    40.406]    XCharSize: 8
[    40.406]    YCharSize: 16
[    40.406]    NumberOfPlanes: 1
[    40.406]    BitsPerPixel: 8
[    40.406]    NumberOfBanks: 1
[    40.406]    MemoryModel: 4
[    40.406]    BankSize: 0
[    40.406]    NumberOfImages: 3
[    40.407]    RedMaskSize: 0
[    40.407]    RedFieldPosition: 0
[    40.407]    GreenMaskSize: 0
[    40.407]    GreenFieldPosition: 0
[    40.407]    BlueMaskSize: 0
[    40.407]    BlueFieldPosition: 0
[    40.407]    RsvdMaskSize: 0
[    40.407]    RsvdFieldPosition: 0
[    40.407]    DirectColorModeInfo: 0
[    40.407]    PhysBasePtr: 0xe0000000
[    40.407]    LinBytesPerScanLine: 1024
[    40.407]    BnkNumberOfImagePages: 3
[    40.407]    LinNumberOfImagePages: 3
[    40.407]    LinRedMaskSize: 0
[    40.407]    LinRedFieldPosition: 0
[    40.407]    LinGreenMaskSize: 0
[    40.407]    LinGreenFieldPosition: 0
[    40.407]    LinBlueMaskSize: 0
[    40.407]    LinBlueFieldPosition: 0
[    40.407]    LinRsvdMaskSize: 0
[    40.407]    LinRsvdFieldPosition: 0
[    40.407]    MaxPixelClock: 229500000
[    40.417] Mode: 106 (1280x1024)
[    40.417]    ModeAttributes: 0x31f
[    40.417]    WinAAttributes: 0x7
[    40.417]    WinBAttributes: 0x0
[    40.417]    WinGranularity: 64
[    40.417]    WinSize: 64
[    40.417]    WinASegment: 0xa000
[    40.417]    WinBSegment: 0x0
[    40.417]    WinFuncPtr: 0xc000a4ae
[    40.417]    BytesPerScanline: 160
[    40.417]    XResolution: 1280
[    40.417]    YResolution: 1024
[    40.417]    XCharSize: 8
[    40.417]    YCharSize: 16
[    40.417]    NumberOfPlanes: 4
[    40.417]    BitsPerPixel: 4
[    40.417]    NumberOfBanks: 1
[    40.417]    MemoryModel: 3
[    40.417]    BankSize: 0
[    40.417]    NumberOfImages: 3
[    40.417]    RedMaskSize: 0
[    40.417]    RedFieldPosition: 0
[    40.417]    GreenMaskSize: 0
[    40.417]    GreenFieldPosition: 0
[    40.417]    BlueMaskSize: 0
[    40.417]    BlueFieldPosition: 0
[    40.417]    RsvdMaskSize: 0
[    40.417]    RsvdFieldPosition: 0
[    40.417]    DirectColorModeInfo: 0
[    40.417]    PhysBasePtr: 0x0
[    40.417]    LinBytesPerScanLine: 160
[    40.417]    BnkNumberOfImagePages: 3
[    40.417]    LinNumberOfImagePages: 3
[    40.417]    LinRedMaskSize: 0
[    40.417]    LinRedFieldPosition: 0
[    40.417]    LinGreenMaskSize: 0
[    40.417]    LinGreenFieldPosition: 0
[    40.418]    LinBlueMaskSize: 0
[    40.418]    LinBlueFieldPosition: 0
[    40.418]    LinRsvdMaskSize: 0
[    40.418]    LinRsvdFieldPosition: 0
[    40.418]    MaxPixelClock: 108500000
[    40.418] Mode: 107 (1280x1024)
[    40.418]    ModeAttributes: 0x39f
[    40.418]    WinAAttributes: 0x7
[    40.418]    WinBAttributes: 0x0
[    40.419]    WinGranularity: 64
[    40.419]    WinSize: 64
[    40.419]    WinASegment: 0xa000
[    40.419]    WinBSegment: 0x0
[    40.419]    WinFuncPtr: 0xc000a4ae
[    40.419]    BytesPerScanline: 1280
[    40.419]    XResolution: 1280
[    40.419]    YResolution: 1024
[    40.419]    XCharSize: 8
[    40.419]    YCharSize: 16
[    40.419]    NumberOfPlanes: 1
[    40.419]    BitsPerPixel: 8
[    40.419]    NumberOfBanks: 1
[    40.419]    MemoryModel: 4
[    40.419]    BankSize: 0
[    40.419]    NumberOfImages: 1
[    40.419]    RedMaskSize: 0
[    40.419]    RedFieldPosition: 0
[    40.419]    GreenMaskSize: 0
[    40.419]    GreenFieldPosition: 0
[    40.419]    BlueMaskSize: 0
[    40.419]    BlueFieldPosition: 0
[    40.419]    RsvdMaskSize: 0
[    40.419]    RsvdFieldPosition: 0
[    40.419]    DirectColorModeInfo: 0
[    40.419]    PhysBasePtr: 0xe0000000
[    40.419]    LinBytesPerScanLine: 1280
[    40.419]    BnkNumberOfImagePages: 1
[    40.419]    LinNumberOfImagePages: 1
[    40.419]    LinRedMaskSize: 0
[    40.419]    LinRedFieldPosition: 0
[    40.419]    LinGreenMaskSize: 0
[    40.419]    LinGreenFieldPosition: 0
[    40.419]    LinBlueMaskSize: 0
[    40.419]    LinBlueFieldPosition: 0
[    40.419]    LinRsvdMaskSize: 0
[    40.419]    LinRsvdFieldPosition: 0
[    40.419]    MaxPixelClock: 229500000
[    40.455] Mode: 108 (80x60)
[    40.455]    ModeAttributes: 0x38f
[    40.455]    WinAAttributes: 0x7
[    40.455]    WinBAttributes: 0x0
[    40.455]    WinGranularity: 32
[    40.455]    WinSize: 32
[    40.455]    WinASegment: 0xb800
[    40.455]    WinBSegment: 0x0
[    40.455]    WinFuncPtr: 0xc000a4ae
[    40.455]    BytesPerScanline: 160
[    40.455]    XResolution: 80
[    40.455]    YResolution: 60
[    40.455]    XCharSize: 8
[    40.455]    YCharSize: 8
[    40.455]    NumberOfPlanes: 1
[    40.455]    BitsPerPixel: 4
[    40.455]    NumberOfBanks: 1
[    40.455]    MemoryModel: 0
[    40.455]    BankSize: 0
[    40.455]    NumberOfImages: 0
[    40.455]    RedMaskSize: 0
[    40.455]    RedFieldPosition: 0
[    40.455]    GreenMaskSize: 0
[    40.455]    GreenFieldPosition: 0
[    40.455]    BlueMaskSize: 0
[    40.455]    BlueFieldPosition: 0
[    40.455]    RsvdMaskSize: 0
[    40.455]    RsvdFieldPosition: 0
[    40.455]    DirectColorModeInfo: 0
[    40.455]    PhysBasePtr: 0xe0000000
[    40.455]    LinBytesPerScanLine: 160
[    40.455]    BnkNumberOfImagePages: 0
[    40.455]    LinNumberOfImagePages: 0
[    40.455]    LinRedMaskSize: 0
[    40.464]    LinRedFieldPosition: 0
[    40.464]    LinGreenMaskSize: 0
[    40.465]    LinGreenFieldPosition: 0
[    40.465]    LinBlueMaskSize: 0
[    40.465]    LinBlueFieldPosition: 0
[    40.465]    LinRsvdMaskSize: 0
[    40.465]    LinRsvdFieldPosition: 0
[    40.465]    MaxPixelClock: 108500000
[    40.466] Mode: 10e (320x200)
[    40.466]    ModeAttributes: 0x39f
[    40.466]    WinAAttributes: 0x7
[    40.466]    WinBAttributes: 0x0
[    40.466]    WinGranularity: 64
[    40.466]    WinSize: 64
[    40.466]    WinASegment: 0xa000
[    40.466]    WinBSegment: 0x0
[    40.466]    WinFuncPtr: 0xc000a4ae
[    40.466]    BytesPerScanline: 640
[    40.466]    XResolution: 320
[    40.466]    YResolution: 200
[    40.466]    XCharSize: 8
[    40.466]    YCharSize: 16
[    40.466]    NumberOfPlanes: 1
[    40.466]    BitsPerPixel: 16
[    40.466]    NumberOfBanks: 1
[    40.466]    MemoryModel: 6
[    40.466]    BankSize: 0
[    40.466]    NumberOfImages: 30
[    40.466]    RedMaskSize: 5
[    40.466]    RedFieldPosition: 11
[    40.466]    GreenMaskSize: 6
[    40.466]    GreenFieldPosition: 5
[    40.466]    BlueMaskSize: 5
[    40.466]    BlueFieldPosition: 0
[    40.466]    RsvdMaskSize: 0
[    40.466]    RsvdFieldPosition: 0
[    40.466]    DirectColorModeInfo: 0
[    40.466]    PhysBasePtr: 0xe0000000
[    40.466]    LinBytesPerScanLine: 640
[    40.466]    BnkNumberOfImagePages: 30
[    40.466]    LinNumberOfImagePages: 30
[    40.466]    LinRedMaskSize: 5
[    40.466]    LinRedFieldPosition: 11
[    40.466]    LinGreenMaskSize: 6
[    40.466]    LinGreenFieldPosition: 5
[    40.466]    LinBlueMaskSize: 5
[    40.466]    LinBlueFieldPosition: 0
[    40.466]    LinRsvdMaskSize: 0
[    40.466]    LinRsvdFieldPosition: 0
[    40.466]    MaxPixelClock: 229500000
[    40.467] *Mode: 10f (320x200)
[    40.467]    ModeAttributes: 0x39f
[    40.467]    WinAAttributes: 0x7
[    40.467]    WinBAttributes: 0x0
[    40.467]    WinGranularity: 64
[    40.467]    WinSize: 64
[    40.467]    WinASegment: 0xa000
[    40.467]    WinBSegment: 0x0
[    40.467]    WinFuncPtr: 0xc000a4ae
[    40.467]    BytesPerScanline: 1280
[    40.467]    XResolution: 320
[    40.467]    YResolution: 200
[    40.467]    XCharSize: 8
[    40.467]    YCharSize: 16
[    40.467]    NumberOfPlanes: 1
[    40.467]    BitsPerPixel: 32
[    40.467]    NumberOfBanks: 1
[    40.467]    MemoryModel: 6
[    40.467]    BankSize: 0
[    40.467]    NumberOfImages: 14
[    40.467]    RedMaskSize: 8
[    40.467]    RedFieldPosition: 16
[    40.467]    GreenMaskSize: 8
[    40.488]    GreenFieldPosition: 8
[    40.488]    BlueMaskSize: 8
[    40.488]    BlueFieldPosition: 0
[    40.488]    RsvdMaskSize: 8
[    40.488]    RsvdFieldPosition: 24
[    40.488]    DirectColorModeInfo: 0
[    40.488]    PhysBasePtr: 0xe0000000
[    40.488]    LinBytesPerScanLine: 1280
[    40.488]    BnkNumberOfImagePages: 14
[    40.488]    LinNumberOfImagePages: 14
[    40.488]    LinRedMaskSize: 8
[    40.488]    LinRedFieldPosition: 16
[    40.488]    LinGreenMaskSize: 8
[    40.488]    LinGreenFieldPosition: 8
[    40.488]    LinBlueMaskSize: 8
[    40.488]    LinBlueFieldPosition: 0
[    40.488]    LinRsvdMaskSize: 8
[    40.488]    LinRsvdFieldPosition: 24
[    40.488]    MaxPixelClock: 229500000
[    40.489] Mode: 111 (640x480)
[    40.489]    ModeAttributes: 0x39f
[    40.489]    WinAAttributes: 0x7
[    40.489]    WinBAttributes: 0x0
[    40.489]    WinGranularity: 64
[    40.489]    WinSize: 64
[    40.489]    WinASegment: 0xa000
[    40.489]    WinBSegment: 0x0
[    40.489]    WinFuncPtr: 0xc000a4ae
[    40.489]    BytesPerScanline: 1280
[    40.489]    XResolution: 640
[    40.489]    YResolution: 480
[    40.489]    XCharSize: 8
[    40.489]    YCharSize: 16
[    40.489]    NumberOfPlanes: 1
....
Bunch of lines like the above ones
....
[    40.581] (II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
[    40.581] (II) VESA(0): <default monitor>: Using hsync range of 31.00-80.00 kHz
[    40.581] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-76.00 Hz
[    40.581] (II) VESA(0): <default monitor>: Using maximum pixel clock of 165.00 MHz
[    40.581] (WW) VESA(0): Unable to estimate virtual size
[    40.585] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    40.585] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    40.585] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    40.585] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    40.585] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    40.585] (**) VESA(0): *Built-in mode "1024x768"
[    40.585] (**) VESA(0): *Built-in mode "800x600"
[    40.585] (**) VESA(0): *Built-in mode "640x480"
[    40.585] (**) VESA(0): Display dimensions: (410, 310) mm
[    40.585] (**) VESA(0): DPI set to (63, 62)
[    40.585] (**) VESA(0): Using "Shadow Framebuffer"
[    40.585] (II) Loading sub module "shadow"
[    40.585] (II) LoadModule: "shadow"
[    40.586] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    40.586] (II) Module shadow: vendor="X.Org Foundation"
[    40.586]    compiled for 1.14.3, module version = 1.1.0
[    40.586]    ABI class: X.Org ANSI C Emulation, version 0.4
[    40.586] (II) Loading sub module "fb"
[    40.586] (II) LoadModule: "fb"
[    40.592] (II) Loading /usr/lib/xorg/modules/libfb.so
[    40.593] (II) Module fb: vendor="X.Org Foundation"
[    40.593]    compiled for 1.14.3, module version = 1.0.0
[    40.593]    ABI class: X.Org ANSI C Emulation, version 0.4
[    40.593] (II) UnloadModule: "modesetting"
[    40.593] (II) Unloading modesetting
[    40.593] (II) UnloadModule: "fbdev"
[    40.593] (II) Unloading fbdev
[    40.593] (II) UnloadSubModule: "fbdevhw"
[    40.593] (II) Unloading fbdevhw
[    40.593] (==) Depth 24 pixmap format is 32 bpp
[    40.593] (II) Loading sub module "int10"
[    40.593] (II) LoadModule: "int10"
[    40.594] (II) Loading /usr/lib/xorg/modules/libint10.so
[    40.596] (II) Module int10: vendor="X.Org Foundation"
[    40.596]    compiled for 1.14.3, module version = 1.0.0
[    40.596]    ABI class: X.Org Video Driver, version 14.1
[    40.596] (II) VESA(0): initializing int10
[    40.597] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    40.622] (II) VESA(0): VESA BIOS detected
[    40.622] (II) VESA(0): VESA VBE Version 3.0
[    40.622] (II) VESA(0): VESA VBE Total Mem: 65536 kB
[    40.622] (II) VESA(0): VESA VBE OEM: NVidia
[    40.622] (II) VESA(0): VESA VBE OEM Software Rev: 4.23
[    40.622] (II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
[    40.622] (II) VESA(0): VESA VBE OEM Product: NV17 () Board
[    40.622] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A2
[    40.623] (II) VESA(0): virtual address = 0xb2ab2000,
    physical address = 0xe0000000, size = 67108864
[    40.647] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    41.069] (==) VESA(0): Default visual is TrueColor
[    41.070] (==) VESA(0): Backing store disabled
[    41.070] (==) VESA(0): DPMS enabled
[    41.070] (==) RandR enabled
[    41.124] (II) SELinux: Disabled on system
[    41.127] (II) AIGLX: Screen 0 is not DRI2 capable
[    41.127] (II) AIGLX: Screen 0 is not DRI capable
[    41.868] (II) AIGLX: Loaded and initialized swrast
[    41.868] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    42.134] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    42.194] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    42.194] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    42.194] (II) LoadModule: "evdev"
[    42.195] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.208] (II) Module evdev: vendor="X.Org Foundation"
[    42.208]    compiled for 1.14.1, module version = 2.7.3
[    42.208]    Module class: X.Org XInput Driver
[    42.208]    ABI class: X.Org XInput driver, version 19.1
[    42.208] (II) Using input driver 'evdev' for 'Video Bus'
[    42.208] (**) Video Bus: always reports core events
[    42.208] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    42.209] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    42.209] (--) evdev: Video Bus: Found keys
[    42.209] (II) evdev: Video Bus: Configuring as keyboard
[    42.209] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:15/LNXVIDEO:00/input/input4/event4"
[    42.209] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    42.209] (**) Option "xkb_rules" "evdev"
[    42.209] (**) Option "xkb_model" "pc105"
[    42.209] (**) Option "xkb_layout" "us"
[    42.210] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    42.210] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    42.210] (II) Using input driver 'evdev' for 'Power Button'
[    42.210] (**) Power Button: always reports core events
[    42.210] (**) evdev: Power Button: Device: "/dev/input/event1"
[    42.210] (--) evdev: Power Button: Vendor 0 Product 0x1
[    42.211] (--) evdev: Power Button: Found keys
[    42.211] (II) evdev: Power Button: Configuring as keyboard
[    42.211] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    42.211] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    42.211] (**) Option "xkb_rules" "evdev"
[    42.211] (**) Option "xkb_model" "pc105"
[    42.211] (**) Option "xkb_layout" "us"
[    42.232] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    42.233] (II) No input driver specified, ignoring this device.
[    42.233] (II) This device may have been added with another device file.
[    42.233] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    42.233] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    42.233] (II) Using input driver 'evdev' for 'Sleep Button'
[    42.233] (**) Sleep Button: always reports core events
[    42.233] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    42.233] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    42.233] (--) evdev: Sleep Button: Found keys
[    42.233] (II) evdev: Sleep Button: Configuring as keyboard
[    42.234] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    42.234] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    42.234] (**) Option "xkb_rules" "evdev"
[    42.234] (**) Option "xkb_model" "pc105"
[    42.234] (**) Option "xkb_layout" "us"
[    42.235] (II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/event5)
[    42.235] (**) Logitech USB RECEIVER: Applying InputClass "evdev pointer catchall"
[    42.235] (II) Using input driver 'evdev' for 'Logitech USB RECEIVER'
[    42.235] (**) Logitech USB RECEIVER: always reports core events
[    42.235] (**) evdev: Logitech USB RECEIVER: Device: "/dev/input/event5"
[    42.235] (--) evdev: Logitech USB RECEIVER: Vendor 0x46d Product 0xc50e
[    42.235] (--) evdev: Logitech USB RECEIVER: Found 20 mouse buttons
[    42.235] (--) evdev: Logitech USB RECEIVER: Found scroll wheel(s)
[    42.235] (--) evdev: Logitech USB RECEIVER: Found relative axes
[    42.235] (--) evdev: Logitech USB RECEIVER: Found x and y relative axes
[    42.236] (II) evdev: Logitech USB RECEIVER: Configuring as mouse
[    42.251] (II) evdev: Logitech USB RECEIVER: Adding scrollwheel support
[    42.251] (**) evdev: Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
[    42.251] (**) evdev: Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.251] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input5/event5"
[    42.251] (II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE, id 9)
[    42.251] (II) evdev: Logitech USB RECEIVER: initialized for relative axes.
[    42.259] (**) Logitech USB RECEIVER: (accel) keeping acceleration scheme 1
[    42.259] (**) Logitech USB RECEIVER: (accel) acceleration profile 0
[    42.259] (**) Logitech USB RECEIVER: (accel) acceleration factor: 2.000
[    42.259] (**) Logitech USB RECEIVER: (accel) acceleration threshold: 4
[    42.263] (II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/mouse0)
[    42.263] (II) No input driver specified, ignoring this device.
[    42.263] (II) This device may have been added with another device file.
[    42.267] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    42.267] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    42.267] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    42.267] (**) AT Translated Set 2 keyboard: always reports core events
[    42.267] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    42.269] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    42.269] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    42.269] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    42.269] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    42.269] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    42.269] (**) Option "xkb_rules" "evdev"
[    42.269] (**) Option "xkb_model" "pc105"
[    42.269] (**) Option "xkb_layout" "us"
[    42.271] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event6)
[    42.271] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    42.271] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    42.271] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    42.271] (**) DualPoint Stick: always reports core events
[    42.271] (**) evdev: DualPoint Stick: Device: "/dev/input/event6"
[    42.271] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    42.271] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    42.271] (--) evdev: DualPoint Stick: Found relative axes
[    42.271] (--) evdev: DualPoint Stick: Found x and y relative axes
[    42.271] (II) evdev: DualPoint Stick: Configuring as mouse
[    42.271] (**) Option "Emulate3Buttons" "true"
[    42.271] (**) Option "EmulateWheel" "true"
[    42.271] (**) Option "EmulateWheelButton" "2"
[    42.271] (**) Option "YAxisMapping" "4 5"
[    42.271] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    42.271] (**) Option "XAxisMapping" "6 7"
[    42.271] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    42.272] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.272] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    42.272] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 11)
[    42.272] (II) evdev: DualPoint Stick: initialized for relative axes.
[    42.273] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    42.273] (**) DualPoint Stick: (accel) acceleration profile 0
[    42.273] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    42.273] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    42.274] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[    42.274] (II) No input driver specified, ignoring this device.
[    42.274] (II) This device may have been added with another device file.
[    42.275] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event7)
[    42.275] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    42.275] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    42.275] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    42.275] (II) LoadModule: "synaptics"
[    42.275] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    42.286] (II) Module synaptics: vendor="X.Org Foundation"
[    42.286]    compiled for 1.14.2, module version = 1.7.1
[    42.286]    Module class: X.Org XInput Driver
[    42.286]    ABI class: X.Org XInput driver, version 19.1
[    42.286] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    42.286] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    42.286] (**) Option "Device" "/dev/input/event7"
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023 (res 0)
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767 (res 0)
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    42.286] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    42.287] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    42.287] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 12)
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.156
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    42.291] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[    42.291] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    78.967] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    81.230] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
@    
[    42.275] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    42.275] (II) LoadModule: "synaptics"
[    42.275] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    42.286] (II) Module synaptics: vendor="X.Org Foundation"
[    42.286]    compiled for 1.14.2, module version = 1.7.1
[    42.286]    Module class: X.Org XInput Driver
[    42.286]    ABI class: X.Org XInput driver, version 19.1
[    42.286] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    42.286] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    42.286] (**) Option "Device" "/dev/input/event7"
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023 (res 0)
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767 (res 0)
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    42.286] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    42.287] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    42.287] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 12)
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.156
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    42.291] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[    42.291] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    78.967] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    81.230] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
@    
[    81.366] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
```

Thanks in advance.

---

### Post by danielsender on 2013-10-30
> **danielsender said:**
> I suspect that is something related to not being able to load the nouveau driver and using the vesa driver. I can't decypher the Xorg.0.log file, can someone help me?
```
[    38.262]
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    38.262] X Protocol Version 11, Revision 0
[    38.262] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    38.262] Current Operating System: Linux kidhug 3.9.0-030900rc6-generic #201304080035 SMP Mon Apr 8 04:44:54 UTC 2013 i686
[    38.262] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.9.0-030900rc6-generic root=UUID=67e485e0-aa01-44ad-b18f-48462d9c906e ro quiet splash vt.handoff=7
[    38.262] Build Date: 15 October 2013  09:23:29AM
[    38.262] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support)
[    38.262] Current version of pixman: 0.30.2
[    38.262]    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    38.262] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    38.262] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 22 22:16:05 2013
[    38.289] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    38.290] (==) No Layout section.  Using the first Screen section.
[    38.290] (==) No screen section available. Using defaults.
[    38.290] (**) |-->Screen "Default Screen Section" (0)
[    38.290] (**) |   |-->Monitor "<default monitor>"
[    38.290] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    38.290] (==) Automatically adding devices
[    38.290] (==) Automatically enabling devices
[    38.290] (==) Automatically adding GPU devices
[    38.290] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    38.290]    Entry deleted from font path.
[    38.290] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    38.290]    Entry deleted from font path.
[    38.290] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    38.290]    Entry deleted from font path.
[    38.291] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    38.291]    Entry deleted from font path.
[    38.291] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    38.291]    Entry deleted from font path.
[    38.291] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    38.291] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    38.291] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    38.291] (II) Loader magic: 0xb77936a0
[    38.291] (II) Module ABI versions:
[    38.291]    X.Org ANSI C Emulation: 0.4
[    38.291]    X.Org Video Driver: 14.1
[    38.291]    X.Org XInput driver : 19.1
[    38.291]    X.Org Server Extension : 7.0
[    38.306] (--) PCI:*(0:1:0:0) 10de:017c:1028:00d5 rev 163, Mem @ 0xfc000000/16777216, 0xe0000000/134217728, 0xdff80000/524288, BIOS @ 0x????????/131072
[    38.321] (II) Open ACPI successful (/var/run/acpid.socket)
[    38.321] Initializing built-in extension Generic Event Extension
[    38.321] Initializing built-in extension SHAPE
[    38.321] Initializing built-in extension MIT-SHM
[    38.321] Initializing built-in extension XInputExtension
[    38.321] Initializing built-in extension XTEST
[    38.321] Initializing built-in extension BIG-REQUESTS
[    38.321] Initializing built-in extension SYNC
[    38.321] Initializing built-in extension XKEYBOARD
[    38.321] Initializing built-in extension XC-MISC
[    38.321] Initializing built-in extension SECURITY
[    38.321] Initializing built-in extension XINERAMA
[    38.321] Initializing built-in extension XFIXES
[    38.321] Initializing built-in extension RENDER
[    38.321] Initializing built-in extension RANDR
[    38.322] Initializing built-in extension COMPOSITE
[    38.322] Initializing built-in extension DAMAGE
[    38.322] Initializing built-in extension MIT-SCREEN-SAVER
[    38.322] Initializing built-in extension DOUBLE-BUFFER
[    38.328] Initializing built-in extension RECORD
[    38.328] Initializing built-in extension DPMS
[    38.328] Initializing built-in extension X-Resource
[    38.328] Initializing built-in extension XVideo
[    38.328] Initializing built-in extension XVideo-MotionCompensation
[    38.328] Initializing built-in extension SELinux
[    38.328] Initializing built-in extension XFree86-VidModeExtension
[    38.328] Initializing built-in extension XFree86-DGA
[    38.328] Initializing built-in extension XFree86-DRI
[    38.328] Initializing built-in extension DRI2
[    38.328] (II) "glx" will be loaded by default.
[    38.328] (WW) "xmir" is not to be loaded by default. Skipping.
[    38.328] (II) LoadModule: "dri2"
[    38.329] (II) Module "dri2" already built-in
[    38.329] (II) LoadModule: "glamoregl"
[    38.391] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    39.061] (II) Module glamoregl: vendor="X.Org Foundation"
[    39.061]    compiled for 1.14.2.901, module version = 0.5.1
[    39.061]    ABI class: X.Org ANSI C Emulation, version 0.4
[    39.061] (II) LoadModule: "glx"
[    39.062] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    39.062] (II) Module glx: vendor="X.Org Foundation"
[    39.062]    compiled for 1.14.3, module version = 1.0.0
[    39.062]    ABI class: X.Org Server Extension, version 7.0
[    39.062] (==) AIGLX enabled
[    39.062] Loading extension GLX
[    39.062] (==) Matched nvidia as autoconfigured driver 0
[    39.062] (==) Matched nouveau as autoconfigured driver 1
[    39.062] (==) Matched vesa as autoconfigured driver 2
[    39.062] (==) Matched modesetting as autoconfigured driver 3
[    39.062] (==) Matched fbdev as autoconfigured driver 4
[    39.062] (==) Assigned the driver to the xf86ConfigLayout
[    39.062] (II) LoadModule: "nvidia"
[    39.082] (WW) Warning, couldn't open module nvidia
[    39.082] (II) UnloadModule: "nvidia"
[    39.082] (II) Unloading nvidia
[    39.082] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    39.082] (II) LoadModule: "nouveau"
[    39.082] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    39.118] (II) Module nouveau: vendor="X.Org Foundation"
[    39.118]    compiled for 1.14.2.901, module version = 1.0.9
[    39.118]    Module class: X.Org Video Driver
[    39.118]    ABI class: X.Org Video Driver, version 14.1
[    39.118] (II) LoadModule: "vesa"
[    39.119] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    39.119] (II) Module vesa: vendor="X.Org Foundation"
[    39.119]    compiled for 1.14.1, module version = 2.3.2
[    39.119]    Module class: X.Org Video Driver
[    39.119]    ABI class: X.Org Video Driver, version 14.1
[    39.119] (II) LoadModule: "modesetting"
[    39.120] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    39.120] (II) Module modesetting: vendor="X.Org Foundation"
[    39.120]    compiled for 1.14.1, module version = 0.8.0
[    39.120]    Module class: X.Org Video Driver
[    39.120]    ABI class: X.Org Video Driver, version 14.1
[    39.120] (II) LoadModule: "fbdev"
[    39.121] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    39.121] (II) Module fbdev: vendor="X.Org Foundation"
[    39.121]    compiled for 1.14.1, module version = 0.4.3
[    39.121]    Module class: X.Org Video Driver
[    39.121]    ABI class: X.Org Video Driver, version 14.1
[    39.121] (==) Matched nvidia as autoconfigured driver 0
[    39.121] (==) Matched nouveau as autoconfigured driver 1
[    39.121] (==) Matched vesa as autoconfigured driver 2
[    39.121] (==) Matched modesetting as autoconfigured driver 3
[    39.121] (==) Matched fbdev as autoconfigured driver 4
[    39.121] (==) Assigned the driver to the xf86ConfigLayout
[    39.121] (II) LoadModule: "nvidia"
[    39.122] (WW) Warning, couldn't open module nvidia
[    39.122] (II) UnloadModule: "nvidia"
[    39.122] (II) Unloading nvidia
[    39.122] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    39.122] (II) LoadModule: "nouveau"
[    39.123] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    39.123] (II) Module nouveau: vendor="X.Org Foundation"
[    39.123]    compiled for 1.14.2.901, module version = 1.0.9
[    39.123]    Module class: X.Org Video Driver
[    39.123]    ABI class: X.Org Video Driver, version 14.1
[    39.123] (II) UnloadModule: "nouveau"
[    39.123] (II) Unloading nouveau
[    39.123] (II) Failed to load module "nouveau" (already loaded, 0)
[    39.123] (II) LoadModule: "vesa"
[    39.156] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    39.156] (II) Module vesa: vendor="X.Org Foundation"
[    39.156]    compiled for 1.14.1, module version = 2.3.2
[    39.156]    Module class: X.Org Video Driver
[    39.156]    ABI class: X.Org Video Driver, version 14.1
[    39.156] (II) UnloadModule: "vesa"
[    39.156] (II) Unloading vesa
[    39.156] (II) Failed to load module "vesa" (already loaded, 0)
[    39.156] (II) LoadModule: "modesetting"
[    39.157] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    39.157] (II) Module modesetting: vendor="X.Org Foundation"
[    39.157]    compiled for 1.14.1, module version = 0.8.0
[    39.157]    Module class: X.Org Video Driver
[    39.157]    ABI class: X.Org Video Driver, version 14.1
[    39.157] (II) UnloadModule: "modesetting"
[    39.157] (II) Unloading modesetting
[    39.157] (II) Failed to load module "modesetting" (already loaded, 0)
[    39.157] (II) LoadModule: "fbdev"
[    39.158] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    39.158] (II) Module fbdev: vendor="X.Org Foundation"
[    39.158]    compiled for 1.14.1, module version = 0.4.3
[    39.158]    Module class: X.Org Video Driver
[    39.158]    ABI class: X.Org Video Driver, version 14.1
[    39.158] (II) UnloadModule: "fbdev"
[    39.158] (II) Unloading fbdev
[    39.158] (II) Failed to load module "fbdev" (already loaded, 0)
[    39.158] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[    39.158] (II) NOUVEAU driver for NVIDIA chipset families :
[    39.158]    RIVA TNT        (NV04)
[    39.158]    RIVA TNT2       (NV05)
[    39.158]    GeForce 256     (NV10)
[    39.158]    GeForce 2       (NV11, NV15)
[    39.158]    GeForce 4MX     (NV17, NV18)
[    39.158]    GeForce 3       (NV20)
[    39.158]    GeForce 4Ti     (NV25, NV28)
[    39.158]    GeForce FX      (NV3x)
[    39.158]    GeForce 6       (NV4x)
[    39.158]    GeForce 7       (G7x)
[    39.159]    GeForce 8       (G8x)
[    39.159]    GeForce GTX 200 (NVA0)
[    39.159]    GeForce GTX 400 (NVC0)
[    39.159] (II) VESA: driver for VESA chipsets: vesa
[    39.159] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    39.159] (II) FBDEV: driver for framebuffer: fbdev
[    39.159] (++) using VT number 7

[    39.159] (EE) [drm] KMS not enabled
[    39.159] (EE) [drm] KMS not enabled
[    39.159] (WW) Falling back to old probe method for modesetting
[    39.160] (EE) open /dev/dri/card0: No such file or directory
[    39.160] (EE) open /dev/dri/card0: No such file or directory
[    39.160] (WW) Falling back to old probe method for fbdev
[    39.160] (II) Loading sub module "fbdevhw"
[    39.160] (II) LoadModule: "fbdevhw"
[    39.160] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    39.161] (II) Module fbdevhw: vendor="X.Org Foundation"
[    39.161]    compiled for 1.14.3, module version = 0.0.2
[    39.161]    ABI class: X.Org Video Driver, version 14.1
[    39.161] (EE) open /dev/fb0: No such file or directory
[    39.161] (II) Loading sub module "vbe"
[    39.161] (II) LoadModule: "vbe"
[    39.161] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    39.162] (II) Module vbe: vendor="X.Org Foundation"
[    39.162]    compiled for 1.14.3, module version = 1.1.0
[    39.162]    ABI class: X.Org Video Driver, version 14.1
[    39.162] (II) Loading sub module "int10"
[    39.162] (II) LoadModule: "int10"
[    39.163] (II) Loading /usr/lib/xorg/modules/libint10.so
[    39.163] (II) Module int10: vendor="X.Org Foundation"
[    39.176]    compiled for 1.14.3, module version = 1.0.0
[    39.176]    ABI class: X.Org Video Driver, version 14.1
[    39.176] (II) VESA(0): initializing int10
[    39.177] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    39.266] (II) VESA(0): VESA BIOS detected
[    39.266] (II) VESA(0): VESA VBE Version 3.0
[    39.266] (II) VESA(0): VESA VBE Total Mem: 65536 kB
[    39.266] (II) VESA(0): VESA VBE OEM: NVidia
[    39.266] (II) VESA(0): VESA VBE OEM Software Rev: 4.23
[    39.266] (II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
[    39.266] (II) VESA(0): VESA VBE OEM Product: NV17 () Board
[    39.266] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A2
[    39.526] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    39.526] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    39.526] (==) VESA(0): RGB weight 888
[    39.526] (==) VESA(0): Default visual is TrueColor
[    39.526] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    39.526] (II) Loading sub module "ddc"
[    39.526] (II) LoadModule: "ddc"
[    39.526] (II) Module "ddc" already built-in
[    39.779] (II) VESA(0): VESA VBE DDC supported
[    39.779] (II) VESA(0): VESA VBE DDC Level 2
[    39.779] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    40.290] (II) VESA(0): VESA VBE DDC read successfully
[    40.291] (II) VESA(0): Manufacturer: DEL  Model: a002  Serial#: 808993100
[    40.291] (II) VESA(0): Year: 2003  Week: 35
[    40.291] (II) VESA(0): EDID Version: 1.3
[    40.291] (II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    40.291] (II) VESA(0): Sync:  Separate  Composite  SyncOnGreen
[    40.291] (II) VESA(0): Max Image Size [cm]: horiz.: 41  vert.: 31
[    40.291] (II) VESA(0): Gamma: 2.50
[    40.291] (II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    40.291] (II) VESA(0): First detailed timing is preferred mode
[    40.291] (II) VESA(0): redX: 0.630 redY: 0.340   greenX: 0.300 greenY: 0.590
[    40.291] (II) VESA(0): blueX: 0.149 blueY: 0.109   whiteX: 0.312 whiteY: 0.328
[    40.291] (II) VESA(0): Supported established timings:
[    40.291] (II) VESA(0): 720x400@70Hz
[    40.291] (II) VESA(0): 640x480@60Hz
[    40.291] (II) VESA(0): 640x480@75Hz
[    40.291] (II) VESA(0): 800x600@60Hz
[    40.291] (II) VESA(0): 800x600@75Hz
[    40.291] (II) VESA(0): 1024x768@60Hz
[    40.291] (II) VESA(0): 1024x768@75Hz
[    40.291] (II) VESA(0): 1280x1024@75Hz
[    40.291] (II) VESA(0): Manufacturer's mask: 0
[    40.291] (II) VESA(0): Supported standard timings:
[    40.291] (II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    40.291] (II) VESA(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    40.291] (II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    40.291] (II) VESA(0): Supported detailed timing:
[    40.291] (II) VESA(0): clock: 162.0 MHz   Image Size:  367 x 275 mm
[    40.291] (II) VESA(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
[    40.291] (II) VESA(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
[    40.291] (II) VESA(0): Serial No: 9E24938S08AL0
[    40.291] (II) VESA(0): Monitor name: DELL 2000FP
[    40.291] (II) VESA(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 80 kHz, PixClock max 165 MHz
[    40.291] (II) VESA(0): EDID (in hex):
[    40.318] (II) VESA(0):  00ffffffffffff0010ac02a04c413830
[    40.318] (II) VESA(0):  230d01030e291f96ea4c40a1574c9726
[    40.318] (II) VESA(0):  1c5054a54b008180a940714f01010101
[    40.318] (II) VESA(0):  010101010101483f403062b0324040c0
[    40.318] (II) VESA(0):  13006f131100001e000000ff00394532
[    40.318] (II) VESA(0):  34393338533038414c30000000fc0044
[    40.318] (II) VESA(0):  454c4c203230303046500a20000000fd
[    40.318] (II) VESA(0):  00384c1f5010000a20202020202000f1
[    40.318] (II) VESA(0): EDID vendor "DEL", prod id 40962
[    40.318] (II) VESA(0): Using EDID range info for horizontal sync
[    40.318] (II) VESA(0): Using EDID range info for vertical refresh
[    40.318] (II) VESA(0): Printing DDC gathered Modelines:
[    40.318] (II) VESA(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz eP)
[    40.318] (II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.318] (II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    40.318] (II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    40.318] (II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    40.318] (II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    40.319] (II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    40.319] (II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.319] (II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    40.319] (II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    40.319] (II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    40.319] (II) VESA(0): Searching for matching VESA mode(s):
[    40.333] Mode: 100 (640x400)
[    40.333]    ModeAttributes: 0x39f
[    40.333]    WinAAttributes: 0x7
[    40.333]    WinBAttributes: 0x0
[    40.333]    WinGranularity: 64
[    40.333]    WinSize: 64
[    40.333]    WinASegment: 0xa000
[    40.333]    WinBSegment: 0x0
[    40.333]    WinFuncPtr: 0xc000a4ae
[    40.333]    BytesPerScanline: 640
[    40.333]    XResolution: 640
[    40.333]    YResolution: 400
[    40.333]    XCharSize: 8
[    40.333]    YCharSize: 16
[    40.333]    NumberOfPlanes: 1
[    40.333]    BitsPerPixel: 8
[    40.333]    NumberOfBanks: 1
[    40.333]    MemoryModel: 4
[    40.333]    BankSize: 0
[    40.333]    NumberOfImages: 14
[    40.333]    RedMaskSize: 0
[    40.333]    RedFieldPosition: 0
[    40.333]    GreenMaskSize: 0
[    40.333]    GreenFieldPosition: 0
[    40.333]    BlueMaskSize: 0
[    40.333]    BlueFieldPosition: 0
[    40.333]    RsvdMaskSize: 0
[    40.333]    RsvdFieldPosition: 0
[    40.333]    DirectColorModeInfo: 0
[    40.333]    PhysBasePtr: 0xe0000000
[    40.333]    LinBytesPerScanLine: 640
[    40.333]    BnkNumberOfImagePages: 14
[    40.333]    LinNumberOfImagePages: 14
[    40.333]    LinRedMaskSize: 0
[    40.333]    LinRedFieldPosition: 0
[    40.333]    LinGreenMaskSize: 0
[    40.333]    LinGreenFieldPosition: 0
[    40.333]    LinBlueMaskSize: 0
[    40.333]    LinBlueFieldPosition: 0
[    40.333]    LinRsvdMaskSize: 0
[    40.333]    LinRsvdFieldPosition: 0
[    40.333]    MaxPixelClock: 229500000
[    40.334] Mode: 101 (640x480)
[    40.334]    ModeAttributes: 0x39f
[    40.334]    WinAAttributes: 0x7
[    40.334]    WinBAttributes: 0x0
[    40.334]    WinGranularity: 64
[    40.334]    WinSize: 64
[    40.334]    WinASegment: 0xa000
[    40.334]    WinBSegment: 0x0
[    40.334]    WinFuncPtr: 0xc000a4ae
[    40.334]    BytesPerScanline: 640
[    40.334]    XResolution: 640
[    40.335]    YResolution: 480
[    40.335]    XCharSize: 8
[    40.335]    YCharSize: 16
[    40.335]    NumberOfPlanes: 1
[    40.335]    BitsPerPixel: 8
[    40.335]    NumberOfBanks: 1
[    40.335]    MemoryModel: 4
[    40.335]    BankSize: 0
[    40.335]    NumberOfImages: 10
[    40.335]    RedMaskSize: 0
[    40.335]    RedFieldPosition: 0
[    40.335]    GreenMaskSize: 0
[    40.335]    GreenFieldPosition: 0
[    40.335]    BlueMaskSize: 0
[    40.335]    BlueFieldPosition: 0
[    40.335]    RsvdMaskSize: 0
[    40.335]    RsvdFieldPosition: 0
[    40.335]    DirectColorModeInfo: 0
[    40.335]    PhysBasePtr: 0xe0000000
[    40.335]    LinBytesPerScanLine: 640
[    40.335]    BnkNumberOfImagePages: 10
[    40.335]    LinNumberOfImagePages: 10
[    40.335]    LinRedMaskSize: 0
[    40.335]    LinRedMaskSize: 0
[    40.335]    LinRedFieldPosition: 0
[    40.335]    LinGreenMaskSize: 0
[    40.335]    LinGreenFieldPosition: 0
[    40.335]    LinBlueMaskSize: 0
[    40.335]    LinBlueFieldPosition: 0
[    40.335]    LinRsvdMaskSize: 0
[    40.335]    LinRsvdFieldPosition: 0
[    40.335]    MaxPixelClock: 229500000
[    40.358] Mode: 102 (800x600)
[    40.358]    ModeAttributes: 0x31f
[    40.358]    WinAAttributes: 0x7
[    40.358]    WinBAttributes: 0x0
[    40.358]    WinGranularity: 64
[    40.358]    WinSize: 64
[    40.358]    WinASegment: 0xa000
[    40.358]    WinBSegment: 0x0
[    40.358]    WinFuncPtr: 0xc000a4ae
[    40.358]    BytesPerScanline: 100
[    40.358]    XResolution: 800
[    40.358]    YResolution: 600
[    40.358]    XCharSize: 8
[    40.358]    YCharSize: 16
[    40.358]    NumberOfPlanes: 4
[    40.358]    BitsPerPixel: 4
[    40.358]    NumberOfBanks: 1
[    40.358]    MemoryModel: 3
[    40.358]    BankSize: 0
[    40.358]    NumberOfImages: 14
[    40.358]    RedMaskSize: 0
[    40.358]    RedFieldPosition: 0
[    40.358]    GreenMaskSize: 0
[    40.358]    GreenFieldPosition: 0
[    40.358]    BlueMaskSize: 0
[    40.358]    BlueFieldPosition: 0
[    40.358]    RsvdMaskSize: 0
[    40.358]    RsvdFieldPosition: 0
[    40.358]    DirectColorModeInfo: 0
[    40.358]    PhysBasePtr: 0x0
[    40.358]    LinBytesPerScanLine: 100
[    40.359]    BnkNumberOfImagePages: 14
[    40.359]    LinNumberOfImagePages: 14
[    40.359]    LinRedMaskSize: 0
[    40.359]    LinRedFieldPosition: 0
[    40.359]    LinGreenMaskSize: 0
[    40.359]    LinGreenFieldPosition: 0
[    40.359]    LinBlueMaskSize: 0
[    40.359]    LinBlueFieldPosition: 0
[    40.359]    LinRsvdMaskSize: 0
[    40.359]    LinRsvdFieldPosition: 0
[    40.359]    MaxPixelClock: 108500000
[    40.359] Mode: 103 (800x600)
[    40.372]    ModeAttributes: 0x39f
[    40.372]    WinAAttributes: 0x7
[    40.372]    WinBAttributes: 0x0
[    40.372]    WinGranularity: 64
[    40.372]    WinSize: 64
[    40.372]    WinASegment: 0xa000
[    40.372]    WinBSegment: 0x0
[    40.372]    WinFuncPtr: 0xc000a4ae
[    40.372]    BytesPerScanline: 800
[    40.372]    XResolution: 800
[    40.372]    YResolution: 600
[    40.372]    XCharSize: 8
[    40.372]    YCharSize: 16
[    40.372]    NumberOfPlanes: 1
[    40.372]    BitsPerPixel: 8
[    40.372]    NumberOfBanks: 1
[    40.372]    MemoryModel: 4
[    40.372]    BankSize: 0
[    40.372]    NumberOfImages: 6
[    40.372]    RedMaskSize: 0
[    40.372]    RedFieldPosition: 0
[    40.372]    GreenMaskSize: 0
[    40.372]    GreenFieldPosition: 0
[    40.372]    BlueMaskSize: 0
[    40.372]    BlueFieldPosition: 0
[    40.372]    RsvdMaskSize: 0
[    40.372]    RsvdFieldPosition: 0
[    40.373]    DirectColorModeInfo: 0
[    40.373]    PhysBasePtr: 0xe0000000
[    40.373]    LinBytesPerScanLine: 800
[    40.373]    BnkNumberOfImagePages: 6
[    40.373]    LinNumberOfImagePages: 6
[    40.373]    LinRedMaskSize: 0
[    40.373]    LinRedFieldPosition: 0
[    40.373]    LinGreenMaskSize: 0
[    40.373]    LinGreenFieldPosition: 0
[    40.373]    LinBlueMaskSize: 0
[    40.373]    LinBlueFieldPosition: 0
[    40.373]    LinRsvdMaskSize: 0
[    40.373]    LinRsvdFieldPosition: 0
[    40.373]    MaxPixelClock: 229500000
[    40.374] Mode: 104 (1024x768)
[    40.374]    ModeAttributes: 0x31f
[    40.374]    WinAAttributes: 0x7
[    40.374]    WinBAttributes: 0x0
[    40.374]    WinGranularity: 64
[    40.374]    WinSize: 64
[    40.374]    WinASegment: 0xa000
[    40.374]    WinBSegment: 0x0
[    40.374]    WinFuncPtr: 0xc000a4ae
[    40.374]    BytesPerScanline: 128
[    40.374]    XResolution: 1024
[    40.374]    YResolution: 768
[    40.374]    XCharSize: 8
[    40.374]    YCharSize: 16
[    40.374]    NumberOfPlanes: 4
[    40.374]    BitsPerPixel: 4
[    40.374]    NumberOfBanks: 1
[    40.374]    MemoryModel: 3
[    40.374]    BankSize: 0
[    40.374]    NumberOfImages: 6
[    40.374]    RedMaskSize: 0
[    40.374]    RedFieldPosition: 0
[    40.374]    BlueMaskSize: 0
[    40.374]    BlueFieldPosition: 0
[    40.374]    RsvdMaskSize: 0
[    40.374]    RsvdFieldPosition: 0
[    40.374]    DirectColorModeInfo: 0
[    40.374]    PhysBasePtr: 0x0
[    40.374]    LinBytesPerScanLine: 128
[    40.374]    BnkNumberOfImagePages: 6
[    40.374]    LinNumberOfImagePages: 6
[    40.374]    LinRedMaskSize: 0
[    40.374]    LinRedFieldPosition: 0
[    40.374]    LinGreenMaskSize: 0
[    40.374]    LinGreenFieldPosition: 0
[    40.374]    LinBlueMaskSize: 0
[    40.374]    LinBlueFieldPosition: 0
[    40.374]    LinRsvdMaskSize: 0
[    40.374]    LinRsvdFieldPosition: 0
[    40.375]    MaxPixelClock: 108500000
[    40.375] Mode: 105 (1024x768)
[    40.375]    ModeAttributes: 0x39f
[    40.375]    WinAAttributes: 0x7
[    40.375]    WinBAttributes: 0x0
[    40.375]    WinGranularity: 64
[    40.375]    WinSize: 64
[    40.375]    WinASegment: 0xa000
[    40.375]    WinBSegment: 0x0
[    40.375]    WinFuncPtr: 0xc000a4ae
[    40.375]    BytesPerScanline: 1024
[    40.375]    XResolution: 1024
[    40.406]    YResolution: 768
[    40.406]    XCharSize: 8
[    40.406]    YCharSize: 16
[    40.406]    NumberOfPlanes: 1
[    40.406]    BitsPerPixel: 8
[    40.406]    NumberOfBanks: 1
[    40.406]    MemoryModel: 4
[    40.406]    BankSize: 0
[    40.406]    NumberOfImages: 3
[    40.407]    RedMaskSize: 0
[    40.407]    RedFieldPosition: 0
[    40.407]    GreenMaskSize: 0
[    40.407]    GreenFieldPosition: 0
[    40.407]    BlueMaskSize: 0
[    40.407]    BlueFieldPosition: 0
[    40.407]    RsvdMaskSize: 0
[    40.407]    RsvdFieldPosition: 0
[    40.407]    DirectColorModeInfo: 0
[    40.407]    PhysBasePtr: 0xe0000000
[    40.407]    LinBytesPerScanLine: 1024
[    40.407]    BnkNumberOfImagePages: 3
[    40.407]    LinNumberOfImagePages: 3
[    40.407]    LinRedMaskSize: 0
[    40.407]    LinRedFieldPosition: 0
[    40.407]    LinGreenMaskSize: 0
[    40.407]    LinGreenFieldPosition: 0
[    40.407]    LinBlueMaskSize: 0
[    40.407]    LinBlueFieldPosition: 0
[    40.407]    LinRsvdMaskSize: 0
[    40.407]    LinRsvdFieldPosition: 0
[    40.407]    MaxPixelClock: 229500000
[    40.417] Mode: 106 (1280x1024)
[    40.417]    ModeAttributes: 0x31f
[    40.417]    WinAAttributes: 0x7
[    40.417]    WinBAttributes: 0x0
[    40.417]    WinGranularity: 64
[    40.417]    WinSize: 64
[    40.417]    WinASegment: 0xa000
[    40.417]    WinBSegment: 0x0
[    40.417]    WinFuncPtr: 0xc000a4ae
[    40.417]    BytesPerScanline: 160
[    40.417]    XResolution: 1280
[    40.417]    YResolution: 1024
[    40.417]    XCharSize: 8
[    40.417]    YCharSize: 16
[    40.417]    NumberOfPlanes: 4
[    40.417]    BitsPerPixel: 4
[    40.417]    NumberOfBanks: 1
[    40.417]    MemoryModel: 3
[    40.417]    BankSize: 0
[    40.417]    NumberOfImages: 3
[    40.417]    RedMaskSize: 0
[    40.417]    RedFieldPosition: 0
[    40.417]    GreenMaskSize: 0
[    40.417]    GreenFieldPosition: 0
[    40.417]    BlueMaskSize: 0
[    40.417]    BlueFieldPosition: 0
[    40.417]    RsvdMaskSize: 0
[    40.417]    RsvdFieldPosition: 0
[    40.417]    DirectColorModeInfo: 0
[    40.417]    PhysBasePtr: 0x0
[    40.417]    LinBytesPerScanLine: 160
[    40.417]    BnkNumberOfImagePages: 3
[    40.417]    LinNumberOfImagePages: 3
[    40.417]    LinRedMaskSize: 0
[    40.417]    LinRedFieldPosition: 0
[    40.417]    LinGreenMaskSize: 0
[    40.417]    LinGreenFieldPosition: 0
[    40.418]    LinBlueMaskSize: 0
[    40.418]    LinBlueFieldPosition: 0
[    40.418]    LinRsvdMaskSize: 0
[    40.418]    LinRsvdFieldPosition: 0
[    40.418]    MaxPixelClock: 108500000
[    40.418] Mode: 107 (1280x1024)
[    40.418]    ModeAttributes: 0x39f
[    40.418]    WinAAttributes: 0x7
[    40.418]    WinBAttributes: 0x0
[    40.419]    WinGranularity: 64
[    40.419]    WinSize: 64
[    40.419]    WinASegment: 0xa000
[    40.419]    WinBSegment: 0x0
[    40.419]    WinFuncPtr: 0xc000a4ae
[    40.419]    BytesPerScanline: 1280
[    40.419]    XResolution: 1280
[    40.419]    YResolution: 1024
[    40.419]    XCharSize: 8
[    40.419]    YCharSize: 16
[    40.419]    NumberOfPlanes: 1
[    40.419]    BitsPerPixel: 8
[    40.419]    NumberOfBanks: 1
[    40.419]    MemoryModel: 4
[    40.419]    BankSize: 0
[    40.419]    NumberOfImages: 1
[    40.419]    RedMaskSize: 0
[    40.419]    RedFieldPosition: 0
[    40.419]    GreenMaskSize: 0
[    40.419]    GreenFieldPosition: 0
[    40.419]    BlueMaskSize: 0
[    40.419]    BlueFieldPosition: 0
[    40.419]    RsvdMaskSize: 0
[    40.419]    RsvdFieldPosition: 0
[    40.419]    DirectColorModeInfo: 0
[    40.419]    PhysBasePtr: 0xe0000000
[    40.419]    LinBytesPerScanLine: 1280
[    40.419]    BnkNumberOfImagePages: 1
[    40.419]    LinNumberOfImagePages: 1
[    40.419]    LinRedMaskSize: 0
[    40.419]    LinRedFieldPosition: 0
[    40.419]    LinGreenMaskSize: 0
[    40.419]    LinGreenFieldPosition: 0
[    40.419]    LinBlueMaskSize: 0
[    40.419]    LinBlueFieldPosition: 0
[    40.419]    LinRsvdMaskSize: 0
[    40.419]    LinRsvdFieldPosition: 0
[    40.419]    MaxPixelClock: 229500000
[    40.455] Mode: 108 (80x60)
[    40.455]    ModeAttributes: 0x38f
[    40.455]    WinAAttributes: 0x7
[    40.455]    WinBAttributes: 0x0
[    40.455]    WinGranularity: 32
[    40.455]    WinSize: 32
[    40.455]    WinASegment: 0xb800
[    40.455]    WinBSegment: 0x0
[    40.455]    WinFuncPtr: 0xc000a4ae
[    40.455]    BytesPerScanline: 160
[    40.455]    XResolution: 80
[    40.455]    YResolution: 60
[    40.455]    XCharSize: 8
[    40.455]    YCharSize: 8
[    40.455]    NumberOfPlanes: 1
[    40.455]    BitsPerPixel: 4
[    40.455]    NumberOfBanks: 1
[    40.455]    MemoryModel: 0
[    40.455]    BankSize: 0
[    40.455]    NumberOfImages: 0
[    40.455]    RedMaskSize: 0
[    40.455]    RedFieldPosition: 0
[    40.455]    GreenMaskSize: 0
[    40.455]    GreenFieldPosition: 0
[    40.455]    BlueMaskSize: 0
[    40.455]    BlueFieldPosition: 0
[    40.455]    RsvdMaskSize: 0
[    40.455]    RsvdFieldPosition: 0
[    40.455]    DirectColorModeInfo: 0
[    40.455]    PhysBasePtr: 0xe0000000
[    40.455]    LinBytesPerScanLine: 160
[    40.455]    BnkNumberOfImagePages: 0
[    40.455]    LinNumberOfImagePages: 0
[    40.455]    LinRedMaskSize: 0
[    40.464]    LinRedFieldPosition: 0
[    40.464]    LinGreenMaskSize: 0
[    40.465]    LinGreenFieldPosition: 0
[    40.465]    LinBlueMaskSize: 0
[    40.465]    LinBlueFieldPosition: 0
[    40.465]    LinRsvdMaskSize: 0
[    40.465]    LinRsvdFieldPosition: 0
[    40.465]    MaxPixelClock: 108500000
[    40.466] Mode: 10e (320x200)
[    40.466]    ModeAttributes: 0x39f
[    40.466]    WinAAttributes: 0x7
[    40.466]    WinBAttributes: 0x0
[    40.466]    WinGranularity: 64
[    40.466]    WinSize: 64
[    40.466]    WinASegment: 0xa000
[    40.466]    WinBSegment: 0x0
[    40.466]    WinFuncPtr: 0xc000a4ae
[    40.466]    BytesPerScanline: 640
[    40.466]    XResolution: 320
[    40.466]    YResolution: 200
[    40.466]    XCharSize: 8
[    40.466]    YCharSize: 16
[    40.466]    NumberOfPlanes: 1
[    40.466]    BitsPerPixel: 16
[    40.466]    NumberOfBanks: 1
[    40.466]    MemoryModel: 6
[    40.466]    BankSize: 0
[    40.466]    NumberOfImages: 30
[    40.466]    RedMaskSize: 5
[    40.466]    RedFieldPosition: 11
[    40.466]    GreenMaskSize: 6
[    40.466]    GreenFieldPosition: 5
[    40.466]    BlueMaskSize: 5
[    40.466]    BlueFieldPosition: 0
[    40.466]    RsvdMaskSize: 0
[    40.466]    RsvdFieldPosition: 0
[    40.466]    DirectColorModeInfo: 0
[    40.466]    PhysBasePtr: 0xe0000000
[    40.466]    LinBytesPerScanLine: 640
[    40.466]    BnkNumberOfImagePages: 30
[    40.466]    LinNumberOfImagePages: 30
[    40.466]    LinRedMaskSize: 5
[    40.466]    LinRedFieldPosition: 11
[    40.466]    LinGreenMaskSize: 6
[    40.466]    LinGreenFieldPosition: 5
[    40.466]    LinBlueMaskSize: 5
[    40.466]    LinBlueFieldPosition: 0
[    40.466]    LinRsvdMaskSize: 0
[    40.466]    LinRsvdFieldPosition: 0
[    40.466]    MaxPixelClock: 229500000
[    40.467] *Mode: 10f (320x200)
[    40.467]    ModeAttributes: 0x39f
[    40.467]    WinAAttributes: 0x7
[    40.467]    WinBAttributes: 0x0
[    40.467]    WinGranularity: 64
[    40.467]    WinSize: 64
[    40.467]    WinASegment: 0xa000
[    40.467]    WinBSegment: 0x0
[    40.467]    WinFuncPtr: 0xc000a4ae
[    40.467]    BytesPerScanline: 1280
[    40.467]    XResolution: 320
[    40.467]    YResolution: 200
[    40.467]    XCharSize: 8
[    40.467]    YCharSize: 16
[    40.467]    NumberOfPlanes: 1
[    40.467]    BitsPerPixel: 32
[    40.467]    NumberOfBanks: 1
[    40.467]    MemoryModel: 6
[    40.467]    BankSize: 0
[    40.467]    NumberOfImages: 14
[    40.467]    RedMaskSize: 8
[    40.467]    RedFieldPosition: 16
[    40.467]    GreenMaskSize: 8
[    40.488]    GreenFieldPosition: 8
[    40.488]    BlueMaskSize: 8
[    40.488]    BlueFieldPosition: 0
[    40.488]    RsvdMaskSize: 8
[    40.488]    RsvdFieldPosition: 24
[    40.488]    DirectColorModeInfo: 0
[    40.488]    PhysBasePtr: 0xe0000000
[    40.488]    LinBytesPerScanLine: 1280
[    40.488]    BnkNumberOfImagePages: 14
[    40.488]    LinNumberOfImagePages: 14
[    40.488]    LinRedMaskSize: 8
[    40.488]    LinRedFieldPosition: 16
[    40.488]    LinGreenMaskSize: 8
[    40.488]    LinGreenFieldPosition: 8
[    40.488]    LinBlueMaskSize: 8
[    40.488]    LinBlueFieldPosition: 0
[    40.488]    LinRsvdMaskSize: 8
[    40.488]    LinRsvdFieldPosition: 24
[    40.488]    MaxPixelClock: 229500000
[    40.489] Mode: 111 (640x480)
[    40.489]    ModeAttributes: 0x39f
[    40.489]    WinAAttributes: 0x7
[    40.489]    WinBAttributes: 0x0
[    40.489]    WinGranularity: 64
[    40.489]    WinSize: 64
[    40.489]    WinASegment: 0xa000
[    40.489]    WinBSegment: 0x0
[    40.489]    WinFuncPtr: 0xc000a4ae
[    40.489]    BytesPerScanline: 1280
[    40.489]    XResolution: 640
[    40.489]    YResolution: 480
[    40.489]    XCharSize: 8
[    40.489]    YCharSize: 16
[    40.489]    NumberOfPlanes: 1
....
Bunch of lines like the above ones
....
[    40.581] (II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
[    40.581] (II) VESA(0): <default monitor>: Using hsync range of 31.00-80.00 kHz
[    40.581] (II) VESA(0): <default monitor>: Using vrefresh range of 56.00-76.00 Hz
[    40.581] (II) VESA(0): <default monitor>: Using maximum pixel clock of 165.00 MHz
[    40.581] (WW) VESA(0): Unable to estimate virtual size
[    40.585] (II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[    40.585] (II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[    40.585] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    40.585] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    40.585] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    40.585] (**) VESA(0): *Built-in mode "1024x768"
[    40.585] (**) VESA(0): *Built-in mode "800x600"
[    40.585] (**) VESA(0): *Built-in mode "640x480"
[    40.585] (**) VESA(0): Display dimensions: (410, 310) mm
[    40.585] (**) VESA(0): DPI set to (63, 62)
[    40.585] (**) VESA(0): Using "Shadow Framebuffer"
[    40.585] (II) Loading sub module "shadow"
[    40.585] (II) LoadModule: "shadow"
[    40.586] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    40.586] (II) Module shadow: vendor="X.Org Foundation"
[    40.586]    compiled for 1.14.3, module version = 1.1.0
[    40.586]    ABI class: X.Org ANSI C Emulation, version 0.4
[    40.586] (II) Loading sub module "fb"
[    40.586] (II) LoadModule: "fb"
[    40.592] (II) Loading /usr/lib/xorg/modules/libfb.so
[    40.593] (II) Module fb: vendor="X.Org Foundation"
[    40.593]    compiled for 1.14.3, module version = 1.0.0
[    40.593]    ABI class: X.Org ANSI C Emulation, version 0.4
[    40.593] (II) UnloadModule: "modesetting"
[    40.593] (II) Unloading modesetting
[    40.593] (II) UnloadModule: "fbdev"
[    40.593] (II) Unloading fbdev
[    40.593] (II) UnloadSubModule: "fbdevhw"
[    40.593] (II) Unloading fbdevhw
[    40.593] (==) Depth 24 pixmap format is 32 bpp
[    40.593] (II) Loading sub module "int10"
[    40.593] (II) LoadModule: "int10"
[    40.594] (II) Loading /usr/lib/xorg/modules/libint10.so
[    40.596] (II) Module int10: vendor="X.Org Foundation"
[    40.596]    compiled for 1.14.3, module version = 1.0.0
[    40.596]    ABI class: X.Org Video Driver, version 14.1
[    40.596] (II) VESA(0): initializing int10
[    40.597] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    40.622] (II) VESA(0): VESA BIOS detected
[    40.622] (II) VESA(0): VESA VBE Version 3.0
[    40.622] (II) VESA(0): VESA VBE Total Mem: 65536 kB
[    40.622] (II) VESA(0): VESA VBE OEM: NVidia
[    40.622] (II) VESA(0): VESA VBE OEM Software Rev: 4.23
[    40.622] (II) VESA(0): VESA VBE OEM Vendor: NVidia Corporation
[    40.622] (II) VESA(0): VESA VBE OEM Product: NV17 () Board
[    40.622] (II) VESA(0): VESA VBE OEM Product Rev: Chip Rev A2
[    40.623] (II) VESA(0): virtual address = 0xb2ab2000,
    physical address = 0xe0000000, size = 67108864
[    40.647] (II) VESA(0): Setting up VESA Mode 0x118 (1024x768)
[    41.069] (==) VESA(0): Default visual is TrueColor
[    41.070] (==) VESA(0): Backing store disabled
[    41.070] (==) VESA(0): DPMS enabled
[    41.070] (==) RandR enabled
[    41.124] (II) SELinux: Disabled on system
[    41.127] (II) AIGLX: Screen 0 is not DRI2 capable
[    41.127] (II) AIGLX: Screen 0 is not DRI capable
[    41.868] (II) AIGLX: Loaded and initialized swrast
[    41.868] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    42.134] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    42.194] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    42.194] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    42.194] (II) LoadModule: "evdev"
[    42.195] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    42.208] (II) Module evdev: vendor="X.Org Foundation"
[    42.208]    compiled for 1.14.1, module version = 2.7.3
[    42.208]    Module class: X.Org XInput Driver
[    42.208]    ABI class: X.Org XInput driver, version 19.1
[    42.208] (II) Using input driver 'evdev' for 'Video Bus'
[    42.208] (**) Video Bus: always reports core events
[    42.208] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    42.209] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    42.209] (--) evdev: Video Bus: Found keys
[    42.209] (II) evdev: Video Bus: Configuring as keyboard
[    42.209] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:15/LNXVIDEO:00/input/input4/event4"
[    42.209] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 6)
[    42.209] (**) Option "xkb_rules" "evdev"
[    42.209] (**) Option "xkb_model" "pc105"
[    42.209] (**) Option "xkb_layout" "us"
[    42.210] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    42.210] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    42.210] (II) Using input driver 'evdev' for 'Power Button'
[    42.210] (**) Power Button: always reports core events
[    42.210] (**) evdev: Power Button: Device: "/dev/input/event1"
[    42.210] (--) evdev: Power Button: Vendor 0 Product 0x1
[    42.211] (--) evdev: Power Button: Found keys
[    42.211] (II) evdev: Power Button: Configuring as keyboard
[    42.211] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[    42.211] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    42.211] (**) Option "xkb_rules" "evdev"
[    42.211] (**) Option "xkb_model" "pc105"
[    42.211] (**) Option "xkb_layout" "us"
[    42.232] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    42.233] (II) No input driver specified, ignoring this device.
[    42.233] (II) This device may have been added with another device file.
[    42.233] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    42.233] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    42.233] (II) Using input driver 'evdev' for 'Sleep Button'
[    42.233] (**) Sleep Button: always reports core events
[    42.233] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[    42.233] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    42.233] (--) evdev: Sleep Button: Found keys
[    42.233] (II) evdev: Sleep Button: Configuring as keyboard
[    42.234] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[    42.234] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[    42.234] (**) Option "xkb_rules" "evdev"
[    42.234] (**) Option "xkb_model" "pc105"
[    42.234] (**) Option "xkb_layout" "us"
[    42.235] (II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/event5)
[    42.235] (**) Logitech USB RECEIVER: Applying InputClass "evdev pointer catchall"
[    42.235] (II) Using input driver 'evdev' for 'Logitech USB RECEIVER'
[    42.235] (**) Logitech USB RECEIVER: always reports core events
[    42.235] (**) evdev: Logitech USB RECEIVER: Device: "/dev/input/event5"
[    42.235] (--) evdev: Logitech USB RECEIVER: Vendor 0x46d Product 0xc50e
[    42.235] (--) evdev: Logitech USB RECEIVER: Found 20 mouse buttons
[    42.235] (--) evdev: Logitech USB RECEIVER: Found scroll wheel(s)
[    42.235] (--) evdev: Logitech USB RECEIVER: Found relative axes
[    42.235] (--) evdev: Logitech USB RECEIVER: Found x and y relative axes
[    42.236] (II) evdev: Logitech USB RECEIVER: Configuring as mouse
[    42.251] (II) evdev: Logitech USB RECEIVER: Adding scrollwheel support
[    42.251] (**) evdev: Logitech USB RECEIVER: YAxisMapping: buttons 4 and 5
[    42.251] (**) evdev: Logitech USB RECEIVER: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.251] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input5/event5"
[    42.251] (II) XINPUT: Adding extended input device "Logitech USB RECEIVER" (type: MOUSE, id 9)
[    42.251] (II) evdev: Logitech USB RECEIVER: initialized for relative axes.
[    42.259] (**) Logitech USB RECEIVER: (accel) keeping acceleration scheme 1
[    42.259] (**) Logitech USB RECEIVER: (accel) acceleration profile 0
[    42.259] (**) Logitech USB RECEIVER: (accel) acceleration factor: 2.000
[    42.259] (**) Logitech USB RECEIVER: (accel) acceleration threshold: 4
[    42.263] (II) config/udev: Adding input device Logitech USB RECEIVER (/dev/input/mouse0)
[    42.263] (II) No input driver specified, ignoring this device.
[    42.263] (II) This device may have been added with another device file.
[    42.267] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    42.267] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    42.267] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    42.267] (**) AT Translated Set 2 keyboard: always reports core events
[    42.267] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    42.269] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    42.269] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    42.269] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    42.269] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    42.269] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    42.269] (**) Option "xkb_rules" "evdev"
[    42.269] (**) Option "xkb_model" "pc105"
[    42.269] (**) Option "xkb_layout" "us"
[    42.271] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event6)
[    42.271] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    42.271] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    42.271] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    42.271] (**) DualPoint Stick: always reports core events
[    42.271] (**) evdev: DualPoint Stick: Device: "/dev/input/event6"
[    42.271] (--) evdev: DualPoint Stick: Vendor 0x2 Product 0x8
[    42.271] (--) evdev: DualPoint Stick: Found 3 mouse buttons
[    42.271] (--) evdev: DualPoint Stick: Found relative axes
[    42.271] (--) evdev: DualPoint Stick: Found x and y relative axes
[    42.271] (II) evdev: DualPoint Stick: Configuring as mouse
[    42.271] (**) Option "Emulate3Buttons" "true"
[    42.271] (**) Option "EmulateWheel" "true"
[    42.271] (**) Option "EmulateWheelButton" "2"
[    42.271] (**) Option "YAxisMapping" "4 5"
[    42.271] (**) evdev: DualPoint Stick: YAxisMapping: buttons 4 and 5
[    42.271] (**) Option "XAxisMapping" "6 7"
[    42.271] (**) evdev: DualPoint Stick: XAxisMapping: buttons 6 and 7
[    42.272] (**) evdev: DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    42.272] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event6"
[    42.272] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE, id 11)
[    42.272] (II) evdev: DualPoint Stick: initialized for relative axes.
[    42.273] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    42.273] (**) DualPoint Stick: (accel) acceleration profile 0
[    42.273] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    42.273] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    42.274] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[    42.274] (II) No input driver specified, ignoring this device.
[    42.274] (II) This device may have been added with another device file.
[    42.275] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event7)
[    42.275] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    42.275] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    42.275] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    42.275] (II) LoadModule: "synaptics"
[    42.275] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    42.286] (II) Module synaptics: vendor="X.Org Foundation"
[    42.286]    compiled for 1.14.2, module version = 1.7.1
[    42.286]    Module class: X.Org XInput Driver
[    42.286]    ABI class: X.Org XInput driver, version 19.1
[    42.286] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    42.286] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    42.286] (**) Option "Device" "/dev/input/event7"
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023 (res 0)
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767 (res 0)
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    42.286] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    42.287] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    42.287] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 12)
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.156
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    42.291] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[    42.291] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    78.967] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    81.230] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
@    
[    42.275] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "Default clickpad buttons"
[    42.275] (II) LoadModule: "synaptics"
[    42.275] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    42.286] (II) Module synaptics: vendor="X.Org Foundation"
[    42.286]    compiled for 1.14.2, module version = 1.7.1
[    42.286]    Module class: X.Org XInput Driver
[    42.286]    ABI class: X.Org XInput driver, version 19.1
[    42.286] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    42.286] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    42.286] (**) Option "Device" "/dev/input/event7"
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023 (res 0)
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767 (res 0)
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    42.286] (II) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: device does not report finger width.
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    42.286] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: Vendor 0x2 Product 0x8
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 15
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    42.287] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    42.287] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD, id 12)
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) MaxSpeed is now 1.75
[    42.287] (**) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: (accel) AccelFactor is now 0.156
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    42.287] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    42.287] (--) synaptics: AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    42.291] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[    42.291] (**) AlpsPS/2 ALPS DualPoint TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    78.967] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    81.230] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
@    
[    81.366] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
```

Thanks in advance.
I found the problem and solution which is shown in posting [http://ubuntuforums.org/showthread.php?t=2181785&page=3&p=12833938#post12833938](http://ubuntuforums.org/showthread.php?t=2181785&page=3&p=12833938#post12833938)

I hope this helps.

Daniel

---

