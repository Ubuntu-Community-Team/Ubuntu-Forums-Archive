---
title: "Strange Display Adapter Issue"
date: 2015-12-30
forum: Desktop Environments
---

### Post by Zack_Magee on 2015-12-30
Hi,

Been having a strange issue with my desktop since I installed UbuntuGnome.

I have 2 display cards, both are Advanced Micro Devices, Inc. [AMD/ATI] Bonaire XTX [Radeon R7 260X/360]. One has 2 monitors and the other has 3. All 5 monitors are 20" 1600x900. When I first booted up, I was presented with all 5 monitors working flawlessly, however the screens were in reverse order (54321). I went into display settings, and changed it to 12345. Had no problems. The next day, I powered up my computer, monitors 1 and 3 were mostly black with some lines at the bottom, 2, 4 and 5 were fully black. I rebooted, no luck. I had to go into recovery console to clear the X settings. That happened every time I booted. Eventually I decided to put the following in my rc.local:

```
/home/zmagee/.config/monito*xml
```

Now, whenever I boot my computer, it boots to the lines, but if I press the reset button, it boots to my desktop with the screens in the reverse order. 

So, to boot my computer, I need to Press power -> wait for the broken output -> press reset -> log in -> re-order my displays. Obviously this is very much a kludge and not a way to work at all. So I ask you- what should I do?

Here is my Xorg.0.log :

