---
title: "No Sound on new Ubuntu 8.10 Install"
date: 2009-03-03
forum: General Help
---

### Post by darinlwebb on 2009-03-03
Hi, first of all, I've been using Ubuntu for about 5 hours now. The past four were spend trying to get my sound working. Everything else is great, I love it, windows be damned! Or, that's what I would be saying if my sound worked. Anywhoo... help please? I've looked a lot of places so here's some info that might be useful for solving this problem:

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0; CONEXANT Analog [CONEXANT Analog]
   Subdevices:1/1
   Subdevice #0: subdevice #0
card 0; Intel [HDA Intel], device 1: Conexand Digital [Conexand Digital]
   Subdevices: 1/1
   Subdevice #0: subdevice #0

All of my volume sliders are up. I'm using a Toshiba P105 with built in harman/kardon speakers with an external volume control, it's all the way up.

I opened the PulseAudio Volume Meter and played an .mp3 file, the meters show activity, but still no sound.

I've been working in desktop support (Windows XP, Vista and Mac), but I'm still completely new to linux. I've enjoyed troubleshooting this, but I think it's time to ask for help. Thanks!

---

### Post by kmrs75 on 2009-06-13
> **darinlwebb said:**
> Hi, first of all, I've been using Ubuntu for about 5 hours now. The past four were spend trying to get my sound working. Everything else is great, I love it, windows be damned! Or, that's what I would be saying if my sound worked. Anywhoo... help please? I've looked a lot of places so here's some info that might be useful for solving this problem:

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0; CONEXANT Analog [CONEXANT Analog]
   Subdevices:1/1
   Subdevice #0: subdevice #0
card 0; Intel [HDA Intel], device 1: Conexand Digital [Conexand Digital]
   Subdevices: 1/1
   Subdevice #0: subdevice #0

All of my volume sliders are up. I'm using a Toshiba P105 with built in harman/kardon speakers with an external volume control, it's all the way up.

I opened the PulseAudio Volume Meter and played an .mp3 file, the meters show activity, but still no sound.

I've been working in desktop support (Windows XP, Vista and Mac), but I'm still completely new to linux. I've enjoyed troubleshooting this, but I think it's time to ask for help. Thanks!

i know its a little late but i just had time to get mine fixed p105 satellite updated the bios very easy to do just burn it to a cd then restart computer. here is the link works great 

[http://www.linlap.com/wiki/toshiba+satellite+p105]("http://www.linlap.com/wiki/toshiba+satellite+p105")

---

