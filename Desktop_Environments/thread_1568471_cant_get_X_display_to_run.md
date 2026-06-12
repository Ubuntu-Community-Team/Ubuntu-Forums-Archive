---
title: "cant get X display to run"
date: 2010-09-05
forum: Desktop Environments
---

### Post by pdc124 on 2010-09-05
im resurrecting an old laptop that ran gentoo +KDE3.5 perfectly well for several years. 
Ive tried to install from the live CDs meerkat ( no graphic display) and then lucid. Graphic screen but no mouse pointer. 

The alternative installation is OK , but when I reboot, I get a splash screen, but then a black screen . the only option is then to switch off. 

The only version of ubuntu that ive been able to install  and then have access to is the server. 
Ive tried adding xcfe + gdm , which both install but on rebooting the same thing happens -  no X display and I need to switch off. 

this is the video hardware 
> 

00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 1712
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Region 1: Memory at fea80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

FWIW the rest of it 

> gravity@gravity:/etc/X11/xdm$ lspci 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
01:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
gravity@gravity:/etc/X11/xdm$ 


Ive looked in the log files ( dont seem to be generating an Xorg.log ) and can find nothing relating to X 


where to next ?

---

