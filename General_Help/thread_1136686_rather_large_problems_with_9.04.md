---
title: "rather large problems with 9.04"
date: 2009-04-25
forum: General Help
---

### Post by Monotoko on 2009-04-25
Okay, im running a laptop at the moment, Fujitsu Siemans V5055 - 2GB of RAM and 2Ghz Dual-Processor.

i recently did a clean install of 9.04 (tried to upgrade but it went terribly wrong...luckily i had everything backed up and just did a clean install)

so i boot into my nice shiny new system and am rather pleased...then it makes the login sound, its so grainy and unhearable. After fiddling around a bit, i had to turn the PCM volume control down to less than a quater of the way, and the master all the way up, and it appears to now be working fine, but i would like to know why it is doing that in the first place? 8.04 never did :S

so once i have that working, i try to connect myself to the internet, it works..now heres the snag, it disconnects almost every 20 minutes..anyone have any idea why?

Finally, i manage to get on the internet in my 20 minute gaps, with flash etc...and decide to run firefox and go onto youtube to watch a video...suddenly my entire computer feels slow, and i mean very slow indeed, so i decided to run the top command from the terminal, and find that firefox is using 75% of my CPU (???)

These are the results of running lspci as i figure the first two are a driver problem, and figure it would be helpful

```
monotoko@katie:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by Monotoko on 2009-04-25
How could i phrase this to get more chance of getting an answer?

---

