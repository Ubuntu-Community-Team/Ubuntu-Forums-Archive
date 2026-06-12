---
title: "Ok this is just crazy"
date: 2005-10-13
forum: Desktop Environments
---

### Post by OpposingForce on 2005-10-13
First ubuntu didnt detect my network card right off the bat on installation, then I went into system --> administration --> networking then everything loaded fine..I saw the wireless connection but it wasnt set up yet so I clicked properties and then it froze and I had to force quit...after that I tried to open up Openoffice programs but all they did was say "Starting openoffice" in the toolbar at the bottom then disapeared not starting, same thing happened with the networking configuration utility when I tried to start that again...before the networking lockup, openoffice programs started up fine and I had no problems..

the other weird thing is that after the networking configuration tool lockup, openoffice seemed to be the only program that wouldnt start, GIMP started, all the gnome games started, firefox started (although with no internet usage because I cant set up my wireless connection due to this bug so Im typing it from windows).

Any ideas on how to fix this bug? I feel much closer to getting that wireless connection working in ubuntu than I did with hoary 5.04 but with this bug...it appears that my progress has been brought to a screeching halt...someone please help

---

### Post by Chris361 on 2005-10-13
What are you running for hardware? What Wireless NIC?

---

### Post by OpposingForce on 2005-10-13
Wireless is 

D-Link AirPremiere DWL-AG530

Hardware? :confused: 

umm can you clarify I am kind of new to linux

---

### Post by Chris361 on 2005-10-13
That's all I was asking haha. I have had a horrible time trying to get my wireless to work too. Have you tried just reinstalling?

---

### Post by OpposingForce on 2005-10-13
[QUOTE=Chris361]That's all I was asking haha. I have had a horrible time trying to get my wireless to work too. Have you tried just reinstalling?[/QUOTE]

reinstall? wtf I just installed this thing and it took forever...there has to be another way

---

### Post by Chris361 on 2005-10-13
> there has to be another way

I am an uber newb too, just wanted to know what Wireless card you were using.

---

### Post by drogoh on 2005-10-13
Eh.  Reinstalling won't work.  Wireless is one of the most tedious things to get going if you're new to Linux.  Look at Ndiswrapper, they support a LOT of D-Link products.

---

### Post by OpposingForce on 2005-10-13
[QUOTE=drogoh]Eh.  Reinstalling won't work.  Wireless is one of the most tedious things to get going if you're new to Linux.  Look at Ndiswrapper, they support a LOT of D-Link products.[/QUOTE]

grwar!!! I cant figure it out! heeelp!

---

### Post by Pfaffa on 2005-10-16
I had the same problem, the cards shipped with an invalid region programmed into them.  Here is how I solved it:
First make sure you don't have an A5 card:  
[http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list](http://madwifi.sourceforge.net/dokuwiki/doku.php?id=compatibility_list)

Install the gcc package under development

Follow the directions on this page:
[http://www.gentoo-wiki.com/HARDWARE_ar5212](http://www.gentoo-wiki.com/HARDWARE_ar5212)
SKIPPING steps 3 & 4

After reloading the driver you should be able to configure the card and start it up.

---

### Post by fimbulvetr on 2005-10-16
If someone asks you about your hardware, go to a terminal and type:

```
lspci -vvv
```

You should get output like this:

```
0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: f0000000-f3ffffff
        BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4541
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 11
        Region 4: I/O ports at bf80 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4541
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 11
        Region 4: I/O ports at bf40 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4541
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 11
        Region 4: I/O ports at bf20 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 014e
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin D routed to IRQ 11
        Region 0: Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR+
        Latency: 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff
        Prefetchable memory behind bridge: fff00000-000fffff
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
        Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corp.: Unknown device 4541
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at <ignored>
        Region 1: I/O ports at <ignored>
        Region 2: I/O ports at <ignored>
        Region 3: I/O ports at <ignored>
        Region 4: I/O ports at bfa0 [size=16]
        Region 5: Memory at 40000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 014e
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 5
        Region 0: I/O ports at b800 [size=256]
        Region 1: I/O ports at bc40 [size=64]
        Region 2: Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Conexant: Unknown device 5422
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 5
        Region 0: I/O ports at b400 [size=256]
        Region 1: I/O ports at b080 [size=128]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 0179
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at f0000000 (32-bit, prefetchable) [size=64M]
        Expansion ROM at 80000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
        Subsystem: Dell: Unknown device 865d
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (16000ns min), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at faff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:02:01.0 CardBus bridge: Texas Instruments: Unknown device ac47 (rev 01)
        Subsystem: Dell: Unknown device 014e
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 40001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 40400000-407ff000 (prefetchable)
        Memory window 1: 40800000-40bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

0000:02:01.1 CardBus bridge: Texas Instruments: Unknown device ac4a (rev 01)
        Subsystem: Dell: Unknown device 014e
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168, Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 40002000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 40c00000-40fff000 (prefetchable)
        Memory window 1: 41000000-413ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
        16-bit legacy interface ports at 0001

0000:02:01.2 FireWire (IEEE 1394): Texas Instruments: Unknown device 802b (prog-if 10 [OHCI])
        Subsystem: Dell: Unknown device 014e
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 1000ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at fafef800 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at fafe8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:01.3 System peripheral: Texas Instruments: Unknown device 8204
        Subsystem: Dell: Unknown device 014e
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Region 0: I/O ports at ecf8 [size=8]
        Capabilities: <available only to root>

0000:02:03.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corp.: Unknown device 2565
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 8500ns max), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at fafee000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

```

You can also do:

```
dmesg
```

From the command line and paste that in here.

---

### Post by Pfaffa on 2005-10-17
Although at least two version of the DWL-AG530 would show up identically that way.  To figure out if you have a non supported A5 goto System > Administration > Device Manager and check the advanced tab of the wireless card.  The A5 has a differnent pci.product.id.  The A1 and A3? have a 0x13 there.

---

