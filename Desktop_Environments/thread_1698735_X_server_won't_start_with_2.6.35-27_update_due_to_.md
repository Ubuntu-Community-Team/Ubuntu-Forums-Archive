---
title: "X server won't start with 2.6.35-27 update due to fglrx"
date: 2011-03-02
forum: Desktop Environments
---

### Post by Freiddie on 2011-03-02
I recently upgraded to the 2.6.35-27 kernel, but it seems that the X-server will always segfault if I try to load the ATI driver for it.  If the ATI driver is turned off then nothing bad happens but then I'd be running without graphics acceleration.

I'm currently using ATI Mobility Radeon HD 5870.  For now, to avoid this issue I'm still using the older 2.6.35-25 kernel, in which the driver seems to work just fine.

I wonder if there's anyone else having the same issue?

Crash log below, if you can find some useful info from it:

```
[    18.786] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    18.786] X Protocol Version 11, Revision 0
[    18.786] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    18.786] Current Operating System: Linux fylwind-G73Jh 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64
[    18.786] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=13f0d0a8-2e85-4c7a-8ade-753723d545c3 ro vga=769 quiet splash
[    18.786] Build Date: 09 January 2011  12:14:27PM
[    18.786] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[    18.786] Current version of pixman: 0.18.4
[    18.786] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    18.786] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.786] (==) Log file: "/var/log/Xorg.1.log", Time: Wed Mar  2 17:20:46 2011
[    18.786] (==) Using config file: "/etc/X11/xorg.conf"
[    18.786] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.786] (==) ServerLayout "aticonfig Layout"
[    18.786] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    18.786] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    18.787] (**) |   |-->Device "aticonfig-Device[0]-0"
[    18.787] (==) Automatically adding devices
[    18.787] (==) Automatically enabling devices
[    18.787] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.787] 	Entry deleted from font path.
[    18.787] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    18.787] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.787] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.787] (II) Loader magic: 0x7d17a0
[    18.787] (II) Module ABI versions:
[    18.787] 	X.Org ANSI C Emulation: 0.4
[    18.787] 	X.Org Video Driver: 8.0
[    18.787] 	X.Org XInput driver : 11.0
[    18.787] 	X.Org Server Extension : 4.0
[    18.788] (--) PCI:*(0:1:0:0) 1002:68a0:1043:1c02 rev 0, Mem @ 0xc0000000/268435456, 0xd0020000/131072, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    18.788] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.788] (II) "extmod" will be loaded by default.
[    18.788] (II) "dbe" will be loaded by default.
[    18.788] (II) "glx" will be loaded by default.
[    18.788] (II) "record" will be loaded by default.
[    18.788] (II) "dri" will be loaded by default.
[    18.788] (II) "dri2" will be loaded by default.
[    18.788] (II) LoadModule: "extmod"
[    18.788] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.788] (II) Module extmod: vendor="X.Org Foundation"
[    18.788] 	compiled for 1.9.0, module version = 1.0.0
[    18.789] 	Module class: X.Org Server Extension
[    18.789] 	ABI class: X.Org Server Extension, version 4.0
[    18.789] (II) Loading extension MIT-SCREEN-SAVER
[    18.789] (II) Loading extension XFree86-VidModeExtension
[    18.789] (II) Loading extension XFree86-DGA
[    18.789] (II) Loading extension DPMS
[    18.789] (II) Loading extension XVideo
[    18.789] (II) Loading extension XVideo-MotionCompensation
[    18.789] (II) Loading extension X-Resource
[    18.789] (II) LoadModule: "dbe"
[    18.789] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.789] (II) Module dbe: vendor="X.Org Foundation"
[    18.789] 	compiled for 1.9.0, module version = 1.0.0
[    18.789] 	Module class: X.Org Server Extension
[    18.789] 	ABI class: X.Org Server Extension, version 4.0
[    18.789] (II) Loading extension DOUBLE-BUFFER
[    18.789] (II) LoadModule: "glx"
[    18.789] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[    18.789] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    18.789] 	compiled for 7.6.0, module version = 1.0.0
[    18.789] (II) Loading extension GLX
[    18.789] (II) LoadModule: "record"
[    18.789] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.790] (II) Module record: vendor="X.Org Foundation"
[    18.790] 	compiled for 1.9.0, module version = 1.13.0
[    18.790] 	Module class: X.Org Server Extension
[    18.790] 	ABI class: X.Org Server Extension, version 4.0
[    18.790] (II) Loading extension RECORD
[    18.790] (II) LoadModule: "dri"
[    18.790] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.790] (II) Module dri: vendor="X.Org Foundation"
[    18.790] 	compiled for 1.9.0, module version = 1.0.0
[    18.790] 	ABI class: X.Org Server Extension, version 4.0
[    18.790] (II) Loading extension XFree86-DRI
[    18.790] (II) LoadModule: "dri2"
[    18.790] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.790] (II) Module dri2: vendor="X.Org Foundation"
[    18.790] 	compiled for 1.9.0, module version = 1.2.0
[    18.790] 	ABI class: X.Org Server Extension, version 4.0
[    18.790] (II) Loading extension DRI2
[    18.790] (II) LoadModule: "fglrx"
[    18.790] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    18.803] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    18.803] 	compiled for 1.4.99.906, module version = 8.78.30
[    18.803] 	Module class: X.Org Video Driver
[    18.803] (II) Loading sub module "fglrxdrm"
[    18.803] (II) LoadModule: "fglrxdrm"
[    18.803] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    18.803] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    18.803] 	compiled for 1.8.99.905, module version = 8.78.30
[    18.803] (II) ATI Proprietary Linux Driver Version Identifier:8.78.30
[    18.803] (II) ATI Proprietary Linux Driver Release Identifier: 8.78.3                               
[    18.803] (II) ATI Proprietary Linux Driver Build Date: Sep 20 2010 21:31:08
[    18.803] (--) using VT number 8

[    18.815] (WW) Falling back to old probe method for fglrx
[    18.829] (II) Loading PCS database from /etc/ati/amdpcsdb
[    18.829] (--) Chipset Supported AMD Graphics Processor (0x68A0) found
[    18.829] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    18.829] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    18.829] (II) AMD Video driver is signed
[    18.829] (II) fglrx(0): pEnt->device->identifier=0x1deb890
[    18.829] (II) fglrx(0): === [xdl_x760_atiddxPreInit] === begin
[    18.829] (II) Loading sub module "vgahw"
[    18.829] (II) LoadModule: "vgahw"
[    18.830] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    18.830] (II) Module vgahw: vendor="X.Org Foundation"
[    18.830] 	compiled for 1.9.0, module version = 0.1.0
[    18.830] 	ABI class: X.Org Video Driver, version 8.0
[    18.830] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    18.830] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    18.830] (==) fglrx(0): Default visual is TrueColor
[    18.830] (**) fglrx(0): Option "DPMS" "true"
[    18.830] (==) fglrx(0): RGB weight 888
[    18.830] (II) fglrx(0): Using 8 bits per RGB 
[    18.830] (==) fglrx(0): Buffer Tiling is ON
[    18.830] (II) Loading sub module "fglrxdrm"
[    18.830] (II) LoadModule: "fglrxdrm"
[    18.830] (II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    18.831] ukiDynamicMajor: failed to open /proc/ati/major
[    18.831] ukiDynamicMajor: failed to open /proc/ati/major
[    18.832] (==) fglrx(0): NoAccel = NO
[    18.832] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    18.832] (--) fglrx(0): Chipset: "ATI Mobility Radeon HD 5800 Series " (Chipset = 0x68a0)
[    18.832] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x1c02)
[    18.832] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    18.832] (--) fglrx(0): Linear framebuffer (phys) at 0xc0000000
[    18.832] (--) fglrx(0): MMIO registers at 0xd0020000
[    18.832] (--) fglrx(0): I/O port at 0x0000d000
[    18.832] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    18.834] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    18.834] (EE) fglrx(0): ACPI: DRM connection failed
[    18.834] (II) Loading sub module "vbe"
[    18.834] (II) LoadModule: "vbe"
[    18.834] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    18.834] (II) Module vbe: vendor="X.Org Foundation"
[    18.834] 	compiled for 1.9.0, module version = 1.1.0
[    18.834] 	ABI class: X.Org Video Driver, version 8.0
[    18.835] (II) fglrx(0): VESA BIOS detected
[    18.835] (II) fglrx(0): VESA VBE Version 3.0
[    18.835] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    18.835] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    18.835] (II) fglrx(0): VESA VBE OEM Software Rev: 12.17
[    18.835] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    18.835] (II) fglrx(0): VESA VBE OEM Product: BROADWAY
[    18.835] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    18.867] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    18.867] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    18.867] (II) fglrx(0): PCIE card detected
[    18.867] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    18.867] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    18.867] (EE) fglrx(0): ACPI: DRM connection failed
[    18.867] (WW) fglrx(0): Hasn't establisted DRM connection
[    18.867] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    18.867] (WW) fglrx(0): No DRM connection for driver fglrx.
[    18.867] (II) fglrx(0): RandR 1.2 support is enabled!
[    18.867] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    18.867] (==) fglrx(0): Center Mode is disabled 
[    18.867] (II) Loading sub module "fb"
[    18.867] (II) LoadModule: "fb"
[    18.867] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.867] (II) Module fb: vendor="X.Org Foundation"
[    18.867] 	compiled for 1.9.0, module version = 1.0.0
[    18.867] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    18.867] (==) fglrx(0): Active stereo disabled
[    18.867] (II) Loading sub module "ddc"
[    18.867] (II) LoadModule: "ddc"
[    18.867] (II) Module "ddc" already built-in
[    18.940] (II) fglrx(0): Output LVDS using monitor section aticonfig-Monitor[0]-0
[    18.940] (II) fglrx(0): Output DFP1 has no monitor section
[    18.940] (II) fglrx(0): Output CRT2 has no monitor section
[    18.940] (II) Loading sub module "ddc"
[    18.940] (II) LoadModule: "ddc"
[    18.940] (II) Module "ddc" already built-in
[    18.940] (II) fglrx(0): Connected Display0: LVDS
[    18.940] (II) fglrx(0): Display0 EDID data ---------------------------
[    18.940] (II) fglrx(0): Manufacturer: HSD  Model: 6a5  Serial#: 6386
[    18.940] (II) fglrx(0): Year: 2010  Week: 3
[    18.940] (II) fglrx(0): EDID Version: 1.3
[    18.940] (II) fglrx(0): Digital Display Input
[    18.940] (II) fglrx(0): Max Image Size [cm]: horiz.: 39  vert.: 23
[    18.940] (II) fglrx(0): Gamma: 2.20
[    18.940] (II) fglrx(0): No DPMS capabilities specified
[    18.940] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.940] (II) fglrx(0): First detailed timing is preferred mode
[    18.940] (II) fglrx(0): redX: 0.612 redY: 0.356   greenX: 0.323 greenY: 0.594
[    18.940] (II) fglrx(0): blueX: 0.148 blueY: 0.092   whiteX: 0.313 whiteY: 0.329
[    18.940] (II) fglrx(0): Manufacturer's mask: 0
[    18.940] (II) fglrx(0): Supported detailed timing:
[    18.940] (II) fglrx(0): clock: 132.6 MHz   Image Size:  382 x 215 mm
[    18.940] (II) fglrx(0): h_active: 1920  h_sync: 1944  h_sync_end 1976 h_blank_end 2016 h_border: 0
[    18.940] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1090 v_blanking: 1096 v_border: 0
[    18.940] (II) fglrx(0):  
[    18.940] (II) fglrx(0): Monitor name: HSD173PUW1
[    18.940] (II) fglrx(0): EDID (in hex):
[    18.940] (II) fglrx(0): 	00ffffffffffff002264a506f2180000
[    18.940] (II) fglrx(0): 	03140103802717780adc259c5b529826
[    18.940] (II) fglrx(0): 	17505400000001010101010101010101
[    18.940] (II) fglrx(0): 	010101010101cc338060703810401820
[    18.940] (II) fglrx(0): 	46007ed710000019000000fe00000000
[    18.940] (II) fglrx(0): 	00000000000000000000000000fc0048
[    18.940] (II) fglrx(0): 	5344313733505557310a202000000010
[    18.940] (II) fglrx(0): 	000a2020202020202020202020200045
[    18.940] (II) fglrx(0): End of Display0 EDID data --------------------
[    18.946] (II) fglrx(0): EDID vendor "HSD", prod id 1701
[    18.946] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.946] (II) fglrx(0): Modeline "1920x1080"x0.0  132.60  1920 1944 1976 2016  1080 1084 1090 1096 -hsync -vsync (65.8 kHz)
[    18.946] (II) fglrx(0): Output LVDS connected
[    18.946] (II) fglrx(0): Output DFP1 disconnected
[    18.946] (II) fglrx(0): Output CRT2 disconnected
[    18.946] (II) fglrx(0): Using exact sizes for initial modes
[    18.946] (II) fglrx(0): Output LVDS using initial mode 1920x1080
[    18.946] (II) fglrx(0): Display dimensions: (390, 230) mm
[    18.946] (II) fglrx(0): DPI set to (125, 119)
[    18.946] (II) fglrx(0): Adapter ATI Mobility Radeon HD 5800 Series  has 2 configurable heads and 1 displays connected.
[    18.946] (==) fglrx(0):  PseudoColor visuals disabled
[    18.946] (II) Loading sub module "ramdac"
[    18.946] (II) LoadModule: "ramdac"
[    18.946] (II) Module "ramdac" already built-in
[    18.946] (==) fglrx(0): NoDRI = NO
[    18.946] (==) fglrx(0): Capabilities: 0x00000000
[    18.946] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    18.946] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    18.946] (==) fglrx(0): UseFastTLS=0
[    18.946] (==) fglrx(0): BlockSignalsOnLock=1
[    18.946] (--) Depth 24 pixmap format is 32 bpp
[    18.947] (EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
[    18.947] (WW) fglrx(0): ***********************************************************
[    18.947] (WW) fglrx(0): * DRI initialization failed                               *
[    18.947] (WW) fglrx(0): * kernel module (fglrx.ko) may be missing or incompatible *
[    18.947] (WW) fglrx(0): * 2D and 3D acceleration disabled                         *
[    18.947] (WW) fglrx(0): ***********************************************************
[    18.947] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x10000000
[    18.996] (II) fglrx(0): FBMM initialized for area (0,0)-(1920,8191)
[    18.996] (II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1920) (front color buffer - assumption)
[    18.996] (II) fglrx(0): Largest offscreen area available: 1920 x 6271
[    18.996] (==) fglrx(0): Backing store disabled
[    18.996] (II) Loading extension FGLRXEXTENSION
[    18.996] (**) fglrx(0): DPMS enabled
[    18.997] (II) fglrx(0): Initialized in-driver Xinerama extension
[    18.997] (WW) fglrx(0): Textured Video not supported without DRI enabled.
[    18.997] (II) LoadModule: "glesx"
[    18.997] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    18.997] (II) Module glesx: vendor="X.Org Foundation"
[    18.997] 	compiled for 1.8.99.905, module version = 1.0.0
[    18.997] (II) Loading extension GLESX
[    18.997] (II) fglrx(0): GLESX enableFlags = 576
[    18.997] (II) fglrx(0): Acceleration enabled
[    18.997] (II) LoadModule: "amdxmm"
[    18.997] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    18.997] (II) Module amdxmm: vendor="X.Org Foundation"
[    18.997] 	compiled for 1.8.99.905, module version = 1.0.0
[    18.997] (EE) fglrx(0): XMM failed to open CMMQS connection.
[    18.997] (EE) fglrx(0): XMM failed to initialize
[    18.997] (WW) fglrx(0): No XV video playback available
[    18.997] (II) fglrx(0): Enable composite support successfully
[    18.997] (WW) fglrx(0): Option "VendorName" is not used
[    18.997] (WW) fglrx(0): Option "ModelName" is not used
[    18.997] (==) fglrx(0): Silken mouse enabled
[    18.997] (==) fglrx(0): Using HW cursor of display infrastructure!
[    18.997] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    18.998] (II) fglrx(0): 'LVDS LCD' ConnectorType, abstracted as 'Panel'
[    18.998] (II) fglrx(0): 'eDP LCD' ConnectorType, abstracted as 'Panel'
[    19.568] (--) RandR disabled
[    19.568] (II) Initializing built-in extension Generic Event Extension
[    19.568] (II) Initializing built-in extension SHAPE
[    19.568] (II) Initializing built-in extension MIT-SHM
[    19.568] (II) Initializing built-in extension XInputExtension
[    19.568] (II) Initializing built-in extension XTEST
[    19.568] (II) Initializing built-in extension BIG-REQUESTS
[    19.568] (II) Initializing built-in extension SYNC
[    19.568] (II) Initializing built-in extension XKEYBOARD
[    19.568] (II) Initializing built-in extension XC-MISC
[    19.568] (II) Initializing built-in extension SECURITY
[    19.568] (II) Initializing built-in extension XINERAMA
[    19.568] (II) Initializing built-in extension XFIXES
[    19.568] (II) Initializing built-in extension RENDER
[    19.568] (II) Initializing built-in extension RANDR
[    19.568] (II) Initializing built-in extension COMPOSITE
[    19.568] (II) Initializing built-in extension DAMAGE
[    19.568] (II) Initializing built-in extension GESTURE
[    19.569] 
Backtrace:
[    19.569] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[    19.569] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[    19.569] 2: /lib/libpthread.so.0 (0x7ff656d0c000+0xfb40) [0x7ff656d1bb40]
[    19.570] 3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_x760_swlDriOpenConnection+0x3a) [0x7ff6538ac8aa]
[    19.570] 4: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0xd) [0x7ff6537e4a8d]
[    19.570] 5: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0x7ff65497d000+0x1a163) [0x7ff654997163]
[    19.570] 6: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0x7ff65497d000+0x1c325) [0x7ff654999325]
[    19.570] 7: /usr/bin/X (InitExtensions+0x89) [0x4945f9]
[    19.570] 8: /usr/bin/X (0x400000+0x216d5) [0x4216d5]
[    19.570] 9: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7ff655c77d8e]
[    19.570] 10: /usr/bin/X (0x400000+0x21409) [0x421409]
[    19.570] Segmentation fault at address 0xa0
[    19.570] 
Caught signal 11 (Segmentation fault). Server aborting
[    19.570] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    19.570] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    19.570] 
[    19.820] (EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
[    19.843]  ddxSigGiveUp: Closing log

```

