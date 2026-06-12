---
title: "Can GNOME 3 be installed on Ubuntu 8.04?"
date: 2012-09-11
forum: Desktop Environments
---

### Post by Sopdu on 2012-09-11
Hi all,

I have a Gateway Lt31 netbook which has an ATI Radeon X1270 graphics chip set. In any case ATI (AMD) has stopped supporting these GPUs (and the open source drivers only support 2d and give weird artifacts in the graphics) and therefore I am stuck with Ubuntu 8.04. I was wondering if it is possible to install the newest incarnation of GNOME on this distro without updating xserver above version 1.5. If so, can anyone recommend a good tutorial on how to do this?

Thanks in advance.

---

### Post by youngunix on 2012-09-11
I have a Gateway T-1628 with the same graphics card, it still works like a charm. However, don't expect much from such card. I'd really recommend an Ubuntu derivative called ([WattOS]("http://www.planetwatt.com/pages/downloads")) it has the Openbox windows manager, and it's meant for very old hardware but I am very impressed with it. It is customizable to an extent, very fast and responsive on an 11yr old computer. Plus, you'll get the latest Precise 12.04 LTS build.

---

### Post by Sopdu on 2012-09-12
Youngunix, thanks for your response. I have considered installing a lighter distro; however this does not solve my fundamental problem. I want to have 3d capability, which only the ATI drivers can achieve for my graphics chip set, and I really like some of the new features of the GNOME 3 desktop environment. So in essence I am wondering if GNOME 3 can be installed without updating xserver past v. 1.5?

Let me add to my question. If GNOME 3 is out of the question is there any way to install Mint's GNOME-2 shell extension on Hardy Heron?

---

### Post by coffeecat on 2012-09-12
> **Sopdu said:**
> 
(and the open source drivers only support 2d and give weird artifacts in the graphics) and therefore I am stuck with Ubuntu 8.04.

Is this your experience with 8.04 or have you tried anything later than 8.04? The version of the open source ati driver that comes with the current version of Ubuntu is much more capable than the one that came with 8.04, although whether it is better with your GPU I don't know. Have you tried 12.04 on that machine? A google hit says that you have 2 GB RAM with that machine, so that's plenty. If you don't want the complication of compiz that is needed for the Unity desktop, you could have a look at [gnome shell remix]("http://ubuntu-gs-remix.sourceforge.net/p/home/"). The 12.10 version is also in development - [thread here]("http://ubuntuforums.org/showthread.php?t=2052509"). You could try running either standard Ubuntu 12.04 or Gnome Shell Remix from a live CD. You might be pleasantly surprised, or you might be disappointed. Either way, you would find out whether it is possible to run gnome 3 on that machine. 8.04 is obsolete and unmaintained and the liklihood of someone having compiled gnome 3 for 8.04 is remote, I would think.

Whatever you do, 8.04 is well past end-of-life and no longer gets security updates.

---

### Post by Bucky Ball on 2012-09-12
Xubuntu 12.04 LTS, then install whatever desktop environment works for you. Done. (Or do a minimal install and add the DE on the way.) 

8.04 LTS is not supported and hasn't been for over a year. Although that may not bother you because everything 'just works' this also means there are no security updates, either. If you are online with this machine that is a bad thing. You are also using very dated versions of software, which may also not bother you. 

10.04 LTS is also current and supported til April 2013. Easy, couple of click upgrade through update manager.

---

### Post by Sopdu on 2012-09-12
The artifacts occur in all Ubuntu/Fedora/Mint/Xubuntu/etc. distros that I have tried (I have installed newer versions of each) that do not support the 3rd party ATI graphics drivers. My research has shown that these drivers are only compatible with distros which run xserver below version 1.5. With the newer distros the graphics artifacts and text distortions occur when using both 2d and 3d acceleration.

I understand that there are some major security risks to running unsupported Ubuntu but it is better to have security risks than a secure netbook that is not usable with the (factory loaded) Windows Vista or a current version of Linux.

The problem is NOT that the 12.04 is too heavy for the machine, but that the open source GPU drivers provided by Linux really suck at both 2d and 3d acceleration.

Ultimately, does anyone know of any (good) still-supported distros that are compatible with the ATI legacy GPU drivers?

---

### Post by Sopdu on 2012-09-12
Here is a post where I included a screen shot of the graphical errors that the open source GPU divers give me in Ubuntu 11.0.4.
[URL="http://ubuntuforums.org/showthread.php?p=11276337#post11276337"]
http://ubuntuforums.org/showthread.php?p=11276337#post11276337[/URL]

---

### Post by Sopdu on 2012-09-12
Let me add this information:

> ATI/AMD dropped Catalyst support for these cards in Catalyst 9-4. These  cards are supported with the legacy ATI 9-3 Catalyst release, but you  MUST use a kernel <= 2.6.28 and Xserver <= 1.5

---

