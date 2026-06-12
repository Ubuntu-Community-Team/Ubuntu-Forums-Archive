---
title: "Lenovo W500 - Changing screen resolution shrinks size of the screen"
date: 2009-08-14
forum: Desktop Environments
---

### Post by randomlyrandom on 2009-08-14
I have a Lenovo W500 running Ubuntu 9.04 with following graphics card:

VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650

I have installed ATI Catalyst Control Center. Initially I had problem of poor performance when desktop effects are enabled. So, I installed xserver-no-backfill driver and after that Desktop Effect works like a charm. But now, I have couple of problems after installing this xserver-no-backfill.

1. My screen resolution seems to be set to maximum and the fonts are very small. When I try to change the resolution to a lower value, say 1440x900 @ 60Hz, the resolution doesn't change. Insted, the screen size shrinks. Now I can see that only 3/4th of my LCD screen is filled and rest is blank/black. 

2. Suspend and hibernate don't work if i have desktop effects enabled. Pasted below lspci output. 

Any help would be greatly appreciated

lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

---

### Post by David Andersson on 2010-08-03
(Late comment, but for the record)

> **pnagral said:**
> 
1. My screen resolution seems to be set to maximum and the fonts are very small. When I try to change the resolution to a lower value...

If the font is too small it is much better to increase font size than to decrease resolution. (Especially if the resolution matches the panel resolution, which i think it did).

Go to System>Preferences>Appearance>Fonts and change font sizes. You can also go on to Details and check DPI (dot per inch). If it is less than 100, it could be worth setting it to 100 or more. (If I have googled correctly, I think the W500 would have 150 DPI).

In firefox, it is also possible to set a minimum font size (Edit>Preferences>Content>Advanced>Minimum font size). I set this to around 10 to be able to see the fine print on some web pages.

---

