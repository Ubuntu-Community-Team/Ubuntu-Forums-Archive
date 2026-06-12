---
title: "ATI Catalyst, no gdm today morning. Why didn't I bought nvidia?"
date: 2011-02-22
forum: Desktop Environments
---

### Post by dpc.ucore.info on 2011-02-22
So I was stupid and careless enough to buy system with ATI Radeon HD6850.

I have Maverick installed (64 bit) and everything was fine yesterday, I did usual update and today I get text prompt.

I tried everything I already learned and upgraded to Catalyst 11.2 too (built packages from downloader installer), but with no luck. I see that aticonfig is now recognizing my card, which is promissing, but I'm unable to get the system to work with fglrx anyway.

I've purged the fglrx and friends, removed /etc/X11/xorg.conf and now I'm running on vesa with lower resolution.

But I'm quite pissed off for loosing my morning on fixing (or failing to fix) yet another problem with ATI.

Please help me restore my good mood and screen resolution.



```

$ uname -r
2.6.35-27-generic

$ less /var/log/apt/history.log
Start-Date: 2011-02-21  19:30:32
Commandline: apt-get dist-upgrade
Install: linux-image-2.6.35-27-generic:amd64 (2.6.35-27.47)
Upgrade: libbrasero-media1:amd64 (2.32.0-0ubuntu2.1, 2.32.0-0ubuntu2.2), linux-generic:amd64 (2.6.35.26.33, 2.6.35.27.34), software-center:amd64 (3.0.7, 3.0.8), linux-firmware:amd64 (1.38.3, 1.38.4), linux-image-generic:amd64 (2.6.35.26.33, 2.6.35.27.34), policykit-1-gnome:amd64 (0.96-2ubuntu4, 0.99-1ubuntu1~maverick1~ppa1), brasero-cdrkit:amd64 (2.32.0-0ubuntu2.1, 2.32.0-0ubuntu2.2), brasero-common:amd64 (2.32.0-0ubuntu2.1, 2.32.0-0ubuntu2.2), brasero:amd64 (2.32.0-0ubuntu2.1, 2.32.0-0ubuntu2.2), linux-libc-dev:amd64 (2.6.35-1026.46, 2.6.35-1027.47), inkscape:amd64 (0.48.0-1ubuntu1, 0.48.0-1ubuntu1.1)
End-Date: 2011-02-21  19:32:20

Start-Date: 2011-02-22  08:27:32
Commandline: apt-get purge fglrx
Purge: fglrx:amd64 (8.821-0ubuntu1), fglrx-dev:amd64 (8.821-0ubuntu1), fglrx-amdcccle:amd64 (8.821-0ubuntu1)
End-Date: 2011-02-22  08:28:02

Start-Date: 2011-02-22  08:37:20
Commandline: apt-get purge fglrx
Purge: fglrx:amd64 (8.821-0ubuntu1), fglrx-dev:amd64 (8.821-0ubuntu1), fglrx-amdcccle:amd64 (8.821-0ubuntu1)
End-Date: 2011-02-22  08:37:59

Start-Date: 2011-02-22  08:55:31
Commandline: apt-get purge fglrx
Purge: fglrx:amd64 (8.821-0ubuntu1), fglrx-dev:amd64 (8.821-0ubuntu1), fglrx-amdcccle:amd64 (8.821-0ubuntu1)
End-Date: 2011-02-22  08:56:11

Start-Date: 2011-02-22  08:56:56
Commandline: apt-get remove linux-image-2.6.35-25-generic linux-image-2.6.35-26-generic linux-headers-2.6.35-25 linux-headers-2.6.35-26
Remove: linux-image-2.6.35-25-generic:amd64 (2.6.35-25.44), linux-headers-2.6.35-25-generic:amd64 (2.6.35-25.44), linux-image-2.6.35-26-generic:amd64 (2.6.35-26.46), linux-headers-2.6.35-25:amd64 (2.6.35-25.44)
End-Date: 2011-02-22  08:57:15

Start-Date: 2011-02-22  09:18:29
Commandline: apt-get purge fglrx
Purge: fglrx:amd64 (8.821-0ubuntu1), fglrx-dev:amd64 (8.821-0ubuntu1), fglrx-amdcccle:amd64 (8.821-0ubuntu1)
End-Date: 2011-02-22  09:18:58

$ sudo cat /var/log/Xorg.1.log
[   355.907] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   355.907] X Protocol Version 11, Revision 0
[   355.907] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[   355.907] Current Operating System: Linux mutex 2.6.35-27-generic #47-Ubuntu SMP Fri Feb 11 22:52:49 UTC 2011 x86_64
[   355.907] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=e176231d-7adc-47c4-864f-60ccd600f314 ro quiet splash
[   355.907] Build Date: 09 January 2011  12:14:27PM
[   355.907] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[   355.907] Current version of pixman: 0.18.4
[   355.907] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   355.907] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   355.907] (==) Log file: "/var/log/Xorg.1.log", Time: Tue Feb 22 09:10:51 2011
[   355.908] (==) Using config file: "/etc/X11/xorg.conf"
[   355.908] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   355.908] (==) ServerLayout "aticonfig Layout"
[   355.908] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[   355.908] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[   355.909] (**) |   |-->Device "aticonfig-Device[0]-0"
[   355.909] (==) Automatically adding devices
[   355.909] (==) Automatically enabling devices
[   355.909] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   355.909] 	Entry deleted from font path.
[   355.909] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   355.909] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   355.909] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   355.909] (II) Loader magic: 0x7d17a0
[   355.909] (II) Module ABI versions:
[   355.909] 	X.Org ANSI C Emulation: 0.4
[   355.909] 	X.Org Video Driver: 8.0
[   355.909] 	X.Org XInput driver : 11.0
[   355.909] 	X.Org Server Extension : 4.0
[   355.911] (--) PCI:*(0:2:0:0) 1002:6739:1787:200f rev 0, Mem @ 0xd0000000/268435456, 0xfebe0000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[   355.911] (II) Open ACPI successful (/var/run/acpid.socket)
[   355.911] (II) "extmod" will be loaded by default.
[   355.911] (II) "dbe" will be loaded by default.
[   355.911] (II) "glx" will be loaded by default.
[   355.911] (II) "record" will be loaded by default.
[   355.911] (II) "dri" will be loaded by default.
[   355.911] (II) "dri2" will be loaded by default.
[   355.911] (II) LoadModule: "extmod"
[   355.912] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   355.912] (II) Module extmod: vendor="X.Org Foundation"
[   355.912] 	compiled for 1.9.0, module version = 1.0.0
[   355.912] 	Module class: X.Org Server Extension
[   355.912] 	ABI class: X.Org Server Extension, version 4.0
[   355.912] (II) Loading extension MIT-SCREEN-SAVER
[   355.912] (II) Loading extension XFree86-VidModeExtension
[   355.912] (II) Loading extension XFree86-DGA
[   355.912] (II) Loading extension DPMS
[   355.912] (II) Loading extension XVideo
[   355.912] (II) Loading extension XVideo-MotionCompensation
[   355.912] (II) Loading extension X-Resource
[   355.912] (II) LoadModule: "dbe"
[   355.913] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   355.913] (II) Module dbe: vendor="X.Org Foundation"
[   355.913] 	compiled for 1.9.0, module version = 1.0.0
[   355.913] 	Module class: X.Org Server Extension
[   355.913] 	ABI class: X.Org Server Extension, version 4.0
[   355.913] (II) Loading extension DOUBLE-BUFFER
[   355.913] (II) LoadModule: "glx"
[   355.913] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[   355.913] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[   355.913] 	compiled for 6.9.0, module version = 1.0.0
[   355.913] (II) Loading extension GLX
[   355.913] (II) LoadModule: "record"
[   355.913] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   355.913] (II) Module record: vendor="X.Org Foundation"
[   355.913] 	compiled for 1.9.0, module version = 1.13.0
[   355.913] 	Module class: X.Org Server Extension
[   355.913] 	ABI class: X.Org Server Extension, version 4.0
[   355.913] (II) Loading extension RECORD
[   355.913] (II) LoadModule: "dri"
[   355.914] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   355.914] (II) Module dri: vendor="X.Org Foundation"
[   355.914] 	compiled for 1.9.0, module version = 1.0.0
[   355.914] 	ABI class: X.Org Server Extension, version 4.0
[   355.914] (II) Loading extension XFree86-DRI
[   355.914] (II) LoadModule: "dri2"
[   355.914] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   355.914] (II) Module dri2: vendor="X.Org Foundation"
[   355.914] 	compiled for 1.9.0, module version = 1.2.0
[   355.914] 	ABI class: X.Org Server Extension, version 4.0
[   355.914] (II) Loading extension DRI2
[   355.914] (II) LoadModule: "fglrx"
[   355.914] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   355.929] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[   355.929] 	compiled for 1.4.99.906, module version = 8.82.8
[   355.929] 	Module class: X.Org Video Driver
[   355.929] (II) Loading sub module "fglrxdrm"
[   355.929] (II) LoadModule: "fglrxdrm"
[   355.929] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   355.930] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[   355.930] 	compiled for 1.4.99.906, module version = 8.82.8
[   355.930] (II) ATI Proprietary Linux Driver Version Identifier:8.82.8
[   355.930] (II) ATI Proprietary Linux Driver Release Identifier: 8.821                                
[   355.930] (II) ATI Proprietary Linux Driver Build Date: Jan 26 2011 17:20:41
[   355.930] (--) using VT number 8

[   355.943] (WW) Falling back to old probe method for fglrx
[   355.946] (II) Loading PCS database from /etc/ati/amdpcsdb
[   355.947] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:2:0) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[   355.947] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[   355.947] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[   355.947] (II) AMD Video driver is signed
[   355.947] (II) fglrx(0): pEnt->device->identifier=0x1635680
[   355.947] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[   355.947] (II) Loading sub module "vgahw"
[   355.947] (II) LoadModule: "vgahw"
[   355.948] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   355.948] (II) Module vgahw: vendor="X.Org Foundation"
[   355.948] 	compiled for 1.9.0, module version = 0.1.0
[   355.948] 	ABI class: X.Org Video Driver, version 8.0
[   355.948] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[   355.948] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   355.948] (==) fglrx(0): Default visual is TrueColor
[   355.948] (**) fglrx(0): Option "DPMS" "true"
[   355.948] (==) fglrx(0): RGB weight 888
[   355.948] (II) fglrx(0): Using 8 bits per RGB 
[   355.948] (==) fglrx(0): Buffer Tiling is ON
[   355.948] (II) Loading sub module "fglrxdrm"
[   355.948] (II) LoadModule: "fglrxdrm"
[   355.948] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   355.952] ukiDynamicMajor: failed to open /proc/ati/major
[   355.952] ukiDynamicMajor: failed to open /proc/ati/major
[   355.952] (==) fglrx(0): NoAccel = NO
[   355.953] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[   355.953] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series " (Chipset = 0x6739)
[   355.953] (--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x200f)
[   355.953] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[   355.953] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[   355.953] (--) fglrx(0): MMIO registers at 0xfebe0000
[   355.953] (--) fglrx(0): I/O port at 0x0000e000
[   355.953] (==) fglrx(0): ROM-BIOS at 0x000c0000
[   355.965] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[   355.966] (EE) fglrx(0): ACPI: DRM connection failed
[   356.146] (II) Loading sub module "vbe"
[   356.146] (II) LoadModule: "vbe"
[   356.147] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   356.147] (II) Module vbe: vendor="X.Org Foundation"
[   356.147] 	compiled for 1.9.0, module version = 1.1.0
[   356.147] 	ABI class: X.Org Video Driver, version 8.0
[   356.147] (II) fglrx(0): VESA BIOS detected
[   356.147] (II) fglrx(0): VESA VBE Version 3.0
[   356.147] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[   356.147] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[   356.147] (II) fglrx(0): VESA VBE OEM Software Rev: 13.7
[   356.147] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[   356.147] (II) fglrx(0): VESA VBE OEM Product: BARTS
[   356.147] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[   356.171] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[   356.171] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[   356.171] (II) fglrx(0): PCIE card detected
[   356.171] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[   356.171] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   356.171] (EE) fglrx(0): ACPI: DRM connection failed
[   356.171] (WW) fglrx(0): Hasn't establisted DRM connection
[   356.171] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[   356.171] (WW) fglrx(0): No DRM connection for driver fglrx.
[   356.171] (II) fglrx(0): RandR 1.2 support is enabled!
[   356.171] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[   356.172] (==) fglrx(0): Center Mode is disabled 
[   356.172] (II) Loading sub module "fb"
[   356.172] (II) LoadModule: "fb"
[   356.172] (II) Loading /usr/lib/xorg/modules/libfb.so
[   356.172] (II) Module fb: vendor="X.Org Foundation"
[   356.172] 	compiled for 1.9.0, module version = 1.0.0
[   356.172] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   356.172] (II) Loading sub module "ddc"
[   356.172] (II) LoadModule: "ddc"
[   356.172] (II) Module "ddc" already built-in
[   356.270] (II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
[   356.270] (II) fglrx(0): Output DFP2 has no monitor section
[   356.270] (II) fglrx(0): Output DFP3 has no monitor section
[   356.270] (II) fglrx(0): Output DFP4 has no monitor section
[   356.270] (II) fglrx(0): Output CRT1 has no monitor section
[   356.270] (II) Loading sub module "ddc"
[   356.270] (II) LoadModule: "ddc"
[   356.270] (II) Module "ddc" already built-in
[   356.271] (II) fglrx(0): Connected Display0: CRT1
[   356.271] (II) fglrx(0): Display0 EDID data ---------------------------
[   356.271] (II) fglrx(0): Manufacturer: SAM  Model: 59a  Serial#: 1129132594
[   356.271] (II) fglrx(0): Year: 2009  Week: 33
[   356.271] (II) fglrx(0): EDID Version: 1.3
[   356.271] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   356.271] (II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
[   356.271] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[   356.271] (II) fglrx(0): Gamma: 2.20
[   356.271] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[   356.271] (II) fglrx(0): First detailed timing is preferred mode
[   356.271] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
[   356.271] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[   356.271] (II) fglrx(0): Supported established timings:
[   356.271] (II) fglrx(0): 640x480@60Hz
[   356.271] (II) fglrx(0): 800x600@56Hz
[   356.271] (II) fglrx(0): 800x600@60Hz
[   356.271] (II) fglrx(0): 1024x768@60Hz
[   356.271] (II) fglrx(0): Manufacturer's mask: 0
[   356.271] (II) fglrx(0): Supported standard timings:
[   356.271] (II) fglrx(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   356.271] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   356.271] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   356.271] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   356.271] (II) fglrx(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   356.271] (II) fglrx(0): Supported detailed timing:
[   356.271] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[   356.271] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   356.271] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   356.271] (II) fglrx(0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 75 kHz, PixClock max 175 MHz
[   356.271] (II) fglrx(0): Monitor name: SyncMaster
[   356.271] (II) fglrx(0): Serial No: HVCS802461
[   356.271] (II) fglrx(0): EDID (in hex):
[   356.271] (II) fglrx(0): 	00ffffffffffff004c2d9a0532324d43
[   356.271] (II) fglrx(0): 	211301030e301b782a3d81a6564a9a24
[   356.271] (II) fglrx(0): 	1250542308008100814081809500b300
[   356.271] (II) fglrx(0): 	010101010101023a801871382d40582c
[   356.271] (II) fglrx(0): 	4500dd0c1100001e000000fd00383d1e
[   356.271] (II) fglrx(0): 	4b11000a202020202020000000fc0053
[   356.271] (II) fglrx(0): 	796e634d61737465720a2020000000ff
[   356.271] (II) fglrx(0): 	00485643533830323436310a20200011
[   356.271] (II) fglrx(0): End of Display0 EDID data --------------------
[   356.281] (II) fglrx(0): EDID for output DFP1
[   356.281] (II) fglrx(0): EDID for output DFP2
[   356.281] (II) fglrx(0): EDID for output DFP3
[   356.281] (II) fglrx(0): EDID for output DFP4
[   356.281] (II) fglrx(0): EDID for output CRT1
[   356.281] (II) fglrx(0): Manufacturer: SAM  Model: 59a  Serial#: 1129132594
[   356.281] (II) fglrx(0): Year: 2009  Week: 33
[   356.281] (II) fglrx(0): EDID Version: 1.3
[   356.281] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[   356.281] (II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
[   356.281] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[   356.282] (II) fglrx(0): Gamma: 2.20
[   356.282] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[   356.282] (II) fglrx(0): First detailed timing is preferred mode
[   356.282] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
[   356.282] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[   356.282] (II) fglrx(0): Supported established timings:
[   356.282] (II) fglrx(0): 640x480@60Hz
[   356.282] (II) fglrx(0): 800x600@56Hz
[   356.282] (II) fglrx(0): 800x600@60Hz
[   356.282] (II) fglrx(0): 1024x768@60Hz
[   356.282] (II) fglrx(0): Manufacturer's mask: 0
[   356.282] (II) fglrx(0): Supported standard timings:
[   356.282] (II) fglrx(0): #0: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   356.282] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[   356.282] (II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   356.282] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[   356.282] (II) fglrx(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   356.282] (II) fglrx(0): Supported detailed timing:
[   356.282] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[   356.282] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   356.282] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   356.282] (II) fglrx(0): Ranges: V min: 56 V max: 61 Hz, H min: 30 H max: 75 kHz, PixClock max 175 MHz
[   356.282] (II) fglrx(0): Monitor name: SyncMaster
[   356.282] (II) fglrx(0): Serial No: HVCS802461
[   356.282] (II) fglrx(0): EDID (in hex):
[   356.282] (II) fglrx(0): 	00000000000000003a202325693a2068
[   356.282] (II) fglrx(0): 	73697a653a20256920207673697a6520
[   356.282] (II) fglrx(0): 	25692020726566726573683a20256920
[   356.282] (II) fglrx(0): 	207669643a2025690a0071382d40582c
[   356.282] (II) fglrx(0): 	4500dd0c1100001e4100000000000000
[   356.282] (II) fglrx(0): 	00000000000000003a20537570706f72
[   356.282] (II) fglrx(0): 	7465642064657461696c65642074696d
[   356.282] (II) fglrx(0): 	696e673a0a00003a0a00310a20200011
[   356.282] (II) fglrx(0): Printing probed modes for output CRT1
[   356.282] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[   356.282] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   356.282] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   356.282] (II) fglrx(0): Modeline "1600x900"x60.0  146.25  1600 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz)
[   356.282] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   356.282] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[   356.282] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   356.282] (II) fglrx(0): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[   356.282] (II) fglrx(0): Modeline "1280x768"x60.0   83.50  1280 1352 1480 1680  768 803 809 831 -hsync +vsync (49.7 kHz)
[   356.282] (II) fglrx(0): Modeline "1280x720"x60.0   83.50  1280 1352 1480 1680  720 803 809 831 -hsync +vsync (49.7 kHz)
[   356.282] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   356.282] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   356.282] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   356.282] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   356.282] (II) fglrx(0): Output DFP1 disconnected
[   356.282] (II) fglrx(0): Output DFP2 disconnected
[   356.282] (II) fglrx(0): Output DFP3 disconnected
[   356.282] (II) fglrx(0): Output DFP4 disconnected
[   356.282] (II) fglrx(0): Output CRT1 connected
[   356.282] (II) fglrx(0): Using exact sizes for initial modes
[   356.282] (II) fglrx(0): Output CRT1 using initial mode 1920x1080
[   356.282] (II) fglrx(0): DPI set to (96, 96)
[   356.282] (II) fglrx(0): Eyefinity capable adapter detected.
[   356.282] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series  has 3 configurable heads and 1 displays connected.
[   356.282] (==) fglrx(0):  PseudoColor visuals disabled
[   356.282] (II) Loading sub module "ramdac"
[   356.282] (II) LoadModule: "ramdac"
[   356.282] (II) Module "ramdac" already built-in
[   356.282] (==) fglrx(0): NoDRI = NO
[   356.282] (==) fglrx(0): Capabilities: 0x00000000
[   356.282] (==) fglrx(0): CapabilitiesEx: 0x00000000
[   356.282] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[   356.282] (**) fglrx(0): UseFastTLS=1
[   356.282] (==) fglrx(0): BlockSignalsOnLock=1
[   356.282] (--) Depth 24 pixmap format is 32 bpp
[   356.282] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[   356.282] (WW) fglrx(0): ***********************************************************
[   356.282] (WW) fglrx(0): * DRI initialization failed                               *
[   356.282] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[   356.282] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[   356.282] (WW) fglrx(0): ***********************************************************
[   356.282] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
[   356.305] (II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
[   356.305] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
[   356.305] (II) fglrx(0): Largest offscreen area available: 1920 x 6271
[   356.305] (==) fglrx(0): Backing store disabled
[   356.305] (II) Loading extension FGLRXEXTENSION
[   356.305] (**) fglrx(0): DPMS enabled
[   356.305] (II) fglrx(0): Initialized in-driver Xinerama extension
[   356.305] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[   356.305] (II) LoadModule: "glesx"
[   356.305] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[   356.306] (II) Module glesx: vendor="X.Org Foundation"
[   356.306] 	compiled for 1.4.99.906, module version = 1.0.0
[   356.306] (II) Loading extension GLESX
[   356.306] (II) fglrx(0): GLESX enableFlags = 576
[   356.306] (II) LoadModule: "amdxmm"
[   356.306] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[   356.306] (II) Module amdxmm: vendor="X.Org Foundation"
[   356.306] 	compiled for 1.4.99.906, module version = 2.0.0
[   356.306] (EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
[   356.306] (EE) fglrx(0): XMM failed to initialize
[   356.306] (WW) fglrx(0): No XV video playback available
[   356.306] (II) fglrx(0): Enable composite support successfully
[   356.306] (WW) fglrx(0): Option "VendorName" is not used
[   356.306] (WW) fglrx(0): Option "ModelName" is not used
[   356.306] (==) fglrx(0): Silken mouse enabled
[   356.306] (==) fglrx(0): Using HW cursor of display infrastructure!
[   356.307] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[   356.392] (--) RandR disabled
[   356.392] (II) Initializing built-in extension Generic Event Extension
[   356.392] (II) Initializing built-in extension SHAPE
[   356.392] (II) Initializing built-in extension MIT-SHM
[   356.392] (II) Initializing built-in extension XInputExtension
[   356.392] (II) Initializing built-in extension XTEST
[   356.392] (II) Initializing built-in extension BIG-REQUESTS
[   356.392] (II) Initializing built-in extension SYNC
[   356.392] (II) Initializing built-in extension XKEYBOARD
[   356.392] (II) Initializing built-in extension XC-MISC
[   356.392] (II) Initializing built-in extension SECURITY
[   356.392] (II) Initializing built-in extension XINERAMA
[   356.392] (II) Initializing built-in extension XFIXES
[   356.392] (II) Initializing built-in extension RENDER
[   356.392] (II) Initializing built-in extension RANDR
[   356.392] (II) Initializing built-in extension COMPOSITE
[   356.392] (II) Initializing built-in extension DAMAGE
[   356.392] (II) Initializing built-in extension GESTURE
[   356.394] 
Backtrace:
[   356.394] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[   356.394] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[   356.394] 2: /lib/libpthread.so.0 (0x7fe65646b000+0xfb40) [0x7fe65647ab40]
[   356.395] 3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_x760_swlDriOpenConnection+0x3a) [0x7fe652ecbc2a]
[   356.395] 4: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0xd) [0x7fe652dfde4d]
[   356.395] 5: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0x7fe6540d1000+0x1b804) [0x7fe6540ec804]
[   356.395] 6: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0x7fe6540d1000+0x1db05) [0x7fe6540eeb05]
[   356.395] 7: /usr/bin/X (InitExtensions+0x89) [0x4945f9]
[   356.395] 8: /usr/bin/X (0x400000+0x216d5) [0x4216d5]
[   356.395] 9: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7fe6553d6d8e]
[   356.395] 10: /usr/bin/X (0x400000+0x21409) [0x421409]
[   356.395] Segmentation fault at address 0xa0
[   356.395] 
Caught signal 11 (Segmentation fault). Server aborting
[   356.395] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   356.395] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   356.395] 
[   356.793] (EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
[   356.804]  ddxSigGiveUp: Closing log

```

