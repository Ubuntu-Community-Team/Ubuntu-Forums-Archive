---
title: "Emergency : Desktop Disappered"
date: 2012-07-13
forum: Desktop Environments
---

### Post by deep2sunny on 2012-07-13
I've Ubuntu 12.04 LTS, today when i logged into my system, my complete desktop disapppered, n only mouse cursor was there. Plz help.

---

### Post by prshah on 2012-07-13
> **deep2sunny said:**
> today when i logged into my system, my complete desktop disapppered, n only mouse cursor was there.

Please try to restart the computer. If the problem persists, please do:

a) Press Ctrl+Alt+F1 to enter a text mode virtual terminal. Login, and give the command```
sudo service lightdm restart
``` Press Ctrl+Alt+F7 to return to the GUI (F8..F10 in some cases).

If it still doesn't work, there MAY be some minor corruption of the HDD; switch back to the virtual terminal, and give the command ```
sudo touch /forcefsck
sudo reboot #reboots the system safely
``` After it boots again, it will automatically run a diskcheck. Do NOT interrupt the disk check.

If the problem still persists, please post the output of the log files as below for a clue to the problem```
tail -20 /var/log/Xorg.0.log
tail -20 /var/log/syslog
```

---

### Post by lolpenguin on 2012-07-13
Run
```
unity --reset
``` if you can open a terminal. Otherwise do it in a teletype.
It is not a problem with the hard drive.

---

### Post by deep2sunny on 2012-07-17
unity -- reset : not working

n sudo service lightdm restart not working

---

### Post by deep2sunny on 2012-07-17
plz reply guys

---

### Post by matt_symes on 2012-07-17
Hi

Post back these 2 log files.

```
sudo cat /var/log/lightdm/lightdm.log
```

 ```
cat /var/log/Xorg.0.log
```

They may contain clues as to what is happening.

Kind regards

---

### Post by deep2sunny on 2012-07-17
dude how do i connect internet in ubuntu 12.04 my upper taskbar to connect internet is gone n i can't even open firefox. only terminal is working

---

### Post by matt_symes on 2012-07-17
Hi

For internet, try a wired connection. If you need help configuring it then post back.

After that...

```
sudo apt-get install pastebinit
``````
sudo cat /var/log/lightdm/lightdm.log | pastebinit
``````
cat /var/log/Xorg.0.log | pastebinit
```Post back both URLs here and we can take a look.

Kind regards

---

### Post by deep2sunny on 2012-07-17
how i'll open the terminal try ur codes, n how will I copy them n paste in this forum, currently working from XP

---

### Post by matt_symes on 2012-07-17
Hi

You will need to boot into ubuntu and drop to a console using

ctrl + alt + f1

> **deep2sunny said:**
> how i'll open the terminal try ur codes, n how will I copy them n paste in this forum, currently working from XP

Post back the URL's returned from the pastebinit commands.
```

matthew@matthew-Aspire-7540 ~ % cat /var/log/Xorg.0.log | pastebinit
http://paste.ubuntu.com/1096835/
matthew@matthew-Aspire-7540 ~ % 
```...so i would post back [http://paste.ubuntu.com/1096835/](http://paste.ubuntu.com/1096835/).

Kind regards

---

### Post by matt_symes on 2012-07-17
Hi

Another option is to boot into a LiveCD/USB and copy the files onto a pen drive.

You can then access them from XP.

You may find this easier.

Kind regards

---

### Post by deep2sunny on 2012-07-17
here is the analysis of two commands

```
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
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, CYPRESS,
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
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS
[    23.356] (II) VESA: driver for VESA chipsets: vesa
[    23.356] (II) FBDEV: driver for framebuffer: fbdev
[    23.356] (++) using VT number 7

