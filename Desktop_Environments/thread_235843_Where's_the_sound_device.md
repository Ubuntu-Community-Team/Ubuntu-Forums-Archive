---
title: "Where's the sound device?"
date: 2006-08-13
forum: Desktop Environments
---

### Post by rocketman768 on 2006-08-13
Hey everybody. I was wondering, if I'm using ALSA, what should my sound device be called? It seems like not too long ago I was doing something like:

'cat blah > /dev/audio'

but now, audio is not there. I was hoping to play around with the audio device a little bit more, but was unable to find the device. Where should it be in Kubuntu 6.06 (custom kernel with emu10k1 built in btw).

'cat /dev/sndstat'
```
Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux pipe-kubuntu 2.6.15.7 #3 PREEMPT Tue Jul 25 01:21:28 EDT 2006 i686
Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Audigy 1 ES [SB0160] (rev.3, serial:0x521102) at 0xb800, irq 201
Intel ICH5 with AD1985 at 0xffaff800, irq 209

Audio devices: NOT ENABLED IN CONFIG

Synth devices:
0: Emu10k1

Midi devices:
0: Audigy MPU-401 (UART)

Timers:
7: system timer

Mixers: NOT ENABLED IN CONFIG

```

---

### Post by rocketman768 on 2006-08-14
Nothing?

---

### Post by stdragon on 2006-08-14
You could try /dev/dsp if it's there

---

### Post by rocketman768 on 2006-08-17
Ok, so I had to load snd-pcm-oss to get /dev/audio. Where are the real alsa devices and how do I use those?

---

