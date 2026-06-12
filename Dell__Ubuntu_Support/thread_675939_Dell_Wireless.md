---
title: "Dell Wireless"
date: 2008-01-23
forum: Dell  Ubuntu Support
---

### Post by chaos315 on 2008-01-23
Hey, I have two dells and one of them has a weird problem. After it comes out of stand-by it loses the entire network list and will not connect wirelessly. If I plug in the LAN it works fine. If I restart the computer with the LAN in, it brings up all of the networks again and works fine (until I leave the computer for a while again) Meanwhile my other laptop works fine the whole time and never skips a beat. The one that works is an older inspiron and the one that has trouble is an XPS m1330. Does anyone know of something that will make this computer stay connected, like a new ndiswrapper or magic line of code that will make everything work again? Sorry that I am such a noob, but virtually windows free!! Thanks!!

---

### Post by Prospero2006 on 2008-01-23
suggestion:

Post the output of lspci

This will give the community a better sense of exactly what the chipset is you are working with. Dell wireless can be really tough. 

I got a latitude working by using a deb called

bcm43xx_compwiz18.1-all.deb

Not much to work with there, but at least it's a start.

---

### Post by chaos315 on 2008-01-23
Sorry, what is the Ispci?

---

### Post by crawall on 2008-01-24
I have the same issues

my lspci report:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

any ideas?

---

### Post by chaos315 on 2008-01-24
Does the same trick work for fixing the problem, or do you have something else that works? I can't help thinking that it is somehow my fault in some way or another. I tried reinstalling the ndiswrapper and that did nothing. I don't really want to go trying things because I don't want to bork my whole system. anyway, if anyone has any suggestions I will try them. Thanks

---

### Post by natehall on 2008-01-24
lspci is a command typed into the terminal. You can get a terminal by going to Applications > Accessories> Terminal. To find out what any command does you can type man in front of the command. Pressing q will get you back to the prompt.

---

