---
title: "Lubuntu 13.10 32bit: Dragging app window causes system to hang awhile."
date: 2013-11-05
forum: Desktop Environments
---

### Post by buzlite on 2013-11-05
Subject:
I'm running Lubuntu 13.10 32bit.
When dragging an application window on the desktop, lubuntu would hang for a few seconds.
I think it has something to do with the nouveau driver.
( have provided the output of dmesg as well as /var/log/Xorg.0.log

Look for '>>>>' indicating when the hanging occurs in the log files.

$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

$ uname -a
Linux tf001 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686 i686 i686 GNU/Linux

$ lsusb
Bus 002 Device 002: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 03f0:2c24 Hewlett-Packard Logitech M-UAL-96 Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO] (rev 10)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller
00:02.2 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev d0)
00:03.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 Multimedia audio controller: C-Media Electronics Inc CMI8738/CMI8768 PCI Audio (rev 10)
00:0a.0 VGA compatible controller: NVIDIA Corporation NV5 [Riva TNT2 Model 64 / Model 64 Pro] (rev 15)
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)


$dmesg

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-12-generic (buildd@komainu) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu7) ) #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 (Ubuntu 3.11.0-12.19-generic 3.11.3)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
...
[   14.460715] Broadcom 43xx driver loaded [ Features: PNL ]
[   14.512098] usb 1-2: new low-speed USB device number 6 using ohci-pci
[   14.726256] usb 1-2: New USB device found, idVendor=03f0, idProduct=2c24
[   14.726266] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   14.726271] usb 1-2: Product: HP USB Laser Mouse
[   14.726275] usb 1-2: Manufacturer: HP
[   14.788751] nouveau  [  DEVICE][0000:00:0a.0] BOOT0  : 0x20154000
[   14.788761] nouveau  [  DEVICE][0000:00:0a.0] Chipset: NV05 (NV05)
[   14.788766] nouveau  [  DEVICE][0000:00:0a.0] Family : NV04
[   14.790672] nouveau  [   VBIOS][0000:00:0a.0] checking PRAMIN for image...
[   14.829948] nouveau  [   VBIOS][0000:00:0a.0] ... appears to be valid
[   14.829954] nouveau  [   VBIOS][0000:00:0a.0] using image from PRAMIN
[   14.829959] nouveau  [   VBIOS][0000:00:0a.0] BMP version 5.11
[   14.830056] nouveau  [   VBIOS][0000:00:0a.0] version 03.05.00.10.00
[   14.940089] usb 2-1: new full-speed USB device number 2 using ohci-pci
[   15.013088] nouveau W[   VBIOS][0000:00:0a.0] DCB table not found
[   15.014003] nouveau W[   VBIOS][0000:00:0a.0] DCB table not found
[   15.034441] nouveau W[   VBIOS][0000:00:0a.0] DCB table not found
[   15.034450] nouveau W[   VBIOS][0000:00:0a.0] DCB table not found
[   15.034528] nouveau W[  PTIMER][0000:00:0a.0] unknown input clock freq
[   15.034543] nouveau  [     PFB][0000:00:0a.0] RAM type: SDRAM
[   15.034547] nouveau  [     PFB][0000:00:0a.0] RAM size: 32 MiB
[   15.034551] nouveau  [     PFB][0000:00:0a.0]    ZCOMP: 0 tags
[   15.112817] [TTM] Zone  kernel: Available graphics memory: 253808 kiB
[   15.112825] [TTM] Initializing pool allocator
[   15.112835] [TTM] Initializing DMA pool allocator
[   15.112864] nouveau  [     DRM] VRAM: 31 MiB
[   15.112868] nouveau  [     DRM] GART: 128 MiB
[   15.112875] nouveau  [     DRM] BMP version 5.17
[   15.112881] nouveau W[     DRM] No DCB data found in VBIOS
[   15.118804] init: failsafe main process (482) killed by TERM signal
[   15.201921] nouveau W[     DRM] No DCB data found in VBIOS
[   15.223715] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   15.223725] [drm] No driver support for vblank timestamp query.
[   15.223950] nouveau  [     DRM] 0 available performance level(s)
[   15.223957] nouveau  [     DRM] c: core 125MHz memory 125MHz
[   15.282838] nouveau  [     DRM] MM: using M2MF for buffer copies
[   15.335676] usb 2-1: New USB device found, idVendor=13b1, idProduct=0020
[   15.335687] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   15.335691] usb 2-1: Product: Compact Wireless-G USB Adapter
[   15.335696] usb 2-1: Manufacturer: Cisco-Linksys
[   15.505232] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   15.684581] nouveau  [     DRM] allocated 1024x768 fb: 0x4000, bo dd0f1e00
[   15.700169] fbcon: nouveaufb (fb0) is primary device
[   15.714757] cfg80211: World regulatory domain updated:
[   15.714760] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.714764] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.714766] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.714768] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.714770] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.714772] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.001627] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   16.001630] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   16.001633] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   16.073218] Console: switching to colour frame buffer device 128x48
[   16.074166] nouveau 0000:00:0a.0: fb0: nouveaufb frame buffer device
[   16.074171] nouveau 0000:00:0a.0: registered panic notifier
[   16.074181] [drm] Initialized nouveau 1.1.1 20120801 for 0000:00:0a.0 on minor 0
[   16.360981] hidraw: raw HID events driver (C) Jiri Kosina
[   16.483233] usbcore: registered new interface driver usbhid
[   16.483242] usbhid: USB HID core driver
[   16.581506] input: HP HP USB Laser Mouse as /devices/pci0000:00/0000:00:02.2/usb1/1-2/1-2:1.0/input/input3
[   16.614408] hid-generic 0003:03F0:2C24.0001: input,hidraw0: USB HID v1.10 Mouse [HP HP USB Laser Mouse] on usb-0000:00:02.2-2/input0
[   16.824093] usb 2-1: reset full-speed USB device number 2 using ohci-pci
********************
>>>> This is around the point when lubuntu hung for a few seconds
********************
[  283.751114] nouveau E[   PFIFO][0000:00:0a.0] DMA_PUSHER - ch 1 [Xorg[1023]] get 0x00029640 put 0x0001cc00 state 0x80006408 (err: INVALID_CMD) push 0x00000000


