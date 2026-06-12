---
title: "TwinView and login screen location"
date: 2007-10-03
forum: Desktop Environments
---

### Post by WiFi Ed on 2007-10-03
I've got my TwinView working well, with an LCD and CRT set of monitors and the screen resolutions I like, but there is one final detail to fix. The LCD is on the left, and is my primary monitor. The GDM login screen however shows up on the right-hand monitor. Is there a way to change this without fiddling with the TwinView settings by way of nvidia-settings?

I've played around with changing the "right of", left of", absolute positioning, etc. and always ended up breaking things and having to copy over my backup copy of xorg.conf to restore TwinView. Is there another way to do this outside of xorg.conf?

Thanks in advance:)

---

### Post by WiFi Ed on 2007-10-08
This is what I love about Ubuntu Linux...

One either gets a ton of responses to a request for help (which has often been the case here on the forum when I needed assistance), or the deafening sound of chirping  crickets; in which case you have to figure it out yourself :)

An hour of Googling dug up the needed info. In case anyone else wants to know the answer:

Adding these three lines to the Device section of my xorg.conf moved the login screen to my lefthand monitor.

  Option         "TwinViewXineramaInfoOrder" "DFP, CRT"
  Option         "UseDisplayDevice" "DFP, CRT"
  Option         "TwinViewOrientation" "DFP LeftOf CRT"

---

### Post by Meson on 2007-10-21
Hey, thanks, I've been becoming an xorg.conf expert over the past few days.  (By necessity, trying to get dual monitors to work correctly with a laptop, docking station, and external monitor.)  The TwinViewXineramaInfoOrder option is a life saver.  I wish I had read the NVidia documentation correctly the first time.

How are you doing with the lid behavior of your system though? (Or are you not using a laptop)

---

