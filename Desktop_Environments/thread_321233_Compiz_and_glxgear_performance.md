---
title: "Compiz and glxgear performance"
date: 2006-12-18
forum: Desktop Environments
---

### Post by Fregster on 2006-12-18
Just been playing, I now have compiz and aiglx working on my system.

I tested the glxgears fps with 3D desktop on and off to give an idea of GFX card load?

here are the numbers:

With 3D on
root@cobra:/home/paul# glxgears -printfps
25002 frames in 5.0 seconds = 5000.288 FPS
29514 frames in 5.0 seconds = 5902.636 FPS
29499 frames in 5.0 seconds = 5899.650 FPS
29036 frames in 5.0 seconds = 5807.106 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

3D off
root@cobra:/home/paul# glxgears -printfps
64702 frames in 5.0 seconds = 12940.374 FPS
69678 frames in 5.0 seconds = 13935.521 FPS
69709 frames in 5.0 seconds = 13941.624 FPS
69779 frames in 5.0 seconds = 13955.613 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

so aprox 5850 : 13940 fps
or               1 :  2.4 ish

bit of a difference, but I guess to be expected?

on a a64 3200+
1 GB Ram
NV 6800 GT 256MB

What numbers are other people getting?

---

### Post by Sqwishy on 2006-12-18
I assume your using gnome. I get about an extra 6000 fps when running kfce instead of gnome. kde and gnome are about the same fps. I havn't tryed E17 because I didn't get it working. I'll post my 'benchmark scores' when i got home.

---

### Post by scooper on 2006-12-18
My AMD64 (running 64 bit Ubuntu) with 1 GB RAM and NV 6600 GT w/128 MB gets the following results:
~4200 fps with Beryl/Emerald
~7400 fps with Beryl/Metacity
or a 43% reduction in speed for the Emerald compositing window manager.

I'm not sure I'm quite so tolerant of a quiet system having such a difference.  Why does Beryl/Emerald absorb so much of the GPU when nothing is happening on the screen except glxgears?!

---

### Post by Fregster on 2006-12-19
Sorry yes, gnome (Ubuntu edgy), latest NV drivers 9x.3x somit.


This is what I was wondering, perhaps someone could point me in the right direction to find out....


Does the GFX card have to cache the desktop in the GFX cards local ram? 

Does it actually render the whole desktop or just the 3D effects the change back to 2D?

Side note to scooper, who is the 64Bit working out for you, I had problems with my wireless (RT2500) on 64Bit, so changed back to 32. Do all the games still work (Wolf ET etc)

Thanks

Freg

---

### Post by scooper on 2006-12-19
> **Fregster said:**
> who is the 64Bit working out for you, I had problems with my wireless (RT2500) on 64Bit, so changed back to 32. Do all the games still work (Wolf ET etc)

I've only had 64 bit running (Edgy) for a couple of weeks.  It's been the best 64 bit experience yet.  I previously tried it with Gentoo a year or two ago.  I'm happy that everything I need is working, including MythTV and other multimedia stuff.  But I don't have wireless and haven't tried many games, other than Planet Penguin Racer.  Other than disappointing performance it ran fine.  At least now I have an explanation for the performance. :)  It still requires some annoying special setup of certain things, but there's a lot of info available and it works.  Can't say I notice a difference, but I haven't done an A-B comparison.

I hope someone can explain the performance drain for compositing or point to an article.  A quick search here didn't land me anything.  It doesn't make sense to me, even if the desktop gets cached on the card, that a lightweight 3D program like glxgears should notice such a big difference.  No visual effect is happening on the desktop (that I can see) while I run the test.  What's competing for the GPU at that moment?  Even more to the point, is there a way to adjust the compositing so that it doesn't drain the GPU as much?  I actually like Beryl mainly for the additional window management features and the real transparency.  I don't care about the water effects, etc.

---

### Post by mcduck on 2006-12-20
> **Fregster said:**
> Sorry yes, gnome (Ubuntu edgy), latest NV drivers 9x.3x somit.


This is what I was wondering, perhaps someone could point me in the right direction to find out....


Does the GFX card have to cache the desktop in the GFX cards local ram? 

Does it actually render the whole desktop or just the 3D effects the change back to 2D?

Side note to scooper, who is the 64Bit working out for you, I had problems with my wireless (RT2500) on 64Bit, so changed back to 32. Do all the games still work (Wolf ET etc)

Thanks

Freg
As far as I know when using XGL the desktop is rendered as 3D all the time, and with AIGLX it should use 3D rendering only when needed. But I'm not sure about the AIGLX because it doesn't work with my graphics card.

Anyway, glxgears is the worst performance test ever made, that's why at some point you had to run it with 'glxgears -iacknowledgethatthistoolisnotabenchmark' to get the FPS output ;)

Sometimes even moving the glxgears window to different place on your display will change the FPS results..

It's only useful to check if you have any 3D acceleration at all.

---

### Post by scooper on 2006-12-20
> **mcduck said:**
> Anyway, glxgears is the worst performance test ever made, that's why at some point you had to run it with 'glxgears -iacknowledgethatthistoolisnotabenchmark' to get the FPS output ;)

Sometimes even moving the glxgears window to different place on your display will change the FPS results..

It's only useful to check if you have any 3D acceleration at all.

I'm well aware that glxgears is not a good benchmark.  But I'm not sure that explains why results  obtained, where the only variation is metacity vs. emerald, vary so greatly (and consistently - in the same direction!).  I'm not trying to determine the precise power of my video card, just a gross approximation of relative performance drain of compositing.

Planet Penguin Racer consistently yields a 20% (125 FPS vs. 100 FPS) performance penalty for running emerald.  I'm really interested in what is happening _while_ the full-screen 3D app is running.  There should be no windows to manage, no effects to render at that particular moment.

I'm not saying this is unforgivable or that I'm annoyed about it.  I'd just like to satisfy my curiousity why it's seems to be true.  Then I'll make the decision about trade-offs and compromises.  Thanks!

---

### Post by Fregster on 2006-12-21
Same here really, just a curiosity as to why there is almost always a 20% - 25% drop in performance.

This also seems to be across the board, CPU and GFX cards.

---

