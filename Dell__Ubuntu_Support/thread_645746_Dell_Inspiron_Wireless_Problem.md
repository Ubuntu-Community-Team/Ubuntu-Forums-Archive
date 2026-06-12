---
title: "Dell Inspiron Wireless Problem"
date: 2007-12-20
forum: Dell  Ubuntu Support
---

### Post by ipatec on 2007-12-20
I've just installed Ubuntu Studio 7.10 on my Dell Inspiron 6400 laptop.
The problem is that when I press Fn + F2 to activate my wifi card nothing happens... the led is closed...
Any advice?

---

### Post by tdeboeser on 2007-12-20
You may need to run the ipwd daemon.  i.e. on my system the actual name of the command is 'ipw3945d-2.6.22-14-386'.  

To run as root ' sudo ipw3945d-2.6.22-14-386'.  

Ez way to see if what yours is, open a terminal start to type ' sudo ipw<*then hit TAB>*'.  If you have it, it'll finish the line for you.


Tom de

---

### Post by reckless2k2 on 2007-12-20
sorry we would need a little more info about your wireless card.

Go to the restricted driver menu and make sure that you don't need an additional install. you're wifi switch should be on/enabled at boot so make sure you boot with the switch powered on. 

try those things....then if you still can not get wireless via the network connections menu, get to a terminal window and post the results of this:

```
lspci -vv
```

---

### Post by ipatec on 2007-12-20
Here are some results:
ipatec@ipatec:~$ sudo ipw3945d-2.6.22-14-rt 
[sudo] password for ipatec:
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2007-12-20 20:33:14: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
ipatec@ipatec:~$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: efd00000-efefffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Memory behind bridge: efc00000-efcfffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=0c, subordinate=0d, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: efa00000-efbfffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000e01fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01bd
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 18
        Region 4: I/O ports at bf80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01bd
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 4: I/O ports at bf60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01bd
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 20
        Region 4: I/O ports at bf40 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01bd
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 21
        Region 4: I/O ports at bf20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at ffa80000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: ef900000-ef9fffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
        Subsystem: Dell Unknown device 01bd
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 80 [Master])
        Subsystem: Dell Unknown device 01bd
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 22
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at bfa0 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
        Subsystem: Dell Unknown device 01bd
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 5
        Region 4: I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400 (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 2003
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Region 1: I/O ports at ee00 [size=256]
        Region 2: Memory at efdf0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at efd00000 [disabled] [size=128K]
        Capabilities: <access denied>

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Inspiron 6400
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at ef9fe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (500ns min, 1000ns max)
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at ef9fd800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19) (prog-if 01)
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64
        Interrupt: pin B routed to IRQ 23
        Region 0: Memory at ef9fd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 9
        Region 0: Memory at ef9fd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 9
        Region 0: Memory at ef9fd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Dell Unknown device 01bd
        Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 9
        Region 0: Memory at ef9fd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
        Subsystem: Dell Unknown device 0007
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at efcfc000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by reckless2k2 on 2007-12-20
as i thought, you have the good ole broadcom device that always causes issues:

Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

there is the broadcom driver but i'm not sure if that works with 943xx. otherwise you are going to need ndiswrapper. it's not a terribly hard procedure to get going but it does require using the terminal for about 5 minutes and then you will be fine after that. 

post a thread on BCM94311MCG help. then it can be addressed there. i'll research on the driver while you do that and more than likely someone has posted already about it or myself or another will get right to you.

---

### Post by reckless2k2 on 2007-12-20
did you try the restricted drivers install i suggested?

---

### Post by reckless2k2 on 2007-12-20
[http://ohioloco.ubuntuforums.org/showthread.php?p=3975998](http://ohioloco.ubuntuforums.org/showthread.php?p=3975998)

let me know but that should help.

---

### Post by ipatec on 2007-12-20
Yes and it doens't worked. The problem was from Ubuntu Studio... because on Gutsy or Vista it works well...
Thanks for help!

---

### Post by reckless2k2 on 2007-12-20
the you will need the straight ndiswrapper setup. let me research and i'll hook it up for ya.

---

### Post by reckless2k2 on 2007-12-20
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

it's item 39 on that page. you will need cabextract installed to extract it. 

you can follow the guide i've put out there before but just place your driver(s). 

[http://ubuntuforums.org/showthread.php?t=611079&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=611079&highlight=ndiswrapper)

make sure you undue the restricted drivers bit first.

****i remember something...there's a bit about blacklisting a bad broadcom driver in order for the fwcutter to work. have you read that? you might want to check that first and or may still need to blacklist the bad driver built into the kernel.****

---

### Post by ipatec on 2007-12-20
Thanks a lot but I've installed Gutsy and anything it's ok now.
I don't know what happened with Ubuntu Studio, because wireless problem was not the only one. I was unable to install other packages... because it was giving me a lot of errors...
Hope that Ubuntu Studio 8.04 will be better.

---

### Post by reckless2k2 on 2007-12-20
i ran into a lot of problem trying to install mythbuntu very much the same way. i just installed the base ubuntu and then added packages i needed rather than the direct offshoots. i'm sure 8.04 will be better though. with the LTS moniker and all.

---

### Post by Lorac1949 on 2007-12-20
> **reckless2k2 said:**
> as i thought, you have the good ole broadcom device that always causes issues:

Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

there is the broadcom driver but i'm not sure if that works with 943xx. otherwise you are going to need ndiswrapper. it's not a terribly hard procedure to get going but it does require using the terminal for about 5 minutes and then you will be fine after that. 

post a thread on BCM94311MCG help. then it can be addressed there. i'll research on the driver while you do that and more than likely someone has posted already about it or myself or another will get right to you.

I had the same issue with the bcm43xx in my Dell Inspiron 1520.  Check out the first post in this thread.  It did the trick for me:

[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

