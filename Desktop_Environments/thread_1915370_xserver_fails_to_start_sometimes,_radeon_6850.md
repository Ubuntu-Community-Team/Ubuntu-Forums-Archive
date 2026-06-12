---
title: "xserver fails to start sometimes, radeon 6850"
date: 2012-01-26
forum: Desktop Environments
---

### Post by HasanYavuzOZDERYA on 2012-01-26
Hi, I have a radeon 6850 graphics card and ubuntu 11.10 amd64 installation. I'm using gnome-shell. Sometimes xserver doesn't start. But sometimes everything works just fine. When xserver doesn't start, I press ctrl+alt+F1 and start xserver typing "startx". That's okay. Then I can run gnome-shell with  "gnome-shell --replace". That's also okay. So it looks like there is no reason for xserver to fail. :S I have tried to install "fglrx". But this messes up with gnome-shell. So I don't want to use it. This is my xorg log upon fail.

```
[    11.950] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    11.950] X Protocol Version 11, Revision 0
[    11.950] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    11.950] Current Operating System: Linux heyyo-990fxa 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[    11.950] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=005ea3b7-36a3-4825-b039-bd629d2b7f82 ro quiet splash vt.handoff=7
[    11.950] Build Date: 19 October 2011  05:21:26AM
[    11.950] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    11.950] Current version of pixman: 0.22.2
[    11.950]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    11.950] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    11.950] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 10 17:25:06 2012
[    11.950] (==) Using config file: "/etc/X11/xorg.conf"
[    11.950] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    11.950] (==) No Layout section.  Using the first Screen section.
[    11.950] (==) No screen section available. Using defaults.
[    11.950] (**) |-->Screen "Default Screen Section" (0)
[    11.950] (**) |   |-->Monitor "<default monitor>"
[    11.951] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    11.951] (==) Automatically adding devices
[    11.951] (==) Automatically enabling devices
[    11.951] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    11.951]     Entry deleted from font path.
[    11.951] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    11.951]     Entry deleted from font path.
[    11.951] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    11.951]     Entry deleted from font path.
[    11.951] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    11.951]     Entry deleted from font path.
[    11.951] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    11.951]     Entry deleted from font path.
[    11.951] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    11.951] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    11.951] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    11.951] (II) Loader magic: 0x7e0220
[    11.951] (II) Module ABI versions:
[    11.951]     X.Org ANSI C Emulation: 0.4
[    11.951]     X.Org Video Driver: 10.0
[    11.951]     X.Org XInput driver : 12.3
[    11.951]     X.Org Server Extension : 5.0
[    11.952] (--) PCI:*(0:1:0:0) 1002:6739:1043:03b4 rev 0, Mem @ 0xd0000000/268435456, 0xfddc0000/131072, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    11.952] (II) Open ACPI successful (/var/run/acpid.socket)
[    11.953] (II) LoadModule: "extmod"
[    11.990] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    11.990] (II) Module extmod: vendor="X.Org Foundation"
[    11.990]     compiled for 1.10.4, module version = 1.0.0
[    11.990]     Module class: X.Org Server Extension
[    11.990]     ABI class: X.Org Server Extension, version 5.0
[    11.990] (II) Loading extension MIT-SCREEN-SAVER
[    11.990] (II) Loading extension XFree86-VidModeExtension
[    11.990] (II) Loading extension XFree86-DGA
[    11.990] (II) Loading extension DPMS
[    11.990] (II) Loading extension XVideo
[    11.990] (II) Loading extension XVideo-MotionCompensation
[    11.990] (II) Loading extension X-Resource
[    11.990] (II) LoadModule: "dbe"
[    11.991] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    11.991] (II) Module dbe: vendor="X.Org Foundation"
[    11.991]     compiled for 1.10.4, module version = 1.0.0
[    11.991]     Module class: X.Org Server Extension
[    11.991]     ABI class: X.Org Server Extension, version 5.0
[    11.991] (II) Loading extension DOUBLE-BUFFER
[    11.991] (II) LoadModule: "glx"
[    11.991] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    11.991] (II) Module glx: vendor="X.Org Foundation"
[    11.991]     compiled for 1.10.4, module version = 1.0.0
[    11.991]     ABI class: X.Org Server Extension, version 5.0
[    11.991] (==) AIGLX enabled
[    11.991] (II) Loading extension GLX
[    11.991] (II) LoadModule: "record"
[    11.991] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.991] (II) Module record: vendor="X.Org Foundation"
[    11.991]     compiled for 1.10.4, module version = 1.13.0
[    11.991]     Module class: X.Org Server Extension
[    11.991]     ABI class: X.Org Server Extension, version 5.0
[    11.991] (II) Loading extension RECORD
[    11.991] (II) LoadModule: "dri"
[    11.991] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    11.991] (II) Module dri: vendor="X.Org Foundation"
[    11.991]     compiled for 1.10.4, module version = 1.0.0
[    11.991]     ABI class: X.Org Server Extension, version 5.0
[    11.991] (II) Loading extension XFree86-DRI
[    11.991] (II) LoadModule: "dri2"
[    11.991] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    11.991] (II) Module dri2: vendor="X.Org Foundation"
[    11.991]     compiled for 1.10.4, module version = 1.2.0
[    11.991]     ABI class: X.Org Server Extension, version 5.0
[    11.991] (II) Loading extension DRI2
[    11.991] (==) Matched fglrx as autoconfigured driver 0
[    11.991] (==) Matched ati as autoconfigured driver 1
[    11.991] (==) Matched vesa as autoconfigured driver 2
[    11.991] (==) Matched fbdev as autoconfigured driver 3
[    11.991] (==) Assigned the driver to the xf86ConfigLayout
[    11.991] (II) LoadModule: "fglrx"
[    11.992] (WW) Warning, couldn't open module fglrx
[    11.992] (II) UnloadModule: "fglrx"
[    11.992] (II) Unloading fglrx
[    11.992] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    11.992] (II) LoadModule: "ati"
[    11.992] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    11.992] (II) Module ati: vendor="X.Org Foundation"
[    11.992]     compiled for 1.10.2.902, module version = 6.14.99
[    11.992]     Module class: X.Org Video Driver
[    11.992]     ABI class: X.Org Video Driver, version 10.0
[    11.992] (II) LoadModule: "radeon"
[    11.992] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    11.992] (II) Module radeon: vendor="X.Org Foundation"
[    11.992]     compiled for 1.10.2.902, module version = 6.14.99
[    11.992]     Module class: X.Org Video Driver
[    11.992]     ABI class: X.Org Video Driver, version 10.0
[    11.992] (II) LoadModule: "vesa"
[    11.992] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    11.992] (II) Module vesa: vendor="X.Org Foundation"
[    11.992]     compiled for 1.10.2, module version = 2.3.0
[    11.992]     Module class: X.Org Video Driver
[    11.992]     ABI class: X.Org Video Driver, version 10.0
[    11.992] (II) LoadModule: "fbdev"
[    11.993] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    11.993] (II) Module fbdev: vendor="X.Org Foundation"
[    11.993]     compiled for 1.10.0, module version = 0.4.2
[    11.993]     ABI class: X.Org Video Driver, version 10.0
[    11.993] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
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
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS
[    11.994] (II) VESA: driver for VESA chipsets: vesa
[    11.994] (II) FBDEV: driver for framebuffer: fbdev
[    11.994] (++) using VT number 7

[    11.994] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    11.994] (II) [KMS] Kernel modesetting enabled.
[    11.994] (WW) Falling back to old probe method for vesa
[    11.994] (WW) Falling back to old probe method for fbdev
[    11.994] (II) Loading sub module "fbdevhw"
[    11.994] (II) LoadModule: "fbdevhw"
[    11.995] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    11.995] (II) Module fbdevhw: vendor="X.Org Foundation"
[    11.995]     compiled for 1.10.4, module version = 0.0.2
[    11.995]     ABI class: X.Org Video Driver, version 10.0
[    11.995] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    11.995] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    11.995] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    11.995] (==) RADEON(0): Default visual is TrueColor
[    11.995] (==) RADEON(0): RGB weight 888
[    11.995] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    11.995] (--) RADEON(0): Chipset: "AMD Radeon HD 6800 Series" (ChipID = 0x6739)
[    11.995] (II) RADEON(0): PCIE card detected
[    11.995] drmOpenDevice: node name is /dev/dri/card0
[    11.995] drmOpenDevice: open result is 12, (OK)
[    12.073] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    12.073] drmOpenDevice: node name is /dev/dri/card0
[    12.073] drmOpenDevice: open result is 12, (OK)
[    12.073] drmOpenByBusid: drmOpenMinor returns 12
[    12.073] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    12.073] drmOpenByBusid: drmGetBusid reports 
[    12.073] drmOpenDevice: node name is /dev/dri/card1
[    12.077] drmOpenByBusid: drmOpenMinor returns -1
[    12.077] drmOpenDevice: node name is /dev/dri/card2
[    12.081] drmOpenByBusid: drmOpenMinor returns -1
[    12.081] drmOpenDevice: node name is /dev/dri/card3
[    12.085] drmOpenByBusid: drmOpenMinor returns -1
[    12.085] drmOpenDevice: node name is /dev/dri/card4
[    12.088] drmOpenByBusid: drmOpenMinor returns -1
[    12.088] drmOpenDevice: node name is /dev/dri/card5
[    12.092] drmOpenByBusid: drmOpenMinor returns -1
[    12.092] drmOpenDevice: node name is /dev/dri/card6
[    12.096] drmOpenByBusid: drmOpenMinor returns -1
[    12.096] drmOpenDevice: node name is /dev/dri/card7
[    12.100] drmOpenByBusid: drmOpenMinor returns -1
[    12.100] drmOpenDevice: node name is /dev/dri/card8
[    12.104] drmOpenByBusid: drmOpenMinor returns -1
[    12.104] drmOpenDevice: node name is /dev/dri/card9
[    12.107] drmOpenByBusid: drmOpenMinor returns -1
[    12.107] drmOpenDevice: node name is /dev/dri/card10
[    12.111] drmOpenByBusid: drmOpenMinor returns -1
[    12.111] drmOpenDevice: node name is /dev/dri/card11
[    12.115] drmOpenByBusid: drmOpenMinor returns -1
[    12.115] drmOpenDevice: node name is /dev/dri/card12
[    12.119] drmOpenByBusid: drmOpenMinor returns -1
[    12.119] drmOpenDevice: node name is /dev/dri/card13
[    12.122] drmOpenByBusid: drmOpenMinor returns -1
[    12.122] drmOpenDevice: node name is /dev/dri/card14
[    12.127] drmOpenByBusid: drmOpenMinor returns -1
[    12.127] drmOpenDevice: node name is /dev/dri/card15
[    12.135] drmOpenByBusid: drmOpenMinor returns -1
[    12.135] drmOpenDevice: node name is /dev/dri/card0
[    12.135] drmOpenDevice: open result is 12, (OK)
[    12.345] drmOpenDevice: node name is /dev/dri/card0
[    12.345] drmOpenDevice: open result is 12, (OK)
[    12.345] drmGetBusid returned ''
[    12.345] (EE) RADEON(0): [drm] failed to set drm interface version.
[    12.345] (EE) RADEON(0): Kernel modesetting setup failed
[    12.345] (II) UnloadModule: "radeon"
[    12.345] (II) Unloading radeon
[    12.345] (EE) Screen(s) found, but none have a usable configuration.
[    12.345] 
Fatal server error:
[    12.345] no screens found
[    12.345] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    12.345] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    12.345] 
[    12.351]  ddxSigGiveUp: Closing log
```

That started to become really annoying. Please give me an idea to solve this..:confused:

---

### Post by alphaamanitin on 2012-02-14
I have the exact same problem, but I can't get x to start at all.  I think this is a kernel bug, we should report this to the linux kernel development group: [http://www.kernel.org/doc/man-pages/reporting_code_bugs.html](http://www.kernel.org/doc/man-pages/reporting_code_bugs.html) for information on reporting kernel bug.

AlphaA

---