[    23.356] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    23.357] (II) [KMS] Kernel modesetting enabled.
[    23.357] (WW) Falling back to old probe method for vesa
[    23.357] (WW) Falling back to old probe method for fbdev
[    23.357] (II) Loading sub module "fbdevhw"
[    23.357] (II) LoadModule: "fbdevhw"
[    23.358] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.358] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.359] 	compiled for 1.11.3, module version = 0.0.2
[    23.359] 	ABI class: X.Org Video Driver, version 11.0
[    23.359] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    23.359] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    23.359] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    23.359] (==) RADEON(0): Default visual is TrueColor
[    23.359] (==) RADEON(0): RGB weight 888
[    23.359] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    23.359] (--) RADEON(0): Chipset: "ATI Radeon Mobility 7000 IGP 4437" (ChipID = 0x4437)
[    23.359] (II) RADEON(0): AGP card detected
[    23.359] drmOpenDevice: node name is /dev/dri/card0
[    23.359] drmOpenDevice: open result is 9, (OK)
[    23.360] drmOpenByBusid: Searching for BusID pci:0000:01:05.0
[    23.360] drmOpenDevice: node name is /dev/dri/card0
[    23.360] drmOpenDevice: open result is 9, (OK)
[    23.360] drmOpenByBusid: drmOpenMinor returns 9
[    23.360] drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
[    23.360] (II) Loading sub module "exa"
[    23.360] (II) LoadModule: "exa"
[    23.361] (II) Loading /usr/lib/xorg/modules/libexa.so
[    23.361] (II) Module exa: vendor="X.Org Foundation"
[    23.361] 	compiled for 1.11.3, module version = 2.5.0
[    23.361] 	ABI class: X.Org Video Driver, version 11.0
[    23.362] (II) RADEON(0): KMS Color Tiling: disabled
[    23.362] (II) RADEON(0): KMS Pageflipping: enabled
[    23.362] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    23.400] (II) RADEON(0): Output VGA-0 has no monitor section
[    23.400] (II) RADEON(0): Output LVDS has no monitor section
[    23.406] (II) RADEON(0): Output S-video has no monitor section
[    23.446] (II) RADEON(0): EDID for output VGA-0
[    23.446] (II) RADEON(0): EDID for output LVDS
[    23.446] (II) RADEON(0): Manufacturer: LGP  Model: 657  Serial#: 0
[    23.446] (II) RADEON(0): Year: 1990  Week: 0
[    23.446] (II) RADEON(0): EDID Version: 1.3
[    23.446] (II) RADEON(0): Digital Display Input
[    23.446] (II) RADEON(0): Max Image Size [cm]: horiz.: 30  vert.: 22
[    23.446] (II) RADEON(0): Gamma: 2.20
[    23.446] (II) RADEON(0): No DPMS capabilities specified
[    23.446] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    23.446] (II) RADEON(0): First detailed timing is preferred mode
[    23.446] (II) RADEON(0): redX: 0.587 redY: 0.343   greenX: 0.320 greenY: 0.529
[    23.447] (II) RADEON(0): blueX: 0.158 blueY: 0.140   whiteX: 0.312 whiteY: 0.328
[    23.447] (II) RADEON(0): Manufacturer's mask: 0
[    23.447] (II) RADEON(0): Supported detailed timing:
[    23.447] (II) RADEON(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
[    23.447] (II) RADEON(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[    23.447] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[    23.447] (II) RADEON(0): Unknown vendor-specific block 0
[    23.447] (II) RADEON(0): Unknown vendor-specific block 0
[    23.447] (II) RADEON(0): EDID (in hex):
[    23.447] (II) RADEON(0): 	00ffffffffffff0030f0570600000000
[    23.447] (II) RADEON(0): 	00000103801e16780a72b09657528728
[    23.447] (II) RADEON(0): 	23505400000001010101010101010101
[    23.447] (II) RADEON(0): 	01010101010164190040410026301888
[    23.447] (II) RADEON(0): 	360030e4100000180000000000000000
[    23.447] (II) RADEON(0): 	0000000000000000000000000000004c
[    23.447] (II) RADEON(0): 	475068696c6970734c43440a00000000
[    23.447] (II) RADEON(0): 	004c503135305830382d413300000026
[    23.447] (II) RADEON(0): Printing probed modes for output LVDS
[    23.447] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.447] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    23.447] (II) RADEON(0): Modeline "848x480"x59.7   31.50  848 872 952 1056  480 483 493 500 -hsync +vsync (29.8 kHz)
[    23.447] (II) RADEON(0): Modeline "720x480"x59.7   26.75  720 744 808 896  480 483 493 500 -hsync +vsync (29.9 kHz)
[    23.447] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    23.453] (II) RADEON(0): EDID for output S-video
[    23.453] (II) RADEON(0): Output VGA-0 disconnected
[    23.453] (II) RADEON(0): Output LVDS connected
[    23.453] (II) RADEON(0): Output S-video disconnected
[    23.453] (II) RADEON(0): Using exact sizes for initial modes
[    23.453] (II) RADEON(0): Output LVDS using initial mode 1024x768
[    23.453] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.453] (II) RADEON(0): mem size init: gart size :3dff000 vram size: s:4000000 visible:3cc0000
[    23.453] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    23.453] (==) RADEON(0): DPI set to (96, 96)
[    23.453] (II) Loading sub module "fb"
[    23.453] (II) LoadModule: "fb"
[    23.454] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.454] (II) Module fb: vendor="X.Org Foundation"
[    23.454] 	compiled for 1.11.3, module version = 1.0.0
[    23.454] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.454] (II) Loading sub module "ramdac"
[    23.454] (II) LoadModule: "ramdac"
[    23.454] (II) Module "ramdac" already built-in
[    23.454] (II) UnloadModule: "vesa"
[    23.454] (II) Unloading vesa
[    23.454] (II) UnloadModule: "fbdev"
[    23.454] (II) Unloading fbdev
[    23.454] (II) UnloadModule: "fbdevhw"
[    23.454] (II) Unloading fbdevhw
[    23.455] (--) Depth 24 pixmap format is 32 bpp
[    23.455] (II) RADEON(0): [DRI2] Setup complete
[    23.455] (II) RADEON(0): [DRI2]   DRI driver: radeon
[    23.455] (II) RADEON(0): [DRI2]   VDPAU driver: radeon
[    23.455] (II) RADEON(0): Front buffer size: 3072K
[    23.455] (II) RADEON(0): VRAM usage limit set to 53222K
[    23.455] (==) RADEON(0): Backing store disabled
[    23.455] (II) RADEON(0): Direct rendering enabled
[    23.455] (II) RADEON(0): Render acceleration enabled for R100 type cards.
[    23.455] (II) RADEON(0): Setting EXA maxPitchBytes
[    23.455] (II) EXA(0): Driver allocated offscreen pixmaps
[    23.455] (II) EXA(0): Driver registered support for the following operations:
[    23.455] (II)         Solid
[    23.455] (II)         Copy
[    23.455] (II)         Composite (RENDER acceleration)
[    23.455] (II)         UploadToScreen
[    23.455] (II)         DownloadFromScreen
[    23.455] (II) RADEON(0): Acceleration enabled
[    23.455] (==) RADEON(0): DPMS enabled
[    23.456] (==) RADEON(0): Silken mouse enabled
[    23.456] (II) RADEON(0): Set up textured video
[    23.456] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    23.456] (II) RADEON(0): [XvMC] Extension initialized.
[    23.456] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.456] (--) RandR disabled
[    23.456] (II) Initializing built-in extension Generic Event Extension
[    23.456] (II) Initializing built-in extension SHAPE
[    23.456] (II) Initializing built-in extension MIT-SHM
[    23.456] (II) Initializing built-in extension XInputExtension
[    23.456] (II) Initializing built-in extension XTEST
[    23.456] (II) Initializing built-in extension BIG-REQUESTS
[    23.456] (II) Initializing built-in extension SYNC
[    23.456] (II) Initializing built-in extension XKEYBOARD
[    23.456] (II) Initializing built-in extension XC-MISC
[    23.456] (II) Initializing built-in extension SECURITY
[    23.456] (II) Initializing built-in extension XINERAMA
[    23.456] (II) Initializing built-in extension XFIXES
[    23.456] (II) Initializing built-in extension RENDER
[    23.456] (II) Initializing built-in extension RANDR
[    23.456] (II) Initializing built-in extension COMPOSITE
[    23.456] (II) Initializing built-in extension DAMAGE
[    23.479] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    23.479] (II) AIGLX: enabled GLX_INTEL_swap_event
[    23.479] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    23.479] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    23.480] (II) AIGLX: Loaded and initialized radeon
[    23.480] (II) GLX: Initialized DRI2 GL provider for screen 0
[    23.481] (II) RADEON(0): Setting screen physical size to 270 x 203
[    23.496] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.502] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    23.502] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.502] (II) LoadModule: "evdev"
[    23.503] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.503] (II) Module evdev: vendor="X.Org Foundation"
[    23.503] 	compiled for 1.11.3, module version = 2.7.0
[    23.503] 	Module class: X.Org XInput Driver
[    23.503] 	ABI class: X.Org XInput driver, version 16.0
[    23.503] (II) Using input driver 'evdev' for 'Power Button'
[    23.504] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.504] (**) Power Button: always reports core events
[    23.504] (**) evdev: Power Button: Device: "/dev/input/event2"
[    23.504] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.504] (--) evdev: Power Button: Found keys
[    23.504] (II) evdev: Power Button: Configuring as keyboard
[    23.504] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    23.504] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.504] (**) Option "xkb_rules" "evdev"
[    23.504] (**) Option "xkb_model" "pc105"
[    23.504] (**) Option "xkb_layout" "us"
[    23.505] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    23.505] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.505] (II) Using input driver 'evdev' for 'Video Bus'
[    23.505] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.505] (**) Video Bus: always reports core events
[    23.505] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    23.506] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.506] (--) evdev: Video Bus: Found keys
[    23.506] (II) evdev: Video Bus: Configuring as keyboard
[    23.506] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:01/LNXVIDEO:00/input/input6/event6"
[    23.506] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    23.506] (**) Option "xkb_rules" "evdev"
[    23.506] (**) Option "xkb_model" "pc105"
[    23.506] (**) Option "xkb_layout" "us"
[    23.507] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.507] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.507] (II) Using input driver 'evdev' for 'Power Button'
[    23.507] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.507] (**) Power Button: always reports core events
[    23.507] (**) evdev: Power Button: Device: "/dev/input/event1"
[    23.507] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.507] (--) evdev: Power Button: Found keys
[    23.507] (II) evdev: Power Button: Configuring as keyboard
[    23.507] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    23.507] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    23.507] (**) Option "xkb_rules" "evdev"
[    23.507] (**) Option "xkb_model" "pc105"
[    23.507] (**) Option "xkb_layout" "us"
[    23.508] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    23.508] (II) No input driver specified, ignoring this device.
[    23.508] (II) This device may have been added with another device file.
[    23.509] (II) config/udev: Adding input device Generic USB K/B (/dev/input/event4)
[    23.509] (**) Generic USB K/B: Applying InputClass "evdev keyboard catchall"
[    23.509] (II) Using input driver 'evdev' for 'Generic USB K/B'
[    23.509] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.509] (**) Generic USB K/B: always reports core events
[    23.509] (**) evdev: Generic USB K/B: Device: "/dev/input/event4"
[    23.509] (--) evdev: Generic USB K/B: Vendor 0x13ba Product 0x17
[    23.509] (--) evdev: Generic USB K/B: Found keys
[    23.509] (II) evdev: Generic USB K/B: Configuring as keyboard
[    23.509] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.0/input/input4/event4"
[    23.509] (II) XINPUT: Adding extended input device "Generic USB K/B" (type: KEYBOARD, id 9)
[    23.510] (**) Option "xkb_rules" "evdev"
[    23.510] (**) Option "xkb_model" "pc105"
[    23.510] (**) Option "xkb_layout" "us"
[    23.511] (II) config/udev: Adding input device Generic USB K/B (/dev/input/event5)
[    23.511] (**) Generic USB K/B: Applying InputClass "evdev pointer catchall"
[    23.511] (**) Generic USB K/B: Applying InputClass "evdev keyboard catchall"
[    23.511] (II) Using input driver 'evdev' for 'Generic USB K/B'
[    23.511] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.511] (**) Generic USB K/B: always reports core events
[    23.511] (**) evdev: Generic USB K/B: Device: "/dev/input/event5"
[    23.511] (--) evdev: Generic USB K/B: Vendor 0x13ba Product 0x17
[    23.511] (--) evdev: Generic USB K/B: Found 3 mouse buttons
[    23.511] (--) evdev: Generic USB K/B: Found scroll wheel(s)
[    23.511] (--) evdev: Generic USB K/B: Found relative axes
[    23.511] (--) evdev: Generic USB K/B: Found x and y relative axes
[    23.511] (--) evdev: Generic USB K/B: Found keys
[    23.511] (II) evdev: Generic USB K/B: Configuring as mouse
[    23.511] (II) evdev: Generic USB K/B: Configuring as keyboard
[    23.511] (II) evdev: Generic USB K/B: Adding scrollwheel support
[    23.511] (**) evdev: Generic USB K/B: YAxisMapping: buttons 4 and 5
[    23.511] (**) evdev: Generic USB K/B: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.511] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:13.0/usb2/2-1/2-1:1.1/input/input5/event5"
[    23.511] (II) XINPUT: Adding extended input device "Generic USB K/B" (type: KEYBOARD, id 10)
[    23.511] (**) Option "xkb_rules" "evdev"
[    23.511] (**) Option "xkb_model" "pc105"
[    23.511] (**) Option "xkb_layout" "us"
[    23.512] (II) evdev: Generic USB K/B: initialized for relative axes.
[    23.512] (**) Generic USB K/B: (accel) keeping acceleration scheme 1
[    23.512] (**) Generic USB K/B: (accel) acceleration profile 0
[    23.512] (**) Generic USB K/B: (accel) acceleration factor: 2.000
[    23.512] (**) Generic USB K/B: (accel) acceleration threshold: 4
[    23.513] (II) config/udev: Adding input device Generic USB K/B (/dev/input/mouse0)
[    23.513] (II) No input driver specified, ignoring this device.
[    23.513] (II) This device may have been added with another device file.
[    23.513] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    23.513] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.513] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.513] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.514] (**) AT Translated Set 2 keyboard: always reports core events
[    23.514] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    23.514] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.514] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.514] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.514] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    23.514] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    23.514] (**) Option "xkb_rules" "evdev"
[    23.514] (**) Option "xkb_model" "pc105"
[    23.514] (**) Option "xkb_layout" "us"
[    24.604] (II) RADEON(0): EDID vendor "LGP", prod id 1623
[    24.604] (II) RADEON(0): Printing DDC gathered Modelines:
[    24.604] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.984] (II) RADEON(0): EDID vendor "LGP", prod id 1623
[    27.984] (II) RADEON(0): Printing DDC gathered Modelines:
[    27.984] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    34.246] (II) RADEON(0): EDID vendor "LGP", prod id 1623
[    34.246] (II) RADEON(0): Printing DDC gathered Modelines:
[    34.246] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.023] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
[    36.318] (II) RADEON(0): EDID vendor "LGP", prod id 1623
[    36.318] (II) RADEON(0): Printing DDC gathered Modelines:
[    36.318] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    39.162] (II) RADEON(0): EDID vendor "LGP", prod id 1623
[    39.162] (II) RADEON(0): Printing DDC gathered Modelines:
[    39.162] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    47.892] (II) AIGLX: Suspending AIGLX clients for VT switch
[   117.573] (II) Open ACPI successful (/var/run/acpid.socket)
[   117.573] (II) AIGLX: Resuming AIGLX clients after VT switch
[   117.612] (II) RADEON(0): EDID vendor "LGP", prod id 1623
[   117.612] (II) RADEON(0): Printing DDC gathered Modelines:
[   117.612] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   117.663] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.xkm
akash@akash-Satellite-A60:~$ 


