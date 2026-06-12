---
title: "Problem with loading hda-intel"
date: 2009-09-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hshelar101 on 2009-09-07
I just bought a dell studio 1555 and loaded ubuntu x64 9.04 on it. For some reason the sound doesnt work. It detects two soundcards with aplay-l

hshelar@hrishi-ubuntu:/usr/src/alsa$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but modprobe snd- returns failed..
hshelar@hrishi-ubuntu:/usr/src/alsa$ sudo modprobe snd-
FATAL: Module snd_ not found

iv tried updating the alsa script and recompiling the drivers from scratch but nothing works.. 

any ideas why?

---

### Post by chinoy on 2009-09-09
it has the stac chip right ?
I downloaded the desktop version of the latest Ubuntu and it detected everything from my bluetooth to wifi to dvd to even  the buttons on the side of my XPS M1530.
But the express card did not detect.
I then downloaded the laptop re-mix kernel and support files it broek everything from the sound to the wifi

---

