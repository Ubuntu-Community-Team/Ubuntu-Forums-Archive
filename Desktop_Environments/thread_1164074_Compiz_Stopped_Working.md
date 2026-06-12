---
title: "Compiz Stopped Working"
date: 2009-05-19
forum: Desktop Environments
---

### Post by rossmc92 on 2009-05-19
Yesterday I started up my laptop only to find that compiz wasn't on. As far as I can see there's no reason why, this is what I get when trying to start it;

ross@ross-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

I only just got a new new TV and I've been using it through the pc slot if thats relevant and I've also tried enabling desktop effects. That didn't work.

---

### Post by regala on 2009-05-19
> **rossmc92 said:**
> Yesterday I started up my laptop only to find that compiz wasn't on. As far as I can see there's no reason why, this is what I get when trying to start it;

ross@ross-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

I only just got a new new TV and I've been using it through the pc slot if thats relevant and I've also tried enabling desktop effects. That didn't work.

which graphic chipset do you use ? (please post the output of lspci)
do you use the TV out and another display at the same time ?
can you post the content of /var/log/Xorg.0.log ?

---

### Post by kalgecin on 2009-05-19
I'm Confirming the report. 
I had the previous version of ubuntu and the compiz was excellent(and it still is there). But here on 9.04, I get exactly the same error.
lspci gives:
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```
and recent Xorg.0.log:
```
(II) intel(0): EDID vendor "HKC", prod id 5462
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" registered at address 0x60.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:E-EDID segment register" removed.
(II) intel(0): I2C bus "CRTDDC_A" removed.
(II) intel(0): EDID vendor "HKC", prod id 5462
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Using hsync ranges from config file
(II) intel(0): Using vrefresh ranges from config file
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): EDID vendor "HKC", prod id 5462
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode

```

---

### Post by regala on 2009-05-19
> **kalgecin said:**
> I'm Confirming the report. 
I had the previous version of ubuntu and the compiz was excellent(and it still is there). But here on 9.04, I get exactly the same error.
lspci gives:


okay, that's what I feared. You have a quite recent intel graphic chipset. There are regressions for 3D graphics support on recent Intel hardware in Jaunty and despite the fact it's been known since at least November, no one cared to warn on these problems. I may be wrong but there are updates for these regressions scheduled for "jaunty-proposed-updates". The relevant packages are xserver-video-intel, libdrm, and maybe xserver-xorg-core. At least, there must be a PPA from the X team to address these particular issues, if not solved in the official release.

Should you try putting
```

Section "Device"
    Driver "intel"
    Option "AccelMethod" "UXA"
EndSection

```
in /etc/X11/xorg.conf, and you may have a better 3D experience

br, mathieu :)

---

### Post by rossmc92 on 2009-05-19
Just to confirm suspicions, heres my output;

lspci:

ross@ross-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.1 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)

and I got "no such file or directory" for /var/log/Xorg.0.log

---

### Post by kalgecin on 2009-05-20
you can look at "log view" under administration

---

### Post by rossmc92 on 2009-05-23
But it doesn't actually allow me to edit the log.

---

