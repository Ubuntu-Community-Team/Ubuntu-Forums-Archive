---
title: "Ati X600: DRI yes, 3D Acc no"
date: 2006-10-16
forum: Desktop Environments
---

### Post by rabside on 2006-10-16
Hi Guys!
I have a very strange problem: if I write fglrxinfo the output is
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Generic
OpenGL version string: 2.0.6065 (8.29.6)

It seems ok, but the performace is very low:
glxgears 
443 frames in 5.0 seconds = 88.458 FPS
441 frames in 5.0 seconds = 88.023 FPS

The Cedega video test tells that DRI is on, but 3D acceleration is off :-k 
What can I do?

---

### Post by sitedesign on 2006-10-16
You need to post your /etc/X11/xorg.conf file so we can help further.

Try also working through one of the guides here:
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

