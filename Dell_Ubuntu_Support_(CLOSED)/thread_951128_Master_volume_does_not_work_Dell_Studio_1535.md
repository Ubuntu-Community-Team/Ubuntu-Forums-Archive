---
title: "Master volume does not work Dell Studio 1535"
date: 2008-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Wolfpack Fan on 2008-10-17
I just purchased a Dell Studio 1535 from a national retailer, and promptly formated the hard drive and installed 8.04. For the most part it was very smooth and my wife is very happy with her new ubuntu laptop.
I have a small problem that is bugging the hell out of me though.

The master volume does not control the volume. I have changed the  volume applet to control PCM, so my slider on the volume control now works. But when I use the hot keys for mute and volume up down, the on-screen display pops up and shows the volume control move, but no sound change. Can anyone tell me how to fix this?  I figure it must be something simple.

@Dell-Studio:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Denny Johnson on 2008-10-17
If you right click your speaker icon, then preferences.....................does that help?
Or how about SYSTEM>PREFERENCES>SOUND.

---

### Post by Blarion on 2008-10-22
Ack, same problem here. This is a very annoying bug. x_x

---

### Post by brnetonboy on 2008-11-28
I had this problem too, very annoying. I don't know why we can't get such a seemingly simple thing right.

It seems that "Master" does nothing. Instead, "PCM" does what you would expect Master to do. "Master Mono" will control the internal PC speaker, "Headphone" will control any speakers plugged into the audio jack (aka the speakers most people have).

Click on "preferences" in the volume control window and you can check which ones you want to show up: I have mine just show PCM, Master Mono and Headphone, since those are the only 3 that do anything for me. 

Was really annoying before I figured it out: I couldn't mute the PC speaker since it had it's own control.

---

