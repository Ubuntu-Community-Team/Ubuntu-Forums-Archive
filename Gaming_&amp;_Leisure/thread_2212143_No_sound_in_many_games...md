---
title: "No sound in many games.."
date: 2014-03-19
forum: Gaming &amp; Leisure
---

### Post by Chuck_Finley on 2014-03-19
I recently switched over to ubuntu and with a lot of trial and error most of my games are now becoming playable. One issue that I cannot find a solution for is not having sound in some games. To name a few :

Vendetta (linux supported)
Fallout 3 nv (running on pol)
World of Warcraft (wine)

I google and I google but I always come to the same conclusion "pulse audio?" I read some things about configuring something called compiz? 

**** List of PLAYBACK Hardware Devices ****
card 0: STX [Xonar STX], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: STX [Xonar STX], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I use a  Asus xonar essence stx sound card. The ati hdmi devices I dont think I need. that just for hdmi right?

Anyone have any way to force these games to use the proper sound devices?

---

### Post by sffvba[e0rt on 2014-03-19
Non technical but perhaps easy fix would be to check "alsamixer" in terminal to see all volumes are un-muted etc... or you could also install Pule Audio Volume Control and see if all of the relevant sliders are up.

---

### Post by Chuck_Finley on 2014-03-19
Pulse Audio volume control did the trick! I disabled all the unused audio devices (onboard and video card). Much thanks :D

---

