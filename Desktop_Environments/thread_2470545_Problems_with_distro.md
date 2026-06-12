---
title: "Problems with distro"
date: 2022-01-03
forum: Desktop Environments
---

### Post by ggomes-29 on 2022-01-03
Hello everyone, everything good?
I'm new to the Linux environment and although I'm not new to the tech world, I'm having some issues in my environment.
I confess that my PC is old and with very old features, but I didn't face problems (apart from the slowness) in the Windows environment. When I migrated to Linux and the Lubuntu and Xubuntu distribution, I had problems ranging from slowdowns to crashes when opening a simple remote access program like TeamViewer.
I'm 100% sure the problem is the video card, but when I try to update, the system says there are no drivers available.
I don't want to go back to Windows, but I can't find a distro that makes it completely stable. I don't overuse the system, wanted some help on how to update the video drivers without breaking the rest of the system.

The machine settings are:
Gigabyte GA-M61PM-S2 (rev. 1.0)
CPU
1. AMD Athlon™ 64 X2 Dual-Core 4200


onboard video card
1. NVIDIA® GeForce 6100 / nForce 430


Memory
4G DDR2 DIMM


        HD
              250 GB

---

### Post by KBar on 2022-01-03
Hello and welcome to the forum!

How exactly did you try updating them?

Purge the current drivers and run the following:
```
sudo ubuntu-drivers autoinstall
```

It will do what it literally is called.

---

### Post by yancek on 2022-01-03
Which release of windows were or are you using?  Also, which Lubuntu/Xubuntu?  Are the Lubuntu/Xubuntu version(s) you have still supported?Are you trying to open a remote application FROM Lubuntu/Xubuntu on another system or the reverse?

---

### Post by guiverc on 2022-01-03
The easiest way to *update* 'drivers' is to switch to the HWE kernel stack if you're using a LTS release and using the GA stack.   As *drivers* are actually kernel modules; switching to the newer stack achieves that goal the easiest way.  But you didn't provide any specifics or release details.

`ubuntu-drivers` is really good at adding closed-source proprietary drivers as was already mentioned; but the initial question is devoid of specifics required to understand the issue; ie. we don't know what OS & release you're using; you mention Lubuntu & Xubuntu but not how they relate - nor most importantly release (*and if LTS which kernel stack was chosen; for Lubuntu & Xubuntu that's decided by the ISO used to install*)

---

### Post by grahammechanical on 2022-01-03
From time to time Nvidia drop support for their older video cards. To find out what proprietary drivers are available by using the terminal type this command:

```
ubuntu-drivers list
```

We need to be connected to the internet for that command to work. If there is no response it could mean that the Nvidia driver is not available. Also, this command:

```
ubuntu-drivers -h
```

gives this reply

> autoinstall  Deprecated, please use "install" instead

If this problem is really caused by the video driver then I suggest using the open source video driver. Which for Nvidia cards is called Nouveau. Nvidia do offer a driver but it will have to be installed using the command line. This driver used to be available for my machine but Ubuntu no longer makes it available. So, I have no idea how useful it is or how safe it is.

[https://www.nvidia.com/en-us/drivers/results/114714/](https://www.nvidia.com/en-us/drivers/results/114714/)

Regards

---

### Post by KBar on 2022-01-03
While it is true that the **autoinstall** command is deprecated, it's self-explanatory and clears up a lot of confusion.

In general, when giving out suggestions, I try to avoid short and ambiguous options in favor of GNU long options (aka mnemonic style).

---

### Post by mIk3_08 on 2022-01-04
> **ggomes-29 said:**
> Hello everyone, everything good?
I'm new to the Linux environment and although I'm not new to the tech world, I'm having some issues in my environment.
I confess that my PC is old and with very old features, but I didn't face problems (apart from the slowness) in the Windows environment. When I migrated to Linux and the Lubuntu and Xubuntu distribution, I had problems ranging from slowdowns to crashes when opening a simple remote access program like TeamViewer.
I'm 100% sure the problem is the video card, but when I try to update, the system says there are no drivers available.
I don't want to go back to Windows, but I can't find a distro that makes it completely stable. I don't overuse the system, wanted some help on how to update the video drivers without breaking the rest of the system.

The machine settings are:
Gigabyte GA-M61PM-S2 (rev. 1.0)
CPU
1. AMD Athlon™ 64 X2 Dual-Core 4200


onboard video card
1. NVIDIA® GeForce 6100 / nForce 430


Memory
4G DDR2 DIMM


        HD
              250 GB

Can you run this command below in your terminal and show us the result here in thread wrap with code. Thanks a lot. 
```
hostnamectl status
```
Cheers

---

### Post by TheFu on 2022-01-04
There are 2 types of GPU drivers in LInux.

The F/LOSS driver which needs to be used with really old cards
and 
the proprietary driver which **may** be used when the vendor provides a supported driver for the kernel being run.

Typically, the proprietary driver will end support (blame nvidia) in 5-10 yrs) and will provide most resolution access that the GPU was advertised to provide.
The F/LOSS driver, named Nouveau [https://nouveau.freedesktop.org/](https://nouveau.freedesktop.org/) , when used with old hardware it may be limited to 800x600 resolutions. That's been my experience with a GeForce 7200 GT.  Support was dropped pre-4.15 kernel, so when 16.04 move to a newer kernel, that card was unsupported.  The Nouveau driver was terrible for that card, so $70 and a GT 1030 fixed that issue.  I really don't care about GPUs and would have been happy with any driver that supported the 1920x1200 resolution of my old monitor. The nvidia drivers for the 7200 did, so when the Nouveau driver didn't, I was a little unhappy. 

Don't get the driver from the vendor, unless it is your last effort to get a working system. Use the drivers provided through the Package Manager you use or through the ubuntu-drivers tool.  You can check the linux support for your GPU on nvidia's website - that for reading only, not downloading a driver.

BTW, AMD drivers seem to have a much longer support period. AMD releases their code, so reverse engineering and praying aren't required.  Intel GPUs/iGPU support has a long history of just working on Linux with a few exceptions.  I've never been hit by intel iGPU driver support issues that weren't expected.  An old N270 iGPU did suck - no mpeg2 or h.264 decoding support in the hardware, so video watching was limited to about 800p resolutions on that Asus Eee. My fix for that was to get the cheapest chromebook I could, which had a celeron with iGPU that had hardware and driver support for both mpeg2 and h.264 decoding. That was 2011. I think every new GPU sold since then included support for both those video codecs.

Beware that Unix/Linux is very different from other non-Unix OSes. Even when things appear to be similar, often they are not. To get the most from Unix systems, a different way of thinking is very helpful. It is easy to become frustrated when prior knowledge/skills don't transfer.  I tried out a MacOS system about 10 yrs ago.  Had to return it after 2 weeks due to massive frustration and my improper expectations that MacOS was based on BSD, which is very much like Unix. Alas, Apple had to rename all the well-known protocols so they could copyright/trademark the names - I needed a secret decoder ring for the Apple -to- standard name conversion.  A few things worked exactly the same as my Unix experience thought, but all the GUI stuff was just so very different.  Windows is even more frustrating after 25 yrs on Unix workstations.  It isn't fair when I expect Windows to work like Unix does. Call it human nature to be frustrated.  I've been using Windows since 1989, but still get frustrated when things that are very easy on Unix aren't possible on Windows.

---

