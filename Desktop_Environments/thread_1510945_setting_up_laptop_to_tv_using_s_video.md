---
title: "setting up laptop to tv using s video"
date: 2010-06-16
forum: Desktop Environments
---

### Post by sup3rtax on 2010-06-16
hello,
complete newbie here.
I have the newest edition of ubuntu (10.4?) and on a dell inspiron 1525. I have purchased a s-video cable with a 7pin thing running from my laptop to yellow, white and red connectors to my tv. I'm really not sure what else i do to make it work because it does not show on my tv... 
From the posts i've read i know i need the appropriate video card so i typed lspci into terminal and got this... tho not sure what it means.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network control


Any help would be greatly appreciated!!!
Thanks

---

### Post by Sylos on 2010-06-16
Hello there.

Im not using 10.04 at the momnet so I cant give you the exact instructions but here is the general idea of it.

In order to run the TV out from the S-video you have to turn it on manually (essentially tell it to send a clone to the TV).

With my desktop I had to install the accelerated driver for my NVIDIA graphics card and then use the NVIDIA settings wizard to set up the second monitor.

To install the accelerated driver I think you go inot System>Restricted hardware or something similar and it will give you the option to turn on the accelerated graphics functions. Click yes and it should download the package.

Hope that helps.

The info from lspci you printed is all the pci connected bits and bobs you have. The second and trid lines appear to be your graphics card etc.

---

### Post by warfacegod on 2010-06-16
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

This could be a problem. As far as I know, there are no drivers for Intel that will show up in Hardware Drivers (Jockey). You'll probably need to get a driver for it from the Intel site. Frankly, I wish you luck. Intel drivers are simply atrocious and you may never get the TV to display properly.

---

### Post by Sylos on 2010-06-16
I was not aware of that. Sorry.

You could try and look in Synaptic and see a thing called *displayconfig-gtk* still exists and could be used. I dont think that required proprietary drivers.

---

### Post by sup3rtax on 2010-06-17
Thanks for your advice, seem like it will be to complicated for me to set up! think may have to buy windows :(

---

### Post by Brandel Valico on 2010-06-17
Lets try this. With everything set-up and plugged in to both the tv and the computer.

Goto System -> Prefrences -> Monitors -> Then try clicking the Detect Monitors button.

---

