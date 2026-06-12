---
title: "Heroes of Newerth Does Not Work"
date: 2012-03-16
forum: Gaming &amp; Leisure
---

### Post by ksukumarrd on 2012-03-16
Hi,
I'm an ubuntu noob and just installed it a couple of days ago.
When i try to run HoN, it shows

warning: The VAD has been replaced by a hack pending a complete rewrite

in the terminal but runs anyway. But when i try to play a game the game auto quits and 

Segmentation fault

is printed out. How do i fix this so i can play HoN.

---

### Post by oldrocker99 on 2012-03-16
What's your hardware? Try lspci in a terminal and post the results. We're here to help.

---

### Post by ksukumarrd on 2012-03-17
Thanks for the quick reply.

This is what i get:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)

---

### Post by Drnflood on 2012-03-17
I thought HoN Required some type of opengl ati/nvidia compatible graphics card? Looks like you are running standard intel chipset drivers?

Found this thread on the HoN Forums.
[http://forums.heroesofnewerth.com/showthread.php?t=354676](http://forums.heroesofnewerth.com/showthread.php?t=354676)


Every Issue I see with this pretty much stems from opengl settings in Nvidia being wrong, or x-org needed to be updated.

---

### Post by ksukumarrd on 2012-03-17
Wait so i can't run Hon with intel graphics card? Is there anything i can do to get around it?


I followed the instructions on some threads with the same error and they were all about a missing file in a directory (like the link Drnflood posted) but it didn't work.

---

