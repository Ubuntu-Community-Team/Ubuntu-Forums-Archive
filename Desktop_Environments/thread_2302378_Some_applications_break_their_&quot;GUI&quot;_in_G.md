---
title: "Some applications break their &quot;GUI&quot; in GNOME"
date: 2015-11-09
forum: Desktop Environments
---

### Post by thejhonjhon123 on 2015-11-09
Hi,

I use Ubuntu 14.04.3 x64 Bits, GNOME Shell 3.10.4


I have a recurring problem when using some applications long. and that his GUI breaks without giving any apparent error.


specifically, when use skype (Canonical repositories) and StarUML. When it breaks one breaks the other simultaneously, and to close and open more applications, they remain broken.


The only solution is to restart the computer, and of course, after a while they break applications.


All other applications run without any problem.


Attached some pictures where the problem is.


can you help me? Thank you.

---

### Post by ajgreeny on 2015-11-10
I have very little knowledge of gnome any more but the problem looks to be a graphic driver problem.

What graphic card do you have and which driver is used?  Show the output of terminal commands```
lspci
sudo lshw -C display
``` one by one.

---

### Post by thejhonjhon123 on 2015-11-10
```

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 9 Series Chipset Family USB xHCI Controller
00:16.0 Communication controller: Intel Corporation 9 Series Chipset Family ME Interface #1
00:1a.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0)
00:1c.2 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 3 (rev d0)
00:1c.3 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 4 (rev d0)
00:1d.0 USB controller: Intel Corporation 9 Series Chipset Family USB EHCI Controller #1
00:1f.0 ISA bridge: Intel Corporation 9 Series Chipset Family Z97 LPC Controller
00:1f.2 SATA controller: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode]
00:1f.3 SMBus: Intel Corporation 9 Series Chipset Family SMBus Controller
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cayman PRO [Radeon HD 6950]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cayman/Antilles HDMI Audio [Radeon HD 6900 Series]
03:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 10)
04:00.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 41)



  *-display               
       descripción: VGA compatible controller
       producto: Cayman PRO [Radeon HD 6950]
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: 00
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi vga_controller bus_master cap_list rom
       configuración: driver=fglrx_pci latency=0
       recursos: irq:51 memoria:e0000000-efffffff memoria:f7e20000-f7e3ffff ioport:e000(size=256) memoria:f7e00000-f7e1ffff


```

---