$ cat /var/log/Xorg.0.log

[    22.031] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[    22.032] X Protocol Version 11, Revision 0
[    22.032] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    22.032] Current Operating System: Linux tf001 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:12:00 UTC 2013 i686
[    22.032] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=cf442ea5-314d-4849-ad80-30e922b0f727 ro quiet splash vt.handoff=7
[    22.032] Build Date: 15 October 2013  09:23:29AM
[    22.032] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.032] Current version of pixman: 0.30.2
[    22.032] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.032] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.032] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov  5 06:06:37 2013
[    22.039] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.039] (==) No Layout section.  Using the first Screen section.
[    22.039] (==) No screen section available. Using defaults.
[    22.039] (**) |-->Screen "Default Screen Section" (0)
[    22.039] (**) |   |-->Monitor "<default monitor>"
[    22.040] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.040] (==) Automatically adding devices
[    22.040] (==) Automatically enabling devices
[    22.040] (==) Automatically adding GPU devices
[    22.040] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.040] 	Entry deleted from font path.
[    22.040] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.040] 	Entry deleted from font path.
[    22.040] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.040] 	Entry deleted from font path.
[    22.040] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    22.040] 	Entry deleted from font path.
[    22.040] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.040] 	Entry deleted from font path.
[    22.040] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.040] 	Entry deleted from font path.
[    22.040] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	built-ins
[    22.040] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.040] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.040] (II) Loader magic: 0xb77726a0
[    22.040] (II) Module ABI versions:
[    22.040] 	X.Org ANSI C Emulation: 0.4
[    22.040] 	X.Org Video Driver: 14.1
[    22.040] 	X.Org XInput driver : 19.1
[    22.040] 	X.Org Server Extension : 7.0
[    22.041] (II) xfree86: Adding drm device (/dev/dri/card0)
[    22.043] (--) PCI:*(0:0:10:0) 10de:002d:0000:0000 rev 21, Mem @ 0xf1000000/16777216, 0xfc000000/33554432, BIOS @ 0x????????/65536
[    22.043] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    22.043] Initializing built-in extension Generic Event Extension
[    22.043] Initializing built-in extension SHAPE
[    22.043] Initializing built-in extension MIT-SHM
[    22.043] Initializing built-in extension XInputExtension
[    22.043] Initializing built-in extension XTEST
[    22.043] Initializing built-in extension BIG-REQUESTS
[    22.043] Initializing built-in extension SYNC
[    22.043] Initializing built-in extension XKEYBOARD
[    22.043] Initializing built-in extension XC-MISC
[    22.043] Initializing built-in extension SECURITY
[    22.043] Initializing built-in extension XINERAMA
[    22.043] Initializing built-in extension XFIXES
[    22.043] Initializing built-in extension RENDER
[    22.043] Initializing built-in extension RANDR
[    22.043] Initializing built-in extension COMPOSITE
[    22.043] Initializing built-in extension DAMAGE
[    22.043] Initializing built-in extension MIT-SCREEN-SAVER
[    22.043] Initializing built-in extension DOUBLE-BUFFER
[    22.043] Initializing built-in extension RECORD
[    22.043] Initializing built-in extension DPMS
[    22.043] Initializing built-in extension X-Resource
[    22.043] Initializing built-in extension XVideo
[    22.043] Initializing built-in extension XVideo-MotionCompensation
[    22.043] Initializing built-in extension SELinux
[    22.043] Initializing built-in extension XFree86-VidModeExtension
[    22.043] Initializing built-in extension XFree86-DGA
[    22.043] Initializing built-in extension XFree86-DRI
[    22.043] Initializing built-in extension DRI2
[    22.043] (II) "glx" will be loaded by default.
[    22.043] (WW) "xmir" is not to be loaded by default. Skipping.
[    22.044] (II) LoadModule: "dri2"
[    22.045] (II) Module "dri2" already built-in
[    22.045] (II) LoadModule: "glamoregl"
[    22.073] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    22.188] (II) Module glamoregl: vendor="X.Org Foundation"
[    22.189] 	compiled for 1.14.2.901, module version = 0.5.1
[    22.189] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.189] (II) LoadModule: "glx"
[    22.189] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.189] (II) Module glx: vendor="X.Org Foundation"
[    22.189] 	compiled for 1.14.3, module version = 1.0.0
[    22.189] 	ABI class: X.Org Server Extension, version 7.0
[    22.189] (==) AIGLX enabled
[    22.189] Loading extension GLX
[    22.190] (==) Matched nvidia as autoconfigured driver 0
[    22.190] (==) Matched nouveau as autoconfigured driver 1
[    22.190] (==) Matched nvidia as autoconfigured driver 2
[    22.190] (==) Matched nouveau as autoconfigured driver 3
[    22.190] (==) Matched vesa as autoconfigured driver 4
[    22.190] (==) Matched modesetting as autoconfigured driver 5
[    22.190] (==) Matched fbdev as autoconfigured driver 6
[    22.190] (==) Assigned the driver to the xf86ConfigLayout
[    22.190] (II) LoadModule: "nvidia"
[    22.191] (WW) Warning, couldn't open module nvidia
[    22.191] (II) UnloadModule: "nvidia"
[    22.191] (II) Unloading nvidia
[    22.191] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    22.191] (II) LoadModule: "nouveau"
[    22.191] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.205] (II) Module nouveau: vendor="X.Org Foundation"
[    22.205] 	compiled for 1.14.2.901, module version = 1.0.9
[    22.205] 	Module class: X.Org Video Driver
[    22.205] 	ABI class: X.Org Video Driver, version 14.1
[    22.205] (II) LoadModule: "vesa"
[    22.206] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.206] (II) Module vesa: vendor="X.Org Foundation"
[    22.206] 	compiled for 1.14.1, module version = 2.3.2
[    22.206] 	Module class: X.Org Video Driver
[    22.206] 	ABI class: X.Org Video Driver, version 14.1
[    22.206] (II) LoadModule: "modesetting"
[    22.206] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.207] (II) Module modesetting: vendor="X.Org Foundation"
[    22.207] 	compiled for 1.14.1, module version = 0.8.0
[    22.207] 	Module class: X.Org Video Driver
[    22.207] 	ABI class: X.Org Video Driver, version 14.1
[    22.207] (II) LoadModule: "fbdev"
[    22.207] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.207] (II) Module fbdev: vendor="X.Org Foundation"
[    22.207] 	compiled for 1.14.1, module version = 0.4.3
[    22.208] 	Module class: X.Org Video Driver
[    22.208] 	ABI class: X.Org Video Driver, version 14.1
[    22.208] (==) Matched nvidia as autoconfigured driver 0
[    22.208] (==) Matched nouveau as autoconfigured driver 1
[    22.208] (==) Matched nvidia as autoconfigured driver 2
[    22.208] (==) Matched nouveau as autoconfigured driver 3
[    22.208] (==) Matched vesa as autoconfigured driver 4
[    22.208] (==) Matched modesetting as autoconfigured driver 5
[    22.208] (==) Matched fbdev as autoconfigured driver 6
[    22.208] (==) Assigned the driver to the xf86ConfigLayout
[    22.208] (II) LoadModule: "nvidia"
[    22.209] (WW) Warning, couldn't open module nvidia
[    22.209] (II) UnloadModule: "nvidia"
[    22.209] (II) Unloading nvidia
[    22.209] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    22.209] (II) LoadModule: "nouveau"
[    22.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.209] (II) Module nouveau: vendor="X.Org Foundation"
[    22.209] 	compiled for 1.14.2.901, module version = 1.0.9
[    22.209] 	Module class: X.Org Video Driver
[    22.209] 	ABI class: X.Org Video Driver, version 14.1
[    22.209] (II) UnloadModule: "nouveau"
[    22.209] (II) Unloading nouveau
[    22.210] (II) Failed to load module "nouveau" (already loaded, 0)
[    22.210] (II) LoadModule: "vesa"
[    22.210] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.210] (II) Module vesa: vendor="X.Org Foundation"
[    22.210] 	compiled for 1.14.1, module version = 2.3.2
[    22.210] 	Module class: X.Org Video Driver
[    22.210] 	ABI class: X.Org Video Driver, version 14.1
[    22.210] (II) UnloadModule: "vesa"
[    22.210] (II) Unloading vesa
[    22.210] (II) Failed to load module "vesa" (already loaded, 0)
[    22.210] (II) LoadModule: "modesetting"
[    22.212] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.212] (II) Module modesetting: vendor="X.Org Foundation"
[    22.212] 	compiled for 1.14.1, module version = 0.8.0
[    22.212] 	Module class: X.Org Video Driver
[    22.212] 	ABI class: X.Org Video Driver, version 14.1
[    22.212] (II) UnloadModule: "modesetting"
[    22.212] (II) Unloading modesetting
[    22.212] (II) Failed to load module "modesetting" (already loaded, 0)
[    22.212] (II) LoadModule: "fbdev"
[    22.213] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.213] (II) Module fbdev: vendor="X.Org Foundation"
[    22.213] 	compiled for 1.14.1, module version = 0.4.3
[    22.213] 	Module class: X.Org Video Driver
[    22.213] 	ABI class: X.Org Video Driver, version 14.1
[    22.213] (II) UnloadModule: "fbdev"
[    22.213] (II) Unloading fbdev
[    22.213] (II) Failed to load module "fbdev" (already loaded, 0)
[    22.213] (II) NOUVEAU driver Date:   Wed Jul 31 10:51:03 2013 +1000
[    22.213] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.213] 	RIVA TNT        (NV04)
[    22.213] 	RIVA TNT2       (NV05)
[    22.213] 	GeForce 256     (NV10)
[    22.213] 	GeForce 2       (NV11, NV15)
[    22.213] 	GeForce 4MX     (NV17, NV18)
[    22.213] 	GeForce 3       (NV20)
[    22.213] 	GeForce 4Ti     (NV25, NV28)
[    22.213] 	GeForce FX      (NV3x)
[    22.214] 	GeForce 6       (NV4x)
[    22.214] 	GeForce 7       (G7x)
[    22.214] 	GeForce 8       (G8x)
[    22.214] 	GeForce GTX 200 (NVA0)
[    22.214] 	GeForce GTX 400 (NVC0)
[    22.214] (II) VESA: driver for VESA chipsets: vesa
[    22.214] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    22.214] (II) FBDEV: driver for framebuffer: fbdev
[    22.214] (++) using VT number 7

