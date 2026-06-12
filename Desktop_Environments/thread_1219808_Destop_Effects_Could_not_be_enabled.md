---
title: "Destop Effects Could not be enabled"
date: 2009-07-22
forum: Desktop Environments
---

### Post by aakar on 2009-07-22
I installed compiz on my ubuntu 8.10 , but it doesnt work ,.....when i go in System > Preference > Appearence and tried to click customize it says desktop effect could not be enabled....


in my terminal i tried to run compiz command and got the following output 

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity 


plz help me .......how to make my desktop get 3 D effects ....
for any help thnx in advance ..........

---

### Post by lotster on 2009-07-22
Just wondering; screen card.  Is your screen card able to handle 3D effects?  If it is, it may be necessary for you to enable proprietary drivers...  Those are the only two cases I've had so far of desktop effects not working.  It's usually activated by default...

---

### Post by bryonak on 2009-07-22
Could you open a terminal, enter ```
lspci
``` and paste the output here?
If you have a Nvidia or ATI graphics card, you have to install the drivers first by clicking on the "Restricted drivers" icon that should pop up in the tray.

---

### Post by aakar on 2009-07-22
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)

---

### Post by oldos2er on 2009-07-22
Have you checked System, Administration, Hardware Drivers to see if you can install proprietary video drivers?

---

### Post by aakar on 2009-07-22
i have installed the Proprietary driver which is listed by the Hardware Driver option, basically it listed two driver among which i installed the recomended driver

---

### Post by oldos2er on 2009-07-22
> **aakar said:**
> i have installed the Proprietary driver which is listed by the Hardware Driver option

 Have you rebooted since then?

---

### Post by aakar on 2009-07-22
yes ..... i have rebooted ....

---