```
[   193.765] _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
[   193.765] _XSERVTransMakeAllCOTSServerListeners: server already running
[   193.765] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[   193.765] X Protocol Version 11, Revision 0
[   193.765] Build Operating System: Linux 3.13.0-68-generic x86_64 Ubuntu
[   193.765] Current Operating System: Linux zack-pc 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64
[   193.765] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-19-generic root=UUID=a0236755-f193-46a1-a6c4-cd469e0a40c0 ro quiet splash vt.handoff=7
[   193.765] Build Date: 12 November 2015  05:33:29PM
[   193.765] xorg-server 2:1.17.2-1ubuntu9.1 (For technical support please see http://www.ubuntu.com/support) 
[   193.765] Current version of pixman: 0.32.6
[   193.765]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   193.765] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   193.765] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 30 10:01:08 2015
[   193.765] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   193.766] (==) No Layout section.  Using the first Screen section.
[   193.766] (==) No screen section available. Using defaults.
[   193.766] (**) |-->Screen "Default Screen Section" (0)
[   193.766] (**) |   |-->Monitor "<default monitor>"
[   193.766] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   193.766] (==) Automatically adding devices
[   193.766] (==) Automatically enabling devices
[   193.766] (==) Automatically adding GPU devices
[   193.766] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   193.766]     Entry deleted from font path.
[   193.766] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   193.766]     Entry deleted from font path.
[   193.766] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   193.766]     Entry deleted from font path.
[   193.766] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    built-ins
[   193.766] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   193.766] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   193.766] (II) Loader magic: 0x56005395ed40
[   193.766] (II) Module ABI versions:
[   193.766]     X.Org ANSI C Emulation: 0.4
[   193.766]     X.Org Video Driver: 19.0
[   193.766]     X.Org XInput driver : 21.0
[   193.766]     X.Org Server Extension : 9.0
[   193.767] (II) xfree86: Adding drm device (/dev/dri/card0)
[   193.767] (II) xfree86: Adding drm device (/dev/dri/card1)
[   193.769] (--) PCI:*(0:1:0:0) 1002:6658:174b:e258 rev 0, Mem @ 0xc0000000/268435456, 0xd0000000/8388608, 0xfea00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[   193.769] (--) PCI: (0:4:0:0) 1002:6658:174b:e258 rev 0, Mem @ 0xa0000000/268435456, 0xb0000000/8388608, 0xfe700000/262144, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[   193.769] (II) LoadModule: "glx"
[   193.769] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   193.770] (II) Module glx: vendor="X.Org Foundation"
[   193.770]     compiled for 1.17.2, module version = 1.0.0
[   193.770]     ABI class: X.Org Server Extension, version 9.0
[   193.770] (==) AIGLX enabled
[   193.770] (==) Matched fglrx as autoconfigured driver 0
[   193.770] (==) Matched ati as autoconfigured driver 1
[   193.770] (==) Matched fglrx as autoconfigured driver 2
[   193.770] (==) Matched ati as autoconfigured driver 3
[   193.770] (==) Matched fglrx as autoconfigured driver 4
[   193.770] (==) Matched ati as autoconfigured driver 5
[   193.770] (==) Matched modesetting as autoconfigured driver 6
[   193.770] (==) Matched fbdev as autoconfigured driver 7
[   193.770] (==) Matched vesa as autoconfigured driver 8
[   193.770] (==) Assigned the driver to the xf86ConfigLayout
[   193.770] (II) LoadModule: "fglrx"
[   193.770] (WW) Warning, couldn't open module fglrx
[   193.770] (II) UnloadModule: "fglrx"
[   193.770] (II) Unloading fglrx
[   193.770] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   193.770] (II) LoadModule: "ati"
[   193.770] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   193.771] (II) Module ati: vendor="X.Org Foundation"
[   193.771]     compiled for 1.17.2, module version = 7.5.99
[   193.771]     Module class: X.Org Video Driver
[   193.771]     ABI class: X.Org Video Driver, version 19.0
[   193.771] (II) LoadModule: "radeon"
[   193.771] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   193.771] (II) Module radeon: vendor="X.Org Foundation"
[   193.771]     compiled for 1.17.2, module version = 7.5.99
[   193.771]     Module class: X.Org Video Driver
[   193.771]     ABI class: X.Org Video Driver, version 19.0
[   193.771] (II) LoadModule: "modesetting"
[   193.771] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   193.771] (II) Module modesetting: vendor="X.Org Foundation"
[   193.771]     compiled for 1.17.2, module version = 1.17.2
[   193.771]     Module class: X.Org Video Driver
[   193.771]     ABI class: X.Org Video Driver, version 19.0
[   193.771] (II) LoadModule: "fbdev"
[   193.771] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   193.771] (II) Module fbdev: vendor="X.Org Foundation"
[   193.771]     compiled for 1.17.1, module version = 0.4.4
[   193.771]     Module class: X.Org Video Driver
[   193.771]     ABI class: X.Org Video Driver, version 19.0
[   193.771] (II) LoadModule: "vesa"
[   193.771] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   193.772] (II) Module vesa: vendor="X.Org Foundation"
[   193.772]     compiled for 1.17.1, module version = 2.3.4
[   193.772]     Module class: X.Org Video Driver
[   193.772]     ABI class: X.Org Video Driver, version 19.0
[   193.772] (==) Matched fglrx as autoconfigured driver 0
[   193.772] (==) Matched ati as autoconfigured driver 1
[   193.772] (==) Matched fglrx as autoconfigured driver 2
[   193.772] (==) Matched ati as autoconfigured driver 3
[   193.772] (==) Matched fglrx as autoconfigured driver 4
[   193.772] (==) Matched ati as autoconfigured driver 5
[   193.772] (==) Matched modesetting as autoconfigured driver 6
[   193.772] (==) Matched fbdev as autoconfigured driver 7
[   193.772] (==) Matched vesa as autoconfigured driver 8
[   193.772] (==) Assigned the driver to the xf86ConfigLayout
[   193.772] (II) LoadModule: "fglrx"
[   193.772] (WW) Warning, couldn't open module fglrx
[   193.772] (II) UnloadModule: "fglrx"
[   193.772] (II) Unloading fglrx
[   193.772] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   193.772] (II) LoadModule: "ati"
[   193.772] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   193.772] (II) Module ati: vendor="X.Org Foundation"
[   193.772]     compiled for 1.17.2, module version = 7.5.99
[   193.772]     Module class: X.Org Video Driver
[   193.772]     ABI class: X.Org Video Driver, version 19.0
[   193.772] (II) LoadModule: "modesetting"
[   193.772] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   193.772] (II) Module modesetting: vendor="X.Org Foundation"
[   193.772]     compiled for 1.17.2, module version = 1.17.2
[   193.772]     Module class: X.Org Video Driver
[   193.772]     ABI class: X.Org Video Driver, version 19.0
[   193.772] (II) UnloadModule: "modesetting"
[   193.772] (II) Unloading modesetting
[   193.772] (II) Failed to load module "modesetting" (already loaded, 0)
[   193.772] (II) LoadModule: "fbdev"
[   193.772] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   193.772] (II) Module fbdev: vendor="X.Org Foundation"
[   193.772]     compiled for 1.17.1, module version = 0.4.4
[   193.772]     Module class: X.Org Video Driver
[   193.772]     ABI class: X.Org Video Driver, version 19.0
[   193.772] (II) UnloadModule: "fbdev"
[   193.773] (II) Unloading fbdev
[   193.773] (II) Failed to load module "fbdev" (already loaded, 0)
[   193.773] (II) LoadModule: "vesa"
[   193.773] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   193.773] (II) Module vesa: vendor="X.Org Foundation"
[   193.773]     compiled for 1.17.1, module version = 2.3.4
[   193.773]     Module class: X.Org Video Driver
[   193.773]     ABI class: X.Org Video Driver, version 19.0
[   193.773] (II) UnloadModule: "vesa"
[   193.773] (II) Unloading vesa
[   193.773] (II) Failed to load module "vesa" (already loaded, 0)
[   193.773] (II) RADEON: Driver for ATI Radeon chipsets:
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
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
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
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
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
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, HAINAN, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS, MULLINS,
    MULLINS, MULLINS, MULLINS, MULLINS, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII
[   193.781] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   193.781] (II) FBDEV: driver for framebuffer: fbdev
[   193.781] (II) VESA: driver for VESA chipsets: vesa
[   193.781] (++) using VT number 2

[   193.781] (II) [KMS] Kernel modesetting enabled.
[   193.781] (II) [KMS] Kernel modesetting enabled.
[   193.781] (WW) Falling back to old probe method for modesetting
[   193.781] (WW) Falling back to old probe method for fbdev
[   193.781] (II) Loading sub module "fbdevhw"
[   193.781] (II) LoadModule: "fbdevhw"
[   193.781] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   193.781] (II) Module fbdevhw: vendor="X.Org Foundation"
[   193.781]     compiled for 1.17.2, module version = 0.0.2
[   193.781]     ABI class: X.Org Video Driver, version 19.0
[   193.781] (WW) Falling back to old probe method for vesa
[   193.781] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   193.781] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   193.781] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   193.781] (==) RADEON(0): Default visual is TrueColor
[   193.781] (==) RADEON(0): RGB weight 888
[   193.781] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   193.781] (--) RADEON(0): Chipset: "BONAIRE" (ChipID = 0x6658)
[   193.781] (II) Loading sub module "dri2"
[   193.781] (II) LoadModule: "dri2"
[   193.781] (II) Module "dri2" already built-in
[   193.782] (II) Loading sub module "glamoregl"
[   193.782] (II) LoadModule: "glamoregl"
[   193.782] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   193.784] (II) Module glamoregl: vendor="X.Org Foundation"
[   193.784]     compiled for 1.17.2, module version = 1.0.0
[   193.784]     ABI class: X.Org ANSI C Emulation, version 0.4
[   193.784] (II) glamor: OpenGL accelerated X.org driver based.
[   193.796] (II) glamor: EGL version 1.4 (DRI2):
[   193.797] (II) RADEON(0): glamor detected, initialising EGL layer.
[   193.797] (II) RADEON(0): KMS Color Tiling: enabled
[   193.797] (II) RADEON(0): KMS Color Tiling 2D: enabled
[   193.797] (II) RADEON(0): KMS Pageflipping: enabled
[   193.797] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[   193.840] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[   193.873] (II) RADEON(0): Output HDMI-0 has no monitor section
[   193.936] (II) RADEON(0): Output DVI-0 has no monitor section
[   193.969] (II) RADEON(0): Output DVI-1 has no monitor section
[   194.012] (II) RADEON(0): EDID for output DisplayPort-0
[   194.012] (II) RADEON(0): Manufacturer: DEL  Model: f03d  Serial#: 826360909
[   194.012] (II) RADEON(0): Year: 2013  Week: 8
[   194.012] (II) RADEON(0): EDID Version: 1.3
[   194.012] (II) RADEON(0): Digital Display Input
[   194.012] (II) RADEON(0): Max Image Size [cm]: horiz.: 44  vert.: 25
[   194.012] (II) RADEON(0): Gamma: 2.20
[   194.012] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[   194.012] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   194.012] (II) RADEON(0): First detailed timing is preferred mode
[   194.012] (II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[   194.012] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[   194.012] (II) RADEON(0): Supported established timings:
[   194.012] (II) RADEON(0): 720x400@70Hz
[   194.012] (II) RADEON(0): 640x480@60Hz
[   194.012] (II) RADEON(0): 640x480@75Hz
[   194.012] (II) RADEON(0): 800x600@60Hz
[   194.012] (II) RADEON(0): 800x600@75Hz
[   194.012] (II) RADEON(0): 1024x768@60Hz
[   194.012] (II) RADEON(0): 1024x768@75Hz
[   194.012] (II) RADEON(0): 1280x1024@75Hz
[   194.012] (II) RADEON(0): Manufacturer's mask: 0
[   194.012] (II) RADEON(0): Supported standard timings:
[   194.012] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   194.012] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   194.012] (II) RADEON(0): #2: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[   194.013] (II) RADEON(0): Supported detailed timing:
[   194.013] (II) RADEON(0): clock: 97.8 MHz   Image Size:  443 x 249 mm
[   194.013] (II) RADEON(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
[   194.013] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
[   194.013] (II) RADEON(0): Serial No: V18WW32K1ADM
[   194.013] (II) RADEON(0): Monitor name: DELL IN2030M
[   194.013] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[   194.013] (II) RADEON(0): EDID (in hex):
[   194.013] (II) RADEON(0):     00ffffffffffff0010ac3df04d444131
[   194.013] (II) RADEON(0):     08170103802c1978eaee95a3544c9926
[   194.013] (II) RADEON(0):     0f5054a54b00714f8180a9c001010101
[   194.013] (II) RADEON(0):     0101010101012f2640a060841a303020
[   194.013] (II) RADEON(0):     3500bbf91000001a000000ff00563138
[   194.013] (II) RADEON(0):     575733324b3141444d0a000000fc0044
[   194.013] (II) RADEON(0):     454c4c20494e323033304d0a000000fd
[   194.013] (II) RADEON(0):     00384c1e5311000a20202020202000c8
[   194.013] (II) RADEON(0): Printing probed modes for output DisplayPort-0
[   194.013] (II) RADEON(0): Modeline "1600x900"x60.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   194.013] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   194.013] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   194.013] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   194.013] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   194.013] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   194.013] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   194.013] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   194.013] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   194.013] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   194.013] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   194.047] (II) RADEON(0): EDID for output HDMI-0
[   194.047] (II) RADEON(0): Manufacturer: ACR  Model: 40c  Serial#: 1360029043
[   194.047] (II) RADEON(0): Year: 2015  Week: 11
[   194.047] (II) RADEON(0): EDID Version: 1.3
[   194.047] (II) RADEON(0): Digital Display Input
[   194.047] (II) RADEON(0): Max Image Size [cm]: horiz.: 43  vert.: 24
[   194.047] (II) RADEON(0): Gamma: 2.20
[   194.047] (II) RADEON(0): DPMS capabilities: Off
[   194.047] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   194.047] (II) RADEON(0): First detailed timing is preferred mode
[   194.047] (II) RADEON(0): redX: 0.641 redY: 0.338   greenX: 0.315 greenY: 0.629
[   194.047] (II) RADEON(0): blueX: 0.159 blueY: 0.059   whiteX: 0.313 whiteY: 0.329
[   194.047] (II) RADEON(0): Supported established timings:
[   194.047] (II) RADEON(0): 720x400@70Hz
[   194.047] (II) RADEON(0): 640x480@60Hz
[   194.047] (II) RADEON(0): 640x480@67Hz
[   194.047] (II) RADEON(0): 640x480@72Hz
[   194.047] (II) RADEON(0): 640x480@75Hz
[   194.047] (II) RADEON(0): 800x600@56Hz
[   194.047] (II) RADEON(0): 800x600@60Hz
[   194.047] (II) RADEON(0): 800x600@72Hz
[   194.047] (II) RADEON(0): 800x600@75Hz
[   194.047] (II) RADEON(0): 832x624@75Hz
[   194.047] (II) RADEON(0): 1024x768@60Hz
[   194.047] (II) RADEON(0): 1024x768@70Hz
[   194.047] (II) RADEON(0): 1024x768@75Hz
[   194.047] (II) RADEON(0): 1152x864@75Hz
[   194.047] (II) RADEON(0): Manufacturer's mask: 0
[   194.047] (II) RADEON(0): Supported standard timings:
[   194.047] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   194.048] (II) RADEON(0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[   194.048] (II) RADEON(0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   194.048] (II) RADEON(0): #3: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[   194.048] (II) RADEON(0): Supported detailed timing:
[   194.048] (II) RADEON(0): clock: 108.0 MHz   Image Size:  432 x 240 mm
[   194.048] (II) RADEON(0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
[   194.048] (II) RADEON(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
[   194.048] (II) RADEON(0): Ranges: V min: 50 V max: 76 Hz, H min: 30 H max: 80 kHz, PixClock max 165 MHz
[   194.048] (II) RADEON(0): Serial No: T1KAA0024203
[   194.048] (II) RADEON(0): Monitor name: Acer K202HQL
[   194.048] (II) RADEON(0): EDID (in hex):
[   194.048] (II) RADEON(0):     00ffffffffffff0004720c0473651051
[   194.048] (II) RADEON(0):     0b190103802b18782a2cc5a45650a128
[   194.048] (II) RADEON(0):     0f5054bfee80714f81c08100a9c00101
[   194.048] (II) RADEON(0):     010101010101302a40c8608464301850
[   194.048] (II) RADEON(0):     1300b0f01000001e000000fd00324c1e
[   194.048] (II) RADEON(0):     5010000a202020202020000000ff0054
[   194.048] (II) RADEON(0):     314b4141303032343230330a000000fc
[   194.048] (II) RADEON(0):     0041636572204b32303248514c0a00e2
[   194.048] (II) RADEON(0): Printing probed modes for output HDMI-0
[   194.048] (II) RADEON(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   194.048] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   194.048] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   194.048] (II) RADEON(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   194.048] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   194.048] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   194.048] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   194.048] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   194.048] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   194.048] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   194.048] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   194.048] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   194.048] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   194.048] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[   194.048] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   194.049] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   194.049] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   194.112] (II) RADEON(0): EDID for output DVI-0
[   194.145] (II) RADEON(0): EDID for output DVI-1
[   194.145] (II) RADEON(0): Manufacturer: DEL  Model: f03d  Serial#: 809908045
[   194.145] (II) RADEON(0): Year: 2013  Week: 18
[   194.145] (II) RADEON(0): EDID Version: 1.3
[   194.145] (II) RADEON(0): Digital Display Input
[   194.145] (II) RADEON(0): Max Image Size [cm]: horiz.: 44  vert.: 25
[   194.145] (II) RADEON(0): Gamma: 2.20
[   194.145] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[   194.145] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   194.145] (II) RADEON(0): First detailed timing is preferred mode
[   194.145] (II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[   194.145] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[   194.145] (II) RADEON(0): Supported established timings:
[   194.145] (II) RADEON(0): 720x400@70Hz
[   194.145] (II) RADEON(0): 640x480@60Hz
[   194.145] (II) RADEON(0): 640x480@75Hz
[   194.145] (II) RADEON(0): 800x600@60Hz
[   194.145] (II) RADEON(0): 800x600@75Hz
[   194.145] (II) RADEON(0): 1024x768@60Hz
[   194.145] (II) RADEON(0): 1024x768@75Hz
[   194.145] (II) RADEON(0): 1280x1024@75Hz
[   194.145] (II) RADEON(0): Manufacturer's mask: 0
[   194.145] (II) RADEON(0): Supported standard timings:
[   194.145] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   194.145] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   194.145] (II) RADEON(0): #2: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[   194.145] (II) RADEON(0): Supported detailed timing:
[   194.145] (II) RADEON(0): clock: 97.8 MHz   Image Size:  443 x 249 mm
[   194.145] (II) RADEON(0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
[   194.145] (II) RADEON(0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
[   194.145] (II) RADEON(0): Serial No: V18WW3530F7M
[   194.145] (II) RADEON(0): Monitor name: DELL IN2030M
[   194.145] (II) RADEON(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 83 kHz, PixClock max 175 MHz
[   194.145] (II) RADEON(0): EDID (in hex):
[   194.145] (II) RADEON(0):     00ffffffffffff0010ac3df04d374630
[   194.145] (II) RADEON(0):     12170103802c1978eaee95a3544c9926
[   194.145] (II) RADEON(0):     0f5054a54b00714f8180a9c001010101
[   194.145] (II) RADEON(0):     0101010101012f2640a060841a303020
[   194.145] (II) RADEON(0):     3500bbf91000001a000000ff00563138
[   194.145] (II) RADEON(0):     57573335333046374d0a000000fc0044
[   194.145] (II) RADEON(0):     454c4c20494e323033304d0a000000fd
[   194.145] (II) RADEON(0):     00384c1e5311000a20202020202000e5
[   194.145] (II) RADEON(0): Printing probed modes for output DVI-1
[   194.145] (II) RADEON(0): Modeline "1600x900"x60.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   194.145] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   194.145] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   194.145] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   194.145] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   194.145] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   194.145] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   194.145] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   194.145] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   194.145] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   194.145] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   194.145] (II) RADEON(0): Output DisplayPort-0 connected
[   194.145] (II) RADEON(0): Output HDMI-0 connected
[   194.145] (II) RADEON(0): Output DVI-0 disconnected
[   194.145] (II) RADEON(0): Output DVI-1 connected
[   194.145] (II) RADEON(0): Using exact sizes for initial modes
[   194.145] (II) RADEON(0): Output DisplayPort-0 using initial mode 1600x900
[   194.145] (II) RADEON(0): Output HDMI-0 using initial mode 1600x900
[   194.145] (II) RADEON(0): Output DVI-1 using initial mode 1600x900
[   194.145] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   194.145] (II) RADEON(0): mem size init: gart size :7f05f000 vram size: s:80000000 visible:7b8bc000
[   194.145] (==) RADEON(0): DPI set to (96, 96)
[   194.145] (II) Loading sub module "fb"
[   194.145] (II) LoadModule: "fb"
[   194.145] (II) Loading /usr/lib/xorg/modules/libfb.so
[   194.145] (II) Module fb: vendor="X.Org Foundation"
[   194.145]     compiled for 1.17.2, module version = 1.0.0
[   194.145]     ABI class: X.Org ANSI C Emulation, version 0.4
[   194.145] (II) Loading sub module "ramdac"
[   194.145] (II) LoadModule: "ramdac"
[   194.145] (II) Module "ramdac" already built-in
[   194.145] (==) RADEON(G0): Depth 24, (--) framebuffer bpp 32
[   194.145] (II) RADEON(G0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   194.145] (==) RADEON(G0): Default visual is TrueColor
[   194.145] (==) RADEON(G0): RGB weight 888
[   194.145] (II) RADEON(G0): Using 8 bits per RGB (8 bit DAC)
[   194.145] (--) RADEON(G0): Chipset: "BONAIRE" (ChipID = 0x6658)
[   194.146] (II) Loading sub module "dri2"
[   194.146] (II) LoadModule: "dri2"
[   194.146] (II) Module "dri2" already built-in
[   194.146] (II) Loading sub module "glamoregl"
[   194.146] (II) LoadModule: "glamoregl"
[   194.146] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   194.146] (II) Module glamoregl: vendor="X.Org Foundation"
[   194.146]     compiled for 1.17.2, module version = 1.0.0
[   194.146]     ABI class: X.Org ANSI C Emulation, version 0.4
[   194.146] (II) glamor: OpenGL accelerated X.org driver based.
[   194.147] (II) glamor: EGL version 1.4 (DRI2):
[   194.148] (II) RADEON(G0): glamor detected, initialising EGL layer.
[   194.148] (II) RADEON(G0): KMS Color Tiling: enabled
[   194.148] (II) RADEON(G0): KMS Color Tiling 2D: enabled
[   194.148] (II) RADEON(G0): KMS Pageflipping: enabled
[   194.148] (II) RADEON(G0): SwapBuffers wait for vsync: enabled
[   194.192] (II) RADEON(G0): Output DisplayPort-1-1 has no monitor section
[   194.193] (II) RADEON(G0): Output HDMI-1-1 has no monitor section
[   194.256] (II) RADEON(G0): Output DVI-1-1 has no monitor section
[   194.289] (II) RADEON(G0): Output DVI-1-1 has no monitor section
[   194.332] (II) RADEON(G0): EDID for output DisplayPort-1-1
[   194.332] (II) RADEON(G0): Manufacturer: ACR  Model: 103  Serial#: 38805072
[   194.332] (II) RADEON(G0): Year: 2010  Week: 25
[   194.332] (II) RADEON(G0): EDID Version: 1.3
[   194.332] (II) RADEON(G0): Digital Display Input
[   194.332] (II) RADEON(G0): Max Image Size [cm]: horiz.: 44  vert.: 25
[   194.332] (II) RADEON(G0): Gamma: 2.20
[   194.332] (II) RADEON(G0): DPMS capabilities: StandBy Suspend Off
[   194.332] (II) RADEON(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   194.332] (II) RADEON(G0): First detailed timing is preferred mode
[   194.332] (II) RADEON(G0): redX: 0.650 redY: 0.335   greenX: 0.295 greenY: 0.605
[   194.332] (II) RADEON(G0): blueX: 0.145 blueY: 0.075   whiteX: 0.313 whiteY: 0.329
[   194.332] (II) RADEON(G0): Supported established timings:
[   194.332] (II) RADEON(G0): 720x400@70Hz
[   194.332] (II) RADEON(G0): 640x480@60Hz
[   194.332] (II) RADEON(G0): 640x480@67Hz
[   194.332] (II) RADEON(G0): 640x480@72Hz
[   194.332] (II) RADEON(G0): 640x480@75Hz
[   194.332] (II) RADEON(G0): 800x600@56Hz
[   194.332] (II) RADEON(G0): 800x600@60Hz
[   194.332] (II) RADEON(G0): 800x600@72Hz
[   194.332] (II) RADEON(G0): 800x600@75Hz
[   194.332] (II) RADEON(G0): 832x624@75Hz
[   194.332] (II) RADEON(G0): 1024x768@60Hz
[   194.332] (II) RADEON(G0): 1024x768@70Hz
[   194.332] (II) RADEON(G0): 1024x768@75Hz
[   194.332] (II) RADEON(G0): 1152x864@75Hz
[   194.332] (II) RADEON(G0): Manufacturer's mask: 0
[   194.332] (II) RADEON(G0): Supported standard timings:
[   194.332] (II) RADEON(G0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   194.332] (II) RADEON(G0): #1: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[   194.332] (II) RADEON(G0): #2: hsize: 1280  vsize 800  refresh: 60  vid: 129
[   194.332] (II) RADEON(G0): Supported detailed timing:
[   194.332] (II) RADEON(G0): clock: 97.8 MHz   Image Size:  443 x 249 mm
[   194.332] (II) RADEON(G0): h_active: 1600  h_sync: 1648  h_sync_end 1680 h_blank_end 1760 h_border: 0
[   194.332] (II) RADEON(G0): v_active: 900  v_sync: 903  v_sync_end 908 v_blanking: 926 v_border: 0
[   194.332] (II) RADEON(G0): Ranges: V min: 56 V max: 75 Hz, H min: 31 H max: 83 kHz, PixClock max 155 MHz
[   194.332] (II) RADEON(G0): Monitor name: Acer H203H
[   194.332] (II) RADEON(G0): Serial No: LJ30W0064337
[   194.332] (II) RADEON(G0): EDID (in hex):
[   194.332] (II) RADEON(G0):     00ffffffffffff0004720301501e5002
[   194.332] (II) RADEON(G0):     19140103802c1978eab815a6554b9b25
[   194.332] (II) RADEON(G0):     135054bfee80714f81c0810001010101
[   194.332] (II) RADEON(G0):     0101010101012f2640a060841a303020
[   194.332] (II) RADEON(G0):     3500bbf91000001a000000fd00384b1f
[   194.332] (II) RADEON(G0):     530f000a202020202020000000fc0041
[   194.332] (II) RADEON(G0):     6365722048323033480a2020000000ff
[   194.332] (II) RADEON(G0):     004c4a333057303036343333370a00da
[   194.332] (II) RADEON(G0): Printing probed modes for output DisplayPort-1-1
[   194.332] (II) RADEON(G0): Modeline "1600x900"x60.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   194.332] (II) RADEON(G0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   194.332] (II) RADEON(G0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   194.332] (II) RADEON(G0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   194.332] (II) RADEON(G0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   194.332] (II) RADEON(G0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   194.332] (II) RADEON(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   194.332] (II) RADEON(G0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   194.332] (II) RADEON(G0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   194.332] (II) RADEON(G0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   194.332] (II) RADEON(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   194.332] (II) RADEON(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   194.332] (II) RADEON(G0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   194.332] (II) RADEON(G0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[   194.332] (II) RADEON(G0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   194.332] (II) RADEON(G0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   194.332] (II) RADEON(G0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   194.333] (II) RADEON(G0): EDID for output HDMI-1-1
[   194.396] (II) RADEON(G0): EDID for output DVI-1-1
[   194.429] (II) RADEON(G0): EDID for output DVI-1-1
[   194.429] (II) RADEON(G0): Manufacturer: GSM  Model: 4eca  Serial#: 100918
[   194.429] (II) RADEON(G0): Year: 2012  Week: 1
[   194.429] (II) RADEON(G0): EDID Version: 1.3
[   194.429] (II) RADEON(G0): Digital Display Input
[   194.429] (II) RADEON(G0): Max Image Size [cm]: horiz.: 45  vert.: 25
[   194.429] (II) RADEON(G0): Gamma: 2.20
[   194.429] (II) RADEON(G0): DPMS capabilities: StandBy Suspend Off
[   194.429] (II) RADEON(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   194.429] (II) RADEON(G0): First detailed timing is preferred mode
[   194.429] (II) RADEON(G0): redX: 0.646 redY: 0.334   greenX: 0.302 greenY: 0.615
[   194.429] (II) RADEON(G0): blueX: 0.146 blueY: 0.066   whiteX: 0.313 whiteY: 0.328
[   194.429] (II) RADEON(G0): Supported established timings:
[   194.429] (II) RADEON(G0): 720x400@70Hz
[   194.429] (II) RADEON(G0): 640x480@60Hz
[   194.429] (II) RADEON(G0): 640x480@75Hz
[   194.429] (II) RADEON(G0): 800x600@56Hz
[   194.429] (II) RADEON(G0): 800x600@60Hz
[   194.429] (II) RADEON(G0): 800x600@75Hz
[   194.429] (II) RADEON(G0): 832x624@75Hz
[   194.429] (II) RADEON(G0): 1024x768@60Hz
[   194.429] (II) RADEON(G0): 1024x768@75Hz
[   194.429] (II) RADEON(G0): 1152x864@75Hz
[   194.429] (II) RADEON(G0): Manufacturer's mask: 0
[   194.429] (II) RADEON(G0): Supported standard timings:
[   194.429] (II) RADEON(G0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   194.429] (II) RADEON(G0): #1: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[   194.429] (II) RADEON(G0): Supported detailed timing:
[   194.429] (II) RADEON(G0): clock: 108.0 MHz   Image Size:  443 x 249 mm
[   194.429] (II) RADEON(G0): h_active: 1600  h_sync: 1624  h_sync_end 1704 h_blank_end 1800 h_border: 0
[   194.429] (II) RADEON(G0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 1000 v_border: 0
[   194.429] (II) RADEON(G0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 135 MHz
[   194.429] (II) RADEON(G0): Monitor name: E2041
[   194.429] (II) RADEON(G0): Serial No: 201NDRF2Y918
[   194.429] (II) RADEON(G0): EDID (in hex):
[   194.429] (II) RADEON(G0):     00ffffffffffff001e6dca4e368a0100
[   194.429] (II) RADEON(G0):     01160103802d1978eaa684a5554d9d25
[   194.429] (II) RADEON(G0):     115054a76a80714fa9c0010101010101
[   194.429] (II) RADEON(G0):     010101010101302a40c8608464301850
[   194.429] (II) RADEON(G0):     1300bbf91000001e000000fd00384b1e
[   194.429] (II) RADEON(G0):     530d000a202020202020000000fc0045
[   194.429] (II) RADEON(G0):     323034310a20202020202020000000ff
[   194.429] (II) RADEON(G0):     003230314e44524632593931380a00cd
[   194.429] (II) RADEON(G0): Printing probed modes for output DVI-1-1
[   194.429] (II) RADEON(G0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   194.429] (II) RADEON(G0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   194.429] (II) RADEON(G0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   194.429] (II) RADEON(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   194.429] (II) RADEON(G0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   194.429] (II) RADEON(G0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   194.429] (II) RADEON(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   194.429] (II) RADEON(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   194.429] (II) RADEON(G0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   194.429] (II) RADEON(G0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   194.429] (II) RADEON(G0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   194.429] (II) RADEON(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   194.429] (II) RADEON(G0): mem size init: gart size :7fb69000 vram size: s:80000000 visible:7e79c000
[   194.429] (==) RADEON(G0): DPI set to (96, 96)
[   194.429] (II) Loading sub module "fb"
[   194.429] (II) LoadModule: "fb"
[   194.429] (II) Loading /usr/lib/xorg/modules/libfb.so
[   194.429] (II) Module fb: vendor="X.Org Foundation"
[   194.429]     compiled for 1.17.2, module version = 1.0.0
[   194.429]     ABI class: X.Org ANSI C Emulation, version 0.4
[   194.429] (II) Loading sub module "ramdac"
[   194.429] (II) LoadModule: "ramdac"
[   194.429] (II) Module "ramdac" already built-in
[   194.429] (II) UnloadModule: "modesetting"
[   194.429] (II) Unloading modesetting
[   194.429] (II) UnloadModule: "fbdev"
[   194.429] (II) Unloading fbdev
[   194.429] (II) UnloadSubModule: "fbdevhw"
[   194.429] (II) Unloading fbdevhw
[   194.429] (II) UnloadModule: "vesa"
[   194.429] (II) Unloading vesa
[   194.429] (--) Depth 24 pixmap format is 32 bpp
[   194.430] (II) RADEON(G0): [DRI2] Setup complete
[   194.430] (II) RADEON(G0): [DRI2]   DRI driver: radeonsi
[   194.430] (II) RADEON(G0): [DRI2]   VDPAU driver: radeonsi
[   194.430] (II) RADEON(G0): Front buffer size: 3072K
[   194.430] (II) RADEON(G0): VRAM usage limit set to 1862107K
[   194.430] (==) RADEON(G0): DRI3 disabled
[   194.430] (==) RADEON(G0): Backing store enabled
[   194.430] (II) RADEON(G0): Direct rendering enabled
[   194.470] (II) RADEON(G0): Use GLAMOR acceleration.
[   194.470] (II) RADEON(G0): Acceleration enabled
[   194.470] (==) RADEON(G0): DPMS enabled
[   194.470] (==) RADEON(G0): Silken mouse enabled
[   194.470] (II) RADEON(G0): Set up textured video (glamor)
[   194.470] (II) RADEON(G0): [XvMC] Associated with GLAMOR Textured Video.
[   194.470] (EE) RADEON(G0): [XvMC] Failed to initialize extension.
[   194.470] (II) RADEON(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   194.470] (II) RADEON(0): [DRI2] Setup complete
[   194.470] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[   194.470] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[   194.470] (II) RADEON(0): Front buffer size: 6000K
[   194.470] (II) RADEON(0): VRAM usage limit set to 1816272K
[   194.470] (==) RADEON(0): DRI3 disabled
[   194.470] (==) RADEON(0): Backing store enabled
[   194.470] (II) RADEON(0): Direct rendering enabled
[   194.506] (II) RADEON(0): Use GLAMOR acceleration.
[   194.506] (II) RADEON(0): Acceleration enabled
[   194.506] (==) RADEON(0): DPMS enabled
[   194.506] (==) RADEON(0): Silken mouse enabled
[   194.506] (II) RADEON(0): Set up textured video (glamor)
[   194.507] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[   194.507] (II) RADEON(0): [XvMC] Extension initialized.
[   194.507] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   194.507] (--) RandR disabled
[   194.510] (II) SELinux: Disabled on system
[   194.511] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   194.512] (II) AIGLX: enabled GLX_ARB_create_context
[   194.512] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   194.512] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[   194.512] (II) AIGLX: enabled GLX_INTEL_swap_event
[   194.512] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   194.512] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[   194.512] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[   194.512] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   194.512] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[   194.513] (II) AIGLX: Loaded and initialized radeonsi
[   194.513] (II) GLX: Initialized DRI2 GL provider for screen 0
[   194.524] (II) RADEON(0): Setting screen physical size to 423 x 238
[   194.538] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   194.563] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   194.563] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   194.563] (II) LoadModule: "evdev"
[   194.563] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   194.563] (II) Module evdev: vendor="X.Org Foundation"
[   194.563]     compiled for 1.17.1, module version = 2.9.2
[   194.564]     Module class: X.Org XInput Driver
[   194.564]     ABI class: X.Org XInput driver, version 21.0
[   194.564] (II) Using input driver 'evdev' for 'Power Button'
[   194.564] (**) Power Button: always reports core events
[   194.564] (**) evdev: Power Button: Device: "/dev/input/event1"
[   194.564] (--) evdev: Power Button: Vendor 0 Product 0x1
[   194.564] (--) evdev: Power Button: Found keys
[   194.564] (II) evdev: Power Button: Configuring as keyboard
[   194.564] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   194.564] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   194.564] (**) Option "xkb_rules" "evdev"
[   194.564] (**) Option "xkb_model" "pc105"
[   194.564] (**) Option "xkb_layout" "us"
[   194.564] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   194.564] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   194.564] (II) Using input driver 'evdev' for 'Power Button'
[   194.564] (**) Power Button: always reports core events
[   194.564] (**) evdev: Power Button: Device: "/dev/input/event0"
[   194.564] (--) evdev: Power Button: Vendor 0 Product 0x1
[   194.564] (--) evdev: Power Button: Found keys
[   194.564] (II) evdev: Power Button: Configuring as keyboard
[   194.564] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   194.564] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   194.564] (**) Option "xkb_rules" "evdev"
[   194.564] (**) Option "xkb_model" "pc105"
[   194.564] (**) Option "xkb_layout" "us"
[   194.565] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event11)
[   194.565] (II) No input driver specified, ignoring this device.
[   194.565] (II) This device may have been added with another device file.
[   194.565] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event12)
[   194.565] (II) No input driver specified, ignoring this device.
[   194.565] (II) This device may have been added with another device file.
[   194.565] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event13)
[   194.565] (II) No input driver specified, ignoring this device.
[   194.565] (II) This device may have been added with another device file.
[   194.565] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event14)
[   194.565] (II) No input driver specified, ignoring this device.
[   194.565] (II) This device may have been added with another device file.
[   194.566] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event15)
[   194.566] (II) No input driver specified, ignoring this device.
[   194.566] (II) This device may have been added with another device file.
[   194.566] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event10)
[   194.566] (II) No input driver specified, ignoring this device.
[   194.566] (II) This device may have been added with another device file.
[   194.566] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event6)
[   194.566] (II) No input driver specified, ignoring this device.
[   194.566] (II) This device may have been added with another device file.
[   194.566] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event7)
[   194.566] (II) No input driver specified, ignoring this device.
[   194.566] (II) This device may have been added with another device file.
[   194.567] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event8)
[   194.567] (II) No input driver specified, ignoring this device.
[   194.567] (II) This device may have been added with another device file.
[   194.567] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event9)
[   194.567] (II) No input driver specified, ignoring this device.
[   194.567] (II) This device may have been added with another device file.
[   194.567] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event4)
[   194.567] (II) No input driver specified, ignoring this device.
[   194.567] (II) This device may have been added with another device file.
[   194.567] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event5)
[   194.567] (II) No input driver specified, ignoring this device.
[   194.567] (II) This device may have been added with another device file.
[   194.568] (II) config/udev: Adding input device Logitech M570 (/dev/input/event2)
[   194.568] (**) Logitech M570: Applying InputClass "evdev pointer catchall"
[   194.568] (II) Using input driver 'evdev' for 'Logitech M570'
[   194.568] (**) Logitech M570: always reports core events
[   194.568] (**) evdev: Logitech M570: Device: "/dev/input/event2"
[   194.568] (--) evdev: Logitech M570: Vendor 0x46d Product 0x1028
[   194.568] (--) evdev: Logitech M570: Found 20 mouse buttons
[   194.568] (--) evdev: Logitech M570: Found scroll wheel(s)
[   194.568] (--) evdev: Logitech M570: Found relative axes
[   194.568] (--) evdev: Logitech M570: Found x and y relative axes
[   194.568] (II) evdev: Logitech M570: Configuring as mouse
[   194.568] (II) evdev: Logitech M570: Adding scrollwheel support
[   194.568] (**) evdev: Logitech M570: YAxisMapping: buttons 4 and 5
[   194.568] (**) evdev: Logitech M570: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   194.568] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:1028.0004/input/input5/event2"
[   194.568] (II) XINPUT: Adding extended input device "Logitech M570" (type: MOUSE, id 8)
[   194.568] (II) evdev: Logitech M570: initialized for relative axes.
[   194.568] (**) Logitech M570: (accel) keeping acceleration scheme 1
[   194.568] (**) Logitech M570: (accel) acceleration profile 0
[   194.568] (**) Logitech M570: (accel) acceleration factor: 2.000
[   194.568] (**) Logitech M570: (accel) acceleration threshold: 4
[   194.568] (II) config/udev: Adding input device Logitech M570 (/dev/input/mouse0)
[   194.568] (II) No input driver specified, ignoring this device.
[   194.568] (II) This device may have been added with another device file.
[   194.569] (II) config/udev: Adding input device Logitech MK700 (/dev/input/event3)
[   194.569] (**) Logitech MK700: Applying InputClass "evdev keyboard catchall"
[   194.569] (II) Using input driver 'evdev' for 'Logitech MK700'
[   194.569] (**) Logitech MK700: always reports core events
[   194.569] (**) evdev: Logitech MK700: Device: "/dev/input/event3"
[   194.569] (--) evdev: Logitech MK700: Vendor 0x46d Product 0x2008
[   194.569] (--) evdev: Logitech MK700: Found 1 mouse buttons
[   194.569] (--) evdev: Logitech MK700: Found scroll wheel(s)
[   194.569] (--) evdev: Logitech MK700: Found relative axes
[   194.569] (II) evdev: Logitech MK700: Forcing relative x/y axes to exist.
[   194.569] (--) evdev: Logitech MK700: Found absolute axes
[   194.569] (II) evdev: Logitech MK700: Forcing absolute x/y axes to exist.
[   194.569] (--) evdev: Logitech MK700: Found keys
[   194.569] (II) evdev: Logitech MK700: Configuring as mouse
[   194.569] (II) evdev: Logitech MK700: Configuring as keyboard
[   194.569] (II) evdev: Logitech MK700: Adding scrollwheel support
[   194.569] (**) evdev: Logitech MK700: YAxisMapping: buttons 4 and 5
[   194.569] (**) evdev: Logitech MK700: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   194.569] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/0003:046D:2008.0005/input/input6/event3"
[   194.569] (II) XINPUT: Adding extended input device "Logitech MK700" (type: KEYBOARD, id 9)
[   194.569] (**) Option "xkb_rules" "evdev"
[   194.569] (**) Option "xkb_model" "pc105"
[   194.569] (**) Option "xkb_layout" "us"
[   194.569] (II) evdev: Logitech MK700: initialized for relative axes.
[   194.569] (WW) evdev: Logitech MK700: ignoring absolute axes.
[   194.569] (**) Logitech MK700: (accel) keeping acceleration scheme 1
[   194.569] (**) Logitech MK700: (accel) acceleration profile 0
[   194.569] (**) Logitech MK700: (accel) acceleration factor: 2.000
[   194.569] (**) Logitech MK700: (accel) acceleration threshold: 4
[   194.569] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event16)
[   194.569] (II) No input driver specified, ignoring this device.
[   194.569] (II) This device may have been added with another device file.
[   194.569] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event17)
[   194.569] (II) No input driver specified, ignoring this device.
[   194.569] (II) This device may have been added with another device file.
[   194.570] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event18)
[   194.570] (II) No input driver specified, ignoring this device.
[   194.570] (II) This device may have been added with another device file.
[   194.570] (II) config/udev: Adding input device HDA ATI SB Line Out Front (/dev/input/event19)
[   194.570] (II) No input driver specified, ignoring this device.
[   194.570] (II) This device may have been added with another device file.
[   194.570] (II) config/udev: Adding input device HDA ATI SB Line Out Surround (/dev/input/event20)
[   194.570] (II) No input driver specified, ignoring this device.
[   194.570] (II) This device may have been added with another device file.
[   194.570] (II) config/udev: Adding input device HDA ATI SB Line Out CLFE (/dev/input/event21)
[   194.570] (II) No input driver specified, ignoring this device.
[   194.570] (II) This device may have been added with another device file.
[   194.570] (II) config/udev: Adding input device HDA ATI SB Line Out Side (/dev/input/event22)
[   194.570] (II) No input driver specified, ignoring this device.
[   194.570] (II) This device may have been added with another device file.
[   194.571] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event23)
[   194.571] (II) No input driver specified, ignoring this device.
[   194.571] (II) This device may have been added with another device file.
[   195.853] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   195.853] (II) RADEON(0): Using EDID range info for horizontal sync
[   195.853] (II) RADEON(0): Using EDID range info for vertical refresh
[   195.853] (II) RADEON(0): Printing DDC gathered Modelines:
[   195.853] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   195.853] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   195.853] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   195.853] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   195.853] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   195.853] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   195.853] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   195.853] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   195.853] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   195.853] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   195.853] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   195.853] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   196.025] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   196.025] (II) RADEON(0): Using hsync ranges from config file
[   196.025] (II) RADEON(0): Using vrefresh ranges from config file
[   196.025] (II) RADEON(0): Printing DDC gathered Modelines:
[   196.025] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   196.025] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   196.025] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   196.025] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   196.025] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   196.025] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   196.025] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   196.025] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   196.025] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   196.025] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   196.025] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   196.025] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   196.068] (II) RADEON(G0): EDID vendor "ACR", prod id 259
[   196.068] (II) RADEON(G0): Using hsync ranges from config file
[   196.068] (II) RADEON(G0): Using vrefresh ranges from config file
[   196.068] (II) RADEON(G0): Printing DDC gathered Modelines:
[   196.068] (II) RADEON(G0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   196.068] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   196.068] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   196.068] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   196.068] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   196.068] (II) RADEON(G0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   196.068] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   196.068] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   196.068] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   196.068] (II) RADEON(G0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   196.068] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   196.068] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   196.068] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   196.068] (II) RADEON(G0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   196.068] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   196.068] (II) RADEON(G0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   196.068] (II) RADEON(G0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   196.224] (II) RADEON(0): Allocate new frame buffer 8000x928 stride 8000
[   196.229] (II) RADEON(0): VRAM usage limit set to 1794672K
[   196.363] (II) RADEON(G0): Allocate new frame buffer 1600x928 stride 1600
[   196.365] (II) RADEON(G0): VRAM usage limit set to 1859472K
[   196.397] (II) RADEON(G0): Allocate new frame buffer 3200x928 stride 3200
[   196.399] (II) RADEON(G0): VRAM usage limit set to 1854072K
[   196.869] (II) XKB: generating xkmfile /tmp/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[   197.393] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   197.393] (II) RADEON(0): Using hsync ranges from config file
[   197.393] (II) RADEON(0): Using vrefresh ranges from config file
[   197.393] (II) RADEON(0): Printing DDC gathered Modelines:
[   197.393] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   197.393] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   197.393] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   197.393] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   197.393] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   197.393] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   197.393] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   197.393] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   197.393] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   197.393] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   197.393] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   197.393] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   197.565] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   197.565] (II) RADEON(0): Using hsync ranges from config file
[   197.565] (II) RADEON(0): Using vrefresh ranges from config file
[   197.565] (II) RADEON(0): Printing DDC gathered Modelines:
[   197.565] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   197.565] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   197.565] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   197.565] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   197.565] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   197.565] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   197.565] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   197.565] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   197.565] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   197.565] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   197.565] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   197.565] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   197.604] (II) RADEON(G0): EDID vendor "ACR", prod id 259
[   197.604] (II) RADEON(G0): Using hsync ranges from config file
[   197.604] (II) RADEON(G0): Using vrefresh ranges from config file
[   197.604] (II) RADEON(G0): Printing DDC gathered Modelines:
[   197.604] (II) RADEON(G0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   197.604] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   197.604] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   197.604] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   197.604] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   197.604] (II) RADEON(G0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   197.604] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   197.604] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   197.604] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   197.604] (II) RADEON(G0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   197.604] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   197.604] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   197.604] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   197.604] (II) RADEON(G0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   197.604] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   197.604] (II) RADEON(G0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[   197.604] (II) RADEON(G0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)
[   198.014] (II) XKB: generating xkmfile /tmp/server-277A7C3E496C7FF8072160FA921DAD853791F8E7.xkm
[   287.725] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   287.725] (II) RADEON(0): Using hsync ranges from config file
[   287.725] (II) RADEON(0): Using vrefresh ranges from config file
[   287.725] (II) RADEON(0): Printing DDC gathered Modelines:
[   287.725] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   287.725] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   287.725] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   287.725] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   287.725] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   287.725] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   287.725] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   287.725] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   287.725] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   287.725] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   287.725] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   287.725] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   287.897] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   287.897] (II) RADEON(0): Using hsync ranges from config file
[   287.897] (II) RADEON(0): Using vrefresh ranges from config file
[   287.897] (II) RADEON(0): Printing DDC gathered Modelines:
[   287.897] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   287.897] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   287.897] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   287.897] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   287.897] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   287.897] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   287.897] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   287.897] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   287.897] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   287.897] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   287.897] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   287.897] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   288.037] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   288.037] (II) RADEON(G0): Using hsync ranges from config file
[   288.037] (II) RADEON(G0): Using vrefresh ranges from config file
[   288.037] (II) RADEON(G0): Printing DDC gathered Modelines:
[   288.037] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   288.037] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   288.037] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   288.037] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   288.037] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   288.037] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   288.037] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   288.037] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   288.037] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   288.037] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   288.037] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   288.037] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   301.066] (II) RADEON(0): Allocate new frame buffer 8000x928 stride 8000
[   301.067] (II) RADEON(0): VRAM usage limit set to 1794672K
[   301.070] (II) RADEON(0): Allocate new frame buffer 6400x928 stride 6400
[   301.072] (II) RADEON(0): VRAM usage limit set to 1800072K
[   301.130] (II) RADEON(0): Allocate new frame buffer 8000x928 stride 8000
[   301.185] (II) RADEON(0): VRAM usage limit set to 1794672K
[   301.413] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   301.413] (II) RADEON(0): Using hsync ranges from config file
[   301.413] (II) RADEON(0): Using vrefresh ranges from config file
[   301.413] (II) RADEON(0): Printing DDC gathered Modelines:
[   301.413] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   301.413] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   301.413] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   301.413] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   301.413] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   301.413] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   301.413] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   301.413] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   301.413] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   301.413] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   301.413] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   301.413] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   301.585] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   301.585] (II) RADEON(0): Using hsync ranges from config file
[   301.585] (II) RADEON(0): Using vrefresh ranges from config file
[   301.585] (II) RADEON(0): Printing DDC gathered Modelines:
[   301.585] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   301.585] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   301.585] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   301.585] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   301.585] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   301.585] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   301.585] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   301.585] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   301.585] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   301.585] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   301.585] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   301.585] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   301.726] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   301.726] (II) RADEON(G0): Using hsync ranges from config file
[   301.726] (II) RADEON(G0): Using vrefresh ranges from config file
[   301.726] (II) RADEON(G0): Printing DDC gathered Modelines:
[   301.726] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   301.726] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   301.726] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   301.726] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   301.726] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   301.726] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   301.726] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   301.726] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   301.726] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   301.726] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   301.726] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   301.726] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   302.409] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   302.409] (II) RADEON(0): Using hsync ranges from config file
[   302.409] (II) RADEON(0): Using vrefresh ranges from config file
[   302.409] (II) RADEON(0): Printing DDC gathered Modelines:
[   302.409] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   302.409] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   302.409] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   302.409] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   302.409] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   302.409] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   302.409] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   302.409] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   302.409] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   302.409] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   302.409] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   302.409] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   302.581] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   302.581] (II) RADEON(0): Using hsync ranges from config file
[   302.581] (II) RADEON(0): Using vrefresh ranges from config file
[   302.581] (II) RADEON(0): Printing DDC gathered Modelines:
[   302.581] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   302.581] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   302.581] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   302.581] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   302.581] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   302.581] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   302.581] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   302.581] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   302.581] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   302.581] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   302.581] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   302.581] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   302.717] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   302.717] (II) RADEON(G0): Using hsync ranges from config file
[   302.717] (II) RADEON(G0): Using vrefresh ranges from config file
[   302.717] (II) RADEON(G0): Printing DDC gathered Modelines:
[   302.717] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   302.717] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   302.717] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   302.717] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   302.717] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   302.717] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   302.717] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   302.717] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   302.717] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   302.717] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   302.717] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   302.717] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   307.271] (II) RADEON(0): Allocate new frame buffer 8000x928 stride 8000
[   307.273] (II) RADEON(0): VRAM usage limit set to 1794672K
[   307.501] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   307.501] (II) RADEON(0): Using hsync ranges from config file
[   307.501] (II) RADEON(0): Using vrefresh ranges from config file
[   307.501] (II) RADEON(0): Printing DDC gathered Modelines:
[   307.501] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   307.501] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   307.501] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   307.501] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   307.501] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   307.501] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   307.501] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   307.501] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   307.501] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   307.501] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   307.501] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   307.501] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   307.673] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   307.673] (II) RADEON(0): Using hsync ranges from config file
[   307.673] (II) RADEON(0): Using vrefresh ranges from config file
[   307.673] (II) RADEON(0): Printing DDC gathered Modelines:
[   307.673] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   307.673] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   307.673] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   307.673] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   307.673] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   307.673] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   307.673] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   307.673] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   307.673] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   307.673] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   307.673] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   307.673] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   307.809] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   307.809] (II) RADEON(G0): Using hsync ranges from config file
[   307.809] (II) RADEON(G0): Using vrefresh ranges from config file
[   307.809] (II) RADEON(G0): Printing DDC gathered Modelines:
[   307.809] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   307.809] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   307.809] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   307.809] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   307.809] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   307.809] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   307.809] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   307.809] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   307.809] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   307.809] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   307.809] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   307.809] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   308.349] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   308.349] (II) RADEON(0): Using hsync ranges from config file
[   308.349] (II) RADEON(0): Using vrefresh ranges from config file
[   308.349] (II) RADEON(0): Printing DDC gathered Modelines:
[   308.349] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   308.349] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   308.349] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   308.349] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   308.349] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   308.349] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   308.349] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   308.349] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   308.349] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   308.349] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   308.349] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   308.349] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   308.521] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   308.521] (II) RADEON(0): Using hsync ranges from config file
[   308.521] (II) RADEON(0): Using vrefresh ranges from config file
[   308.521] (II) RADEON(0): Printing DDC gathered Modelines:
[   308.521] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   308.521] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   308.521] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   308.521] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   308.521] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   308.521] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   308.521] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   308.521] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   308.521] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   308.521] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   308.521] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   308.521] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   308.661] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   308.661] (II) RADEON(G0): Using hsync ranges from config file
[   308.661] (II) RADEON(G0): Using vrefresh ranges from config file
[   308.661] (II) RADEON(G0): Printing DDC gathered Modelines:
[   308.661] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   308.661] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   308.661] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   308.661] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   308.661] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   308.661] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   308.661] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   308.661] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   308.661] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   308.661] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   308.661] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   308.661] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   309.395] (II) RADEON(0): Allocate new frame buffer 8000x928 stride 8000
[   309.397] (II) RADEON(0): VRAM usage limit set to 1794672K
[   309.689] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   309.689] (II) RADEON(0): Using hsync ranges from config file
[   309.689] (II) RADEON(0): Using vrefresh ranges from config file
[   309.689] (II) RADEON(0): Printing DDC gathered Modelines:
[   309.689] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   309.689] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   309.689] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   309.689] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   309.689] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   309.689] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   309.689] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   309.689] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   309.689] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   309.689] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   309.689] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   309.689] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   309.861] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   309.861] (II) RADEON(0): Using hsync ranges from config file
[   309.861] (II) RADEON(0): Using vrefresh ranges from config file
[   309.861] (II) RADEON(0): Printing DDC gathered Modelines:
[   309.861] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   309.861] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   309.861] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   309.861] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   309.861] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   309.861] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   309.861] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   309.861] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   309.862] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   309.862] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   309.862] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   309.862] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   310.001] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   310.001] (II) RADEON(G0): Using hsync ranges from config file
[   310.001] (II) RADEON(G0): Using vrefresh ranges from config file
[   310.001] (II) RADEON(G0): Printing DDC gathered Modelines:
[   310.001] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   310.001] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   310.001] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   310.001] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   310.001] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   310.001] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   310.001] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   310.001] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   310.001] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   310.001] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   310.001] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   310.001] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   310.173] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   310.173] (II) RADEON(0): Using hsync ranges from config file
[   310.173] (II) RADEON(0): Using vrefresh ranges from config file
[   310.173] (II) RADEON(0): Printing DDC gathered Modelines:
[   310.173] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   310.173] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   310.173] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   310.173] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   310.173] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   310.173] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   310.173] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   310.173] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   310.173] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   310.173] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   310.173] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   310.173] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   310.345] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   310.345] (II) RADEON(0): Using hsync ranges from config file
[   310.345] (II) RADEON(0): Using vrefresh ranges from config file
[   310.345] (II) RADEON(0): Printing DDC gathered Modelines:
[   310.345] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   310.345] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   310.345] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   310.345] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   310.345] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   310.345] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   310.345] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   310.345] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   310.345] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   310.345] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   310.345] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   310.345] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   310.485] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   310.485] (II) RADEON(G0): Using hsync ranges from config file
[   310.485] (II) RADEON(G0): Using vrefresh ranges from config file
[   310.485] (II) RADEON(G0): Printing DDC gathered Modelines:
[   310.485] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   310.485] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   310.485] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   310.485] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   310.485] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   310.485] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   310.485] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   310.485] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   310.485] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   310.485] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   310.485] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   310.485] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   339.297] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   339.297] (II) RADEON(0): Using hsync ranges from config file
[   339.297] (II) RADEON(0): Using vrefresh ranges from config file
[   339.297] (II) RADEON(0): Printing DDC gathered Modelines:
[   339.297] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   339.297] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   339.297] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   339.297] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   339.297] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   339.297] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   339.297] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   339.297] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   339.297] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   339.297] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   339.297] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   339.297] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   339.469] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   339.469] (II) RADEON(0): Using hsync ranges from config file
[   339.469] (II) RADEON(0): Using vrefresh ranges from config file
[   339.469] (II) RADEON(0): Printing DDC gathered Modelines:
[   339.469] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   339.469] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   339.469] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   339.469] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   339.469] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   339.469] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   339.469] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   339.469] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   339.469] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   339.469] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   339.469] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   339.469] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   339.605] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   339.605] (II) RADEON(G0): Using hsync ranges from config file
[   339.605] (II) RADEON(G0): Using vrefresh ranges from config file
[   339.605] (II) RADEON(G0): Printing DDC gathered Modelines:
[   339.605] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   339.605] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   339.605] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   339.605] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   339.605] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   339.605] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   339.605] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   339.605] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   339.605] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   339.605] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   339.605] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   339.605] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   344.163] (II) RADEON(0): Allocate new frame buffer 8000x928 stride 8000
[   344.164] (II) RADEON(0): VRAM usage limit set to 1794672K
[   344.353] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   344.353] (II) RADEON(0): Using hsync ranges from config file
[   344.353] (II) RADEON(0): Using vrefresh ranges from config file
[   344.353] (II) RADEON(0): Printing DDC gathered Modelines:
[   344.353] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   344.353] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   344.353] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   344.353] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   344.353] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   344.353] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   344.353] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   344.353] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   344.353] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   344.353] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   344.353] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   344.353] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   344.525] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   344.525] (II) RADEON(0): Using hsync ranges from config file
[   344.525] (II) RADEON(0): Using vrefresh ranges from config file
[   344.525] (II) RADEON(0): Printing DDC gathered Modelines:
[   344.525] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   344.525] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   344.525] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   344.525] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   344.525] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   344.525] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   344.525] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   344.525] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   344.525] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   344.525] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   344.525] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   344.525] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   344.665] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   344.665] (II) RADEON(G0): Using hsync ranges from config file
[   344.665] (II) RADEON(G0): Using vrefresh ranges from config file
[   344.665] (II) RADEON(G0): Printing DDC gathered Modelines:
[   344.665] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   344.665] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   344.665] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   344.665] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   344.665] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   344.665] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   344.665] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   344.665] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   344.665] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   344.665] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   344.665] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   344.665] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   345.001] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   345.001] (II) RADEON(0): Using hsync ranges from config file
[   345.001] (II) RADEON(0): Using vrefresh ranges from config file
[   345.001] (II) RADEON(0): Printing DDC gathered Modelines:
[   345.001] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   345.001] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   345.001] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   345.001] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   345.001] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   345.001] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   345.001] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   345.001] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   345.001] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   345.001] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   345.001] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   345.001] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   345.173] (II) RADEON(0): EDID vendor "DEL", prod id 61501
[   345.173] (II) RADEON(0): Using hsync ranges from config file
[   345.173] (II) RADEON(0): Using vrefresh ranges from config file
[   345.173] (II) RADEON(0): Printing DDC gathered Modelines:
[   345.173] (II) RADEON(0): Modeline "1600x900"x0.0   97.75  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.5 kHz eP)
[   345.173] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   345.173] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   345.173] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   345.173] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   345.173] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   345.173] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   345.173] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   345.173] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   345.173] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   345.173] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   345.173] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[   345.313] (II) RADEON(G0): EDID vendor "GSM", prod id 20170
[   345.313] (II) RADEON(G0): Using hsync ranges from config file
[   345.313] (II) RADEON(G0): Using vrefresh ranges from config file
[   345.313] (II) RADEON(G0): Printing DDC gathered Modelines:
[   345.313] (II) RADEON(G0): Modeline "1600x900"x0.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz eP)
[   345.313] (II) RADEON(G0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   345.313] (II) RADEON(G0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   345.313] (II) RADEON(G0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   345.313] (II) RADEON(G0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   345.313] (II) RADEON(G0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   345.313] (II) RADEON(G0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   345.313] (II) RADEON(G0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   345.313] (II) RADEON(G0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   345.313] (II) RADEON(G0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   345.313] (II) RADEON(G0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   345.313] (II) RADEON(G0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)


```

---

### Post by Zack_Magee on 2016-01-12
Bump.. Any ideas?

---

