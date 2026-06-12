---
title: "Laggy windows and out of sync players"
date: 2011-10-04
forum: Desktop Environments
---

### Post by chrgjen on 2011-10-04
Hey guys.

I have been using ubuntu for a short time on my machine and i want to keep using ubuntu but due to grafics lagging it makes the experience of using a fast system fall flat. The windows are lagging when i drag them around and all the player i have tryed are out of sync. I dont know if this problem is supposed to be in a different category. Is this a common problem?

---

### Post by ajgreeny on 2011-10-04
This sounds like a graphics card driver problem.  What hardware do you have?

Show the output of ```
lspci
``` and ```
sudo lshw -c display
``` in terminal.

---

### Post by chrgjen on 2011-10-04
I had a feeling it had something to do with the grafics card. When i tried disabling the recommended driver the windows ran smooth again, didn't test the players though. Oh, and also, the mouse freezes sometimes for about two or three seconds. I think this is related to the lagging of the grafics also.  I hope you can help.

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV730 PRO [Radeon HD 4650]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

*-display               
       description: VGA compatible controller
       product: RV730 PRO [Radeon HD 4650]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:46 memory:d0000000-dfffffff memory:fdde0000-fddeffff ioport:ce00(size=256) memory:fdd00000-fdd1ffff

---