```

---

### Post by matt_symes on 2012-07-17
Hi

The results from your xorg log file show that X is starting correctly and that usually means LightDM is also running correctly.

I suspect it's a problem with Unity.

Boot into a root console from the grub menu and create a new user. The root console is text based but don't let that worry you.

To boot into the recovery console, reboot the Ubuntu PC and on the grub menu select the recovery option. It will look something like this

> Ubuntu, with Linux 3.5.0-030500rc6-generic (**recovery mode**)although the numbers may be different. When you get the recovery menu select the root console option. If you don't get the GRUB menu at startup then press (and keep depressed) the shift key when the computer starts.

When booted into the recovery console, type these command one after another.

```
mount -o remount,rw /
``````
adduser recovery
```Enter a password and hit enter your the rwest of the fields. select the Y option.

For reference, here's one i added (you will not need the sudo command in the root console though.
```

matthew@matthew-Aspire-7540 ~ % sudo adduser recovery
Adding user `recovery' ...
Adding new group `recovery' (1003) ...
Adding new user `recovery' (1003) with group `recovery' ...
Creating home directory `/home/recovery' ...
Copying files from `/etc/skel' ...
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
Changing the user information for recovery
Enter the new value, or press ENTER for the default
        Full Name []: 
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [Y/n] y
matthew@matthew-Aspire-7540 ~ % 
```Then type (Big G below)

```
usermod -aG admin recovery
```Finally type

```
reboot
```Select the user recovery from the login screen and log in as that user. Do you have a working desktop ?

Also, post back errors.

Kind regards

---

### Post by deep2sunny on 2012-07-17
what will this do

---

### Post by matt_symes on 2012-07-17
Hi

This will create a new user (called recovery) along side your user. 

You can then try to login as that user (called recovery) from the Lightdm login screen.. 

That user (recovery) will have all the default settings so if you can login as user recovery then it means your personal settings for you usual account are broken, otherwise it means system settings are broken.

Kind regards

---

### Post by deep2sunny on 2012-07-18
I tried everything u mentioned. nothing worked so i reinstalled Ubuntu 12.04 LTS and everything is back to normal.

Plz mark it as solved

---

