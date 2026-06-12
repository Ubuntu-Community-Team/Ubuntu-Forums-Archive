---
title: "Studio 15 Wireless Problems..."
date: 2008-09-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Synthetic_Anarchist on 2008-09-15
Hey I everyone,

I'm new to linux and just recently bought Dell's Studio 15 with Ubuntu preinstalled. The wireless worked fine upon first using it...but I wanted to try a few other distros and in the process I accidentally uninstalled ubuntu, anyways now after reinstalling Ubuntu the internet doesn't work - it didn't work on any of the other distros either. 

I've attempted to install other drivers with ndiswrapper but after I do, they say: **Hardware Present: No**

This is the read for the "lspci" command:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

This is the read out for lshw -C network command: 
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: 00:21:70:73:de:d9
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full ip=192.168.1.100 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s


Can anyone help me out?

P.S. I read somewhere on this site that the driver that used is for Studio 15 is this one [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)... but I don't know how to install that since it doesn't appear to have .inf file????

---

### Post by superm1 on 2008-09-15
I'll give you 3 options:

1)
Did you create a recovery DVD after you first booted it?  That DVD will have functional wireless.

2)
Other option is to install 8.04.1.  The gold 8.04 CD's don't support the Broadcom wireless.  The 8.04.1 ones do.

3)
Last option is to fully update an 8.04 install.  The wireless support is introduced later.

---

### Post by Bucky Ball on 2008-09-15
Try going to hardware drivers and making sure the Broadcom B43 Driver is checked and in use:

System->Admin->Hardware Drivers.

Oddly, you can sometimes bring it back to life by unchecking it, logging out, back in and check it again (it will reinstall itself and anything that might have gone missing).

---

### Post by superm1 on 2008-09-15
This machine is *NOT* supported by Broadcom B43.

---

### Post by Bucky Ball on 2008-09-15
> **superm1 said:**
> This machine is *NOT* supported by Broadcom B43.

Interesting superm. How does it get up? What a pity cos I got my Broadcom card up in about 5 minutes using B43-fwcutter and that hardware driver. Is the lack of support a Dell ´innovation´?

---

### Post by superm1 on 2008-09-15
> **Bucky Ball said:**
> Interesting superm. How does it get up? What a pity cos I got my Broadcom card up in about 5 minutes using B43-fwcutter and that hardware driver. Is the lack of support a Dell ´innovation´?
This is newer hardware that isn't supported by B43 as of yet.  Only a proprietary Broadcom driver is available to support it at this time.

---

### Post by sizemore101 on 2008-09-15
> **superm1 said:**
> I'll give you 3 options:

1)
Did you create a recovery DVD after you first booted it?  That DVD will have functional wireless.

2)
Other option is to install 8.04.1.  The gold 8.04 CD's don't support the Broadcom wireless.  The 8.04.1 ones do.

3)
Last option is to fully update an 8.04 install.  The wireless support is introduced later.

This worked, thanks. I reinstalled Ubuntu completely with an 8.04.1 live cd that I downloaded as opposed to the 8.04 that came with the computer and now after allowing the updates to go through wireless is working perfectly. Much appreciated.

---

### Post by Mehrban on 2008-11-23
> **superm1 said:**
> This is newer hardware that isn't supported by B43 as of yet.  Only a proprietary Broadcom driver is available to support it at this time.

suprem I need ur help please,
I have a 64 bit dell 1535 with broad com 4319 usb, I cannot install ndiswrapper, in hardware manager, I couldnt see any hardware recognized by ubuntu

---

### Post by Mehrban on 2008-11-23
need help 
dell 1535 w.l. bc4310,usb

---

### Post by superm1 on 2008-11-23
If you have a 4310 w/ Ubuntu 8.04, make sure you do ALL of your updates so that it shows up in HW manager.

If you have 8.10, you just need to make sure you update the package listings once and it will show up in HW manager.

---

### Post by Mehrban on 2008-11-24
> **superm1 said:**
> If you have a 4310 w/ Ubuntu 8.04, make sure you do ALL of your updates so that it shows up in HW manager.

If you have 8.10, you just need to make sure you update the package listings once and it will show up in HW manager.

Superm1 , I can not connect to internet , so how do I update?
I am using 8.04.1
in hardware it shows WL enabled but , in network manager there is nothing!!!. please help me I am novice to ubuntu

---

### Post by superm1 on 2008-11-24
If wl is enabled in HW manager, then just make sure your wifi switch is flipped "on"

---

### Post by Bucky Ball on 2008-11-24
> **Mehrban said:**
> Superm1 , I can not connect to internet , so how do I update?


Have you got an ethernet cable and a router to plug it into? Shutdown, plug up and reboot. That should work and make the job of getting wifi up a lot easier (and easier to post terminal output here). :)

---

