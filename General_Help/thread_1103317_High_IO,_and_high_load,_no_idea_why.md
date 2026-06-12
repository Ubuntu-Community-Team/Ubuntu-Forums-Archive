---
title: "High IO, and high load, no idea why"
date: 2009-03-22
forum: General Help
---

### Post by pronto185 on 2009-03-22
Here is a screen shot from htop
[http://pronto185.com/linux/screens/windowshots/03_22_09_16:26:44window.png](http://pronto185.com/linux/screens/windowshots/03_22_09_16:26:44window.png)

what the hell is going on :| , I've tried rebooting, killing them
they just stay there >.<


and my load has not gone under 1.3 since this started happening, when it is normally never above 0.05 


ubuntu 8.10,  64bit
 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux


edit:
this issue for now has stoped, not 100% sure why since i did a few things
did that apt-get update && apt-get autoremove
also i did notice some script i made a while back to auto mount harddrives was mounting my main hdd twice to / and another place 
(guess its always good to make sure your scripts will work when you things around)
well the things with the high IO in the red are still there, but my load avarage is back under 0.8

---

