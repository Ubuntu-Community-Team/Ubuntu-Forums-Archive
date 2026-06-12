---
title: "No sound on Dell Mini 9 with NBR 9.04"
date: 2009-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LeoPanthera on 2009-05-12
Just installed Ubuntu 9.04 NBR on my new Dell Mini 9, and I can't get any sound out of it.

I've tried turning the "Speaker" volume up as per the documentation, but I still don't get any sound from any application.

Here's the output of lspci:

```
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
    Subsystem: Dell Device [1028:02b0]
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f0540000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```Any ideas?

---

### Post by ugm6hr on 2009-05-12
That is odd.

I installed 9.04 NBR on my Mini 9 and sound worked out-of-the-box.  Haven't tried headphones yet, but the speakers work fine.

---

### Post by iggykoopa on 2009-05-13
I was having a lot of issues with sound in 9.04 as well. I just removed pulseaudio and everything is working good now.

---

### Post by LeoPanthera on 2009-05-14
Turns out the hardware itself was faulty. It's gone back to Dell.

---

