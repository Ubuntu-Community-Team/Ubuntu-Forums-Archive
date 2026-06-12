---
title: "Desktop effects just stopped."
date: 2009-12-02
forum: Desktop Environments
---

### Post by willro on 2009-12-02
Ok, so for the longest time i've used the extra desktop effects no problem. then i hooked up my monster flat screen and suddenly had problems. if i had done my research i would have seen this causes the problem. but, i do not know how to fix it. I've already went into display and changed the resolution back down to 1280 x 800, but every time i go to eneable desktop effects, it searches for drivers. then tells me that Desktop effects could not be enabled. the graphics on my laptop are from a radeon xpress 200m.
I've tried to fix the problem using Envyng to get a driver, but that lead to my computer only booting in text mode(solved in a different thread) so i don't think that will be the answer.

---

### Post by willro on 2009-12-04
still need help with this problem... desktop effects work fine when running off of liveCD

---

### Post by willro on 2009-12-08
well, i guess i'll bump this against since it doesn't stay on the front page for longer then 30 seconds

---

### Post by gabe17 on 2009-12-09
Have you installed the drivers from your grafics card manufactors site? I think it could help. I have the same problem with ubuntu effects, sometimes they are working and sometimes not. Do you have an ATI grafics card?

---

### Post by willro on 2009-12-09
> **gabe17 said:**
> Have you installed the drivers from your grafics card manufactors site? I think it could help. I have the same problem with ubuntu effects, sometimes they are working and sometimes not. Do you have an ATI grafics card?
yes i have an ATI graphics. its an Radion Express 200m.i've tried to do drivers, but catalyst doesn't start and the instructions from ATI's website are a pain to use.

---

### Post by gabe17 on 2009-12-11
Yes, I've realised there are many problems with ATI grafics card and their drivers for linux, I have been struggling with it for few weeks.

---

### Post by willro on 2009-12-11
the whole thing is is that it was working fine until i hooked up my laptop to my screen which messed with my display settings and set it to higher then what is possible on my laptop. and according to other sites, what should have fixxed it was me lowering my display res back down to 1200x800(roughly) which is what it's supposed to be, well that didn't fix it.


when i go to start the ATI control center i get an error message

"No ati graphics driver is installed"

well ... really? isn't that what your used for? lol

---

### Post by gabe17 on 2009-12-11
No, I used not to get this message, but my Catalyst center used not to start anywise and I sometimes have problems with visual effects, which are sometimes not smooth.

---

### Post by willro on 2009-12-11
well my effecs worked just fine, and looked great, but now they don't work at all.

"desktop effects could not be enabled"

---

### Post by willro on 2009-12-11
ok how about i propose a new question since no one can answer my last one. how to i reinable the default xorg driver instead of the crummy Flgrx driver that i think i have, checked my logs from xorg and this is the first one.

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux willis-laptop 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-16-generic root=UUID=968363f6-1269-4d5c-a7e3-c7a3f00134cf ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 11 09:34:51 2009
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:5a62:1179:ff04 ATI Technologies Inc RC410 [Radeon Xpress 200M] rev 0, Mem @ 0xd0000000/268435456, 0xc0000000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default ati Device 0"
        Driver    "ati"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default ati Screen 0"
        Device    "Builtin Default ati Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default ati Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default ati Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default ati Device 0"
(==) No monitor specified for screen "Builtin Default ati Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
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
    compiled for 1.6.4, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.66.10
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 6.12.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 6.12.99
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
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
    ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
    ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI Radeon RV730 (AGP),
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
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
    ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
    ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
    ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
    ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
    ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
    ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI RS880
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 01@00:05:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000c0000000
(II) RADEON(0): MMIO registers at 0x00000000c0000000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
    "Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200M 5A62 (PCIE)" (ChipID = 0x5a62)
