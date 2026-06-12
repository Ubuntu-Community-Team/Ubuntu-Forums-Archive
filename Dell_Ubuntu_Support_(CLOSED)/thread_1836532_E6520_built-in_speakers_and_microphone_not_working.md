---
title: "E6520: built-in speakers and microphone not working"
date: 2011-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by benbc on 2011-08-31
Hello

I have a Dell Latitude E6520 with Ubuntu 10.10 preinstalled. I get no sound from the built-in speakers and can't get ALSA to recognize the built-in microphone.

The laptop has a combined speaker/mic socket (designed for headsets). I can get output to analogue speakers from that okay (haven't got an appropriate headset to try the mic there).

I have tried various settings in gnome-volume-control and alsamixer with no improvement. Everything is unmuted and turned up. Alsamixer reports "this sound device does not have any capture controls."

Here's some possibly useful information about the hardware:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT ID 76e7

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GPU 1c HDMI/DP
```Any advice or help gratefully received.

Thanks
-Ben

---

### Post by benbc on 2011-09-01
This is a driver problem, fixed in later releases of alsa. See instructions at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/792233](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/792233).

---

