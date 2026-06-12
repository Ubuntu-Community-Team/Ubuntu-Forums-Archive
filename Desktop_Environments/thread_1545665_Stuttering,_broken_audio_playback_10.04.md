---
title: "Stuttering, broken audio playback 10.04"
date: 2010-08-04
forum: Desktop Environments
---

### Post by blackdalek on 2010-08-04
I recently installed 64bit Ubuntu 10.04 on a machine (previously only had fedora on it).
I can't get the on board audio card to work as anything other than stereo.
When I select the hardware as anything 5.1 I get broken, stuttering audio playback from ALL programs which produce sound.


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 812a
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at dc00 [size=256]
	I/O ports at e000 [size=256]
	Memory at d3103000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0


Machine is AMD Athlon(tm) 64 Processor 3500+ with 1Gb memory.

---

### Post by jmfal on 2010-08-04
Maybe this thread will help. It`s in the multimedia/video section.

TITLED: HDA INTEL OPTIONS,  by markbuntu if i`m not mistaken.

I looked at it yesterday and it was about 5-6 pages back probably farther now.

follow the commands in a terminal. read the first post just about everything you need should be there.

---

### Post by blackdalek on 2010-08-05
I found the soloution :D

I had mistakenly thought this was a 5.1 (6 channel) sound card, but in reality it is 7.1 (8 channel). Simply changing the hardware selection in sound prefs from 5.1 to 7.1 got rid of the stuttering/broken audio.

Incidentally, I worked out the name of the motherboard with this audio card is ASUS A8N-SLI nForce 4 (or "Deluxe" I think).
The serial number on the board is 59ZM092861.

Thank you.

---

### Post by provy on 2011-01-18
I actually had the same problem with that motherboard on 32bit Ubuntu 10.04. Thanks for the heads up on the 7.1 selection. 

I am also running a 4.1 speaker system that has two outputs. I was having trouble getting the sound to come out correctly and I actually plugged both into a splitter and plugged that into a single analog connector. Hope that helps for anyone having the same problems of getting all speakers to fire.

---

