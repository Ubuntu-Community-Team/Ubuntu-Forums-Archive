---
title: "Compiz unusable after dist-upgrade ubuntu 10.10"
date: 2010-10-15
forum: Desktop Environments
---

### Post by CesarOscar on 2010-10-15
A couple days ago a made a dist-upgrade on ubuntu 10.10, soon after that all my compiz effects were completely disable and i'm not able to get it back on. In the "effects" bar on appearance when i change it to either normal or advance, just says it wasn't able to activate the effects. On compiz-config manager, composite, opengl and gnome compatibility don't activate when selected and doesn't recognize each other (when activate opengl indicates that needs composite active to work, even if it is already active). After close, changes doesn't work.

---

### Post by Grig on 2010-10-15
I have the same problem.  The nvidia 260.19.12 driver *works*, but "Desktop Effects" fails [same when I roll back to 173.something].  I am not sure where to look.  I see my xorg.conf has been changed, so I am going to poke around the options as suggested here:

[http://us.download.nvidia.com/XFree86/Linux-x86/260.19.12/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86/260.19.12/README/xconfigoptions.html)

I have heard rumors (nothing verified yet) that this has to do with Xorg 1.9 which comes with Ubuntu 10.10.  I am trying to nail down that rumor as well.

This is what NVIDIA put in my xorg.conf, it's sort of basic:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

Video card:
```
01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2) (prog-if 00 [VGA controller])
        Subsystem: eVga.com. Corp. Device c383
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at d0000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at d1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at d2000000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
                Address: 0000000000000000  Data: 0000
        Capabilities: [78] Express (v1) Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <4us
                        ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 512 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x16, ASPM L0s, Latency L0 <1us, L1 <16us
                        ClockPM- Surprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 128 bytes Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100 v1] Virtual Channel
                Caps:   LPEVC=0 RefClk=100ns PATEntryBits=1
                Arb:    Fixed- WRR32- WRR64- WRR128-
                Ctrl:   ArbSelect=Fixed
                Status: InProgress-
                VC0:    Caps:   PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
                        Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
                        Ctrl:   Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
                        Status: NegoPending- InProgress-
        Capabilities: [128 v1] Power Budgeting <?>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-173, nvidia-current, nouveau, nvidiafb

```

---

### Post by CesarOscar on 2010-10-15
My laptop doesn't have nvidia, it has intel graphics, but i'll give it a search and check if the problem is the same.

---

### Post by mdkhirul on 2010-10-15
I also have the same problem..cannot choose visual effect on Appearance Preferences.Who else know how to fix it...??

---

### Post by eR2 on 2010-10-16
Same problem here. Nvidia 260.19.12 can't start visual effects in Appearance Settings. Help anyone?

---

### Post by eR2 on 2010-10-16
Ok, not sure I did everything right but I did what is written here 
[http://ubuntuforums.org/showthread.php?t=1593523](http://ubuntuforums.org/showthread.php?t=1593523)

and things seem to work so far. 

Disabled Compiz Packagers PPA in sources
Removed all compiz packages (including fusion-icon and emerald)
Refreshed sources in Synaptic

I then installed compiz through Tweak Ubuntu.
Than I manually chose packages in synaptic that were related to compiz and I new I had them installed prior to deinstallation but for some reason they weren't installed by Tweak Ubuntu.

Logged out, logged in.

---

