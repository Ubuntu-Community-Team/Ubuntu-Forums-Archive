---
title: "The system performance is low (Ubuntu 9.04)"
date: 2009-05-03
forum: General Help
---

### Post by van_002 on 2009-05-03
Hello, this is my problem in ubuntu 9.04:

The system in general, from the folder to firefox or any aplication, got a slow performance.
Saying this I mean that the scroll of the windows, or any kind of navigation shows a LAG!.
I must solve this because this issue also affects the video performance as well. I found strange that the OS loads as expected. So this must be a video drivers issue I guess but everithing seems to be OK in the "xorg.conf"
The details of my pc are:

ASUS P5SD2-VM motherboard  (this is a graphic integrated, i've got no 3d acceleration but the rendering is "On")
2.5 Gh
1Gb RAM


LSPCI:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)


The OS is in a 40Gb space of the disk ,  I configure the partition with a 11Gb swap .
(Windows is in a 50Gb partition, but I don't think that this is important)

So, this are the details of my current problem in ubuntu 9.04 ,  note that this LAG doesn't happens in my PC with ubuntu 8.10 . (I update the system because a Ethernet driver issue, so , i've solved that but now I have this).



I started with ubuntu recently.  

Cheers.

Hope someone can help me.

Thanks in advance.

---

### Post by van_002 on 2009-05-05
No one ? :(

---

### Post by JDShewey on 2009-05-05
Try typing "top" at a command prompt. This will tell what processes are using the most system resources. You can use this to find out what is hogging all of your system resources.

---

### Post by TomB19 on 2009-05-05
Try going to System Settings -> Desktop -> Desktop Effects and uncheck the desktop effects box.

I suspect you will find turning off desktop effects makes everything quite snappy.

---

### Post by van_002 on 2009-05-05
all the effects are off (as a mather of fact the system don't let me activate anyone).

and in the top :

The xorg command is normally consuming 2% of the CPU.

Now,,,, If I perform all most anything the Xorg goes to 90% or + of the CPU usage.

:(

---

### Post by kemorc on 2009-05-05
how much ram do you have set aside for your onboard graphics?

Jaunty appears to have an issue with something that hogs all the resources... I'd go back to 8.10 BUT my USB WNIC doesn't work in it.

---

### Post by Arup on 2009-05-05
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

This site carries the latest drivers for your site, adding the ppa lines to your repos would enable you to get the latest sis driver.

---

### Post by van_002 on 2009-05-05
sorry,  i did't understand that well.-  can you explain it a little more basic. 

(sorry , i'm pretty newbbie) :(

---

