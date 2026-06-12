---
title: "Sound Card Help!"
date: 2005-07-09
forum: Desktop Environments
---

### Post by holycow on 2005-07-09
After reading and trying the sound card guides in these forums, I am still soundless...

Here's the output I have...
holycow@dell:/dev $ lspci
0000:00:00.0 Host bridge: Intel Corp. Server Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. Server Memory Controller Hub PCI Express Port (rev 04)
0000:00:02.0 Display controller: Intel Corp. Graphics Controller (rev 04)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:04:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)
0000:04:01.0 Multimedia audio controller: VLSI Technology Inc Thunderbird (rev 06)
0000:04:01.1 Input device controller: VLSI Technology Inc Thunderbird
0000:04:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
 ](*,)                                                                      

Any help is greatly appreciated.
-holycow-

---

### Post by scoon on 2005-07-14
Hey there, 

[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-VLSI#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-VLSI#matrix)

Doesn't appear that your chips are supported. 

regards, 

scoon

---

