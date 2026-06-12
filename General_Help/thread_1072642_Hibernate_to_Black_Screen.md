---
title: "Hibernate to Black Screen"
date: 2009-02-17
forum: General Help
---

### Post by lvleph on 2009-02-17
I have seen posts about resuming from hibernate and getting a blank screen, but I don't even make it that far. I click hibernate and it just sits there with a black screen and a cursor. I can ctrl+alt+f# except ctrl+alt+f7 which does nothing. The other f options result in a login that does not allow me to type. Similarly for sleep, but the f options don't work at all.

lspci
```

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

```
I have the proprietary ATI drivers installed. My swap is 1GB and my ram is 2GB. Any ideas?

I also tried the [this](http://www.ubuntu-eee.com/wiki/index.php5?title=Fix:_hibernate)

---

### Post by lvleph on 2009-02-23
I have been doing some diagnosing. What I have discovered is that when I run s2disk I get the following error:
```

s2disk: Could not use the resume device (try swapon -a). Reason: No such device
```
But swapon -a does not fix the problem.

---

### Post by fjgaude on 2009-02-24
I would think that the swap space should be at least as large as the amount of RAM available, else...

---

### Post by lvleph on 2009-02-24
Yeah, I forgot to mention that I increased my swap to 2GB to be sure that was not the problem. Also, I have made some progress, but I am still stuck. I used
```
dpkg-reconfigure uswsusp
```
And then used
```
s2disk
```
Which resulted in a message telling me that it was created the image, but it seemed to just hang. Any ideas on how to fix that?

---

### Post by fjgaude on 2009-02-24
Sorry I have no knowledge of **s2disk**. How did you get it onto a Ubuntu system?

---

### Post by lvleph on 2009-02-24
sudo apt-get install uswsusp

---

### Post by fjgaude on 2009-02-24
Okay and thanks... doing a google I get this:

[http://ubuntuforums.org/archive/index.php/t-2260.h...%3C/t-478299.html](http://ubuntuforums.org/archive/index.php/t-2260.h...%3C/t-478299.html)

and this:

[http://ubuntuforums.org/archive/index.php/t-574583.html](http://ubuntuforums.org/archive/index.php/t-574583.html)

Any help?

---

### Post by lvleph on 2009-02-24
In the first link the OP states
> modified the kernel boot parameters to include acpi_sleep=s3_bios,s3_mode vga=0 and removed splash (in /boot/grub/menu.lst)
I have no idea how to do that. I suppose I will search a bit and see what I see.

---

### Post by fjgaude on 2009-02-24
Good luck!

---

### Post by cometa2k7 on 2009-02-25
I was always told to have my swap around 1.5x the size of my RAM. I have 2Gb of RAM, and so I use 3Gb of swap.

I would suggest that you increase the size of your swap to around 3Gb - you may need to do this using a live CD if you need to shrink another partition slightly.

---

### Post by jjpcexpert on 2009-02-25
if you use GParted Live, you can increase swap to 8 GiB and things will be all well AND your RAM won't get pooped.

---

### Post by lvleph on 2009-02-26
I upped to 3GB, but it didn't fix anything.

---

### Post by cometa2k7 on 2009-02-28
> **lvleph said:**
> I upped to 3GB, but it didn't fix anything.

Oh, I hoped that it would - my logic is that not having enough swap would mean that the RAM couldn't be copied completely, which may cause it to not work.

Anyway, I hope it'll be fixed, but I'm all out of suggestions.

---

### Post by lvleph on 2009-02-28
This pretty much sucks, because I am always needing to hibernate. It makes my work much easier that way.

---

### Post by fjgaude on 2009-02-28
My only suggestion would be to try other ATI video drivers and see if that works... ATI is somewhat late to the Linux game, thus most of us only use Nvidia.

---

### Post by lvleph on 2009-03-01
ATI use to produce linux drivers a while back but then stopped for some reason. I will look into a different driver. I am currently using the restricted driver that come with 8.10.

```
fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.8087 Release

```

---

