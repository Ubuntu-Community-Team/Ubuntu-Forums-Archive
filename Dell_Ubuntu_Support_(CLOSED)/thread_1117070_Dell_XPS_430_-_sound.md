---
title: "Dell XPS 430 - sound"
date: 2009-04-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gotigersducksvols on 2009-04-05
Hi y'all,
  I recenty bought a Dell XPS 430 and put Ubuntu on it (as I do with all computers). Everything works out of the box except for sound. I've read several threads regarding my particular sound "card" but nothing seems to work. Here is my relevant information:

> 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 02ae
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at febdc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


My desktop has the X48 chipset. I've tried using pulseaudio instead of ALSA. I've looked at and used directions from at least 5 threads here to no avail. Thanks in advance for the help/advice.

Edit: I'm using Ubuntu 8.10 AMD64

Edit 2: I upgraded to 9.04 Beta and messed with a bunch of stuff until it worked. I don't know if it is the 9.04 or the messing around with stuff that finally fixed it, but I'm happy that it works now.

---