[    22.215] (II) [drm] nouveau interface version: 1.1.1
[    22.215] (WW) Falling back to old probe method for vesa
[    22.215] (WW) Falling back to old probe method for modesetting
[    22.215] (WW) Falling back to old probe method for fbdev
[    22.215] (II) Loading sub module "fbdevhw"
[    22.215] (II) LoadModule: "fbdevhw"
[    22.216] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.216] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.216] 	compiled for 1.14.3, module version = 0.0.2
[    22.216] 	ABI class: X.Org Video Driver, version 14.1
[    22.217] (II) Loading sub module "dri2"
[    22.217] (II) LoadModule: "dri2"
[    22.217] (II) Module "dri2" already built-in
[    22.217] (--) NOUVEAU(0): Chipset: "NVIDIA NV05"
[    22.217] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.217] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    22.217] (==) NOUVEAU(0): RGB weight 888
[    22.217] (==) NOUVEAU(0): Default visual is TrueColor
[    22.217] (==) NOUVEAU(0): Using HW cursor
[    22.217] (==) NOUVEAU(0): Page flipping enabled
[    22.217] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[    22.239] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    22.264] (II) NOUVEAU(0): EDID for output VGA-1
[    22.264] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[    22.264] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.264] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.264] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    22.264] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    22.264] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[    22.264] (II) NOUVEAU(0): Output VGA-1 connected
[    22.264] (II) NOUVEAU(0): Using exact sizes for initial modes
[    22.264] (II) NOUVEAU(0): Output VGA-1 using initial mode 1024x768
[    22.264] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.264] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 0)
[    22.264] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    22.264] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.264] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    22.264] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.264] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    22.264] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    22.264] (**) NOUVEAU(0):  Driver mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz
[    22.264] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz e)
[    22.264] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    22.264] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[    22.264] (==) NOUVEAU(0): DPI set to (96, 96)
[    22.264] (II) Loading sub module "fb"
[    22.264] (II) LoadModule: "fb"
[    22.265] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.265] (II) Module fb: vendor="X.Org Foundation"
[    22.265] 	compiled for 1.14.3, module version = 1.0.0
[    22.265] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.265] (II) Loading sub module "exa"
[    22.265] (II) LoadModule: "exa"
[    22.266] (II) Loading /usr/lib/xorg/modules/libexa.so
[    22.266] (II) Module exa: vendor="X.Org Foundation"
[    22.266] 	compiled for 1.14.3, module version = 2.6.0
[    22.266] 	ABI class: X.Org Video Driver, version 14.1
[    22.266] (II) Loading sub module "shadowfb"
[    22.266] (II) LoadModule: "shadowfb"
[    22.266] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    22.266] (II) Module shadowfb: vendor="X.Org Foundation"
[    22.266] 	compiled for 1.14.3, module version = 1.0.0
[    22.267] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.267] (II) UnloadModule: "vesa"
[    22.267] (II) Unloading vesa
[    22.267] (II) UnloadModule: "modesetting"
[    22.267] (II) Unloading modesetting
[    22.267] (II) UnloadModule: "fbdev"
[    22.267] (II) Unloading fbdev
[    22.267] (II) UnloadSubModule: "fbdevhw"
[    22.267] (II) Unloading fbdevhw
[    22.267] (--) Depth 24 pixmap format is 32 bpp
[    22.268] (II) NOUVEAU(0): Opened GPU channel 0
[    22.269] (II) NOUVEAU(0): [DRI2] Setup complete
[    22.269] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau_vieux
[    22.269] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau_vieux
[    22.269] (II) EXA(0): Driver allocated offscreen pixmaps
[    22.269] (II) EXA(0): Driver registered support for the following operations:
[    22.269] (II)         Solid
[    22.269] (II)         Copy
[    22.269] (II)         UploadToScreen
[    22.269] (II)         DownloadFromScreen
[    22.269] (==) NOUVEAU(0): Backing store disabled
[    22.269] (==) NOUVEAU(0): Silken mouse enabled
[    22.269] (==) NOUVEAU(0): DPMS enabled
[    22.269] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.270] (--) RandR disabled
[    22.285] (II) SELinux: Disabled on system
[    22.388] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    22.388] (II) AIGLX: enabled GLX_INTEL_swap_event
[    22.388] (II) AIGLX: enabled GLX_ARB_create_context
[    22.388] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    22.388] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    22.388] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    22.388] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    22.389] (II) AIGLX: Loaded and initialized nouveau_vieux
[    22.389] (II) GLX: Initialized DRI2 GL provider for screen 0
[    22.401] (II) NOUVEAU(0): NVEnterVT is called.
[    22.402] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[    22.402] resize called 1024 768
[    22.419] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.433] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.433] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.433] (II) LoadModule: "evdev"
[    22.434] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.448] (II) Module evdev: vendor="X.Org Foundation"
[    22.449] 	compiled for 1.14.1, module version = 2.7.3
[    22.449] 	Module class: X.Org XInput Driver
[    22.449] 	ABI class: X.Org XInput driver, version 19.1
[    22.449] (II) Using input driver 'evdev' for 'Power Button'
[    22.449] (**) Power Button: always reports core events
[    22.449] (**) evdev: Power Button: Device: "/dev/input/event1"
[    22.449] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.449] (--) evdev: Power Button: Found keys
[    22.449] (II) evdev: Power Button: Configuring as keyboard
[    22.449] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.449] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    22.449] (**) Option "xkb_rules" "evdev"
[    22.449] (**) Option "xkb_model" "pc105"
[    22.449] (**) Option "xkb_layout" "us"
[    22.450] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.450] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.450] (II) Using input driver 'evdev' for 'Power Button'
[    22.451] (**) Power Button: always reports core events
[    22.451] (**) evdev: Power Button: Device: "/dev/input/event0"
[    22.451] (--) evdev: Power Button: Vendor 0 Product 0x1
[    22.451] (--) evdev: Power Button: Found keys
[    22.451] (II) evdev: Power Button: Configuring as keyboard
[    22.451] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.451] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    22.451] (**) Option "xkb_rules" "evdev"
[    22.451] (**) Option "xkb_model" "pc105"
[    22.451] (**) Option "xkb_layout" "us"
[    22.455] (II) config/udev: Adding input device HP HP USB Laser Mouse (/dev/input/event3)
[    22.455] (**) HP HP USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[    22.455] (II) Using input driver 'evdev' for 'HP HP USB Laser Mouse'
[    22.455] (**) HP HP USB Laser Mouse: always reports core events
[    22.455] (**) evdev: HP HP USB Laser Mouse: Device: "/dev/input/event3"
[    22.455] (--) evdev: HP HP USB Laser Mouse: Vendor 0x3f0 Product 0x2c24
[    22.456] (--) evdev: HP HP USB Laser Mouse: Found 3 mouse buttons
[    22.456] (--) evdev: HP HP USB Laser Mouse: Found scroll wheel(s)
[    22.456] (--) evdev: HP HP USB Laser Mouse: Found relative axes
[    22.456] (--) evdev: HP HP USB Laser Mouse: Found x and y relative axes
[    22.456] (II) evdev: HP HP USB Laser Mouse: Configuring as mouse
[    22.456] (II) evdev: HP HP USB Laser Mouse: Adding scrollwheel support
[    22.456] (**) evdev: HP HP USB Laser Mouse: YAxisMapping: buttons 4 and 5
[    22.456] (**) evdev: HP HP USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.456] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.2/usb1/1-2/1-2:1.0/input/input3/event3"
[    22.456] (II) XINPUT: Adding extended input device "HP HP USB Laser Mouse" (type: MOUSE, id 8)
[    22.456] (II) evdev: HP HP USB Laser Mouse: initialized for relative axes.
[    22.456] (**) HP HP USB Laser Mouse: (accel) keeping acceleration scheme 1
[    22.456] (**) HP HP USB Laser Mouse: (accel) acceleration profile 0
[    22.456] (**) HP HP USB Laser Mouse: (accel) acceleration factor: 2.000
[    22.456] (**) HP HP USB Laser Mouse: (accel) acceleration threshold: 4
[    22.457] (II) config/udev: Adding input device HP HP USB Laser Mouse (/dev/input/mouse0)
[    22.457] (II) No input driver specified, ignoring this device.
[    22.457] (II) This device may have been added with another device file.
[    22.457] (II) config/udev: Adding drm device (/dev/dri/card0)
[    22.457] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    22.460] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    22.460] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    22.460] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    22.460] (**) AT Translated Set 2 keyboard: always reports core events
[    22.460] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    22.460] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    22.460] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    22.460] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    22.460] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    22.460] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    22.460] (**) Option "xkb_rules" "evdev"
[    22.460] (**) Option "xkb_model" "pc105"
[    22.460] (**) Option "xkb_layout" "us"
********************
>>>> This is around the point when lubuntu hung for a few seconds
********************
(EE) [mi] EQ overflowing.  Additional events will be discarded until existing events are processed.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb76ee0b9]
(EE) 1: /usr/bin/X (mieqEnqueue+0x213) [0xb76ce113]
(EE) 2: /usr/bin/X (QueuePointerEvents+0x6d) [0xb75a21ad]
(EE) 3: /usr/bin/X (xf86PostMotionEventM+0x24b) [0xb75db84b]
(EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0xb6c3d000+0x4726) [0xb6c41726]
(EE) 5: /usr/bin/X (0xb754e000+0x7ce85) [0xb75cae85]
(EE) 6: /usr/bin/X (0xb754e000+0xa7d5b) [0xb75f5d5b]
(EE) 7: (vdso) (__kernel_sigreturn+0x0) [0xb752b400]
(EE) 8: (vdso) (__kernel_vsyscall+0x10) [0xb752b424]
(EE) 9: /lib/i386-linux-gnu/libc.so.6 (ioctl+0x19) [0xb7207d09]
(EE) 10: /usr/lib/i386-linux-gnu/libdrm.so.2 (drmIoctl+0x40) [0xb742a9e0]
(EE) 11: /usr/lib/i386-linux-gnu/libdrm.so.2 (drmCommandWrite+0x3c) [0xb742d3dc]
(EE) 12: /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2 (nouveau_bo_wait+0xa5) [0xb6c4cee5]
(EE) 13: /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2 (nouveau_bo_map+0x33) [0xb6c4cf43]
(EE) 14: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0xb6c53000+0x5592) [0xb6c58592]
(EE) 15: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x3ec9) [0xb6c00ec9]
(EE) 16: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x75d3) [0xb6c045d3]
(EE) 17: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x10710) [0xb6c0d710]
(EE) 18: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x98c0) [0xb6c068c0]
(EE) 19: /usr/bin/X (miCopyRegion+0x1b8) [0xb76cc248]
(EE) 20: /usr/bin/X (miDoCopy+0x518) [0xb76cc868]
(EE) 21: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x7d62) [0xb6c04d62]
(EE) 22: /usr/bin/X (0xb754e000+0x126480) [0xb7674480]
(EE) 23: /usr/bin/X (0xb754e000+0x17f75f) [0xb76cd75f]
(EE) 24: /usr/bin/X (0xb754e000+0x18f25a) [0xb76dd25a]
(EE) 25: /usr/bin/X (0xb754e000+0x190807) [0xb76de807]
(EE) 26: /usr/bin/X (BlockHandler+0x49) [0xb758e809]
(EE) 27: /usr/bin/X (WaitForSomething+0xf8) [0xb76eb3e8]
(EE) 28: /usr/bin/X (0xb754e000+0x3c20e) [0xb758a20e]
(EE) 29: /usr/bin/X (0xb754e000+0x2a52a) [0xb757852a]
(EE) 30: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0xb7138905]
(EE) 31: /usr/bin/X (0xb754e000+0x2a908) [0xb7578908]
(EE) 
(EE) [mi] These backtraces from mieqEnqueue may point to a culprit higher up the stack.
(EE) [mi] mieq is *NOT* the cause.  It is a victim.
(EE) [mi] EQ overflow continuing.  100 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb76ee0b9]
(EE) 1: /usr/bin/X (mieqEnqueue+0xe5) [0xb76cdfe5]
(EE) 2: /usr/bin/X (QueuePointerEvents+0x6d) [0xb75a21ad]
(EE) 3: /usr/bin/X (xf86PostMotionEventM+0x24b) [0xb75db84b]
(EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0xb6c3d000+0x4726) [0xb6c41726]
(EE) 5: /usr/bin/X (0xb754e000+0x7ce85) [0xb75cae85]
(EE) 6: /usr/bin/X (0xb754e000+0xa7d5b) [0xb75f5d5b]
(EE) 7: (vdso) (__kernel_sigreturn+0x0) [0xb752b400]
(EE) 8: (vdso) (__kernel_vsyscall+0x10) [0xb752b424]
(EE) 9: /lib/i386-linux-gnu/libc.so.6 (ioctl+0x19) [0xb7207d09]
(EE) 10: /usr/lib/i386-linux-gnu/libdrm.so.2 (drmIoctl+0x40) [0xb742a9e0]
(EE) 11: /usr/lib/i386-linux-gnu/libdrm.so.2 (drmCommandWrite+0x3c) [0xb742d3dc]
(EE) 12: /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2 (nouveau_bo_wait+0xa5) [0xb6c4cee5]
(EE) 13: /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2 (nouveau_bo_map+0x33) [0xb6c4cf43]
(EE) 14: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0xb6c53000+0x5592) [0xb6c58592]
(EE) 15: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x3ec9) [0xb6c00ec9]
(EE) 16: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x75d3) [0xb6c045d3]
(EE) 17: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x10710) [0xb6c0d710]
(EE) 18: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x98c0) [0xb6c068c0]
(EE) 19: /usr/bin/X (miCopyRegion+0x1b8) [0xb76cc248]
(EE) 20: /usr/bin/X (miDoCopy+0x518) [0xb76cc868]
(EE) 21: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x7d62) [0xb6c04d62]
(EE) 22: /usr/bin/X (0xb754e000+0x126480) [0xb7674480]
(EE) 23: /usr/bin/X (0xb754e000+0x17f75f) [0xb76cd75f]
(EE) 24: /usr/bin/X (0xb754e000+0x18f25a) [0xb76dd25a]
(EE) 25: /usr/bin/X (0xb754e000+0x190807) [0xb76de807]
(EE) 26: /usr/bin/X (BlockHandler+0x49) [0xb758e809]
(EE) 27: /usr/bin/X (WaitForSomething+0xf8) [0xb76eb3e8]
(EE) 28: /usr/bin/X (0xb754e000+0x3c20e) [0xb758a20e]
(EE) 29: /usr/bin/X (0xb754e000+0x2a52a) [0xb757852a]
(EE) 30: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0xb7138905]
(EE) 31: /usr/bin/X (0xb754e000+0x2a908) [0xb7578908]
(EE) 
(EE) [mi] EQ overflow continuing.  200 events have been dropped.
(EE) 
(EE) Backtrace:
(EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb76ee0b9]
(EE) 1: /usr/bin/X (mieqEnqueue+0xe5) [0xb76cdfe5]
(EE) 2: /usr/bin/X (QueuePointerEvents+0x6d) [0xb75a21ad]
(EE) 3: /usr/bin/X (xf86PostMotionEventM+0x24b) [0xb75db84b]
(EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0xb6c3d000+0x4726) [0xb6c41726]
(EE) 5: /usr/bin/X (0xb754e000+0x7ce85) [0xb75cae85]
(EE) 6: /usr/bin/X (0xb754e000+0xa7d5b) [0xb75f5d5b]
(EE) 7: (vdso) (__kernel_sigreturn+0x0) [0xb752b400]
(EE) 8: (vdso) (__kernel_vsyscall+0x10) [0xb752b424]
(EE) 9: /lib/i386-linux-gnu/libc.so.6 (ioctl+0x19) [0xb7207d09]
(EE) 10: /usr/lib/i386-linux-gnu/libdrm.so.2 (drmIoctl+0x40) [0xb742a9e0]
(EE) 11: /usr/lib/i386-linux-gnu/libdrm.so.2 (drmCommandWrite+0x3c) [0xb742d3dc]
(EE) 12: /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2 (nouveau_bo_wait+0xa5) [0xb6c4cee5]
(EE) 13: /usr/lib/i386-linux-gnu/libdrm_nouveau.so.2 (nouveau_bo_map+0x33) [0xb6c4cf43]
(EE) 14: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0xb6c53000+0x5592) [0xb6c58592]
(EE) 15: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x3ec9) [0xb6c00ec9]
(EE) 16: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x75d3) [0xb6c045d3]
(EE) 17: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x10710) [0xb6c0d710]
(EE) 18: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x98c0) [0xb6c068c0]
(EE) 19: /usr/bin/X (miCopyRegion+0x1b8) [0xb76cc248]
(EE) 20: /usr/bin/X (miDoCopy+0x518) [0xb76cc868]
(EE) 21: /usr/lib/xorg/modules/libexa.so (0xb6bfd000+0x7d62) [0xb6c04d62]
(EE) 22: /usr/bin/X (0xb754e000+0x126480) [0xb7674480]
(EE) 23: /usr/bin/X (0xb754e000+0x17f75f) [0xb76cd75f]
(EE) 24: /usr/bin/X (0xb754e000+0x18f25a) [0xb76dd25a]
(EE) 25: /usr/bin/X (0xb754e000+0x190807) [0xb76de807]
(EE) 26: /usr/bin/X (BlockHandler+0x49) [0xb758e809]
(EE) 27: /usr/bin/X (WaitForSomething+0xf8) [0xb76eb3e8]
(EE) 28: /usr/bin/X (0xb754e000+0x3c20e) [0xb758a20e]
(EE) 29: /usr/bin/X (0xb754e000+0x2a52a) [0xb757852a]
(EE) 30: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0xb7138905]
(EE) 31: /usr/bin/X (0xb754e000+0x2a908) [0xb7578908]
(EE) 
[   298.749] [mi] Increasing EQ size to 512 to prevent dropped events.
[   298.751] [mi] EQ processing has resumed after 235 dropped events.
[   298.751] [mi] This may be caused my a misbehaving driver monopolizing the server's resources.

---

