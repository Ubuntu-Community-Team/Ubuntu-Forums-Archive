---
title: "Question about Beryl"
date: 2007-03-30
forum: Desktop Effects &amp; Customization
---

### Post by Inkubas on 2007-03-30
I'd like to install Beryl as well as configure my Graphic Card. Here's the problem among many. I'm not quite sure as to what my graphic card is. Is there a command to let me know what I'm running and also is there a way to find out if you've configured your 3D graphics accelerator?

I've searched up my laptop but there are many models of the same one and I can't be sure as to what is my exact video card.

My laptop is a Hp Pavilion dv1000 Dual Centrino. I believe that the video card is at 180Mb.

Any help on finding out what kind of graphic card I've got and what company it runs under, or about how to install Beryl on my computer (if I can) would be greatly appreciated.


-Thanks

---

### Post by taurus on 2007-03-30
Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by Campingman on 2007-03-30
How about system/administration/device manager

---

### Post by Inkubas on 2007-03-30
Thank you both. Here are my specs

******************************************************************************************
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:08.0 Ethernet controller: Intel Corporation Intel(R) PRO/100 VE Network Connection (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
05:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

***************************************************************************************


Think I can Beryl with this configuration? Anyone willing to help a noob out? Deal with error after error, crappy scenarios, long hours wasted on basic commands, confusion, stress, headaches, idiotic remarks and questions, all for free?
If so, please, do post :). I can use all the help from being weened off windows.

:)

---

### Post by eentonig on 2007-03-30
I'm running i with the Intel card. So I don't think you'll have problems.

How much RAM do you have? And how fast is your CPU?

Anyway, I just installed Beryl (and related packages) via apt-get and started 

> beryl-manager

---

### Post by Inkubas on 2007-03-30
It's a dual centrino with each processor being at 1.6 Ghz (I believe) and I've got about 1 gig of RAM

---

