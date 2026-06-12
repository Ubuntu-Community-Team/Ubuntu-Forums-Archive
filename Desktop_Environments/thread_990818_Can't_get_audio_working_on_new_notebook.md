---
title: "Can't get audio working on new notebook"
date: 2008-11-23
forum: Desktop Environments
---

### Post by pssturges on 2008-11-23
Hi,

Just brought home my shiny new Medion Akoya notebook PC. I just can't seem to get any audio working. Ubuntu is showing the sound card as follows:
```
 
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

```

Initially alsa wasn't even finding any audio device, so I downloaded the latest alsa (1.0.18rc3), complied & installed it. Now the card is detected by alsa but I can't get any sound.

```

phil@phil-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 5: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

In the mixer I only get one slider for ALSA, Master.
On Realtek ALC268 (OSS Mixer ) I get 5. Volume, Microphone, PCM-2, In-gain & Digital-1. Seems, no mater how I adjust the sliders, I can't get any sound.

Any Ideas? Is the sound card just too new to have decent drivers, perhaps?

Cheers,
Phil

---

