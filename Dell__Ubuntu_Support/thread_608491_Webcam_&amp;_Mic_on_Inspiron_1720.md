---
title: "Webcam &amp; Mic on Inspiron 1720"
date: 2007-11-10
forum: Dell  Ubuntu Support
---

### Post by pkzew on 2007-11-10
HI...

on my Dell runs Gusty perfect, but i've one problem. I don't find a solution for the integrated webcam/Mic.


Have anyone a solution for me ?


CU
pkzew

---

### Post by groovete on 2007-11-10
Hi!

I got the webcam on my Inspirion 1720 to work with ekiga and at least with cheese. The instruction is for the Inspiron 1520, but it worked for my 1720 too. Have a look here:
[http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

The mic I didn't get to work so far.

---

### Post by pkzew on 2007-11-11
THX....

it work's....

---

### Post by roger99 on 2007-11-11
I have both the webcam and the mic working on my laptop, was just a case of installing linux-backports-modules-generic, and then selecting the digital mic option in the mixer.  Simple as that, works perfectly, now with skype 2.0 beta i have totally integrated video and voice calls, excellent.

---

### Post by BoomShaka on 2008-07-06
Hi

I'm still having trouble with my mic. Does anyone know a resource that could help me debug it?

I have installed the backports module for hardy... guess I should try reboot.

---

### Post by szandor on 2008-07-07
> **BoomShaka said:**
> Hi

I'm still having trouble with my mic. Does anyone know a resource that could help me debug it?

I have installed the backports module for hardy... guess I should try reboot.

i did not have to install the backports. i set the input to pulseaudio in sound preferences. i may have had to unmute the mic in alsamixer but other than that getting the mic going was pretty much out of the box without additional packages. it was the second thing i tested after the install was done. the first being the webcam in flash (v4l) which also works with some tweaking. this is based off the alternate iso install. i used audacity 1.3 for recording/playback testing and tokbox for flash/cam.

---

