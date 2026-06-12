---
title: "Alsa is not working, out of ideas."
date: 2008-11-12
forum: Desktop Environments
---

### Post by SimbaSpirit on 2008-11-12
Greetings, I'm not incredibly savvy with ubuntu yet, but I'm getting there slowly :P

One little hitch I'm having is having to use OSS instead of alsa. While OSS works, the one-program-at-a-time thing is a real turnoff.

I followed the Comprehensive sound troubleshooting article ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)) as far as I could and I still can't get any sound via alsa.

I'm running a dell computer with a SB Live card on Ibex.

I just ran 
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

```
And still no sound.

Here are some readouts that I hope will help:

lspci -v

```

#lspci -v
(everything audio-related)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Dell Device 0174
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at ee00 [size=256]
	I/O ports at edc0 [size=64]
	Memory at febffa00 (32-bit, non-prefetchable) [size=512]
	Memory at febff900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

02:02.0 Multimedia audio controller: Creative Labs [SB Live! Value] EMU10k1X
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at df20 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1X
	Kernel modules: snd-emu10k1x

02:02.1 Input device controller: Creative Labs [SB Live! Value] Input device controller
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 64
	I/O ports at df18 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: Emu10k1_gameport
	Kernel modules: emu10k1-gp


```

aplay -l
```

card 0: Live [Dell Sound Blaster Live!], device 0: emu10k1x [EMU10K1X Front]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 1: emu10k1x [EMU10K1X Rear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Live [Dell Sound Blaster Live!], device 2: emu10k1x [EMU10K1X Center/LFE]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I've also tried modprobing snd-emu10k1-gp (which ubuntu seems to suggest) and snd-ca-0106 (which wikipedia seemed to suggest) and still nothing.

Can anyone think of something I haven't tried short of reformatting?

Thanks,
-SimbaSpirit

---

### Post by SimbaSpirit on 2008-11-12
Some more information if it helps anyone:

amixer:
```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65536
  Mono:
  Front Left: Playback 65536 [100%] [on]
  Front Right: Playback 65536 [100%] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch cswitch-joined
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 65536
  Front Left: Capture 0 [0%] [on]
  Front Right: Capture 0 [0%] [on]

```

lsmod:

```

soundcore              15328  2 snd
snd_page_alloc         16136  4 snd_ca0106,snd_intel8x0,snd_emu10k1x,snd_pcm

```

---

### Post by SimbaSpirit on 2008-11-12
40 views and no reply?

If you recommend reformatting that's helpful too :P

---

