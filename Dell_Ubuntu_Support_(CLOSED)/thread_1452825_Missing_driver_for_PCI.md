---
title: "Missing driver for PCI ?"
date: 2010-04-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by foobar66 on 2010-04-12
Hi, I have a Dell Studio 1737 with Ubuntu installed.

When I type "lspci -k", I can see that there is one PCI device which does not have a driver.

The device is on 00:1e.0 bus address (00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)).

Does anyone know what this device is/does?
Is there a driver for it available in the linux kernel (2.6.32) and what option do I need to select in the driver config to enable it? (I am running a custom built kernel).

The result is shown below:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
    Kernel driver in use: pcieport
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
    Kernel driver in use: pcieport
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
    Kernel driver in use: pcieport
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
    Kernel driver in use: radeon
    Kernel modules: radeon
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Kernel driver in use: iwlagn
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
    Kernel driver in use: tg3
    Kernel modules: tg3

---

### Post by cascade9 on 2010-04-12
Its a PCI to PCI bridge. 

I could try to explain it, but this is probably eaiser- 

[http://arstechnica.com/old/content/2004/07/pcie.ars/3](http://arstechnica.com/old/content/2004/07/pcie.ars/3)

You dont need drivers for it, or do anything to enable it. ;)

---

