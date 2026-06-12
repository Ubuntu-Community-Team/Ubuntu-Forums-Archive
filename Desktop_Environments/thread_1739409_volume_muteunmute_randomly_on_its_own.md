---
title: "volume mute/unmute randomly on its own"
date: 2011-04-25
forum: Desktop Environments
---

### Post by jrbjr5 on 2011-04-25
The volume on my computer randomly mutes/unmutes itself rapidly at unpredictable intervals.  sometimes it works fine, other times it does not.  I cannot find out what the problem is.  I have never had this problem until recently, and this problem has surfaced in ubuntu 10.10, 10.04, 64 and 32 bit versions of the operating systems.  I have used this hardware setup for a year before this problem ever surfaced.  My hardware is installed and working fine, I just cannot figure out why this is happening.  Does anyone know of some commands I can use to find out what is causing the volume to mute/unmute itself?  Any help is greatly appreciated, thank you!

---

### Post by secayford on 2011-06-09
I've been having the same issue for months. First on Kubuntu 10.10, now on 11.04. Nothing crashes, nothing gets logged, I just have to unmute the sound every once in a while. Using the onboard audio:

```

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at fbff4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel 

```It was particularly bad today, I just switched the headphones from the front audio port to the rear. Seems to have improved for the moment.

---

