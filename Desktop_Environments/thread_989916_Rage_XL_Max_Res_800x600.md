---
title: "Rage XL Max Res 800x600"
date: 2008-11-22
forum: Desktop Environments
---

### Post by ex800 on 2008-11-22
Hi, 

Clean install of 8.10 (previously running 2003 server), and all updates applied. The screen resolution applet shows 800*600 as the max resolution. grandr also shows 800*600 as the max resolution.

Hardware is a HP ML110 G2, lspci -vv gives this for the graphics card

--------------------------------
0a:03.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
        Subsystem: Hewlett-Packard Company Device 4752
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 66 (2000ns min), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 10
        Region 0: Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: I/O ports at 4000 [size=256]
        Region 2: Memory at dd220000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at dc000000 [disabled] [size=128K]
        Capabilities: [5c] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel modules: atyfb
--------------------------------

The monitor is an Acer AL1706 which is usually connected to an SGI Fuel running at 1280*1024.

After reading several threads on here, I tried changing the refresh rate between 60 and 56 to no avail, then I tried using envyng, which required a clean install to resolve.

To my limited knowledge, its as if its not reading the monitor correctly.

Any suggestion on how to get more than 800*600 would be appreciated.

---

