---
title: "New ATI Driver"
date: 2011-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Timsworth on 2011-02-26
Hi guys.  I've been using Ubuntu as my main OS for a good 3 months or so by now, so I'm still learning all that I can.

I was trying to get wine to run my Steam games properly earlier and decided to download an official ATI driver for my Mobility Radeon HD 5000 series.  It installed fine, but now there are a lot of graphical 'glitches' on my desktop in the form of AWN having a white box all around it, and none of the Compiz effects working.  I've been trying to roll back my driver to the one provided by the 'Additional Drivers' tool: 'ATI/AMD proprietary FGLRX graphics driver' but whenever I try to activate it, it says 'SystemError: installArchives() failed'.

I've looked online a bit, but nothing has helped.  Reconfiguring my x server (or something along those lines) didn't work.  I assume I need to uninstall this driver that I've installed manually and then reinstall the older one through the additional drivers menu, but can't find anything helping me out.

Edit: The driver I installed was the Catalyst 11.2 and I didn't uninstall or remove my previous driver because I'm a n00b.  Could this be a problem?

Here's a lspci dump(is it helps): 
> 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
07:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
07:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
07:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
07:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

Cheers.

---

### Post by Timsworth on 2011-02-27
Okay, I managed to fix it by just installing the previous driver.  There's a new 'problem' now, though.  I just want to know; each time I install a new driver without uninstalling the previous one (I physically couldn't do it for some reason), are files just piling up on top of each other, or are the files that are no longer being used being deleted?  My HDD space seems to have gone down since installing twice.

---

