---
title: "XGL is ******* slowly with Intel GMA 900 (onboard videocard)"
date: 2006-09-21
forum: Desktop Environments
---

### Post by 8200 on 2006-09-21
Hi.
I really like XGL but I it doesn't work (actually, it works, but too slow) with my notebook (HP NX6110: Pentium M 1,86GHz, 1GB Ram, Intel GMA915 Onboard). I think there must be a way to get XGL working with my graphics card, or is it too slow?

Is there a patch or something to get XGL working on machines with slower graphic chips like my one?

greets,
arthur

---

### Post by ronmarley1 on 2006-09-21
First, I would try turning off the Blur plugin and see if that helps performance.
Secondly, I was not able to XGL working on an Intel 855GM on my laptop, but I did get AIGLX working, and I think it runs nicely (with Blur turned off).  I used this HOWTO a few weeks ago.  Make sure you read the whole thread, as there may be changes since then.
[http://www.ubuntuforums.org/showthread.php?t=244559](http://www.ubuntuforums.org/showthread.php?t=244559)

---

### Post by l.tambiah on 2006-09-21
I personally think the graphics card is not powerful enough, it will work but it will be slow.

---

### Post by altaaa on 2006-09-21
Actually I have the same laptop as you, only with the 1,4 GHz Celeron. I use aiglx instead of xgl and performance is pretty good... So it isn't the hardware.

---

### Post by ayoli on 2006-09-21
AIGLX is recommended for Intel chipsets, how to for aiglx on dapper here:
[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

btw, it's easier on edgy since aiglx is in xorg 7.1 which means only compiz to install

---

### Post by 8200 on 2006-09-21
Hey thank you all very much! :cool: :KS 

With AIGXL and without Blur effect it works pretty good (my CPU is even constantly running with 800Mhz).

Only playing videos with VLC does't work any more.

---

### Post by l.tambiah on 2006-09-21
Well I have learnt something new there, I also own an  Intel Extreme Graphics 855GM, I am glad to here that AIGLX isn't resource hungry as I thought.  I'll have to try it out  ;-).

---

