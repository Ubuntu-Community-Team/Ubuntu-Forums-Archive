---
title: "splash screen doesnt appers (lcd monitor)"
date: 2007-04-13
forum: Desktop Environments
---

### Post by eduac on 2007-04-13
I have a problem to work with lcd monitor on kubuntu 6.10.  I cant see the splash screen after i change to lcd monitor. Anyone have a idea to solve this?

there is my lspci output:

> 
$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 315PRO PCI/AGP VGA Display Adapter
02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)



---

### Post by tgm4883 on 2007-04-13
can you see other things on your lcd monitor?  (ie bios bootup?  Desktop?)

---

### Post by eduac on 2007-04-13
> **tgm4883 said:**
> can you see other things on your lcd monitor?  (ie bios bootup?  Desktop?)

bios - yes
kubuntu splash screen - no
kde splash screen - yes
kde - yes

---

### Post by tgm4883 on 2007-04-13
Did you set this up on a different monitor then upgrade to an lcd panel?  Is kubuntu-artwork-usplash installed?  Am i correct to assume that this is not a functionality problem, but just something that you would like fixed?  Are there any error messages (such as signal out of range?)

---

### Post by eduac on 2007-04-13
> **tgm4883 said:**
> Did you set this up on a different monitor then upgrade to an lcd panel?  Is kubuntu-artwork-usplash installed?  Am i correct to assume that this is not a functionality problem, but just something that you would like fixed?  Are there any error messages (such as signal out of range?)

appears: 

> 
attetion

mode not supported


---

### Post by tgm4883 on 2007-04-13
[http://ubuntuforums.org/showthread.php?t=405297](http://ubuntuforums.org/showthread.php?t=405297)

Read post #9.

It doesn't work, but I think it is due to him leaving in the # at the beginning of the line effectively commenting it out.  I have posed this question to him in the thread and am waiting a response.

---

### Post by tgm4883 on 2007-04-13
Wrong thread

---

