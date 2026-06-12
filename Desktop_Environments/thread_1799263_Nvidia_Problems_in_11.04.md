---
title: "Nvidia Problems in 11.04"
date: 2011-07-07
forum: Desktop Environments
---

### Post by eshmun on 2011-07-07
Hiii, i'm trying to install ubuntu 11.04 on mi computer, and every things is ok, but when i try to install my nvidia graphics drivers it's crash... monitor start blinking and do not start unity or any thing... 

Hardware:
Dell intel xeon 3.2 GHz.
NVidia Quadro FX 1000 (128 mb)

I try install recommended drivers, but not working... any idea?

Thanks

---

### Post by Reba T on 2011-07-07
I hope someone helps with this query, it seems similar to why I am here.

Trying to install both Ubuntu 10 or 11 on my PC I end up with just a black screen and nothing apparent happening. I have a Nvidia 9600 video card fitted in my PC.

---

### Post by wildmanne39 on 2011-07-07
> **eshmun said:**
> Hiii, i'm trying to install ubuntu 11.04 on mi computer, and every things is ok, but when i try to install my nvidia graphics drivers it's crash... monitor start blinking and do not start unity or any thing... 

Hardware:
Dell intel xeon 3.2 GHz.
NVidia Quadro FX 1000 (128 mb)

I try install recommended drivers, but not working... any idea?

ThanksHi, try a different nvidia driver, see if there is another one in additional drivers, if not got to there website and install one from there, the one in additional drivers is the preferred one.

---

### Post by wildmanne39 on 2011-07-07
> **Reba T said:**
> I hope someone helps with this query, it seems similar to why I am here.

Trying to install both Ubuntu 10 or 11 on my PC I end up with just a black screen and nothing apparent happening. I have a Nvidia 9600 video card fitted in my PC.
Hi, your issue is not the same as the other persons issue, you need to start a thread of your own with a good title that describes your issue. I think this link is what you need to get you into ubuntu so you can install your driver.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by MG&amp;TL on 2011-07-07
If all else fails, there might be a nouveau (open-source, modded for ubuntu) driver under additional drivers, although I can personally testify to it working and providing 3d acceleration, but being very buggy indeed.

Try all possible Nvidia routes first, though. Then follow wildmanne's suggestions. Then anyone else's. If absolutely nothing else helps, then install the nouveau one. I have a different graphics card though, so it may not be there at all.

---

### Post by eshmun on 2011-07-08
well my friend, that do not work for me, problem remains, a can log in, but the desktop start blinking, only sees the default ubuntu backgrounds, no task bars, no icons, just the background... and run some test ( $ /usr/lib/nux/unity_support_test -p ) and says me that have full support for unity, so i do not know what to do... if i install unity 2d it's work fine, but this is not the idea...

Thanks

---

### Post by Duncan Williams on 2011-07-08
probably down to opengl support.
This is required to run 3D applications like compiz/unity.

As stated, it might be worth installing and using the nouveau drivers. 

Other than that make absolutely sure you have the right nvidia driver installed for your 9600 card. (as there are different drivers for different models)

you can also try a couple of utilities that make the settings for the window manager easier.
> fusion-icon
> ccsm
(from software manager)

---

### Post by wildmanne39 on 2011-07-08
> **eshmun said:**
> well my friend, that do not work for me, problem remains, a can log in, but the desktop start blinking, only sees the default ubuntu backgrounds, no task bars, no icons, just the background... and run some test ( $ /usr/lib/nux/unity_support_test -p ) and says me that have full support for unity, so i do not know what to do... if i install unity 2d it's work fine, but this is not the idea...

ThanksHi, have a look at this link it is for that exact problem.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

