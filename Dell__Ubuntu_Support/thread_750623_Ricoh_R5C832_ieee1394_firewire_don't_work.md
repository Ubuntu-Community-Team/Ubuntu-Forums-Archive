---
title: "Ricoh R5C832 ieee1394 firewire don't work"
date: 2008-04-09
forum: Dell  Ubuntu Support
---

### Post by fdap on 2008-04-09
Hello. I'm searching a solution for long time but no success :(. Ricoh R5C832 works for cards but not for ieee1394 port (dell m1330, etc.). Impossible to plug a hard disk or other ilink peripherals. Some informations : 

```
$ sudo lspci -v | grep -A5 1394
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
Subsystem: Dell Unknown device 0209
Flags: bus master, medium devsel, latency 64, IRQ 18
Memory at fe4ff800 (32-bit, non-prefetchable) [size=2K]
Capabilities: [dc] Power Management version 2

$ sudo modprobe raw1394
$ sudo modprobe dv1394

$ sudo chmod 777 /dev/raw1394
$ sudo mount /dev/raw1394 /media/disk
mount: /dev/raw1394 n’est pas un périphérique de type bloc
```

Any ideas ?

---

### Post by ethanay on 2008-06-04
i have the same, and am having problems getting an echo audiofire2 firewire audio card to work -- try gscanbus to see if the system recognizes your device

you can run it straight or do gscanbus -v3 for a lot of debug info that you can copy/paste

at the very least it will provide more info

also, try testlibraw, which should come with the raw1394 driver

good luck

---

