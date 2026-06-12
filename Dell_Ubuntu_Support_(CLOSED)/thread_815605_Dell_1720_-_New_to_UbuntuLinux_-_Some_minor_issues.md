---
title: "Dell 1720 - New to Ubuntu/Linux - Some minor issues"
date: 2008-06-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bmoney80 on 2008-06-01
Okay, so first I just want to say that please excuse any noobish statements/questions that I may make/ask - I've been using Ubuntu/Linux for about 3 days. My only experience with this type of operating system goes back to when I was like 13 years old using dial up IRC and actually using dos prompt to manage programs/files.  

So I bought a Dell 1720 about 6 months ago and my experience with Vista was friggin terrible. While I've always had a strong dislike for windows, I really think many of my problems came from Dell - who knowingly manufactured computers with hardware incompatible with the vista release. 

Anyways, after over 100 BSOD errors, a dozen factory image restores, and 10324238942734 instances where I wanted to through my laptop through drywall - I replaced what I found to be a faulty hard drive and installed Ubuntu. Other than a few issues with my wireless card and audio driver - Ive had a really sweet experience so far. Im running the 64bit 8.04 release on a 1720 (T5450, 4gb, 1505 wireless n). You guys really have an awesome community where people are cool with helpin us noobs out and Ive been able to solve most of my issues with just doin a little homework. 

While most of my issues have been easy to solve - theres one thing in particular I'm completely baffled by.  So as I mentioned before, I have a 1505 draft n card. I followed some links to a page that listed a bunch of broadcom drivers and instructions on how to set everything up - which worked great. I have a stable connection when doing basic internet browsing/downloading but recently I setup virtualbox with xp so I could use my bodog poker account. Everything is perfect withthat - I can get on and ive played for hours without interruptions. Then I tried to install my usenext software that I had from when operating under vista ... which is when some of my issues began. 

Now before I get busted on for using UseNext, I'm only using this until I use up all of my download gigs then I'm switching to some kind of torrent program (any suggestions???). But while I'm forced to use up what I already paid for - Im having issues with connectivity. Once I start downloading a large file my connection goes completely - and not just on usenext. I can no longer get a connection for pidgen or firefox. I've tried reestablishing a connection but nothing works and I'm left to reboot. Once I reboot I'm fine. As long as I dont try Usenext I never lose my connection - its just when I'm using that particular program. Ive also downloaded Usenext's linux software which causes the same exact problem - which typically interrupts more quickly then my virtualbox/xp connection. Oh, and I'll initially get a connection to Usenext, but lets say I start downloading something that 800mb .. I'll get 15% downloaded and then the connection craps out on me. 

Any suggestions on what could be causing this and any possible solutions? Any advice would be really appreciated. As I said - I've been using Ubuntu for a few days and I love it but I'm just not use to how everything works and I have to constantly look up all of the terminal commands.

Thanks in advance.

Ben

---

### Post by wak_wak on 2008-06-01
Start with going to a session and type in lspic.  Post the output...

---

### Post by bmoney80 on 2008-06-01
bmoney@bmoney:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

