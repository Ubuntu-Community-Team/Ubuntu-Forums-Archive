---
title: "Mplayer broken video playback and low performance problem"
date: 2006-05-22
forum: Desktop Environments
---

### Post by beewer on 2006-05-22
Hi. 

I have Ubuntu 5.10 and mplayer installed. My computer has athlon xp2800+ processor, 1Gig ram, nvidia geforce fx5600 video card and 19" tft.


I have two problems which are propably related to each other:

1. If I use xv video output driver performance is good but if I switch to full screen video output get broken.
It's hard to describe the error but it seems that every other horizontal line is few pixels too much right or left (interlace error?).

2. If I use gl video output driver full screen video output is otherwise ok but system has serious performance problems. Frames are dropped and high resolution videos look more like dia shows than video.


I have installed nvidia drivers but could it be that something is missing from my xorg.conf?

Any suggestions what could help would be highly appreciated.

edit: I remembered something that might be usefull, I used to use xv video output driver but after I changed from crt to tft problem appeared. At that time I had to put 
Option "ConnectedMonitor" "DFP"
to my xorg.conf.

-b

---

