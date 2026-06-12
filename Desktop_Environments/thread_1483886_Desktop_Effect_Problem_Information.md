---
title: "Desktop Effect Problem Information"
date: 2010-05-15
forum: Desktop Environments
---

### Post by ajay.444 on 2010-05-15
Extra effect work well in my PC with 8.04, but after this any new version give that "desktop effect could not be enabled"

My ubuntu lspci o/p is 
{
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel C

Can buy a graphics card is only option? suggest me plz.

---

### Post by Silent Warrior on 2010-05-15
Hm... I don't remember precisely what, but there was some change a while back - maybe changing the Intel-driver's rendering-method from XAA to EXA (or the other way around?). I have no idea what that means.

I tried to find a spot on the Wiki for you, but I don't know if I found a good one... Anyway, you might be interested in knowing that Intel canned interactive e-mail support for that chip in 2005. (Intel i845G)
I discovered this through a search: [https://bugs.launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-intel/+bug/541492?comments=all](https://bugs.launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-intel/+bug/541492?comments=all)
There's a link to a PPA with backported drivers - use at your own risk, and NOT AT ALL if you don't know how to recover.

Ha! I think THIS is what you're after, though: [http://ubuntuforums.org/showthread.php?t=1468668](http://ubuntuforums.org/showthread.php?t=1468668)

---

