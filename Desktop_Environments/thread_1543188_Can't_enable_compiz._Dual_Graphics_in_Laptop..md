---
title: "Can't enable compiz. Dual Graphics in Laptop."
date: 2010-07-31
forum: Desktop Environments
---

### Post by JK3mp on 2010-07-31
I can't seem to enable compiz graphics in my ASUS laptop. My lspci is below....

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a74 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
03:00.0 Network controller: Intel Corporation WiFi Link 100 Series
04:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)

```

I believe it has Nvidia for high performance and Intel for when its supposed to be in power saver mode. But now when i set Hardware propreitary driver it says Recommended Driver: Another version of this driver is in use. And still has the activate button but when i hit it, then restart, It comes up a blinking login screen, so i go recovery shell and Xorg -configure. Well if i go to the Nvidia Settings screen it says you are not using Nvidia drivers please go to terminal and run nvidia-xconfig a to build a new xorg.conf. When i do that and reboot I get the same blinking login issue. Thus i'm stuck. I was recommended compiz-check which didn't work b/c of dual graphics. Any help much appreciated. Thank you! =)

---

