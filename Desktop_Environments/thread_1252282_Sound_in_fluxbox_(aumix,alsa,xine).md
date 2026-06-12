---
title: "Sound in fluxbox (aumix,alsa,xine)"
date: 2009-08-28
forum: Desktop Environments
---

### Post by grzeslaw on 2009-08-28
Hello,

Few days ago, I made a fresh install of buntu 9.04 on my Lenovo laptop.

Fist Question:
When I start my fluxbox sessin. in default sound is muted, and I need to run aumix and move first plunger to unmute the sound. I try to store settings by pressing Z (polish: Zapisz, english Save). but after restart the sound is still muted. How can I solve it?

Second Question:
When I open new xine window with move, the sound is also muted. I move the plunger up and she sound works fine. But! When i close the movie, and open new movie in xine, the sound is muted agin. Why?  What do I need to do, to set always unmute the sound in xine?

Third question:
How can I mute all system sounds in Fluxbox? 

My hardware soundcard specyfication:
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo Device 2066
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE- FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
                LnkCap: Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

When I play mp3 in audacious, the default driver which works for me is: ALSA Output driver.

---

### Post by stanca on 2009-08-29
[https://answers.launchpad.net/ubuntu/+question/68564](https://answers.launchpad.net/ubuntu/+question/68564)

---

### Post by grzeslaw on 2009-08-31
Thank U very much stanca. This is good solution for my fist question and works fine for me.

But what about question nr2 and nr3 ?

Regards

---

