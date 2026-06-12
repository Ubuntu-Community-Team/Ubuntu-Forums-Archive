---
title: "Dell Optiplex 745 - No Audio - Tried Everything!"
date: 2008-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dizzygoldfish on 2008-09-16
Hi all,

I'm very much a noobie to the world of Ubuntu.  So far everything has been great.  However, no matter what I do I cannot get sound to work on my Optiplex 745.  

I have been all through the instructions found [here.]("http://ubuntuforums.org/showthread.php?t=205449")  I can see the various audio levels in alsamixer and everything seems to be setup properly but no dice.  Just for the record, I've also tried the Dell Wiki, some stuff at the ALSA project site, and all kinds of other tutorials.

I also went through the advice found [here]("http://ubuntuforums.org/archive/index.php/t-465599.html") but that actually caused my sound card to stop functioning all together.  I eventually reinstalled Ubuntu.

Can anyone help me figure out what I'm missing?  My card may not be supported, according to the Alsa website it looked like they had several ICH"X" listed but not my ICH8.  Is that the case?

Thanks!


Results of aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Results of lspci -v:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Dell OptiPlex 745
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at dfffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

```

If you need additional info, please ask.

---

### Post by dizzygoldfish on 2008-09-22
Bump.

I could really use some help.  Perhaps I'm should be in the beginner forum?

Thanks,

Dizzy

---

### Post by overdrank on 2008-09-23
Thread closed see duplicate here
[http://ubuntuforums.org/showthread.php?t=927916](http://ubuntuforums.org/showthread.php?t=927916)

---