---

### Post by deconstrained on 2011-02-22
Use a driver from Canonical. Last time I tried manually installing a vendor-supplied graphics driver it completely messed everything up. The way Canonical has it set up is pretty seamless but impossible to fix manually if something goes wrong. Your current problems are probably caused by Ubuntu not recognizing that your hardware is ATI and prompting you to downloading a Catalyst driver version that's been tested by the community (or did you ignore this suggestion?)

*How do I bought nvidia?*

Sorry, couldn't resist. :-P

---

### Post by dpc.ucore.info on 2011-02-22
I've tried and drivers from Canonical do not work. I remember they didn't in the past as well, as they were too old for this card.

---

### Post by deconstrained on 2011-02-22
Best I can think of is downloading the driver in rpm format, converting it to deb with the 'alien' utility, and then installing it with dpkg (as suggested in the README). dpkg might then perform the necessary actions to set up a kernel interface or whatever else might be needed.

---

### Post by dpc.ucore.info on 2011-02-22
Why would it be better than using debs generated by installer? What README are you mentioning?

---

### Post by deconstrained on 2011-02-22
A readme on AMD's website with a section in it beginning with 'note to debian users' that's probably not as recent as the readme that was included in the package *you* downloaded in your attempts to install the driver.

Seriously though, you're in uncharted waters. The Ubuntu developers themselves are working on this right now for all we know, so any mean-time solution will either be half-assed or take a lot of time and effort.

---

### Post by dpc.ucore.info on 2011-02-22
OK. I've fixed it, finally.

So this time I did everything from within the Xorg session (running in vesa) which is strange because I was told running from X is unsafe.

I've used added this repo for newer Xorg: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
and did update.

Also, I remember building packages as a normal user (no sudo).

And when doing dpkg -i *.deb the output was bit different. The actual module was compiled and installed.

Reboot right after the process.

And finally the unsupported logo at the right bottom of the screen is gone.

---

### Post by 0004tom on 2011-02-22
> **dpc.ucore.info said:**
> And finally the unsupported logo at the right bottom of the screen is gone.

yep 11.02 officially adds support to the HD6xxx series.

---