---

### Post by Melvin1981 on 2011-03-03
The same issue with ATI Mobility Radeon HD 4200 Series and kernel 2.6.35-27. Using previous kernel 2.6.35-25. No problem with this version.

---

### Post by wikes82 on 2011-03-03
I'm having the same issue here, reverting back to 2.6.35-25 kernel at the moment.

---

### Post by thomas.wihl on 2011-03-07
Same here with my ATI Radeon HD 5450
No problem on my other machine with an older Radeon.

---

### Post by Krytarik on 2011-03-08
How did you all install the driver? Via "Additional Drivers"/package manager, or manually with the installer from AMDs website?

If the first mentioned is the case, try upgrading to the driver provided by Ubuntu-X-Swat, those is more recent than those in the official repo (at least for Maverick/Lucid):
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by thomas.wihl on 2011-03-08
Thanks Krytarik, that worked for me, I was always looking to get some more recent fglrx drivers on my system without using the installer from ATI/AMD (that always ruined my system).  Btw.: I used the "Additional Drivers" version.

---

### Post by Freiddie on 2011-03-08
> **Krytarik said:**
> How did you all install the driver? Via "Additional Drivers"/package manager, or manually with the installer from AMDs website?

If the first mentioned is the case, try upgrading to the driver provided by Ubuntu-X-Swat, those is more recent than those in the official repo (at least for Maverick/Lucid):
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

The driver was installed from "Additional Drivers" (Ubuntu repo).  I tried installing from the AMD website some time ago (before the new kernel was installed) and I messed up so badly that I had to reinstall, so I never went back that route again.

I'll try the commands that you mentioned and report back to see if the problem gets fixed.

---

### Post by Krytarik on 2011-03-08
> **Freiddie said:**
> I tried installing from the AMD website some time ago (before the new kernel was installed) and I messed up so badly that I had to reinstall, so I never went back that route again.

In fact, I would always choose the package-based install if possible, wether it is via "Hardware/Additional Drivers" or even via package-manager. Basically because you can safely remove it when needed and you don't have to re-install the driver each time the kernel gets upgraded. And as a side-effect the driver gets updated automatically if the package-provider regularily updates its packages based on the latest version of the official proprietary driver, and that seems to be the case with Ubuntu-X-Swat's PPA.

---

### Post by Freiddie on 2011-03-10
Well, your plan worked perfectly.  I can now run the new kernel without the display driver crashing.  Thanks!

---

### Post by wikes82 on 2011-03-12
Thank Krytarik, your solution works...

---

