---
title: "Compiz 3d cube no longer working after upgrade to 10.04"
date: 2010-05-23
forum: Desktop Environments
---

### Post by tonyps on 2010-05-23
Morning,
ATI Radeon 3100 is the video board...

So, I upgraded to the latest 10.04 ubuntu from the previous 9.10. I encountered numerous issue, but eh upgrade completed and I am able to successfully login, and access most of the features.
I cannot however get Compiz Desktop Cube to work. Compiz launches, but the cube feature will not work. Also, I keep getting dpkg errors after any updates...
Below is the output of various command as I am trying to get the Compiz working correctly

Compiz will not launch. Actually the app launches, however I cannot get the cube to launch...
ccsm output
ccsm
Loading icons...





ideo card is ATI Radeon 3100


Glxinfo output
sudo glxinfo | grep -i render
no output on screen

var/log/Xorg.0.log file
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux poppy-laptop 2.6.32-22-generic-pae #33-Ubuntu SMP Wed Apr 28 14:57:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=16ca1333-c4bf-4bc6-a9bb-dbc78fb8a5ba ro quiet splash
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 23 11:16:03 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:9613:1179:ff1e ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics] rev 0, Mem @ 0xd0000000/268435456, 0xe8400000/65536, 0xe8300000/1048576, I/O @ 0x00008000/256
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched ati as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 6.13.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.4.1
	ABI class: X.Org Video Driver, version 6.0
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
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
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
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4290, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5900 Series, ATI Radeon HD 5900 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 5700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, CEDAR, CEDAR, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, CEDAR, ATI Radeon HD 5450,
	CEDAR
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:05:0
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.0.2
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): TOTO SAYS 00000000e8400000
(II) RADEON(0): MMIO registers at 0x00000000e8400000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.1.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon 3100 Graphics" (ChipID = 0x9613)
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCI card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Video Driver, version 6.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1002 SubsystemID: 0x1002
	IOBaseAddress: 0x8000
	Filename: BR31934C.bin
	BIOS Bootup Message: 
Tos_Chelsea_MC RS780MC DDR2 200e/500m                                       

(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0xfffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0xfffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 350000
(II) RADEON(0): Default Memory Clock: 400000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 14320
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] This chipset requires a kernel module version of 1.17.0,
[dri] but the kernel reports a version of 2.0.0.[dri] If using legacy modesetting, upgrade your kernel.
[dri] If using kernel modesetting, make sure your module is
[dri] loaded prior to starting X, and that this driver was built
[dri] with support for KMS.
[dri] Disabling DRI.
(II) RADEON(0): using shadow framebuffer
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling disabled
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): PLL parameters: rf=1432 rd=12 min=90000 max=120000; xclk=40000
(WW) RADEON(0): LVDS Info:
XRes: 1366, YRes: 768, DotClock: 72330
HBlank: 160, HOverPlus: 48, HSyncWidth: 32
VBlank: 22, VOverPlus: 2, VSyncWidth: 5
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e40
(II) RADEON(0): Port1:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7e50
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
finished output detect: 1
finished all detect
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1366x768"x60.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1366x768
(II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux/libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) RADEON(0): RADEONScreenInit d0000000 0 0
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
(II) RADEON(0): Dynamic Power Management Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x10000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1536,8191)
(II) RADEON(0): Reserved area from (0,1366) to (1536,1368)
(II) RADEON(0): Largest offscreen area available: 1536 x 6823
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(EE) RADEON(0): Acceleration initialization failed
(II) RADEON(0): Acceleration disabled
(==) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00804000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x0080a000
(II) RADEON(0): Largest offscreen area available: 1536 x 6815
(II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
Output CRT1 disable success
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
Output DIG0 transmitter setup success
Blank CRTC 0 success
Disable CRTC memreq 0 success
Disable CRTC 0 success
Mode 1366x768 - 1526 790 10
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x00cf00c0 0x00cf00c0
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
Picked PLL 0
before 7233
after 7233
best_freq: 72495
best_feedback_div: 162
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 16
(II) RADEON(0): crtc(0) Clock: mode 72330, PLL 724950
(II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0xA2(162), fracfbdiv 0, pdiv 16
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DIG0 transmitter setup success
Output DIG1 encoder setup success
Output DIG1 encoder setup success
Output DIG1 encoder setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Output DIG0 transmitter setup success
Enable CRTC 0 success
Enable CRTC memreq 0 success
Unblank CRTC 0 success
Output CRT1 disable success
Blank CRTC 1 success
Disable CRTC memreq 1 success
Disable CRTC 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) GLX error: Can not get required symbols.
(II) RADEON(0): Setting screen physical size to 361 x 203
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event2)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Video Bus (/dev/input/event7)
(**) Video Bus: Applying InputClass "evdev keyboard catchall"
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event7"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Lid Switch (/dev/input/event1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
(**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event5"
(II) Logitech USB Receiver: Found 20 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Configuring as mouse
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(II) Logitech USB Receiver: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event6)
(**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event6"
(II) Logitech USB Receiver: Found 1 mouse buttons
(II) Logitech USB Receiver: Found scroll wheel(s)
(II) Logitech USB Receiver: Found relative axes
(II) Logitech USB Receiver: Found absolute axes
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as mouse
(II) Logitech USB Receiver: Configuring as keyboard
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(EE) Logitech USB Receiver: failed to initialize for relative axes.
(II) Logitech USB Receiver: initialized for absolute axes.
(II) config/udev: Adding input device USB2.0 UVC WebCam (/dev/input/event8)
(**) USB2.0 UVC WebCam: Applying InputClass "evdev keyboard catchall"
(**) USB2.0 UVC WebCam: always reports core events
(**) USB2.0 UVC WebCam: Device: "/dev/input/event8"
(II) USB2.0 UVC WebCam: Found keys
(II) USB2.0 UVC WebCam: Configuring as keyboard
(II) XINPUT: Adding extended input device "USB2.0 UVC WebCam" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event10)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(II) Synaptics touchpad driver version 1.2.2
(**) Option "Device" "/dev/input/event9"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
(**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event3)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): EDID vendor "SEC", prod id 13889
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): EDID vendor "SEC", prod id 13889
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): EDID vendor "SEC", prod id 13889
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): EDID vendor "SEC", prod id 13889
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): EDID vendor "SEC", prod id 13889
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): EDID vendor "SEC", prod id 13889
Dac detection success
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1366x768"x0.0   72.33  1366 1414 1446 1526  768 770 775 790 -hsync -vsync (47.4 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3641  Serial#: 0
(II) RADEON(0): Year: 2008  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 35  vert.: 20
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 72.3 MHz   Image Size:  353 x 198 mm
(II) RADEON(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1526 h_border: 0
(II) RADEON(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 790 v_border: 0
(II) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  160AT06-T01
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff004ca3413600000000
(II) RADEON(0): 	00120103802314780a87f594574f8c27
(II) RADEON(0): 	27505400000001010101010101010101
(II) RADEON(0): 	010101010101411c56a0500016303020
(II) RADEON(0): 	250061c6100000190000000f00000000
(II) RADEON(0): 	0000000000235c026700000000fe0053
(II) RADEON(0): 	414d53554e470a2020202020000000fe
(II) RADEON(0): 	00313630415430362d5430310a200006
(II) RADEON(0): EDID vendor "SEC", prod id 13889
(II)XKB: generating xkmfile /var/lib/xkb/server-E0DB3B9AFB03991C0327C6EEA244E95565400538.xkm

output of ./compiz-check
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics]
 Driver in use:         radeon
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

Any and all assistance greatly appreciated.
Tony ...

---

