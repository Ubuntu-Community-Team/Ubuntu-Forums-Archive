---
title: "vostro 1320 graphics"
date: 2009-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by korvirlol on 2009-09-18
Hello,

I made a thread about this in a different topic, but i think it got deleted???

Anyways, much to my surprise, when i installed ubuntu on this new laptop, the wireless and audio worked right away, i was fully expecting a fight with this. 

Im noticing that some of the animations arent particularly fluid. Specifically, when im doing some developping, i might have a couple terminals open, a text editor and a browser and when i try to alt tab between them, its really choppy/laggy. Also, some slow problems with javascript. I originally thought that the video drivers were installed by default because the resolution is really good... but im not really convinced.

Im relatively new to the ubuntu scene, so im not 100% sure on how to check these things, or what it all means... the output of lspci -vv:
```


00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02bb
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 2295
    Region 0: Memory at f6800000 (64-bit, non-prefetchable) [size=4M]
    Region 2: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 4: I/O ports at 1800 [size=8]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02bb
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at f6100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

```

(this isnt sudo, let me know if it should be).

Anyways, so i read some confusing thread online about how the drivers for this chipset may have a bug, or are not finished or something... but i didnt really understand it all.

Is there any kind of work around?

Any help is greatly appreciated.

---

### Post by korvirlol on 2009-09-19
shameless bump

---

### Post by korvirlol on 2009-09-21
Sorry for bumping my own thread. 

Does anyone have any advice?

---

