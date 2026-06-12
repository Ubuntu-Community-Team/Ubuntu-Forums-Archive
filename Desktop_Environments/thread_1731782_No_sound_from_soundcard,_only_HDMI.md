---
title: "No sound from soundcard, only HDMI"
date: 2011-04-17
forum: Desktop Environments
---

### Post by asai on 2011-04-17
Hi,

I have just installed a new video card in my desktop, with HDMI.
Fantastic picture through the HDMI, but i get no sound from the jack output in my computer. When I open the controls, it only shows the video card.
There is sound from the HDMI, but this is not what i want...

Is there anyway to disable sound trough HDMI, but keep video?
And get sound from the sound card instead?

---

### Post by asai on 2011-04-18
*BUMP*

This is still an issue... Anyone?
:(

---

### Post by asai on 2011-04-22
Some HW info:

Graphics card: Radeon HD4350
Sound card: Intel 82801AA AC97

```
lspci | grep audio
``` shows nothing.
```
aplay -l 
```shows
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Any suggestions?

---

### Post by asai on 2011-05-03
*bump*

---

### Post by asai on 2011-05-04
Found part of the reason for this:
The problem is on a HP machine.
In BIOS the onboard soundcard can be switched on or off, and on auto.
My setting where auto. It is now set on.

When I run lshw I get this:
```
*-multimedia UNCLAIMED
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: latency=0 maxlatency=5 mingnt=2
          resources: memory:fe024000-fe027fff

```
Earlier I could run alsamixer and set the audio.
When I run this now it says this:
```
cannot open mixer: No such file or directory
```
Alsa-base and alsa-utils are both installed.
This happened after I installed drivers from Realtec.

Any suggestions?

---

### Post by mörgæs on 2011-05-05
Try browsing through the posts by **lidex**. He knows this stuff.

---

### Post by asai on 2011-05-05
Thanks for your tip.
I have found a few things to check out.

I will report the results. :)

---

### Post by asai on 2011-05-07
Solution here: [http://ubuntuforums.org/showthread.php?t=1750001](http://ubuntuforums.org/showthread.php?t=1750001)

---

