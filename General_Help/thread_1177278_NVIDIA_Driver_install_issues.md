---
title: "NVIDIA Driver install issues"
date: 2009-06-03
forum: General Help
---

### Post by David Crockett on 2009-06-03
Hi all as a beginner I am stumped:   

I have been attempting to install a NVIDIA driver for my video card.   
I get the following message when I try to use the NVIDIA tool to modify display preferences:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

How do I do  this? I have tried to go into the terminal and run sudo nvidia-xconfig and I get bad command as an error.  Please help.

---

### Post by Arup on 2009-06-03
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Please follow this guide here to a T.

---

### Post by David Crockett on 2009-06-03
Thanks for the info.  but I have tried this and I sill cannot get it to work.   It wants me to run nvidia-xonfig  from the root.   I have tried sudo nvidia-xconfig and all I get is bad command.

---

### Post by VastOne on 2009-06-03
> **David Crockett said:**
> Thanks for the info.  but I have tried this and I sill cannot get it to work.   It wants me to run nvidia-xonfig  from the root.   I have tried sudo nvidia-xconfig and all I get is bad command.

Run this

```
lspci

```

Report back exactly what it says after

 VGA compatible controller:

When you installed the nVidia driver from [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978) as Arup advised, what exactly happened during the install?  Did the install ask you several questions that you had to answer, one about a kernel?

---

### Post by David Crockett on 2009-06-05
I get the following:
00:00.0 Host bridge: Intel Corporation 82820 820 (Camino) Chipset Host Bridge (MCH) (rev 03)
00:01.0 PCI bridge: Intel Corporation 82820 820 (Camino) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
02:08.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:0a.0 USB Controller: NEC Corporation USB (rev 43)
02:0a.1 USB Controller: NEC Corporation USB (rev 43)
02:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)

---

