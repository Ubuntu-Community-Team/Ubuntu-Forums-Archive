---
title: "Problem with soundcard device enumeration"
date: 2006-06-01
forum: Desktop Environments
---

### Post by balleklorin on 2006-06-01
I have two soundcards in my configuration a internal nvidiachipset AC97 and a external USB2 Edirol UA-1000 card. 

Both work fine, but somethimes my usb card is the hw:0 card and somethimes my chipset soundcard is hw:0, even though both cards are turned on during bootup. This is bit annoying as I have to select output device upon each boot.

Is there a way to force my chipset soundcard to always be hw:0  and my usb card to be hw:1 (if its on?)

---

### Post by soze on 2006-06-01
I would love a solution to this as well.
I've somewhat addressed it with having udev rules create symlinks, but the bottom line is that I can't count on my /dev/dsp to be a particular audio device.

See this thread for more info: 
[http://www.ubuntuforums.org/showthread.php?t=175171](http://www.ubuntuforums.org/showthread.php?t=175171)

---

