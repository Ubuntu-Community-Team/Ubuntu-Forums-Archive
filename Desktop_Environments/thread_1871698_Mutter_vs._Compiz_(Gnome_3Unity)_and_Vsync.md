---
title: "Mutter vs. Compiz (Gnome 3/Unity) and Vsync:"
date: 2011-10-29
forum: Desktop Environments
---

### Post by Oranges10e on 2011-10-29
Hello guys,
 
long time no read :o
 
I thought this issue was fixed and addressed with Ubuntu 11.04 (ccsm, OpenGL Plugin). I guess it wasn't, because I can see it again in 11.10. Vsync is enabled via the OpenGL plugin @default.
 
**_Hardware:_** Core 2 Duo, 4GB RAM, Nvidia 8600GT and 8800GT. Ubuntu 32bit and 64bit. Prop. drivers installed. Also on: Core i7, 4GB RAM, 460 GTX.
 
**_Unity with Compiz:_** When the system is idle: No tearing. 
 
This changes as soon as I put the system under "load". I can see a lot of tearing going on. This is visible when you move the windows around, while doing all this. Stuff I do from day to day: Loading Software via the Software-Centre, surfing through the Web (with some Flash), chatting with my friends, watching a movie and or listening to music.
 
**_Gnome 3 with Mutter:_** Idle and under load: It doesn't matter what I do; the Desktop stays tear-free _all_ the time. I have yet to see a single tearing window or video, while doing the above mentioned stuff and more. 
 
_**My question therefor is:** _What does Mutter do, that Compiz doesn't? Why is Compiz trying hard to keep the desktop tear-free for years, and failing at that under higher load, and why does Mutter do it without problems?
 
Nvidia once told me (a long, long time ago - in a far, far away galaxy), that they have no solution to provide me with, in order to get a 100% tear-free experience, while using Compiz. They only gave me some tipps, in order to reduce the tearing - but nothing to kill it 100%. 
 
Thanks! :KS

---

### Post by crdlb on 2011-10-29
Owen Taylor, a GNOME developer, wrote a [blog post]("http://blog.fishsoup.net/2011/06/13/benchmarking-compositor-performance/") on this subject. It covers some of the differences between Mutter and Compiz.

---

### Post by Oranges10e on 2011-11-01
Hi, sorry for the late response.
 
Thanks for the link! I will look in to it right now. I'm not sure how much I am going to understand, though. It seems very technical. 
 
Oranges :popcorn:

---

### Post by crdlb on 2011-11-01
I didn't mean to imply that it would have a solution for your problem with compiz, only that it discusses how it is that mutter can have dramatically better performance than compiz on the same system.

---

### Post by typhoon_tip on 2011-11-01
I had the same problem with my ATI, and started from 11.04. In the past, Sync to VBlank on compiz never worked with fglrx drivers installed. Then they upgraded the driver and they have the setting in the fglrx. So all was perfect in 10.04 and 10.10.

What happened from 11.04, was that Sync to VBlank in compiz worked, but at the same time, I had this function on the video card, and result was a lot of tearing and irregular effects on screen. It all went away after I did the following:

- Disable Sync to VBlank in compiz totally
- Open composite plugin, and set a frame rate higher and multiple of your screen's frequency (I have 60Hz, I set to 90 FPS)
- Enable tear-free option (vblank sync in NVIDIA X settings) in your graphic card directly

With the above procedure, I have a perfectly stable and tear free Unity.

---

