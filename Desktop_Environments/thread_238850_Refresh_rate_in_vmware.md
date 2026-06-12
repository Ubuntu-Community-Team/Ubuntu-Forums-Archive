---
title: "Refresh rate in vmware"
date: 2006-08-18
forum: Desktop Environments
---

### Post by CuBone on 2006-08-18
Hi, 

I'm using vmware server to run Win XP. My problem is that my Ubuntu (the main OS on my machine) is running 1280 x 1024 @ 75hz but the monitor in the VM says its running in 85 Hz. So when I go to fullscreen i get an out of range error on my monitor. Does anyone now how to change the refreshrate in the virtual Win XP to 75Hz?

---

### Post by murataht on 2006-08-18
i use xp under vmware in my laptop. so the refresh rate is 60hz for my laptop lcd. but under vmware it says 85hz for the screen. and no problem with going to the full screen mode. if the higher rate should cause problem, mine should not work, either. but in my case, it does not cause problems. 

if, still you think it is the cause of the problem, how about change the refresh rate inside the xp. i think you know the screen resolution settings and there is advanced setup button leads to the refresh rate setup.

goodluck.

Murat

---

### Post by CuBone on 2006-08-18
I can't change it in XP. There is only one choice and its 85 Hz

---

### Post by evil_elman on 2006-08-18
Same thing here... 85Hz in VMWare and I have a laptop screen running at 60Hz...

---

### Post by CuBone on 2006-08-18
So then the problem might lay in my ubuntu settings and not in the VMWare settings?

---

### Post by murataht on 2006-08-18
I still don't think, the difference between rate is the root of the problem. are you using lcd or crt one? in my case and in the evil_elman's case, the difference does not trig a problem. evil_elman and I have one thing in common it is lcd. if you are using crt stuff, maybe it would be different. then maybe you should try to change the ubuntu's refresh rate.

---

### Post by evil_elman on 2006-08-18
I tried (just for fun) to change the laptop screen's refresh rate from 60 (default) to 200. The result is that (to my big surprise) Ubuntu and Gnome is SOOOOOOO much smoother now but it doesn't affect VMWare Server in any way. Still says 85Hz and it just works as usual.

CORRECTION: There actually is some kind of difference in VMWare. I notice it when I play Heroes of Might and Magic IV in a Windows XP Pro SP2 vm. All the animations for when creatures and heroes move around the map are quite a lot smoother now. Also scrolling the map is considerably smoother now. :cool: 

General responsiveness in Windows and mouse cursor is also slightly improved (not as dramatic as the game, though).

---

### Post by CuBone on 2006-08-19
I'm using a lcd. (SONY SMD-S75A) and the graphics is handled by a ati X850 pro.

never mind. My monitor wasn't identified correctly. Now everything works like a charm.

---

### Post by murataht on 2006-08-19
> **evil_elman said:**
> I tried (just for fun) to change the laptop screen's refresh rate from 60 (default) to 200. The result is that (to my big surprise) Ubuntu and Gnome is SOOOOOOO much smoother now but it doesn't affect VMWare Server in any way. Still says 85Hz and it just works as usual.

CORRECTION: There actually is some kind of difference in VMWare. I notice it when I play Heroes of Might and Magic IV in a Windows XP Pro SP2 vm. All the animations for when creatures and heroes move around the map are quite a lot smoother now. Also scrolling the map is considerably smoother now. :cool: 

General responsiveness in Windows and mouse cursor is also slightly improved (not as dramatic as the game, though).

how did you change the rate from 60 to 200?

---

