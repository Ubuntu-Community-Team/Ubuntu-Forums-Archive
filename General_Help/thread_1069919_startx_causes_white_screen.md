---
title: "startx causes white screen"
date: 2009-02-14
forum: General Help
---

### Post by prem1er on 2009-02-14
When booting as soon as the x terminal tries to start I get a white screen.  New laptop with new hardware ASUS F8Va-B1. No idea what could be going on.  Anyone got any suggestions?

---

### Post by prem1er on 2009-02-14
xorg log file...

> 

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux bt 2.6.28.1 #2 SMP Wed Feb 4 21:50:02 EST 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader 
fpresent
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 14 12:45:48 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.

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
(--) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3650 rev 0, Mem @ 0xd0000000/0, 0xfdef0000/0, I/O @ 0x0000c000/0, BIOS @ 0x????????/131072

(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]

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

(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout

(II) LoadModule: "radeon"


(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so

(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 6.9.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1

(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610, ATI RV670,
	ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE, ATI Radeon HD 3470,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI FireMV 2450, ATI FireMV 2260,
	ATI FireMV 2260, ATI ATI Radeon HD 3600 Series,
	ATI ATI Radeon HD 3650 AGP, ATI ATI Radeon HD 3600 PRO,
	ATI ATI Radeon HD 3600 XT, ATI ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics

(II) Primary Device is: PCI 01@00:00:0

(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]

(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

(II) Setting vga for screen 0.

(II) RADEON(0): MMIO registers at 0x00000000fdef0000: size 64KB

(II) RADEON(0): PCI bus 1 card 0 func 0

(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32

(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor

(II) Loading sub module "vgahw"

(II) LoadModule: "vgahw"


(II) Loading /usr/lib/xorg/modules//libvgahw.so

(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1

(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888

(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Mobility Radeon HD 3650" (ChipID = 0x9591)
(WW) RADEON(0): R600 support is mostly incomplete and very experimental
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000

(II) RADEON(0): PCIE card detected

(II) RADEON(0): using shadow framebuffer

(II) Loading sub module "shadow"

(II) LoadModule: "shadow"


(II) Loading /usr/lib/xorg/modules//libshadow.so

(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4

(II) Loading sub module "int10"

(II) LoadModule: "int10"


(II) Loading /usr/lib/xorg/modules//libint10.so

(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1

(II) RADEON(0): initializing int10

(II) RADEON(0): Primary V_BIOS segment is: 0xc000

(II) RADEON(0): ATOM BIOS detected

(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1043 SubsystemID: 0x1872
	IOBaseAddress: 0xc000
	Filename:             
	BIOS Bootup Message: 
F8Va M86M DDR2 600e/400m ASID:A19129.010$                                   

(II) RADEON(0): Framebuffer space used by Firmware (kb): 16

(II) RADEON(0): Start of VRAM area used by Firmware: 0x3fffc000

(II) RADEON(0): AtomBIOS requests 16kB of VRAM scratch space

(II) RADEON(0): AtomBIOS VRAM scratch base: 0x3fffc000

(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead

(II) RADEON(0): Default Engine Clock: 600000

(II) RADEON(0): Default Memory Clock: 400000

(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000

(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0

(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500

(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000

(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000

(II) RADEON(0): Direct rendering not officially supported on RN50/RS600/R600

(II) RADEON(0): Generation 2 PCI interface, using max accessible memory

(II) RADEON(0): Detected total video RAM=1048576K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)

(II) RADEON(0): Color tiling disabled

(II) RADEON(0): Max desktop size set to 2560x1600

(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf

(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf

(II) Loading sub module "ddc"

(II) LoadModule: "ddc"

(II) Module "ddc" already built-in

(II) Loading sub module "i2c"

(II) LoadModule: "i2c"

(II) Module "i2c" already built-in

(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 400.000000

(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
object id 0005 01
src object id 2115 21
record type 1
record type 4
object id 000e 01
src object id 211f 31
record type 1
record type 4
object id 000c 01
src object id 221e 30
record type 1
record type 2
record type 4

(II) RADEON(0): Output VGA-0 has no monitor section

(II) RADEON(0): I2C bus "VGA-0" initialized.

(II) RADEON(0): Output LVDS has no monitor section

(WW) RADEON(0): LVDS Info:
XRes: 1440, YRes: 900, DotClock: 108000
HBlank: 320, HOverPlus: 48, HSyncWidth: 32
VBlank: 12, VOverPlus: 3, VSyncWidth: 6

(II) RADEON(0): I2C bus "LVDS" initialized.

(II) RADEON(0): Output HDMI-0 has no monitor 

(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- 0x7e40

(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- LVDS
 DAC Type  -- None
 TMDS Type -- None
 DDC Type  -- 0x7f68

(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- HDMI-B
 DAC Type  -- None
 TMDS Type -- UNIPHY
 DDC Type  -- 0x7e20

(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.

(II) RADEON(0): I2C device "VGA-0:ddc2" removed.

(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 0

(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.

(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2

(II) RADEON(0): EDID data from the display on output: LVDS ----------------------

(II) RADEON(0): Manufacturer: CMO  Model: 1431  Serial#: 0

(II) RADEON(0): Year: 1990  Week: 0

(II) RADEON(0): EDID Version: 1.3

(II) RADEON(0): Digital Display Input

(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19

(II) RADEON(0): Gamma: 2.20

(II) RADEON(0): No DPMS capabilities specified

(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 

(II) RADEON(0): First detailed timing is preferred mode

(II) RADEON(0): redX: 0.590 redY: 0.340   greenX: 0.318 greenY: 0.540

(II) RADEON(0): blueX: 0.152 blueY: 0.125   whiteX: 0.313 whiteY: 0.329

(II) RADEON(0): Manufacturer's mask: 0

(II) RADEON(0): Supported additional Video Mode:

(II) RADEON(0): clock: 88.8 MHz   Image Size:  303 x 190 mm

(II) RADEON(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0

(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0

(II) RADEON(0):  N141C3-L02

(II) RADEON(0):  CMO

(II) RADEON(0):  N141C3-L02

(II) RADEON(0): EDID (in hex):

(II) RADEON(0): 	00ffffffffffff000daf311400000000

(II) RADEON(0): 	00000103801e13780a09059757518a27

(II) RADEON(0): 	20505400000001010101010101010101

(II) RADEON(0): 	010101010101ab22a0a050841a303020

(II) RADEON(0): 	36002fbe10000018000000fe004e3134

(II) RADEON(0): 	3143332d4c30320a2020000000fe0043

(II) RADEON(0): 	4d4f0a202020202020202020000000fe

(II) RADEON(0): 	004e31343143332d4c30320a20200035
finished output detect: 1

(II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.

(II) RADEON(0): I2C device "HDMI-0:ddc2" removed.

(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
finished output detect: 2
finished all detect
before xf86InitialConfiguration

(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.

(II) RADEON(0): I2C device "VGA-0:ddc2" removed.

(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success

(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2

(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: CMO  Model: 1431  Serial#: 0

(II) RADEON(0): Year: 1990  Week: 0

(II) RADEON(0): EDID Version: 1.3

(II) RADEON(0): Digital Display Input

(II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 19

(II) RADEON(0): Gamma: 2.20

(II) RADEON(0): No DPMS capabilities specified

(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 

(II) RADEON(0): First detailed timing is preferred mode

(II) RADEON(0): redX: 0.590 redY: 0.340   greenX: 0.318 greenY: 0.540

(II) RADEON(0): blueX: 0.152 blueY: 0.125   whiteX: 0.313 whiteY: 0.329

(II) RADEON(0): Manufacturer's mask: 0

(II) RADEON(0): Supported additional Video Mode:

(II) RADEON(0): clock: 88.8 MHz   Image Size:  303 x 190 mm

(II) RADEON(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0

(II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0

(II) RADEON(0):  N141C3-L02

(II) RADEON(0):  CMO

(II) RADEON(0):  N141C3-L02

(II) RADEON(0): EDID (in hex):

(II) RADEON(0): 	00ffffffffffff000daf311400000000

(II) RADEON(0): 	00000103801e13780a09059757518a27

(II) RADEON(0): 	20505400000001010101010101010101

(II) RADEON(0): 	010101010101ab22a0a050841a303020

(II) RADEON(0): 	36002fbe10000018000000fe004e3134

(II) RADEON(0): 	3143332d4c30320a2020000000fe0043

(II) RADEON(0): 	4d4f0a202020202020202020000000fe

(II) RADEON(0): 	004e31343143332d4c30320a20200035
in RADEONProbeOutputModes

(II) RADEON(0): EDID vendor "CMO", prod id 5169

(II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.

(II) RADEON(0): I2C device "HDMI-0:ddc2" removed.

(II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection

(II) RADEON(0): Output VGA-0 disconnected

(II) RADEON(0): Output LVDS connected

(II) RADEON(0): Output HDMI-0 disconnected

(II) RADEON(0): Using exact sizes for initial modes

(II) RADEON(0): Output LVDS using initial mode 1440x900
after xf86InitialConfiguration
(==) RADEON(0): DPI set to (96, 96)

(II) Loading sub module "fb"

(II) LoadModule: "fb"


(II) Loading /usr/lib/xorg/modules//libfb.so

(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)

(II) Loading sub module "ramdac"

(II) LoadModule: "ramdac"

(II) Module "ramdac" already built-in
(==) RADEON(0): No acceleration support available on R600 yet.

(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).

(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp

(II) do I need RAC?  No, I don't.

(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)

(II) RADEON(0): RADEONScreenInit d0000000 0 0
Output DIG2 dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
mc fb loc is 000f00d0

(II) RADEON(0): RADEONInitMemoryMap() : 

(II) RADEON(0):   mem_size         : 0x40000000

(II) RADEON(0):   MC_FB_LOCATION   : 0x000f00d0

(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000

(II) RADEON(0): Depth moves disabled by default

(II) RADEON(0): Memory manager initialized to (0,0) (1472,8191)

(II) RADEON(0): Reserved area from (0,1440) to (1472,1442)

(II) RADEON(0): Largest offscreen area available: 1472 x 6749

(II) RADEON(0): RADEONRestoreMemMapRegisters() : 

(II) RADEON(0):   MC_FB_LOCATION   : 0x000f00d0 0x00ff00c0

(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled

(WW) RADEON(0): Direct rendering disabled

(EE) RADEON(0): Acceleration initialization failed

(II) RADEON(0): Acceleration disabled

(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled

(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00819000

(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x0081f000

(II) RADEON(0): Largest offscreen area available: 1472 x 6741
Output 68 disable success
Output DIG2 dpms success
Output DIG1 dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Output DIG2 dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1440x900 - 1600 926 10

(II) RADEON(0): RADEONRestoreMemMapRegisters() : 

(II) RADEON(0):   MC_FB_LOCATION   : 0x000f00d0 0x000f00d0

(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 88750000
best_freq: 88750000
best_feedback_div: 355
best_ref_div: 12
best_post_div: 9

(II) RADEON(0): crtc(0) Clock: mode 88750, PLL 88750

(II) RADEON(0): crtc(0) PLL  : refdiv 12, fbdiv 0x163(355), pdiv 9
Set CRTC PLL success
Set CRTC Timing success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
Output DIG2 setup success
Output DIG2 transmitter setup success
Output DIG2 dpms success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output 68 disable success
Output DIG1 dpms success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success

(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled

(II) Initializing built-in extension MIT-SHM

(II) Initializing built-in extension XInputExtension

(II) Initializing built-in extension XTEST

(II) Initializing built-in extension XKEYBOARD

(II) Initializing built-in extension XC-APPGROUP

(II) Initializing built-in extension SECURITY

(II) Initializing built-in extension XINERAMA

(II) Initializing built-in extension XFIXES

(II) Initializing built-in extension RENDER

(II) Initializing built-in extension RANDR

(II) Initializing built-in extension COMPOSITE

(II) Initializing built-in extension DAMAGE

(II) Initializing built-in extension XEVIE

(II) AIGLX: Screen 0 is not DRI capable

(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so

(II) GLX: Initialized DRISWRAST GL provider for screen 0

(II) RADEON(0): Setting screen physical size to 303 x 190

(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad

(II) LoadModule: "synaptics"


(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so

(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.15.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1

(II) Synaptics touchpad driver version 0.15.2

(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472

(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(**) Option "Device" "/dev/input/event6"
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events

(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)

(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472

(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(--) SynPS/2 Synaptics TouchPad touchpad found

(II) config/hal: Adding input device Video Bus

(II) LoadModule: "evdev"


(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so

(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"

(II) Video Bus: Found keys

(II) Video Bus: Configuring as keyboard

(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"

(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"

(II) AT Translated Set 2 keyboard: Found keys

(II) AT Translated Set 2 keyboard: Configuring as keyboard

(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"

(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"

(II) Macintosh mouse button emulation: Found x and y relative axes

(II) Macintosh mouse button emulation: Found 3 mouse buttons

(II) Macintosh mouse button emulation: Configuring as mouse

(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

(II) UnloadModule: "synaptics"

(II) Video Bus: Close

(II) UnloadModule: "evdev"

(II) AT Translated Set 2 keyboard: Close

(II) UnloadModule: "evdev"

(II) Macintosh mouse button emulation: Close

(II) UnloadModule: "evdev"
Output DIG2 dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success

(II) RADEON(0): RADEONRestoreMemMapRegisters() : 

(II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00c0 0x000f00d0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000

(II) RADEON(0): avivo_restore !
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success




---

