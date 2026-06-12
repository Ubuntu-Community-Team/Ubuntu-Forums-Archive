---
title: "Dell Dimension 2400 GE Force FX 5500 on Ubuntu 11.10"
date: 2012-04-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by theknightlinux on 2012-04-06
Hello, I have installed Ubuntu 11.10 on a Dell Dimension 2400 for my brother. I upgraded it to 1.5gb of RAM. And I have added a GeForce FX5500. Ubuntu doesn't seem to be operating in its full performance. It feels slow. I believe the problem is with the video card fx5500. I've tried all the drivers suggested by Ubuntu (173 and 96, current and post release updates). I've also tried other guides and instructions that I've found here in Ubuntu Forums and by Google for fixing the problem, but nothing I've tried seems to work, and sometimes when trying one of the guides it has led me to a black screen on boot up. The last thing I've found out is that when I typed lspci, I believe that the onboard video card is the one loaded by the system and not the nvidia geforce fx5500, I don't know as also the geforce card appears on the list. This is what I get when I type lspci:

00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:06.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)


I'm really new to Linux, but as of two months trying it as my main OS on my computer, I'm very satisfied with it. And I would like to try to run all the visual effects in Compiz and the different docks with OpenGL on this Dell Dimension 2400 like I try it on my main computer. I would really appreciate any help or suggestions if there's a solution to correct this problem, or it there's not. Thanks.

---

### Post by mikewhatever on 2012-04-09
You expect too much of an eight year old piece of hardware, it's too old to run a recent version of Compiz (used in Unity). Try installing the recommended driver, and selecting Ubuntu2d at the login screen. If it still feels slow, try Xubuntu or Lubuntu, they use lighter window managers, and should provide better responsiveness.

---

### Post by theknightlinux on 2012-04-09
Thanks for your suggestion Mike. Well, I believe the only fallback for the Dimension 2400 is the video card. As for the CPU and the RAM I believe they're quite decent for a Ubuntu installation. But I did installed as you suggested. I installed Ubuntu 11.10, and am running it with Unity 3D. I didn't installed the GeForce card, I just left the onboard graphics card. It feels OK, but I know it can feel better. I've found out Ubuntu 11.10 doesn't support the i82845 onboard graphics card, it just loads the unkown driver and it's a problem that doesn't have a solution as of Apr. 9, 2012. The computer is OK, though, but can't run things with OpenGL and all that kind of stuff, but still, can do a lot of things. Thanks.

---

