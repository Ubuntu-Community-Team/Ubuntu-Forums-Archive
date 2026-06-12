---
title: "Dell Latitude D620 - Sound stops working after a while"
date: 2008-11-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LinkDJ on 2008-11-13
I've got a Dell Latitude D620 running a fresh install of Intrepid Ibex and I've got a weird sound problem. When the computer first turns on the sound works great. Then I leave the computer alone for a while, come back, no sound. 

My laptop stays plugged in while I'm away, and it's set to never sleep or hibernate, just to blank the screen. So it doesn't seem to be a problem with sleep/hibernate, just a weird sound problem. (sidenote: I also tested hibernation and the same thing happens too.)

Originally I was having this problem after upgrading from Hardly to Intrepid, so I figured something messed up in the upgrade. But after formatting and reinstalling from scratch I've got the same issue.

I've searched around for a while hoping for a fix, and I came across this old thread: [http://ubuntuforums.org/showthread.php?t=209740](http://ubuntuforums.org/showthread.php?t=209740) but I followed its tips and it didn't help.

Any suggestions would be appreciated, as this is pretty frustrating.

---

### Post by Zeroedout on 2008-12-04
I feel your pain, same laptop. When I first upgraded, it would sometimes play sound sometimes not, but would always do either one or the other. Now sound is gone completely from alsa and pulse but works for oss (I don't want to use oss!). Just to be sure we are having the same problem, does oss work fine for you?

---

### Post by LinkDJ on 2008-12-06
> **Zeroedout said:**
> Just to be sure we are having the same problem, does oss work fine for you?

It's hard to tell. Lately it's been working more often than not, even though the only thing I've done is install updates. I'll do some testing next time it stops working.

---

### Post by LinkDJ on 2008-12-30
It stopped working again and I tested. ALSA, OSS, Pulse, nothing works. It just says "Connection refused" or says another application is using the device. Reboot, everything works again.

I tried killing any application that could have been using sound, but nothing helped.

---

