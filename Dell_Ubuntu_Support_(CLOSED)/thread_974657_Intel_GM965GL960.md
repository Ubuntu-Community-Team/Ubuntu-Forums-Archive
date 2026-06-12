---
title: "Intel GM965/GL960"
date: 2008-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by degtukas on 2008-11-07
Hi,

I have recently upgraded to Intrepid (x64) my Dell Latitude D830 laptop with Intel GM965/GL960 integrated video card. I had no problems with video on Hardy, but now I cannot enable desktop effects.

"lshw -C dispay" shows that the video card is UNCLAIMED; /etc/X11/xorg.conf entry for "Driver" is "intel". There are no entries for blacklisted drivers in /etc/modprobe.d/blacklist for "intel" except for "snd_intel8x0m" - but I assume this has something to do with the sound, not video.

How can I make it work properly?

---

### Post by edgaruy1980 on 2008-11-07
well, I have a lenovo notebook with the same on-board video (i965 X1000) and I was playing, then switch the advance desktop setting, to texture processing on fall back and the whole system crashed, had to re install.
I think is because of the limited bandwidth of the on-board video.
Also I had before Vista and it was not really good the i965 on aero, so just chech on the repositories if you have the latest driver like Synaptic package manager.

---

### Post by degtukas on 2009-11-06
Well, I guess the problem is solved in Karmic.

---

