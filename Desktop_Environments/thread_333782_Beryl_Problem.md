---
title: "Beryl Problem"
date: 2007-01-07
forum: Desktop Environments
---

### Post by hedgefighter on 2007-01-07
Hi,
I hope someone can help me. I've been working at this all day. I'm trying to get Beryl/XGL running on my 6.10 ubuntu with ATI Radeon 9250 and fglrx drivers. I followed the tutorial here: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
and when I try to login with Xgl it just hangs on a blank brown screen and then throws me back to the login screen. I'm assuming that beryl is crashing for some reason. I also looked at several other tutorials including the one from beryl project website and I got varying results. The main difference between the tutorials seems to be the startxgl scripts. At one point I actually logged in with xgl but instead of the beryl splash I got a fuzzy static grey screen and that was about it.  Any suggestions? Thanks a lot.

---

### Post by Waappu on 2007-01-07
Hi

I have also ATI 9250 card and never get XGL working, but AiGLX works great
I used these guides
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

---

### Post by hedgefighter on 2007-01-08
Well, I tried to get AiGLX going and I got the drivers just fine but had a weird problem. I use a 19" widescreen LCD and for some reason the image with the ati driver is shifted way over to the left. Manually adjusting the panel doesn't even move the image back enough to the correct point.  However, the fglrx driver doesn't have this problem. So, I guess I need help with either problem at this point: 1. Getting Xgl to load with the fglrx driver or 2. getting my monitor to correctly display with the ati driver. :confused:

---

### Post by Random20230808 on 2007-01-08
Are you sure that the fglrx driver is installed correctly?
If not, maybe the instructions you find at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") will help you.
If you are sure, you must go to the next step which is to be sure that the Xgl is installed correctly...

---

### Post by hedgefighter on 2007-01-08
Yup, seems to be. fglrxinfo gives me what it is supposed to.

---

### Post by Random20230808 on 2007-01-09
What about Xgl? Have you taken a look at [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")?
You can find three or four good tips to check out if Xgl is running correctly.

---

### Post by iluva on 2007-01-09
the problem ouccures with the newest .deb snapshot of beryl also here on my machine where everything worked great before the update. so if it "should" work but throwes you back to the login screen, don't mid the configuration and wait for the next update or downgrade to an older one.

---

