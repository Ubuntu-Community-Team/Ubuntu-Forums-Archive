---
title: "Drives showing up twice"
date: 2012-11-08
forum: Desktop Environments
---

### Post by duranl on 2012-11-08
I've had this annoying problem since I installed Xubuntu 12.10.  My drives show up twice (see attached picture).  This also happens on the Desktop, which I have completely disabled because it's annoying.  Also, when I open a folder using the bottom task panel, it takes a while to open (~7-10 seconds) and it opens two windows of the same folder.  Any idea on how to start trouble shooting this so there aren't any more duplicates?  Thanks!

lspci
> 0:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6520G]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:16.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:16.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
03:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)

---

### Post by Mr_JMM on 2012-11-08
Yep. This is a WELL known and WELL discussed bug that seems to effect Xubuntu and LinuxMint with XFCE desktop. It's irritating I know but again, it's well known, is listed in launchpad and should be fixed for 13.04 if not before.

Have a quick search in this section and you'll see numerous solutions. 

I prefer if people do their own searching, it's easy enough however - [http://ubuntuforums.org/showthread.php?t=2079661](http://ubuntuforums.org/showthread.php?t=2079661).
But please, that took a few seconds for me to find, as it would have you.

---

### Post by duranl on 2012-11-09
Thanks!  I'm still new with Linux, so sometimes I have trouble coming up with search terms.

---

### Post by Mr_JMM on 2012-11-09
No worries. I hope these little irks don't put you off *buntu.

You're right though, sometimes it takes some experimentation to get accurate search results.

---

### Post by llanitedave on 2012-11-10
Well, this thread certainly helped me.  I had the same issue, and the fact that I found it on the main page made it easy.

I understand it can get frustrating to answer the same questions repeatedly, but patience sure pays dividends to the user base in general.

Since this is apparently such a common problem, why not make this particular solution a sticky?

---

### Post by anirbanghosh on 2012-11-10
Fix released.

[https://launchpad.net/ubuntu/+source/thunar/1.4.0-1ubuntu2.1](https://launchpad.net/ubuntu/+source/thunar/1.4.0-1ubuntu2.1)

---

