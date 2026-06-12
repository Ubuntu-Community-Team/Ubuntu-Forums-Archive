---
title: "Video Problems Feisty + Desktop Effects + ATI"
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by juanvicfer on 2007-06-04
Hi Guys! I'm having some trouble with Desktop Effects with an ATI card and the video player...

The video turns black when i resize the screen or switch to full screen.
I was wondering if the problem is that the community drivers for ATI don't work smooth or something similar....

Any ideas what the problem is??
Thanks in advance!

---

### Post by Campingman on 2007-06-04
Try these fixes, it may sort it out, it usually sorts out no video when effects enabled:
By solicitus
If you load a terminal and do a;
$ gstreamer-properties
in the Video tab there is a drop down box for Plugin. I had a similar issue and selected "X Window System (No Xv)" and that solved my issue.
This sorts out Totem
If you use VLC, this should do the trick:
In VLC if you go to settings/preferences/video/output modules click advanced options you can change the video output, I have tried X11 video output and Xvideo extension video output, both now display the video in VLC (a bit choppy though)

Hope this helps

[http://ubuntuforums.org/showthread.php?t=415012](http://ubuntuforums.org/showthread.php?t=415012)

---

### Post by cvmostert on 2007-06-15
Thanks, this solved my problems too... did not really miss desktop effects.. but its cool that i could have both video and the effects if i wanted to.. 
Cheers

---

