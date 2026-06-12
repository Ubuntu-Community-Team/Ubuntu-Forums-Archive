---
title: "Desktop flashing"
date: 2008-12-06
forum: Desktop Environments
---

### Post by andre80 on 2008-12-06
Hi,

I tried Kubuntu 8.10 and its flashing on and off on my laptop, then i tried plugging in a monitor and the flashing stops, but the monitor is showing the desktop and its blinking. i guess its something has to do with the dual head support.

my lapotp is nec versa p8100 and here is my lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:02.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
01:02.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
01:02.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
01:02.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

Add:
I tried Ubuntu 8.10 and its fine, it did flashed once to twice after X finished initialized, so I use ubuntu 8.10 at the mean time waiting for the flashing problem to solve, the KDE desktop is soooo coooool

---

### Post by skelbley08 on 2008-12-06
This might be helpful; worked for me. Go into System Settings, click the advanced tab, then Service Manager. Stop the "Detecting RANDR (Monitor changes)" service. Worked for me.

Hope this helps.:D

---

