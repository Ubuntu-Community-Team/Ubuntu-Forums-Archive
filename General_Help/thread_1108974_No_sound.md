---
title: "No sound"
date: 2009-03-28
forum: General Help
---

### Post by overwingexit on 2009-03-28
For some reason I have lost all of my sound on my computer running ubuntu 8.04. Iam using a headset the M. Lifechat as my speaker, i dont know why it  is listed as default though. The only sound I can hear is the startup sound however i have to take out the usb and plug in back in to hear the sound and I can do this multiple times after i have already opened up ubuntu. Also in the system-preference-sound folder not only is the Nvidia and Lifechat listed but a Realtek AC97 (oss) is listed as well. Can someone help me? would switching to 8.10 alleviate some of these sound problems?

 0 snd_intel8x0
 1 snd_usb_audio

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by bertolo on 2009-04-06
try this:
open volume control, preferences, enable all the xit there. put volume in max in all parameters.
then in switches choose headphones and disable the other two options below.
ps:select HDA intel drivers.
this was my solution when i had the same problem

---

