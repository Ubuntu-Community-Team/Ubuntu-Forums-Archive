---
title: "Optiplex GX260 Ubutnu 10.4 Blank Screen problem"
date: 2011-01-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cheruvim on 2011-01-08
Hello, I have a Dell OPtiplex GX260 that I upgraded recently from 9.04 Karmic Koala to 10.4 LTS. Since the upgrade, there have been many problems, sound quality degrading being one of them.

However the main problem I'm having is that after working in the GUI for a while, the screen goes completely blank. If I log in using ssh to the box and try to restart gdm it says "WARNING can't access display manager".

The only way to get the system back on it's feet is to reboot the machine.

Any ideas? I've tried moving xorg.conf and tried dpkg reconfigure, nothing works! is the optiplex machine enough to handle 10.4? Should I lower resolution or something?

---

### Post by cheruvim on 2011-01-08
Also is there anyway to log the gnome session? At least to get some clues as to why my screen goes blank after a time.

---

### Post by cheruvim on 2011-01-08
> **cheruvim said:**
> Also is there anyway to log the gnome session? At least to get some clues as to why my screen goes blank after a time.

So Logging in ssh after this happened AGAIN I look at dmessage since I see the dmessage daemon is writing something and here's the following error message gets repeated over and over:

[23240.324873] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 326944 at 326840)
[23242.380018] [drm:i915_gem_idle] *ERROR* hardware wedged
[23243.504741] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
[23243.860041] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[23243.860052] render error detected, EIR: 0x00000000


So does that mean my GPU is hosed or does it mean that the driver is not right? Is there an alternative driver I can use for it?

---

### Post by cheruvim on 2011-01-08
> **cheruvim said:**
> So Logging in ssh after this happened AGAIN I look at dmessage since I see the dmessage daemon is writing something and here's the following error message gets repeated over and over:

[23240.324873] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5 (awaiting 326944 at 326840)
[23242.380018] [drm:i915_gem_idle] *ERROR* hardware wedged
[23243.504741] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
[23243.860041] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[23243.860052] render error detected, EIR: 0x00000000


So does that mean my GPU is hosed or does it mean that the driver is not right? Is there an alternative driver I can use for it?

What I also see is that Xorg starts fails and then keeps starting again. How do I keep the hardware from getting wedged? Is this a sign the video hardware is failing? It's the onboard VGA, so I'm not sure what state its in.

---

### Post by cheruvim on 2011-01-08
I also saw another post that requested pci info. Let me just post that here. 

Here is the VGA info. Let me know if you need anything else.

00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 01)
        Subsystem: Dell Device [1028:0126]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Region 1: Memory at ff680000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [d0] Power Management version 1
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Kernel modules: i915

---

### Post by adnane002 on 2011-01-20
Hello,
look at this [wiki page]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") it contains some fixes for you, i have an Optiplex GX260 with a 10.04(with the same conf as you), Xorg were crashing all the time, i installed the intel driver from the glasen ppa(see the wiki page) and it's working for me.

[Edit]
You can test the available fix from [the bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/541492")

[Upstream Bug Report]("https://bugs.freedesktop.org/show_bug.cgi?id=27187")

---

### Post by cheruvim on 2011-01-27
hey adane,

Thanks for that! I just finished installing the glassen kernel and we'll see what happens. It looks like it cleaned out not only whatever drivers were not compatible but all the ones I tried out before it.. :)

Thanks again for the help!
C.

---

### Post by cheruvim on 2011-01-28
So I've had Xorg session open for about 9 hours and no blank screen. However there is another strange problem that is probably unrelated... 

When I move the move either my speakers or my monitor makes a buzzing sound. Even when all sounds are muted this buzzing sound can be heard. 

There is no buzzing sound when the mouse is not moving.

I'll do some research, however, if you've heard of this problem and can point me in the right direction, that would be most appreciated.

Thanks,
Carl.

---

### Post by cheruvim on 2011-02-24
> **cheruvim said:**
> So I've had Xorg session open for about 9 hours and no blank screen. However there is another strange problem that is probably unrelated... 

When I move the move either my speakers or my monitor makes a buzzing sound. Even when all sounds are muted this buzzing sound can be heard. 

There is no buzzing sound when the mouse is not moving.

I'll do some research, however, if you've heard of this problem and can point me in the right direction, that would be most appreciated.

Thanks,
Carl.

Looks like an upgrade from the repository fixed this. So we should be all good. I've not had problems since pulling the intel chipset libs from this repository.

rockin'
:guitar:

---

