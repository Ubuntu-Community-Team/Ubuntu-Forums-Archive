---
title: "Suspend/Hibernate - Jaunty trouble"
date: 2009-05-16
forum: General Help
---

### Post by ConnorIRL on 2009-05-16
How do I get these two to work?  Every time I try it, it just goes to a black screen and locks itself up, and I have to restart my laptop.  It's annoying because when I was on Windows, that was one of the things I loved, that I was able to turn it on and off quick without waiting for it to boot up again.

Thanks! :)

---

### Post by ConnorIRL on 2009-05-16
Can anybody save me? :)

---

### Post by ConnorIRL on 2009-05-18
A bunch of views but no replies, hopefully that doesn't mean there is no hope!

---

### Post by Falcon1002 on 2009-05-18
What video card do you have?
What laptop do you have?
I had a similar problem, not quite the same but similar, that was do to the graphics card driver.

---

### Post by ConnorIRL on 2009-05-18
> lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Device 7914
00:05.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1)
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


I don't even know where to start looking.  I have a Toshiba Satellite laptop.

---

### Post by Falcon1002 on 2009-05-18
It appears to me that you have a card that is similar to mine. (I looked at this line)> 01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series] 
I had to install the driver for my card from here -->[http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx"). Doing that solved the problems I had on 8.10 (I do not use 9.04 because of graphics problems). I don't know if this will fix your problem but it might solve it. 
Also are you new to Ubuntu with 9.04 or did you use an earlier version? Hope I can be of some help.:D

---

