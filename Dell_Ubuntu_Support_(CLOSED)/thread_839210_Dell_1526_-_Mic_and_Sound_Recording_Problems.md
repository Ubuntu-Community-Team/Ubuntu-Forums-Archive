---
title: "Dell 1526 - Mic and Sound Recording Problems"
date: 2008-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nitindb on 2008-06-24
Hi, I've recently purchased a Dell Inspiron 1526 PC and have managed to get almost everything working fine with an Ubuntu 8.04 installation.  There is however a problem with sound recording that need help with.  The output from the speakers are fine......and headphone output is also fine.......but the recorded sound from the mix is a messy, hissing kind of sound.  

I have attached the results of lshw with this post and the below is the result from lspci:-

00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

---

### Post by nitindb on 2008-06-25
If there is anyone out there that can help with this, do have a go!  I've got everything else configured......just the mic and sound recording issue thats causing problems.

Any help would be much appreciated.

---

### Post by halln on 2008-07-05
try this link: [http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

---

### Post by nitindb on 2008-07-10
Hi,
After some searching I was able to get the laptop's inbuilt mic working.  I modified the etc/modprobe.d/alsa-base file by adding the following line at the end of the file and then rebooting the system:- 
options snd-hda-intel model=dell-3stack

I got this information by visiting the following thread:-
[http://ubuntuforums.org/archive/index.php/t-616845.html](http://ubuntuforums.org/archive/index.php/t-616845.html)

The only problem is that I can't get an external mic to work with the front mic jack.  Any solutions for this?

---

### Post by pistoncito on 2008-07-11
Hi, i have the 1526 notebook, with the same audio cards, but i couldn't make the internal mic works, did you make some other thing that add this final line to alsa-base conf?

Al other audio works fine.

Thanks

---

