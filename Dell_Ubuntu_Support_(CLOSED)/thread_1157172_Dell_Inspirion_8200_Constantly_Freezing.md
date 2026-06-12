---
title: "Dell Inspirion 8200 Constantly Freezing"
date: 2009-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by italianoman421 on 2009-05-12
I posted this earlier, but I think it was the wrong sub-forum.I have a dell Inspiration 8200 running 9.04 that is constantly freezing. I have cleaned the computer of dust using the compressed air cans you can buy. So at this point I have only a limited idea about why it could be freezing. One possibility is that the fans do not seem to be running very often but when I went to download a driver to increase their run time the computer froze within five minutes of turning it on, so I do not think over heating could be a problem.

This is the computer info that popped up after hitting command ~ lshw

description: Computer
width: 32 bits
*-core
description: Motherboard
physical id: 0
*-memory
description: System memory
physical id: 1
size: 383MiB
*-cpu
product: Mobile Intel(R) Pentium(R) 4 - M CPU 1.70GHz
vendor: Intel Corp.
physical id: 2
bus info: cpu@0
version: 15.2.7
size: 1200MHz
capacity: 1200MHz
width: 32 bits
capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid cpufreq
configuration: id=0
*-cache:0
description: L1 cache
physical id: 0
size: 8KiB
*-cache:1
description: L2 cache
physical id: 1
size: 512KiB
*-pci
description: Host bridge
product: 82845 845 [Brookdale] Chipset Host Bridge
vendor: Intel Corporation
physical id: 100
bus info: pci@0000:00:00.0
version: 04
width: 32 bits
clock: 33MHz
configuration: driver=agpgart-intel module=intel_agp
*-pci:0
description: PCI bridge
product: 82845 845 [Brookdale] Chipset AGP Bridge
vendor: Intel Corporation
physical id: 1
bus info: pci@0000:00:01.0
version: 04
width: 32 bits
clock: 66MHz
capabilities: pci bus_master
*-display
description: VGA compatible controller
product: NV11 [GeForce2 Go]
vendor: nVidia Corporation
physical id: 0
bus info: pci@0000:01:00.0
version: b2
width: 32 bits
clock: 66MHz
capabilities: bus_master vga_palette cap_list
configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
*-usb:0
description: USB Controller
product: 82801CA/CAM USB Controller #1
vendor: Intel Corporation
physical id: 1d
bus info: pci@0000:00:1d.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-usb:1
description: USB Controller
product: 82801CA/CAM USB Controller #3
vendor: Intel Corporation
physical id: 1d.2
bus info: pci@0000:00:1d.2
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=uhci_hcd latency=0 module=uhci_hcd
*-pci:1
description: PCI bridge
product: 82801 Mobile PCI Bridge
vendor: Intel Corporation
physical id: 1e
bus info: pci@0000:00:1e.0
version: 42
width: 32 bits
clock: 33MHz
capabilities: pci bus_master
*-network
description: Ethernet interface
product: 3c905C-TX/TX-M [Tornado]
vendor: 3Com Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 78
serial: 00:08:74:3e:5f:2f
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=3c59x ip=192.168.0.5 latency=32 maxlatency=10 mingnt=10 module=3c59x multicast=yes
*-pcmcia:0
description: CardBus bridge
product: PCI4451 PC card Cardbus Controller
vendor: Texas Instruments
physical id: 1
bus info: pci@0000:02:01.0
version: 00
width: 32 bits
clock: 33MHz
capabilities: pcmcia bus_master cap_list
configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
*-pcmcia:1
description: CardBus bridge
product: PCI4451 PC card Cardbus Controller
vendor: Texas Instruments
physical id: 1.1
bus info: pci@0000:02:01.1
version: 00
width: 32 bits
clock: 33MHz
capabilities: pcmcia bus_master cap_list
configuration: driver=yenta_cardbus latency=176 maxlatency=5 module=yenta_socket
*-firewire
description: FireWire (IEEE 1394)
product: PCI4451 IEEE-1394 Controller
vendor: Texas Instruments
physical id: 1.2
bus info: pci@0000:02:01.2
version: 00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: driver=ohci1394 latency=32 maxlatency=4 mingnt=2 module=ohci1394
*-isa
description: ISA bridge
product: 82801CAM ISA Bridge (LPC)
vendor: Intel Corporation
physical id: 1f
bus info: pci@0000:00:1f.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: isa bus_master
configuration: latency=0
*-ide
description: IDE interface
product: 82801CAM IDE U100 Controller
vendor: Intel Corporation
physical id: 1f.1
bus info: pci@0000:00:1f.1
version: 02
width: 32 bits
clock: 33MHz
capabilities: ide bus_master
configuration: driver=ata_piix latency=0
*-multimedia
description: Multimedia audio controller
product: 82801CA/CAM AC'97 Audio Controller
vendor: Intel Corporation
physical id: 1f.5
bus info: pci@0000:00:1f.5
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=Intel ICH latency=0 module=snd_intel8x0
*-communication UNCLAIMED
description: Modem
product: 82801CA/CAM AC'97 Modem Controller
vendor: Intel Corporation
physical id: 1f.6
bus info: pci@0000:00:1f.6
version: 02
width: 32 bits
clock: 33MHz
configuration: latency=0
*-network
description: Wireless interface
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:07:00.0
logical name: wmaster0
version: 20
serial: 00:09:5b:8a:79:82
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=rtl8180 ip=192.168.0.126 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11b
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 0e:15:42:df:c5:1f
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
dominick@dominick-laptop:~$

---

### Post by coffeeaddict22 on 2009-05-13
The system dumps information of all sorts in a few files.  Start by trying ```
dmesg
``` just after a crash and scroll back up until you find the problem messages.  They're also accessible by System/Admin/Log File Messages, or by looking through the files at /var/log/ -open a terminal, ```
cd /var/log/ 
ls
``` ; however theres a few files there and you'll want some idea of what might be causing it before you start ferreting through it all.  Are you doing anything when it happens?  If you're not 100% sure it's not a heat issue, have you tried monitoring with a gnome applet?  Have a look in synaptic for hardware- there's 3 or 4 options.

---

