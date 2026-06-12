---
title: "Desktop Effects + Unminimize Window = X crash (looks like logging in again)"
date: 2010-11-23
forum: Desktop Environments
---

### Post by Ubuntiac on 2010-11-23
Hi there,

I'm getting X crashing every single time I unminimize a window with desktop effects enabled (even if I have no effects ticked in the all effects tab). I'm seeing a lot of similar reports around the web, although users often don't seem to realize exactly how to trigger the problem, or that it's X crashing not just "KDE logging in again".

Common symptoms:
[LIST]
[*]KDE 4.5.2
[*]Xorg 1.9
[*]ATI / Intel / Catalyst drivers
[*]"X server for display :0 terminated unexpectedly" in Xorg.0.log sometimes.
[*] A number of people report only having the problem with KMS turned off
[/LIST]

Updating kernel to mainline / mainline 2.6.36 / mainline 2.6.37-rc2 changes nothing.

Xorg.0.log:
```
[    26.445] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    26.502] X Protocol Version 11, Revision 0
[    26.502] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    26.502] Current Operating System: Linux neo 2.6.36-020636rc7-generic #201010070908 SMP Thu Oct 7 10:21:05 UTC 2010 i686
[    26.502] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-020636rc7-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
[    26.502] Build Date: 16 September 2010  05:39:22PM
[    26.502] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    26.502] Current version of pixman: 0.18.4
[    26.502] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    26.502] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.502] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 00:51:38 2010
[    26.537] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.537] (==) No Layout section.  Using the first Screen section.
[    26.537] (==) No screen section available. Using defaults.
[    26.537] (**) |-->Screen "Default Screen Section" (0)
[    26.537] (**) |   |-->Monitor "<default monitor>"
[    26.538] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    26.538] (==) Automatically adding devices
[    26.538] (==) Automatically enabling devices
[    26.538] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.538] 	Entry deleted from font path.
[    26.538] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    26.538] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.538] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.538] (II) Loader magic: 0x81f8e00
[    26.538] (II) Module ABI versions:
[    26.538] 	X.Org ANSI C Emulation: 0.4
[    26.538] 	X.Org Video Driver: 8.0
[    26.538] 	X.Org XInput driver : 11.0
[    26.538] 	X.Org Server Extension : 4.0
[    26.540] (--) PCI:*(0:1:5:0) 1002:7942:1028:0204 rev 0, Mem @ 0xe0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000ee00/256
[    26.540] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.540] (II) LoadModule: "extmod"
[    26.628] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.628] (II) Module extmod: vendor="X.Org Foundation"
[    26.628] 	compiled for 1.9.0, module version = 1.0.0
[    26.628] 	Module class: X.Org Server Extension
[    26.628] 	ABI class: X.Org Server Extension, version 4.0
[    26.628] (II) Loading extension MIT-SCREEN-SAVER
[    26.628] (II) Loading extension XFree86-VidModeExtension
[    26.628] (II) Loading extension XFree86-DGA
[    26.628] (II) Loading extension DPMS
[    26.628] (II) Loading extension XVideo
[    26.628] (II) Loading extension XVideo-MotionCompensation
[    26.628] (II) Loading extension X-Resource
[    26.628] (II) LoadModule: "dbe"
[    26.629] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.629] (II) Module dbe: vendor="X.Org Foundation"
[    26.629] 	compiled for 1.9.0, module version = 1.0.0
[    26.629] 	Module class: X.Org Server Extension
[    26.629] 	ABI class: X.Org Server Extension, version 4.0
[    26.629] (II) Loading extension DOUBLE-BUFFER
[    26.629] (II) LoadModule: "glx"
[    26.630] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.630] (II) Module glx: vendor="X.Org Foundation"
[    26.630] 	compiled for 1.9.0, module version = 1.0.0
[    26.630] 	ABI class: X.Org Server Extension, version 4.0
[    26.630] (==) AIGLX enabled
[    26.630] (II) Loading extension GLX
[    26.630] (II) LoadModule: "record"
[    26.631] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.631] (II) Module record: vendor="X.Org Foundation"
[    26.631] 	compiled for 1.9.0, module version = 1.13.0
[    26.631] 	Module class: X.Org Server Extension
[    26.631] 	ABI class: X.Org Server Extension, version 4.0
[    26.631] (II) Loading extension RECORD
[    26.631] (II) LoadModule: "dri"
[    26.632] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.632] (II) Module dri: vendor="X.Org Foundation"
[    26.632] 	compiled for 1.9.0, module version = 1.0.0
[    26.632] 	ABI class: X.Org Server Extension, version 4.0
[    26.632] (II) Loading extension XFree86-DRI
[    26.632] (II) LoadModule: "dri2"
[    26.633] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.633] (II) Module dri2: vendor="X.Org Foundation"
[    26.633] 	compiled for 1.9.0, module version = 1.2.0
[    26.633] 	ABI class: X.Org Server Extension, version 4.0
[    26.633] (II) Loading extension DRI2
[    26.633] (==) Matched ati as autoconfigured driver 0
[    26.633] (==) Matched vesa as autoconfigured driver 1
[    26.633] (==) Matched fbdev as autoconfigured driver 2
[    26.633] (==) Assigned the driver to the xf86ConfigLayout
[    26.633] (II) LoadModule: "ati"
[    26.633] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    26.633] (II) Module ati: vendor="X.Org Foundation"
[    26.633] 	compiled for 1.9.0, module version = 6.13.1
[    26.633] 	Module class: X.Org Video Driver
[    26.633] 	ABI class: X.Org Video Driver, version 8.0
[    26.634] (II) LoadModule: "radeon"
[    26.634] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    26.634] (II) Module radeon: vendor="X.Org Foundation"
[    26.634] 	compiled for 1.9.0, module version = 6.13.1
[    26.634] 	Module class: X.Org Video Driver
[    26.634] 	ABI class: X.Org Video Driver, version 8.0
[    26.634] (II) LoadModule: "vesa"
[    26.635] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.635] (II) Module vesa: vendor="X.Org Foundation"
[    26.635] 	compiled for 1.8.99.905, module version = 2.3.0
[    26.635] 	Module class: X.Org Video Driver
[    26.635] 	ABI class: X.Org Video Driver, version 8.0
[    26.635] (II) LoadModule: "fbdev"
[    26.635] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.635] (II) Module fbdev: vendor="X.Org Foundation"
[    26.635] 	compiled for 1.8.99.905, module version = 0.4.2
[    26.635] 	ABI class: X.Org Video Driver, version 8.0
[    26.635] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
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
[    26.641] (II) VESA: driver for VESA chipsets: vesa
[    26.641] (II) FBDEV: driver for framebuffer: fbdev
[    26.641] (++) using VT number 7

[    26.642] (II) [KMS] drm report modesetting isn't supported.
[    26.642] (WW) Falling back to old probe method for vesa
[    26.642] (WW) Falling back to old probe method for fbdev
[    26.642] (II) Loading sub module "fbdevhw"
[    26.642] (II) LoadModule: "fbdevhw"
[    26.643] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.643] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.643] 	compiled for 1.9.0, module version = 0.0.2
[    26.643] 	ABI class: X.Org Video Driver, version 8.0
[    26.643] (EE) open /dev/fb0: No such file or directory
[    26.643] (II) RADEON(0): TOTO SAYS 00000000feaf0000
[    26.643] (II) RADEON(0): MMIO registers at 0x00000000feaf0000: size 64KB
[    26.643] (II) RADEON(0): PCI bus 1 card 5 func 0
[    26.643] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    26.643] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    26.643] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    26.643] (==) RADEON(0): Default visual is TrueColor
[    26.643] (II) Loading sub module "vgahw"
[    26.643] (II) LoadModule: "vgahw"
[    26.644] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    26.644] (II) Module vgahw: vendor="X.Org Foundation"
[    26.644] 	compiled for 1.9.0, module version = 0.1.0
[    26.644] 	ABI class: X.Org Video Driver, version 8.0
[    26.644] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    26.644] (==) RADEON(0): RGB weight 888
[    26.644] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    26.644] (--) RADEON(0): Chipset: "ATI Radeon X1200" (ChipID = 0x7942)
[    26.644] (--) RADEON(0): Linear framebuffer at 0x00000000e0000000
[    26.644] (II) RADEON(0): PCI card detected
[    26.644] (II) Loading sub module "int10"
[    26.644] (II) LoadModule: "int10"
[    26.645] (II) Loading /usr/lib/xorg/modules/libint10.so
[    26.645] (II) Module int10: vendor="X.Org Foundation"
[    26.645] 	compiled for 1.9.0, module version = 1.0.0
[    26.645] 	ABI class: X.Org Video Driver, version 8.0
[    26.645] (II) RADEON(0): initializing int10
[    26.646] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    26.646] (II) RADEON(0): ATOM BIOS detected
[    26.646] (II) RADEON(0): ATOM BIOS Rom: 
[    26.646] 	SubsystemVendorID: 0x1028 SubsystemID: 0x0204
[    26.646] 	IOBaseAddress: 0xee00
[    26.646] 	Filename: br26397.bin 
[    26.646] 	BIOS Bootup Message: 
ATI Radeon Xpress 1250 for Dell/Parker                                      

[    26.646] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    26.646] (II) RADEON(0): Start of VRAM area used by Firmware: 0xfffb000
[    26.646] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    26.646] (II) RADEON(0): AtomBIOS VRAM scratch base: 0xfffb000
[    26.646] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    26.646] (II) RADEON(0): Default Engine Clock: 350000
[    26.646] (II) RADEON(0): Default Memory Clock: 333000
[    26.646] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    26.646] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    26.646] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    26.646] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    26.646] (II) RADEON(0): Maximum Pixel Clock: 400000
[    26.646] (II) RADEON(0): Reference Clock: 14320
[    26.646] drmOpenDevice: node name is /dev/dri/card0
[    26.647] drmOpenDevice: open result is 12, (OK)
[    26.648] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    26.648] drmOpenDevice: node name is /dev/dri/card0
[    26.649] drmOpenDevice: open result is 12, (OK)
[    26.649] drmOpenByBusid: drmOpenMinor returns 12
[    26.649] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    26.650] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.33.0
[    26.650] (==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

[    26.650] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    26.650] (II) RADEON(0): Generation 2 PCI interface, using max accessible memory
[    26.650] (II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
[    26.650] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[    26.650] (II) RADEON(0): Color tiling enabled by default
[    26.650] (II) Loading sub module "ddc"
[    26.650] (II) LoadModule: "ddc"
[    26.650] (II) Module "ddc" already built-in
[    26.650] (II) Loading sub module "i2c"
[    26.650] (II) LoadModule: "i2c"
[    26.650] (II) Module "i2c" already built-in
[    26.650] (II) RADEON(0): PLL parameters: rf=1432 rd=12 min=70000 max=120000; xclk=40000
[    26.650] (WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 71450
HBlank: 168, HOverPlus: 48, HSyncWidth: 32
VBlank: 22, VOverPlus: 3, VSyncWidth: 6
[    26.651] (II) RADEON(0): Output VGA-0 has no monitor section
[    26.651] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    26.651] (II) RADEON(0): Output LVDS has no monitor section
[    26.651] (II) RADEON(0): I2C bus "LVDS" initialized.
[    26.651] (II) RADEON(0): Output DVI-0 has no monitor section
[    26.651] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    26.651] (II) RADEON(0): Port0:
[    26.651]   XRANDR name: VGA-0
[    26.651]   Connector: VGA
[    26.651]   CRT1: INTERNAL_KLDSCP_DAC1
[    26.651]   DDC reg: 0x7e40
[    26.651] (II) RADEON(0): Port1:
[    26.651]   XRANDR name: LVDS
[    26.651]   Connector: LVDS
[    26.651]   LCD1: INTERNAL_LVTM1
[    26.651]   DDC reg: 0x7e40
[    26.651] (II) RADEON(0): Port2:
[    26.651]   XRANDR name: DVI-0
[    26.651]   Connector: DVI-D
[    26.651]   DFP2: INTERNAL_DDI
[    26.651]   DDC reg: 0x7e40
[    26.651] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    26.721] Dac detection success
[    26.721] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    26.721] finished output detect: 0
[    26.721] (II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
[    26.786] (II) RADEON(0): EDID for output LVDS
[    26.787] (II) RADEON(0): Manufacturer: AUO  Model: 4214  Serial#: 0
[    26.787] (II) RADEON(0): Year: 2007  Week: 1
[    26.787] (II) RADEON(0): EDID Version: 1.3
[    26.787] (II) RADEON(0): Digital Display Input
[    26.787] (II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[    26.787] (II) RADEON(0): Gamma: 2.20
[    26.787] (II) RADEON(0): No DPMS capabilities specified
[    26.787] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.787] (II) RADEON(0): First detailed timing is preferred mode
[    26.787] (II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.330 greenY: 0.575
[    26.787] (II) RADEON(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[    26.787] (II) RADEON(0): Manufacturer's mask: 0
[    26.787] (II) RADEON(0): Supported detailed timing:
[    26.787] (II) RADEON(0): clock: 71.5 MHz   Image Size:  261 x 163 mm
[    26.787] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1448 h_border: 0
[    26.787] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.787] (II) RADEON(0): Supported detailed timing:
[    26.787] (II) RADEON(0): clock: 70.3 MHz   Image Size:  261 x 163 mm
[    26.787] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1424 h_border: 0
[    26.787] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.787] (II) RADEON(0):  KX774B121EW4
[    26.787] (II) RADEON(0):  	4`„ÿ
[    26.787] (II) RADEON(0): EDID (in hex):
[    26.787] (II) RADEON(0): 	00ffffffffffff0006af144200000000
[    26.787] (II) RADEON(0): 	01110103801a10780a89e59457549327
[    26.787] (II) RADEON(0): 	22505400000001010101010101010101
[    26.787] (II) RADEON(0): 	010101010101e91b00a8502016303020
[    26.787] (II) RADEON(0): 	360005a310000019761b009050201630
[    26.787] (II) RADEON(0): 	3020360005a310000000000000fe004b
[    26.787] (II) RADEON(0): 	583737340242313231455734000000fe
[    26.787] (II) RADEON(0): 	00090f151a346084ff01010a2020001b
[    26.787] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    26.787] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    26.787] (II) RADEON(0): Manufacturer: AUO  Model: 4214  Serial#: 0
[    26.787] (II) RADEON(0): Year: 2007  Week: 1
[    26.787] (II) RADEON(0): EDID Version: 1.3
[    26.787] (II) RADEON(0): Digital Display Input
[    26.787] (II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[    26.787] (II) RADEON(0): Gamma: 2.20
[    26.787] (II) RADEON(0): No DPMS capabilities specified
[    26.787] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.787] (II) RADEON(0): First detailed timing is preferred mode
[    26.787] (II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.330 greenY: 0.575
[    26.787] (II) RADEON(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[    26.787] (II) RADEON(0): Manufacturer's mask: 0
[    26.787] (II) RADEON(0): Supported detailed timing:
[    26.788] (II) RADEON(0): clock: 71.5 MHz   Image Size:  261 x 163 mm
[    26.788] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1448 h_border: 0
[    26.788] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.788] (II) RADEON(0): Supported detailed timing:
[    26.788] (II) RADEON(0): clock: 70.3 MHz   Image Size:  261 x 163 mm
[    26.788] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1424 h_border: 0
[    26.788] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.788] (II) RADEON(0):  KX774B121EW4
[    26.788] (II) RADEON(0):  	4`„ÿ
[    26.788] (II) RADEON(0): EDID (in hex):
[    26.788] (II) RADEON(0): 	00ffffffffffff0006af144200000000
[    26.788] (II) RADEON(0): 	01110103801a10780a89e59457549327
[    26.788] (II) RADEON(0): 	22505400000001010101010101010101
[    26.788] (II) RADEON(0): 	010101010101e91b00a8502016303020
[    26.788] (II) RADEON(0): 	360005a310000019761b009050201630
[    26.788] (II) RADEON(0): 	3020360005a310000000000000fe004b
[    26.788] (II) RADEON(0): 	583737340242313231455734000000fe
[    26.788] (II) RADEON(0): 	00090f151a346084ff01010a2020001b
[    26.788] finished output detect: 1
[    26.788] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    26.793] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    26.793] finished output detect: 2
[    26.793] finished all detect
[    26.861] Dac detection success
[    26.862] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    26.862] (II) RADEON(0): EDID for output VGA-0
[    26.938] (II) RADEON(0): EDID for output LVDS
[    26.938] (II) RADEON(0): Manufacturer: AUO  Model: 4214  Serial#: 0
[    26.938] (II) RADEON(0): Year: 2007  Week: 1
[    26.938] (II) RADEON(0): EDID Version: 1.3
[    26.938] (II) RADEON(0): Digital Display Input
[    26.938] (II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[    26.938] (II) RADEON(0): Gamma: 2.20
[    26.938] (II) RADEON(0): No DPMS capabilities specified
[    26.938] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.938] (II) RADEON(0): First detailed timing is preferred mode
[    26.938] (II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.330 greenY: 0.575
[    26.938] (II) RADEON(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[    26.938] (II) RADEON(0): Manufacturer's mask: 0
[    26.938] (II) RADEON(0): Supported detailed timing:
[    26.938] (II) RADEON(0): clock: 71.5 MHz   Image Size:  261 x 163 mm
[    26.938] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1448 h_border: 0
[    26.938] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.938] (II) RADEON(0): Supported detailed timing:
[    26.938] (II) RADEON(0): clock: 70.3 MHz   Image Size:  261 x 163 mm
[    26.938] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1424 h_border: 0
[    26.938] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.938] (II) RADEON(0):  KX774B121EW4
[    26.938] (II) RADEON(0):  	4`„ÿ
[    26.938] (II) RADEON(0): EDID (in hex):
[    26.938] (II) RADEON(0): 	00ffffffffffff0006af144200000000
[    26.938] (II) RADEON(0): 	01110103801a10780a89e59457549327
[    26.938] (II) RADEON(0): 	22505400000001010101010101010101
[    26.938] (II) RADEON(0): 	010101010101e91b00a8502016303020
[    26.938] (II) RADEON(0): 	360005a310000019761b009050201630
[    26.938] (II) RADEON(0): 	3020360005a310000000000000fe004b
[    26.938] (II) RADEON(0): 	583737340242313231455734000000fe
[    26.938] (II) RADEON(0): 	00090f151a346084ff01010a2020001b
[    26.938] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    26.939] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    26.939] (II) RADEON(0): Manufacturer: AUO  Model: 4214  Serial#: 0
[    26.939] (II) RADEON(0): Year: 2007  Week: 1
[    26.939] (II) RADEON(0): EDID Version: 1.3
[    26.939] (II) RADEON(0): Digital Display Input
[    26.939] (II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[    26.939] (II) RADEON(0): Gamma: 2.20
[    26.939] (II) RADEON(0): No DPMS capabilities specified
[    26.939] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.939] (II) RADEON(0): First detailed timing is preferred mode
[    26.939] (II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.330 greenY: 0.575
[    26.939] (II) RADEON(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[    26.939] (II) RADEON(0): Manufacturer's mask: 0
[    26.939] (II) RADEON(0): Supported detailed timing:
[    26.939] (II) RADEON(0): clock: 71.5 MHz   Image Size:  261 x 163 mm
[    26.939] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1448 h_border: 0
[    26.939] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.939] (II) RADEON(0): Supported detailed timing:
[    26.939] (II) RADEON(0): clock: 70.3 MHz   Image Size:  261 x 163 mm
[    26.939] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1424 h_border: 0
[    26.939] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    26.939] (II) RADEON(0):  KX774B121EW4
[    26.939] (II) RADEON(0):  	4`„ÿ
[    26.939] (II) RADEON(0): EDID (in hex):
[    26.939] (II) RADEON(0): 	00ffffffffffff0006af144200000000
[    26.939] (II) RADEON(0): 	01110103801a10780a89e59457549327
[    26.939] (II) RADEON(0): 	22505400000001010101010101010101
[    26.939] (II) RADEON(0): 	010101010101e91b00a8502016303020
[    26.939] (II) RADEON(0): 	360005a310000019761b009050201630
[    26.939] (II) RADEON(0): 	3020360005a310000000000000fe004b
[    26.939] (II) RADEON(0): 	583737340242313231455734000000fe
[    26.939] (II) RADEON(0): 	00090f151a346084ff01010a2020001b
[    26.939] (II) RADEON(0): EDID vendor "AUO", prod id 16916
[    26.939] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    26.939] (II) RADEON(0): Printing probed modes for output LVDS
[    26.939] (II) RADEON(0): Modeline "1280x800"x60.0   71.45  1280 1328 1360 1448  800 803 809 822 -hsync -vsync (49.3 kHz)
[    26.939] (II) RADEON(0): Modeline "1280x800"x60.1   70.30  1280 1328 1360 1424  800 803 809 822 -hsync -vsync (49.4 kHz)
[    26.939] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    26.939] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    26.939] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    26.940] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    26.940] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    26.945] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    26.945] (II) RADEON(0): EDID for output DVI-0
[    26.945] (II) RADEON(0): Output VGA-0 disconnected
[    26.945] (II) RADEON(0): Output LVDS connected
[    26.945] (II) RADEON(0): Output DVI-0 disconnected
[    26.945] (II) RADEON(0): Using exact sizes for initial modes
[    26.945] (II) RADEON(0): Output LVDS using initial mode 1280x800
[    26.945] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.945] (==) RADEON(0): DPI set to (96, 96)
[    26.945] (II) Loading sub module "fb"
[    26.945] (II) LoadModule: "fb"
[    26.945] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.945] (II) Module fb: vendor="X.Org Foundation"
[    26.945] 	compiled for 1.9.0, module version = 1.0.0
[    26.946] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.946] (II) Loading sub module "ramdac"
[    26.946] (II) LoadModule: "ramdac"
[    26.946] (II) Module "ramdac" already built-in
[    26.946] (==) RADEON(0): Using EXA acceleration architecture
[    26.946] (II) Loading sub module "exa"
[    26.946] (II) LoadModule: "exa"
[    26.946] (II) Loading /usr/lib/xorg/modules/libexa.so
[    26.946] (II) Module exa: vendor="X.Org Foundation"
[    26.946] 	compiled for 1.9.0, module version = 2.5.0
[    26.946] 	ABI class: X.Org Video Driver, version 8.0
[    26.946] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    26.946] (II) UnloadModule: "vesa"
[    26.946] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.946] (II) UnloadModule: "fbdev"
[    26.946] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.946] (II) UnloadModule: "fbdevhw"
[    26.946] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    26.946] (--) Depth 24 pixmap format is 32 bpp
[    26.946] (II) RADEON(0): RADEONScreenInit e0000000 0 0
[    27.462] Output LCD1 disable success
[    27.756] Blank CRTC 0 success
[    27.756] Disable CRTC 0 success
[    27.756] Blank CRTC 1 success
[    27.756] Disable CRTC 1 success
[    27.756] (II) RADEON(0): Dynamic Power Management Disabled
[    27.756] (==) RADEON(0): Using 24 bit depth buffer
[    27.757] (II) RADEON(0): RADEONInitMemoryMap() : 
[    27.757] (II) RADEON(0):   mem_size         : 0x10000000
[    27.757] (II) RADEON(0):   MC_FB_LOCATION   : 0xbfffb000
[    27.757] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    27.757] (II) RADEON(0): Depth moves disabled by default
[    27.757] (II) RADEON(0): Allocating from a screen of 262080 kb
[    27.757] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00640000
[    27.757] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00644000
[    27.757] (II) RADEON(0): Will use 6400 kb for front buffer at offset 0x00000000
[    27.757] (II) RADEON(0): Will use 64 kb for PCI GART at offset 0x0fff0000
[    27.757] (II) RADEON(0): Will use 6400 kb for back buffer at offset 0x00648000
[    27.757] (II) RADEON(0): Will use 6400 kb for depth buffer at offset 0x00c88000
[    27.757] (II) RADEON(0): Will use 120832 kb for textures at offset 0x012c8000
[    27.757] (II) RADEON(0): Will use 122016 kb for X Server offscreen at offset 0x088c8000
[    27.757] drmOpenDevice: node name is /dev/dri/card0
[    27.758] drmOpenDevice: open result is 12, (OK)
[    27.759] drmOpenDevice: node name is /dev/dri/card0
[    27.760] drmOpenDevice: open result is 12, (OK)
[    27.761] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    27.761] drmOpenDevice: node name is /dev/dri/card0
[    27.762] drmOpenDevice: open result is 12, (OK)
[    27.762] drmOpenByBusid: drmOpenMinor returns 12
[    27.762] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    27.762] (II) [drm] DRM interface version 1.4
[    27.762] (II) [drm] DRM open master succeeded.
[    27.762] (II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
[    27.762] (II) RADEON(0): [drm] framebuffer handle = 0xe0000000
[    27.762] (II) RADEON(0): [drm] added 1 reserved context for kernel
[    27.762] (II) RADEON(0): X context handle = 0x1
[    27.762] (II) RADEON(0): [drm] installed DRM signal handler
[    27.798] (II) RADEON(0): [pci] 32768 kB allocated with handle 0xf895e000
[    27.798] (II) RADEON(0): [pci] ring handle = 0xf895e000
[    27.798] (II) RADEON(0): [pci] Ring mapped at 0xb7158000
[    27.798] (II) RADEON(0): [pci] Ring contents 0x00000000
[    27.798] (II) RADEON(0): [pci] ring read ptr handle = 0xf8a5f000
[    27.798] (II) RADEON(0): [pci] Ring read ptr mapped at 0xb73a3000
[    27.798] (II) RADEON(0): [pci] Ring read ptr contents 0x00000000
[    27.798] (II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8a60000
[    27.798] (II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xa6ed1000
[    27.798] (II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
[    27.798] (II) RADEON(0): [pci] GART texture map handle = 0xf8c60000
[    27.798] (II) RADEON(0): [pci] GART Texture map mapped at 0xa5251000
[    27.798] (II) RADEON(0): [drm] register handle = 0x2fd5e000
[    27.798] (II) RADEON(0): [dri] Visual configs initialized
[    27.798] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    27.798] (II) RADEON(0):   MC_FB_LOCATION   : 0xbfffb000 0xbfffb000
[    27.798] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    27.809] (==) RADEON(0): Backing store disabled
[    27.809] (II) RADEON(0): [DRI] installation complete
[    27.876] (II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
[    27.876] (II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
[    27.876] (II) RADEON(0): [drm] dma control initialized, using IRQ 18
[    27.876] (II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
[    27.876] (WW) RADEON(0): DRI init changed memory map, adjusting ...
[    27.876] (WW) RADEON(0):   MC_FB_LOCATION  was: 0xbfffb000 is: 0xbfffb000
[    27.877] (WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0x00000000
[    27.877] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    27.877] (II) RADEON(0):   MC_FB_LOCATION   : 0xbfffb000 0xbfffb000
[    27.877] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
[    27.877] (II) RADEON(0): Direct rendering enabled
[    27.877] (II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
[    27.877] (II) RADEON(0): Setting EXA maxPitchBytes
[    27.877] (II) RADEON(0): num quad-pipes is 1
[    27.877] (II) EXA(0): Offscreen pixmap area of 124944384 bytes
[    27.877] (II) EXA(0): Driver registered support for the following operations:
[    27.877] (II)         Solid
[    27.877] (II)         Copy
[    27.877] (II)         Composite (RENDER acceleration)
[    27.877] (II)         UploadToScreen
[    27.877] (II)         DownloadFromScreen
[    27.877] (II) RADEON(0): Acceleration enabled
[    27.877] (==) RADEON(0): DPMS enabled
[    27.877] (==) RADEON(0): Silken mouse enabled
[    27.877] (II) RADEON(0): Set up textured video
[    27.884] Output CRT1 disable success
[    27.890] Output LCD1 disable success
[    27.890] Output DFP2 disable success
[    27.890] Blank CRTC 0 success
[    27.890] Disable CRTC 0 success
[    27.890] Blank CRTC 1 success
[    27.890] Disable CRTC 1 success
[    27.890] Output LCD1 disable success
[    27.890] Blank CRTC 0 success
[    27.890] Disable CRTC 0 success
[    27.890] Mode 1280x800 - 1448 822 10
[    27.890] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    27.890] (II) RADEON(0):   MC_FB_LOCATION   : 0xbfffb000 0xbfffb000
[    27.890] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
[    27.890] Picked PLL 0
[    27.890] best_freq: 71600
[    27.890] best_feedback_div: 160
[    27.890] best_frac_feedback_div: 0
[    27.890] best_ref_div: 2
[    27.890] best_post_div: 16
[    27.890] (II) RADEON(0): crtc(0) Clock: mode 71450, PLL 716000
[    27.890] (II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0xA0(160), fracfbdiv 0, pdiv 16
[    27.893] Set CRTC 0 PLL success
[    27.893] Set CRTC Timing success
[    27.893] Set CRTC 0 Overscan success
[    27.893] Not using RMX
[    27.893] scaler 0 setup success
[    27.893] Set CRTC 0 Source success
[    27.893] crtc 0 YUV disable setup success
[    27.894] Output digital setup success
[    27.966] Output LCD1 enable success
[    27.966] Enable CRTC 0 success
[    27.966] Unblank CRTC 0 success
[    27.966] Output CRT1 disable success
[    27.966] Output DFP2 disable success
[    27.966] Blank CRTC 1 success
[    27.966] Disable CRTC 1 success
[    27.966] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    27.967] (--) RandR disabled
[    27.967] (II) Initializing built-in extension Generic Event Extension
[    27.967] (II) Initializing built-in extension SHAPE
[    27.967] (II) Initializing built-in extension MIT-SHM
[    27.967] (II) Initializing built-in extension XInputExtension
[    27.967] (II) Initializing built-in extension XTEST
[    27.967] (II) Initializing built-in extension BIG-REQUESTS
[    27.967] (II) Initializing built-in extension SYNC
[    27.967] (II) Initializing built-in extension XKEYBOARD
[    27.967] (II) Initializing built-in extension XC-MISC
[    27.967] (II) Initializing built-in extension SECURITY
[    27.967] (II) Initializing built-in extension XINERAMA
[    27.967] (II) Initializing built-in extension XFIXES
[    27.967] (II) Initializing built-in extension RENDER
[    27.967] (II) Initializing built-in extension RANDR
[    27.967] (II) Initializing built-in extension COMPOSITE
[    27.967] (II) Initializing built-in extension DAMAGE
[    27.967] (II) Initializing built-in extension GESTURE
[    27.987] (II) AIGLX: Screen 0 is not DRI2 capable
[    27.987] drmOpenDevice: node name is /dev/dri/card0
[    27.987] drmOpenDevice: open result is 13, (OK)
[    27.987] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    27.987] drmOpenDevice: node name is /dev/dri/card0
[    27.987] drmOpenDevice: open result is 13, (OK)
[    27.987] drmOpenByBusid: drmOpenMinor returns 13
[    27.987] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    28.047] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    28.047] (II) AIGLX: enabled GLX_SGI_make_current_read
[    28.047] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    28.047] (II) AIGLX: enabled GLX_texture_from_pixmap with driver support
[    28.048] (II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
[    28.048] (II) GLX: Initialized DRI GL provider for screen 0
[    28.048] (II) RADEON(0): Setting screen physical size to 338 x 211
[    28.081] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.099] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    28.100] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.100] (II) LoadModule: "evdev"
[    28.101] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.101] (II) Module evdev: vendor="X.Org Foundation"
[    28.101] 	compiled for 1.9.0, module version = 2.3.2
[    28.101] 	Module class: X.Org XInput Driver
[    28.101] 	ABI class: X.Org XInput driver, version 11.0
[    28.101] (**) Video Bus: always reports core events
[    28.101] (**) Video Bus: Device: "/dev/input/event9"
[    28.101] (II) Video Bus: Found keys
[    28.101] (II) Video Bus: Configuring as keyboard
[    28.101] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    28.101] (**) Option "xkb_rules" "evdev"
[    28.101] (**) Option "xkb_model" "pc105"
[    28.101] (**) Option "xkb_layout" "us"
[    28.103] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.103] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.103] (**) Power Button: always reports core events
[    28.103] (**) Power Button: Device: "/dev/input/event1"
[    28.103] (II) Power Button: Found keys
[    28.103] (II) Power Button: Configuring as keyboard
[    28.103] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.103] (**) Option "xkb_rules" "evdev"
[    28.103] (**) Option "xkb_model" "pc105"
[    28.103] (**) Option "xkb_layout" "us"
[    28.104] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.104] (II) No input driver/identifier specified (ignoring)
[    28.104] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    28.104] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.104] (**) Sleep Button: always reports core events
[    28.104] (**) Sleep Button: Device: "/dev/input/event2"
[    28.105] (II) Sleep Button: Found keys
[    28.105] (II) Sleep Button: Configuring as keyboard
[    28.105] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    28.105] (**) Option "xkb_rules" "evdev"
[    28.105] (**) Option "xkb_model" "pc105"
[    28.105] (**) Option "xkb_layout" "us"
[    28.107] (II) config/udev: Adding input device N-Trig Pen (/dev/input/event4)
[    28.107] (**) N-Trig Pen: Applying InputClass "evdev tablet catchall"
[    28.107] (**) N-Trig Pen: Applying InputClass "Wacom N-Trig class"
[    28.107] (II) LoadModule: "wacom"
[    28.108] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    28.108] (II) Module wacom: vendor="X.Org Foundation"
[    28.108] 	compiled for 1.8.99.905, module version = 0.10.8
[    28.108] 	Module class: X.Org XInput Driver
[    28.108] 	ABI class: X.Org XInput driver, version 11.0
[    28.108] (**) Option "Device" "/dev/input/event4"
[    28.108] (II) N-Trig Pen: type not specified, assuming 'stylus'.
[    28.108] (II) N-Trig Pen: other types will be automatically added.
[    28.109] (**) N-Trig Pen stylus: always reports core events
[    28.109] (**) Option "Button2" "3"
[    28.109] (--) N-Trig Pen stylus: using pressure threshold of 27 for button 1
[    28.109] (--) N-Trig Pen stylus: Wacom USB TabletPC tablet maxX=9600 maxY=7200 maxZ=256 resX=934 resY=1122  tilt=disabled
[    28.109] (II) N-Trig Pen stylus: hotplugging dependent devices.
[    28.109] (**) N-Trig Pen eraser: Applying InputClass "evdev tablet catchall"
[    28.109] (**) N-Trig Pen eraser: Applying InputClass "Wacom N-Trig class"
[    28.109] (**) Option "Device" "/dev/input/event4"
[    28.112] (**) N-Trig Pen eraser: always reports core events
[    28.112] (**) Option "Button2" "3"
[    28.112] (--) N-Trig Pen eraser: Wacom USB TabletPC tablet maxX=9600 maxY=7200 maxZ=256 resX=934 resY=1122  tilt=disabled
[    28.112] (II) XINPUT: Adding extended input device "N-Trig Pen eraser" (type: ERASER)
[    28.112] (--) N-Trig Pen eraser: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=934 resol Y=1122
[    28.116] (II) N-Trig Pen stylus: hotplugging completed.
[    28.116] (II) XINPUT: Adding extended input device "N-Trig Pen stylus" (type: STYLUS)
[    28.116] (--) N-Trig Pen stylus: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=934 resol Y=1122
[    28.117] (II) config/udev: Adding input device N-Trig Pen (/dev/input/mouse0)
[    28.117] (II) No input driver/identifier specified (ignoring)
[    28.117] (II) config/udev: Adding input device N-Trig Touchscreen (/dev/input/event5)
[    28.117] (**) N-Trig Touchscreen: Applying InputClass "evdev touchscreen catchall"
[    28.117] (**) N-Trig Touchscreen: always reports core events
[    28.117] (**) N-Trig Touchscreen: Device: "/dev/input/event5"
[    28.120] (II) N-Trig Touchscreen: Found absolute axes
[    28.120] (II) N-Trig Touchscreen: Found x and y absolute axes
[    28.120] (II) N-Trig Touchscreen: Found absolute touchscreen
[    28.120] (II) N-Trig Touchscreen: Configuring as touchscreen
[    28.120] (**) N-Trig Touchscreen: YAxisMapping: buttons 4 and 5
[    28.120] (**) N-Trig Touchscreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.120] (II) XINPUT: Adding extended input device "N-Trig Touchscreen" (type: TOUCHSCREEN)
[    28.120] (II) N-Trig Touchscreen: initialized for absolute axes.
[    28.121] (II) config/udev: Adding input device N-Trig Touchscreen (/dev/input/mouse1)
[    28.121] (II) No input driver/identifier specified (ignoring)
[    28.121] (II) config/udev: Adding input device N-Trig Pen (/dev/input/event6)
[    28.121] (**) N-Trig Pen: Applying InputClass "evdev tablet catchall"
[    28.121] (**) N-Trig Pen: Applying InputClass "Wacom N-Trig class"
[    28.121] (**) Option "Device" "/dev/input/event6"
[    28.122] (II) N-Trig Pen: type not specified, assuming 'stylus'.
[    28.122] (II) N-Trig Pen: other types will be automatically added.
[    28.122] (**) N-Trig Pen stylus: always reports core events
[    28.122] (**) Option "Button2" "3"
[    28.122] (--) N-Trig Pen stylus: using pressure threshold of 27 for button 1
[    28.122] (--) N-Trig Pen stylus: Wacom USB TabletPC tablet maxX=9600 maxY=7200 maxZ=256 resX=934 resY=1122  tilt=disabled
[    28.122] (II) N-Trig Pen stylus: hotplugging dependent devices.
[    28.122] (**) N-Trig Pen eraser: Applying InputClass "evdev tablet catchall"
[    28.122] (**) N-Trig Pen eraser: Applying InputClass "Wacom N-Trig class"
[    28.122] (**) Option "Device" "/dev/input/event6"
[    28.122] (**) N-Trig Pen eraser: always reports core events
[    28.122] (**) Option "Button2" "3"
[    28.122] (--) N-Trig Pen eraser: Wacom USB TabletPC tablet maxX=9600 maxY=7200 maxZ=256 resX=934 resY=1122  tilt=disabled
[    28.124] (II) XINPUT: Adding extended input device "N-Trig Pen eraser" (type: ERASER)
[    28.124] (--) N-Trig Pen eraser: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=934 resol Y=1122
[    28.132] (II) N-Trig Pen stylus: hotplugging completed.
[    28.132] (II) XINPUT: Adding extended input device "N-Trig Pen stylus" (type: STYLUS)
[    28.132] (--) N-Trig Pen stylus: top X=0 top Y=0 bottom X=9600 bottom Y=7200 resol X=934 resol Y=1122
[    28.133] (II) config/udev: Adding input device N-Trig Pen (/dev/input/mouse2)
[    28.133] (II) No input driver/identifier specified (ignoring)
[    28.133] (II) config/udev: Adding input device N-Trig Touchscreen (/dev/input/event7)
[    28.133] (**) N-Trig Touchscreen: Applying InputClass "evdev touchscreen catchall"
[    28.133] (**) N-Trig Touchscreen: always reports core events
[    28.133] (**) N-Trig Touchscreen: Device: "/dev/input/event7"
[    28.133] (II) N-Trig Touchscreen: Found absolute axes
[    28.133] (II) N-Trig Touchscreen: Found x and y absolute axes
[    28.134] (II) N-Trig Touchscreen: Found absolute touchscreen
[    28.134] (II) N-Trig Touchscreen: Configuring as touchscreen
[    28.134] (**) N-Trig Touchscreen: YAxisMapping: buttons 4 and 5
[    28.134] (**) N-Trig Touchscreen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.134] (II) XINPUT: Adding extended input device "N-Trig Touchscreen" (type: TOUCHSCREEN)
[    28.134] (II) N-Trig Touchscreen: initialized for absolute axes.
[    28.134] (II) config/udev: Adding input device N-Trig Touchscreen (/dev/input/mouse3)
[    28.134] (II) No input driver/identifier specified (ignoring)
[    28.139] (II) config/udev: Adding input device HDA ATI SB Mic at Ext Left Jack (/dev/input/event10)
[    28.139] (II) No input driver/identifier specified (ignoring)
[    28.139] (II) config/udev: Adding input device HDA ATI SB HP Out at Ext Left Jack (/dev/input/event11)
[    28.139] (II) No input driver/identifier specified (ignoring)
[    28.141] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    28.141] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.141] (**) AT Translated Set 2 keyboard: always reports core events
[    28.141] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    28.141] (II) AT Translated Set 2 keyboard: Found keys
[    28.141] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    28.141] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    28.141] (**) Option "xkb_rules" "evdev"
[    28.141] (**) Option "xkb_model" "pc105"
[    28.141] (**) Option "xkb_layout" "us"
[    28.142] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event12)
[    28.142] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    28.142] (**) PS/2 Generic Mouse: always reports core events
[    28.142] (**) PS/2 Generic Mouse: Device: "/dev/input/event12"
[    28.142] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[    28.142] (II) PS/2 Generic Mouse: Found relative axes
[    28.142] (II) PS/2 Generic Mouse: Found x and y relative axes
[    28.142] (II) PS/2 Generic Mouse: Configuring as mouse
[    28.143] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    28.143] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.143] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    28.143] (II) PS/2 Generic Mouse: initialized for relative axes.
[    28.143] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse4)
[    28.143] (II) No input driver/identifier specified (ignoring)
[    28.148] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[    28.148] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    28.148] (**) Dell WMI hotkeys: always reports core events
[    28.148] (**) Dell WMI hotkeys: Device: "/dev/input/event8"
[    28.148] (II) Dell WMI hotkeys: Found keys
[    28.148] (II) Dell WMI hotkeys: Configuring as keyboard
[    28.148] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    28.148] (**) Option "xkb_rules" "evdev"
[    28.149] (**) Option "xkb_model" "pc105"
[    28.149] (**) Option "xkb_layout" "us"
[    41.321] Dac detection success
[    41.321] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    41.383] (II) RADEON(0): EDID vendor "AUO", prod id 16916
[    41.383] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    41.383] (II) RADEON(0): Printing DDC gathered Modelines:
[    41.383] (II) RADEON(0): Modeline "1280x800"x0.0   71.45  1280 1328 1360 1448  800 803 809 822 -hsync -vsync (49.3 kHz)
[    41.383] (II) RADEON(0): Modeline "1280x800"x0.0   70.30  1280 1328 1360 1424  800 803 809 822 -hsync -vsync (49.4 kHz)
[    41.383] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    41.383] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    41.383] (II) RADEON(0): Manufacturer: AUO  Model: 4214  Serial#: 0
[    41.383] (II) RADEON(0): Year: 2007  Week: 1
[    41.383] (II) RADEON(0): EDID Version: 1.3
[    41.383] (II) RADEON(0): Digital Display Input
[    41.383] (II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[    41.383] (II) RADEON(0): Gamma: 2.20
[    41.383] (II) RADEON(0): No DPMS capabilities specified
[    41.383] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    41.383] (II) RADEON(0): First detailed timing is preferred mode
[    41.383] (II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.330 greenY: 0.575
[    41.383] (II) RADEON(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[    41.383] (II) RADEON(0): Manufacturer's mask: 0
[    41.383] (II) RADEON(0): Supported detailed timing:
[    41.383] (II) RADEON(0): clock: 71.5 MHz   Image Size:  261 x 163 mm
[    41.383] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1448 h_border: 0
[    41.383] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    41.383] (II) RADEON(0): Supported detailed timing:
[    41.383] (II) RADEON(0): clock: 70.3 MHz   Image Size:  261 x 163 mm
[    41.383] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1424 h_border: 0
[    41.383] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    41.383] (II) RADEON(0):  KX774B121EW4
[    41.383] (II) RADEON(0):  	4`„ÿ
[    41.383] (II) RADEON(0): EDID (in hex):
[    41.383] (II) RADEON(0): 	00ffffffffffff0006af144200000000
[    41.383] (II) RADEON(0): 	01110103801a10780a89e59457549327
[    41.383] (II) RADEON(0): 	22505400000001010101010101010101
[    41.383] (II) RADEON(0): 	010101010101e91b00a8502016303020
[    41.383] (II) RADEON(0): 	360005a310000019761b009050201630
[    41.383] (II) RADEON(0): 	3020360005a310000000000000fe004b
[    41.383] (II) RADEON(0): 	583737340242313231455734000000fe
[    41.383] (II) RADEON(0): 	00090f151a346084ff01010a2020001b
[    41.384] (II) RADEON(0): EDID vendor "AUO", prod id 16916
[    41.384] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    41.389] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    49.423] Dac detection success
[    49.423] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[    49.538] (II) RADEON(0): EDID vendor "AUO", prod id 16916
[    49.538] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    49.538] (II) RADEON(0): Printing DDC gathered Modelines:
[    49.538] (II) RADEON(0): Modeline "1280x800"x0.0   71.45  1280 1328 1360 1448  800 803 809 822 -hsync -vsync (49.3 kHz)
[    49.538] (II) RADEON(0): Modeline "1280x800"x0.0   70.30  1280 1328 1360 1424  800 803 809 822 -hsync -vsync (49.4 kHz)
[    49.538] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
[    49.538] (II) RADEON(0): EDID data from the display on output: LVDS ----------------------
[    49.538] (II) RADEON(0): Manufacturer: AUO  Model: 4214  Serial#: 0
[    49.538] (II) RADEON(0): Year: 2007  Week: 1
[    49.538] (II) RADEON(0): EDID Version: 1.3
[    49.538] (II) RADEON(0): Digital Display Input
[    49.538] (II) RADEON(0): Max Image Size [cm]: horiz.: 26  vert.: 16
[    49.538] (II) RADEON(0): Gamma: 2.20
[    49.538] (II) RADEON(0): No DPMS capabilities specified
[    49.538] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    49.538] (II) RADEON(0): First detailed timing is preferred mode
[    49.538] (II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.330 greenY: 0.575
[    49.538] (II) RADEON(0): blueX: 0.155 blueY: 0.135   whiteX: 0.313 whiteY: 0.329
[    49.538] (II) RADEON(0): Manufacturer's mask: 0
[    49.538] (II) RADEON(0): Supported detailed timing:
[    49.538] (II) RADEON(0): clock: 71.5 MHz   Image Size:  261 x 163 mm
[    49.538] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1448 h_border: 0
[    49.538] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    49.538] (II) RADEON(0): Supported detailed timing:
[    49.538] (II) RADEON(0): clock: 70.3 MHz   Image Size:  261 x 163 mm
[    49.538] (II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1424 h_border: 0
[    49.539] (II) RADEON(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 822 v_border: 0
[    49.539] (II) RADEON(0):  KX774B121EW4
[    49.539] (II) RADEON(0):  	4`„ÿ
[    49.539] (II) RADEON(0): EDID (in hex):
[    49.539] (II) RADEON(0): 	00ffffffffffff0006af144200000000
[    49.539] (II) RADEON(0): 	01110103801a10780a89e59457549327
[    49.539] (II) RADEON(0): 	22505400000001010101010101010101
[    49.539] (II) RADEON(0): 	010101010101e91b00a8502016303020
[    49.539] (II) RADEON(0): 	360005a310000019761b009050201630
[    49.539] (II) RADEON(0): 	3020360005a310000000000000fe004b
[    49.539] (II) RADEON(0): 	583737340242313231455734000000fe
[    49.539] (II) RADEON(0): 	00090f151a346084ff01010a2020001b
[    49.539] (II) RADEON(0): EDID vendor "AUO", prod id 16916
[    49.539] (II) RADEON(0): DDCModeFromDetailedTiming: 1280x800 Warning: We only handle separate sync.
[    49.553] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 0
[    62.668] 
Backtrace:
[    62.668] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
[    62.668] 1: /usr/bin/X (0x8048000+0x5da8d) [0x80a5a8d]
[    62.668] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb77df40c]
[    62.669] 3: /usr/bin/X (FreeResource+0x112) [0x808f4b2]
[    62.669] 4: /usr/lib/xorg/modules/extensions/libglx.so (0xb73bf000+0x336d0) [0xb73f26d0]
[    62.669] 5: /usr/lib/xorg/modules/extensions/libglx.so (0xb73bf000+0x36ab2) [0xb73f5ab2]
[    62.669] 6: /usr/bin/X (0x8048000+0x26087) [0x806e087]
[    62.669] 7: /usr/bin/X (0x8048000+0x1a5ba) [0x80625ba]
[    62.669] 8: /lib/libc.so.6 (__libc_start_main+0xe7) [0xb7509ce7]
[    62.669] 9: /usr/bin/X (0x8048000+0x1a191) [0x8062191]
[    62.669] Segmentation fault at address 0x921d200c
[    62.669] 
Caught signal 11 (Segmentation fault). Server aborting
[    62.669] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    62.669] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    62.669] 
[    62.670] (II) Video Bus: Close
[    62.670] (II) UnloadModule: "evdev"
[    62.670] (II) Power Button: Close
[    62.670] (II) UnloadModule: "evdev"
[    62.671] (II) Sleep Button: Close
[    62.671] (II) UnloadModule: "evdev"
[    62.672] (II) UnloadModule: "wacom"
[    62.680] (II) N-Trig Pen stylus: removing automatically added devices.
[    62.681] (II) UnloadModule: "wacom"
[    62.684] (II) N-Trig Touchscreen: Close
[    62.684] (II) UnloadModule: "evdev"
[    62.685] (II) UnloadModule: "wacom"
[    62.692] (II) N-Trig Pen stylus: removing automatically added devices.
[    62.693] (II) UnloadModule: "wacom"
[    62.696] (II) N-Trig Touchscreen: Close
[    62.696] (II) UnloadModule: "evdev"
[    62.697] (II) AT Translated Set 2 keyboard: Close
[    62.697] (II) UnloadModule: "evdev"
[    62.704] (II) PS/2 Generic Mouse: Close
[    62.704] (II) UnloadModule: "evdev"
[    62.705] (II) Dell WMI hotkeys: Close
[    62.705] (II) UnloadModule: "evdev"
[    62.705] (II) AIGLX: Suspending AIGLX clients for VT switch
[    63.111] Output LCD1 disable success
[    63.127] Blank CRTC 0 success
[    63.127] Disable CRTC 0 success
[    63.127] Blank CRTC 1 success
[    63.127] Disable CRTC 1 success
[    63.127] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    63.127] (II) RADEON(0):   MC_FB_LOCATION   : 0xbfffb000 0xbfffb000
[    63.127] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
[    63.127] (II) RADEON(0): avivo_restore !
[    63.128] Enable CRTC 0 success
[    63.144] Unblank CRTC 0 success
[    63.152]  ddxSigGiveUp: Closing log

```

kdm.log
```
*********************************WARN_ONCE*********************************
File radeon_dma.c function radeonReleaseDmaRegions line 340
Leaking dma buffer object!
***************************************************************************

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
1: /usr/bin/X (0x8048000+0x5da8d) [0x80a5a8d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xdef40c]
3: /usr/bin/X (FreeClientResources+0xed) [0x808f04d]
4: /usr/bin/X (FreeAllResources+0x60) [0x808f120]
5: /usr/bin/X (0x8048000+0x1a5e6) [0x80625e6]
6: /lib/libc.so.6 (__libc_start_main+0xe7) [0x2a6ce7]
7: /usr/bin/X (0x8048000+0x1a191) [0x8062191]
Segmentation fault at address 0x401129c4

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Enable CRTC 0 success
Unblank CRTC 0 success
 ddxSigGiveUp: Closing log

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.37-020637rc2-generic #201011160905 SMP Tue Nov 16 10:15:47 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637rc2-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 00:34:19 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] drm report modesetting isn't supported.
(EE) open /dev/fb0: No such file or directory
(EE) RADEON(0): Unable to map MMIO aperture. Invalid argument (22)
(EE) RADEON(0): Memory map the MMIO region failed
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
md5sum: /etc/X11/xorg.conf: No such file or directory
/etc/gdm/failsafeXServer: line 141: /var/log/gdm/failsafe.log: No such file or directory
Warning:  Cannot write to /var/log/gdm/failsafe.log
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X  -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.37-020637rc2-generic #201011160905 SMP Tue Nov 16 10:15:47 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637rc2-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Tue Nov 23 00:34:20 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.37-020637rc2-generic #201011160905 SMP Tue Nov 16 10:15:47 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637rc2-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 00:34:34 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] drm report modesetting isn't supported.
(EE) open /dev/fb0: No such file or directory
(EE) RADEON(0): Unable to map MMIO aperture. Invalid argument (22)
(EE) RADEON(0): Memory map the MMIO region failed
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
md5sum: /etc/X11/xorg.conf: No such file or directory
/etc/gdm/failsafeXServer: line 141: /var/log/gdm/failsafe.log: No such file or directory
Warning:  Cannot write to /var/log/gdm/failsafe.log
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X  -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.37-020637rc2-generic #201011160905 SMP Tue Nov 16 10:15:47 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637rc2-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Tue Nov 23 00:34:34 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) VESA(0): Driver can't support depth 24
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 15.

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.37-020637rc2-generic #201011160905 SMP Tue Nov 16 10:15:47 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637rc2-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 00:36:58 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] drm report modesetting isn't supported.
(EE) open /dev/fb0: No such file or directory
(EE) RADEON(0): Unable to map MMIO aperture. Invalid argument (22)
(EE) RADEON(0): Memory map the MMIO region failed
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
md5sum: /etc/X11/xorg.conf: No such file or directory
/etc/gdm/failsafeXServer: line 141: /var/log/gdm/failsafe.log: No such file or directory
Warning:  Cannot write to /var/log/gdm/failsafe.log
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe -- /usr/bin/X  -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.37-020637rc2-generic #201011160905 SMP Tue Nov 16 10:15:47 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-020637rc2-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Tue Nov 23 00:36:59 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) VESA(0): No matching modes
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.


waiting for X server to begin accepting connections  ddxSigGiveUp: Closing log

giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 15.

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.37-999-generic #201011060905 SMP Sat Nov 6 10:15:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-999-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 00:38:01 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] drm report modesetting isn't supported.
(EE) open /dev/fb0: No such file or directory
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e40
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVTM1
  DDC reg: 0x7e40
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP2: INTERNAL_DDI
  DDC reg: 0x7e40
Dac detection success
finished output detect: 0
finished output detect: 1
finished output detect: 2
finished all detect
Dac detection success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output CRT1 disable success
Output LCD1 disable success
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x800 - 1448 822 10
Picked PLL 0
best_freq: 71600
best_feedback_div: 160
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 16
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output digital setup success
Output LCD1 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Output CRT1 disable success
Output DFP2 disable success
Blank CRTC 1 success
Disable CRTC 1 success
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/0488914584/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QFile::remove: Empty or null file name
Dac detection success
Dac detection success

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
1: /usr/bin/X (0x8048000+0x5da8d) [0x80a5a8d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb777540c]
3: /usr/bin/X (FreeResource+0x112) [0x808f4b2]
4: /usr/lib/xorg/modules/extensions/libglx.so (0xb7355000+0x336d0) [0xb73886d0]
5: /usr/lib/xorg/modules/extensions/libglx.so (0xb7355000+0x36ab2) [0xb738bab2]
6: /usr/bin/X (0x8048000+0x26087) [0x806e087]
7: /usr/bin/X (0x8048000+0x1a5ba) [0x80625ba]
8: /lib/libc.so.6 (__libc_start_main+0xe7) [0xb749fce7]
9: /usr/bin/X (0x8048000+0x1a191) [0x8062191]
Segmentation fault at address 0x9165100c

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Enable CRTC 0 success
Unblank CRTC 0 success
 ddxSigGiveUp: Closing log

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.37-999-generic #201011060905 SMP Sat Nov 6 10:15:29 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.37-999-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 00:38:55 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] drm report modesetting isn't supported.
(EE) open /dev/fb0: No such file or directory
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e40
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVTM1
  DDC reg: 0x7e40
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP2: INTERNAL_DDI
  DDC reg: 0x7e40
Dac detection success
finished output detect: 0
finished output detect: 1
finished output detect: 2
finished all detect
Dac detection success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output CRT1 disable success
Output LCD1 disable success
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x800 - 1448 822 10
Picked PLL 0
best_freq: 71600
best_feedback_div: 160
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 16
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output digital setup success
Output LCD1 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Output CRT1 disable success
Output DFP2 disable success
Blank CRTC 1 success
Disable CRTC 1 success
Dac detection success
Dac detection success

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
1: /usr/bin/X (0x8048000+0x5da8d) [0x80a5a8d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb787a40c]
3: /usr/bin/X (FreeClientResources+0xed) [0x808f04d]
4: /usr/bin/X (FreeAllResources+0x60) [0x808f120]
5: /usr/bin/X (0x8048000+0x1a5e6) [0x80625e6]
6: /lib/libc.so.6 (__libc_start_main+0xe7) [0xb75a4ce7]
7: /usr/bin/X (0x8048000+0x1a191) [0x8062191]
Segmentation fault at address 0x4

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Enable CRTC 0 success
Unblank CRTC 0 success
 ddxSigGiveUp: Closing log

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.36-020636rc7-generic #201010070908 SMP Thu Oct 7 10:21:05 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-020636rc7-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 00:51:38 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] drm report modesetting isn't supported.
(EE) open /dev/fb0: No such file or directory
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e40
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVTM1
  DDC reg: 0x7e40
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP2: INTERNAL_DDI
  DDC reg: 0x7e40
Dac detection success
finished output detect: 0
finished output detect: 1
finished output detect: 2
finished all detect
Dac detection success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output CRT1 disable success
Output LCD1 disable success
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x800 - 1448 822 10
Picked PLL 0
best_freq: 71600
best_feedback_div: 160
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 16
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output digital setup success
Output LCD1 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Output CRT1 disable success
Output DFP2 disable success
Blank CRTC 1 success
Disable CRTC 1 success
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /tmp/0043468706/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 
QFile::remove: Empty or null file name
Dac detection success
Dac detection success

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e82fb]
1: /usr/bin/X (0x8048000+0x5da8d) [0x80a5a8d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb77df40c]
3: /usr/bin/X (FreeResource+0x112) [0x808f4b2]
4: /usr/lib/xorg/modules/extensions/libglx.so (0xb73bf000+0x336d0) [0xb73f26d0]
5: /usr/lib/xorg/modules/extensions/libglx.so (0xb73bf000+0x36ab2) [0xb73f5ab2]
6: /usr/bin/X (0x8048000+0x26087) [0x806e087]
7: /usr/bin/X (0x8048000+0x1a5ba) [0x80625ba]
8: /lib/libc.so.6 (__libc_start_main+0xe7) [0xb7509ce7]
9: /usr/bin/X (0x8048000+0x1a191) [0x8062191]
Segmentation fault at address 0x921d200c

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Enable CRTC 0 success
Unblank CRTC 0 success
 ddxSigGiveUp: Closing log

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux neo 2.6.36-020636rc7-generic #201010070908 SMP Thu Oct 7 10:21:05 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.36-020636rc7-generic root=UUID=ec43c8bb-04fb-4b27-9041-8b7af0f96dea ro quiet splash nomodeset radeon.modeset=0
Build Date: 16 September 2010  05:39:22PM
xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 23 00:52:15 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] drm report modesetting isn't supported.
(EE) open /dev/fb0: No such file or directory
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e40
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVTM1
  DDC reg: 0x7e40
  XRANDR name: DVI-0
  Connector: DVI-D
  DFP2: INTERNAL_DDI
  DDC reg: 0x7e40
Dac detection success
finished output detect: 0
finished output detect: 1
finished output detect: 2
finished all detect
Dac detection success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output CRT1 disable success
Output LCD1 disable success
Output DFP2 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output LCD1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1280x800 - 1448 822 10
Picked PLL 0
best_freq: 71600
best_feedback_div: 160
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 16
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output digital setup success
Output LCD1 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Output CRT1 disable success
Output DFP2 disable success
Blank CRTC 1 success
Disable CRTC 1 success
Dac detection success
Dac detection success
*********************************WARN_ONCE*********************************
File radeon_dma.c function radeonReleaseDmaRegions line 340
Leaking dma buffer object!
***************************************************************************

```

Possibly related links:
[https://bbs.archlinux.org/viewtopic.php?pid=845112](https://bbs.archlinux.org/viewtopic.php?pid=845112)
[http://kubuntuforums.net/forums/index.php?topic=3114123.0](http://kubuntuforums.net/forums/index.php?topic=3114123.0)
[http://ubuntuforums.org/showthread.php?t=1455746](http://ubuntuforums.org/showthread.php?t=1455746)
[https://bugs.freedesktop.org/show_bug.cgi?id=25179](https://bugs.freedesktop.org/show_bug.cgi?id=25179)
[http://ca.ubuntuforums.org/showthread.php?t=1593410&page=2](http://ca.ubuntuforums.org/showthread.php?t=1593410&page=2)

Any ideas, anyone?

---

