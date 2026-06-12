---
title: "Dolphin Emulator"
date: 2011-04-04
forum: Gaming &amp; Leisure
---

### Post by Dark Shinobi on 2011-04-04
Ok, after some trial and error, I managed to compile a working version of the dolphin emulator. With my *cough* inferior hardware, I am only getting about 15fps, so I was wondering how I could write a bash script to disable all unneeded applications to run it at a slightly better speed. 

H/W path           Device      Class       Description
======================================================
                               system      Inspiron 1545
/0                             bus         0G848F
/0/0                           memory      64KiB BIOS
/0/400                         processor   Pentium(R) Dual-Core CPU       T4400 
/0/400/700                     memory      128KiB L1 cache
/0/400/701                     memory      1MiB L2 cache
/0/1000                        memory      3GiB System Memory
/0/1000/0                      memory      1GiB DIMM DDR Synchronous 800 MHz (1.
/0/1000/1                      memory      2GiB DIMM DDR Synchronous 800 MHz (1.
/0/100                         bridge      Mobile 4 Series Chipset Memory Contro
/0/100/2                       display     Mobile 4 Series Chipset Integrated Gr
/0/100/2.1                     display     Mobile 4 Series Chipset Integrated Gr
/0/100/1a                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1a.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801I (ICH9 Family) HD Audio Control
/0/100/1c                      bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.1                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.1/0      eth1        network     BCM4312 802.11b/g
/0/100/1c.2                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1c.2/0      eth0        network     88E8040 PCI-E Fast Ethernet Controlle
/0/100/1c.4                    bridge      82801I (ICH9 Family) PCI Express Port
/0/100/1d                      bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.1                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.2                    bus         82801I (ICH9 Family) USB UHCI Control
/0/100/1d.7                    bus         82801I (ICH9 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      ICH9M LPC Interface Controller
/0/100/1f.2        scsi0       storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0      /dev/sda    disk        250GB WDC WD2500BEVT-7
/0/100/1f.2/0/1    /dev/sda1   volume      39MiB Windows FAT volume
/0/100/1f.2/0/4    /dev/sda4   volume      232GiB EXT4 volume
/0/100/1f.2/0/4/5  /dev/sda5   volume      227GiB Linux filesystem partition
/0/100/1f.2/0/4/6  /dev/sda6   volume      5175MiB Linux swap / Solaris partitio
/0/100/1f.2/1      /dev/cdrom  disk        DVD+-RW TS-L633C
/0/100/1f.3                    bus         82801I (ICH9 Family) SMBus Controller
/0/1               scsi6       storage     
/0/1/0.0.0         /dev/sdb    disk        SCSI Disk
/1                             power       DELL P505M9C
/2                 vboxnet0    network     Ethernet interface

---

### Post by Philsoki on 2011-04-05
Integrated graphics... It's possible to squeeze more performance out, for sure. But you'll probably be lucky to get a max of 30FPS - and that's a really, really long-shot.

What do you get from the following:
```
lspci |more
```
```
uname -a
```
```
uname -r
```
```
cat /etc/issue
```

*Sigh* I uninstalled Linux and went back to Windows today because I finally got a decent graphics card so I could play games.. But just typing commands makes me want to re-install it...

---

### Post by supergirlkara on 2011-04-05
I have a good graphics card and I am running Ubuntu 10.04 Lucid....When I run the latest Dolphin Emulator with a game cube game, it really goes very slow. It also depends on the compatibility of the game you are trying to run, but I'm trying to run Eternal Darkness, and it plays ok, but the slow downs are significant, and I can't see the start menu. Over all I am sure its a good emulator....I just need to play a game thats better compatible with dolphin-emu I guess. :-(

---

### Post by Philsoki on 2011-04-06
> **supergirlkara said:**
> I have a good graphics card and I am running Ubuntu 10.04 Lucid....When I run the latest Dolphin Emulator with a game cube game, it really goes very slow. It also depends on the compatibility of the game you are trying to run, but I'm trying to run Eternal Darkness, and it plays ok, but the slow downs are significant, and I can't see the start menu. Over all I am sure its a good emulator....I just need to play a game thats better compatible with dolphin-emu I guess. :-(
You need a really fast CPU for Dolphin and only a moderate graphics card. You could have two Nvidia 460's running in SLI and 6GB RAM, but if your CPU is Pentium 4 HT or lower you're going to get a slow frame rate anyway.

Dolphin is really CPU intensive. 

My friend runs Dolphin great, we play Super Smash Bro's Brawl on it all the time in HD using two wired XBOX 360 controllers. It's freaking awesome! :D

---

### Post by Dark Shinobi on 2011-04-06
And its a crappy intel chipset too. Well before I switched to linux, I would be able to get something like 30fps on windwaker (I only own 3 games), and something tells me I should be able to get at least that in a linux environment. Here is the output...

  	 	 	 	 	 	p { margin-bottom: 0.08in; }a:link {  }  00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller 
  Hub (rev 07) 
 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Int 
 egrated Graphics Controller (rev 07) 
 00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated 
  Graphics Controller (rev 07) 
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll 
 er #4 (rev 03) 
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll 
 er #5 (rev 03) 
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll 
 er #6 (rev 03) 
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control 
 ler #2 (rev 03) 
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller 
  (rev 03) 
 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (r 
 ev 03) 
 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (r 
 ev 03) 
 00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (r 
 ev 03) 
 00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (r 
 ev 03) 
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll 
 er #1 (rev 03) 
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll 
 er #2 (rev 03) 
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controll 
 er #3 (rev 03) 
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Control 
 ler #1 (rev 03) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
 00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
 00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 0 
 3) 
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
 09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Et 
 hernet Controller (rev 13) 
 0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
 

 Linux ubuntu 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux 
 

 Ubuntu 10.04.2 LTS \n \l 





Also for some reason, Ubuntu reports my VRAM is being 64 megs, when in windows it was dynamic sometimes being up to 1Gb. Is there a way to have Ubuntu borrow more system memory for the VRAM?

---

### Post by supergirlkara on 2011-04-06
I have an Intel(R) Quad2Core CPU Q9300 w/ 8gb of ddr3 ram. That should be more than enough to play dolphin. Like I said in my post some games work, and some games do not.

---

### Post by Dark Shinobi on 2011-04-07
I only own 3 games, so does anyone know how well the frame rate will be on either Wind Waker, Twilight Princess, or Tales of Phantasia. So far, the Frame rate is something between 10-15 a sec. Just trying to squeeze as much out as possible :)

---

