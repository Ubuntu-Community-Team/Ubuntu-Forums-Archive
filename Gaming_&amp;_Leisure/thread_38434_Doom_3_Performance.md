---
title: "Doom 3 Performance"
date: 2005-05-31
forum: Gaming &amp; Leisure
---

### Post by ishkabob on 2005-05-31
Hey everyone, I'm somewhat of a newbie to the linux gaming scene.  I've had success with some older (c.a. '99-'02) games in cedega; Jedi Knight 2 etc...  I recently installed the recent linux binary for Doom 3 and copied over the .pak files from my now dead windows partition and began to play.  The game runs pretty well I guess.  It runs at 640 x 480 and only lags out when alot of stuff is happening.  
Here are my specs:

AMD Athlon 1700+ (~1.4 ghz)
geForce FX 5200
768 MB Ram

I guess I'm wondering if there is anything I can tweak for a noticeable performance boost.  Would running a 686 kernel as opposed to a 386 kernel do anything?  Or perhaps buillding the nVidia driver's from source?  Any hints on game settings?

Also, if I wante d performance boost, sould buying a new video card do the trick, or would I have to update my entire system with a better cpu and memory and motherboard.  I'm not really sure which is more important:  video card and memory or processing power.  

Any help is greatly appreciated.

---

### Post by jkndrkn on 2005-05-31
Try the 686 kernel. The 386 kernel can't make use of some of your modern processor's new tricks.

Let us know if you noticed any improved performance.

---

### Post by wasynyt on 2005-05-31
I would say it depends.. how fast graphiccard are you goingto get... you have a pretty healthy ammount of memory, but if its below 333 mhz i cant recomend upgrading processor as better processors would require at least 333 mhz to work properly.. so get yourself new graphiccard, something like 6600 (not gt as it would waste as your processor is too slow, invest in onboard memory instead) or 5700 vanilla or ultra not xt and if possible 256 mb onboard memory..
in Doom 3 those both are important if you wont invest in the other the other will suffer (i am spaeking about highend hardware now)

---

### Post by ishkabob on 2005-05-31
Thanks for the tips guys (and gals?).  I'll try a new kernel when I go home tonight and post again.

---

### Post by ishkabob on 2005-05-31
This small situation raised an interesting point.  I was unsure which kernel image to install, k7 or 686 as I have an Athlon XP and there does not seem to be a definitive official response to this.  I, therefore, installed both of them and tried both.  Glxgears showed no difference, but there was a slight difference in gameplay.  I found that the 686 kernel improved the gameplay, not only over the 386 image, but slightly over the k7 package.  Ubuntu identifies my cpu as i686 in hal so i guess this makes sense.  I read that the k7 packages makes use of 3dnow! technology, but I guess that doesn't mean that the 686 packages don't.  

The bottom line is that on my machine, the 686 kernel image works a little better for 3d games, namely doom 3.  If I discover anything else, I'll post in this thread again.

Thanks for the suggestions again!

P.S.
does anyone know how to prevent Doom 3 from not changing your desktop resolution back to normal?

---