(--) RADEON(0): Linear framebuffer at 0x00000000d0000000
(II) RADEON(0): PCI card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
(EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
(II) RADEON(0): Detected total video RAM=131072K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 100, max_in_pll: 1350, xclk: 26600, sclk: 300.000000, mclk: 266.000000
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000; xclk=26600
(II) RADEON(0): Panel ID string: SEC                     
(II) RADEON(0): Panel Size from BIOS: 1280x800
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1280, YRes: 800, DotClock: 68940
HBlank: 128, HOverPlus: 16, HSyncWidth: 48
VBlank: 16, VOverPlus: 1, VSyncWidth: 3
(WW) RADEON(0): LCD DDC Info Table found!
(II) RADEON(0): Output VGA-0 has no monitor section
(II) RADEON(0): I2C bus "VGA-0" initialized.
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): I2C bus "LVDS" initialized.
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL NTSC-J 
(II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_DAC2
  DDC reg: 0x68
(II) RADEON(0): Port1:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_LVDS
  DDC reg: 0x1a0
(II) RADEON(0): Port2:
  XRANDR name: S-video
  Connector: S-video
  TV1: INTERNAL_DAC2
  DDC reg: 0x0
(II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
finished output detect: 0
(II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
finished output detect: 1
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 disconnected
(II) RADEON(0): Output LVDS connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output LVDS using initial mode 1280x800
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit d0000000 0 0
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable LVDS
(II) RADEON(0): Dynamic Power Management Disabled
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x08000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1280) to (1280,1282)
(II) RADEON(0): Largest offscreen area available: 1280 x 6909
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(==) RADEON(0): Backing store disabled
(WW) RADEON(0): Direct rendering disabled
(II) RADEON(0): XAA Render acceleration unsupported on Radeon 9500/9700 and newer. Please use EXA instead.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): num quad-pipes is 1
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00642800
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00647800
(II) RADEON(0): Largest offscreen area available: 1280 x 6901
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): Set up overlay video
(II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
disable TVDAC
disable LVDS
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Setting vga for screen 0.
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
(II) RADEON(0): Setting screen physical size to 331 x 207
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
(II) config/hal: Adding input device Power Button
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.2.5
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event2"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
Changing OV0_BASE_ADDR from 0x38000000 to 0x38400000
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable TVDAC
disable LVDS
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable TVDAC
disable LVDS
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable TVDAC
disable LVDS
disable TV
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
disable LVDS
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x3fff3800 0x3fff3800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
set RMX
set LVDS
enable LVDS
disable TVDAC
disable TV
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): EDID for output LVDS
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1280x800"x0.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Output: LVDS, Detected Monitor Type: 2
(II) RADEON(0): EDID data from the display on output: LVDS ----------------------
(II) RADEON(0): Manufacturer: SEC  Model: 3633  Serial#: 0
(II) RADEON(0): Year: 2005  Week: 0
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 33  vert.: 21
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): No DPMS capabilities specified
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
(II) RADEON(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
(II) RADEON(0): h_active: 1280  h_sync: 1296  h_sync_end 1344 h_blank_end 1408 h_border: 0
(II) RADEON(0): v_active: 800  v_sync: 801  v_sync_end 804 v_blanking: 816 v_border: 0
(WW) RADEON(0): Unknown vendor-specific block f
(II) RADEON(0):  SAMSUNG
(II) RADEON(0):  LTN154X3-L06
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):     00ffffffffffff004ca3333600000000
(II) RADEON(0):     000f0103802115780a87f594574f8c27
(II) RADEON(0):     27505400000001010101010101010101
(II) RADEON(0):     010101010101ee1a0080502010301030
(II) RADEON(0):     13004bcf100000190000000f00000000
(II) RADEON(0):     00000000002387026402000000fe0053
(II) RADEON(0):     414d53554e470a2020202020000000fe
(II) RADEON(0):     004c544e31353458332d4c30360a0070
(II) RADEON(0): EDID vendor "SEC", prod id 13875
(II) RADEON(0): Printing probed modes for output LVDS
(II) RADEON(0): Modeline "1280x800"x60.0   68.94  1280 1296 1344 1408  800 801 804 816 -hsync -vsync (49.0 kHz)
(II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
(II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output: S-video, Detected Monitor Type: 0
(II) RADEON(0): EDID for output S-video

```

and the second one,

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux willis-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=968363f6-1269-4d5c-a7e3-c7a3f00134cf ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Sun Nov 29 18:32:53 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Configured Screen Device" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Configured Video Device"
(==) No monitor specified for screen "Configured Screen Device".
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:1:5:0) 1002:5a62:1179:ff04 ATI Technologies Inc RC410 [Radeon Xpress 200M] rev 0, Mem @ 0xd0000000/268435456, 0xc0000000/65536, I/O @ 0x00009000/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.66.10
(II) Loading extension XFree86-DRI
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.66.10
    Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.66.10
(II) ATI Proprietary Linux Driver Release Identifier: 8.66.1                               
(II) ATI Proprietary Linux Driver Build Date: Sep  3 2009 21:35:19
(II) PCS database file /etc/ati/amdpcsdb not found
(II)   Creating PCS database from initial defaults instead
(--) Assigning device section with no busID to primary device
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log

```

and that second log(log 01) repeats itself through log 5. the one thing i notice that is different is that there is no Radion spam flying all over the place..

also the situation is even more annoying, i cant start Blender since this started, nor can i start Tron or any games to show that ubuntu isn't just something for getting confused on.

---

### Post by metalf8801 on 2009-12-11
just in case you didn't already try this 
go to 
System &#8594; Administration &#8594; Hardware Drivers 
and try install your ATI drivers from there 

I hope this helped 
dan

---

### Post by willro on 2009-12-11
> **metalf8801 said:**
> just in case you didn't already try this 
go to 
System &#8594; Administration &#8594; Hardware Drivers 
and try install your ATI drivers from there 

I hope this helped 
dan

No proprietary drivers installed.

---

### Post by metalf8801 on 2009-12-11
I'm sorry I don't really think I can help you 

but in case you haven't look at this documentation 
[https://help.ubuntu.com/9.10/desktop-effects/C/](https://help.ubuntu.com/9.10/desktop-effects/C/) 
it might help

sorry thats the best I can do 


oh have u tried the IRC chat room? 

good luck if you figure out how to fix it please post a how to in the wiki

---

### Post by willro on 2009-12-14
> **metalf8801 said:**
> I'm sorry I don't really think I can help you 

but in case you haven't look at this documentation 
[https://help.ubuntu.com/9.10/desktop-effects/C/](https://help.ubuntu.com/9.10/desktop-effects/C/) 
it might help

sorry thats the best I can do 


oh have u tried the IRC chat room? 

good luck if you figure out how to fix it please post a how to in the wiki

sorry that didn't help, where is the irc chat?

---

### Post by willro on 2009-12-16
well then, i guess i'll bump this again.

---

