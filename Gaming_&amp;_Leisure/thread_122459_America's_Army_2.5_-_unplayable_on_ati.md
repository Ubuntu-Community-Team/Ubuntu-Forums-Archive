---
title: "America's Army 2.5 - unplayable on ati?"
date: 2006-01-27
forum: Gaming &amp; Leisure
---

### Post by shu on 2006-01-27
Hi

I'm searching for some info for a long time and can't find anything valuable. I'm trying to play AA 2.5 online. I have Athlon 2500+, 1GB of ram memory and radeon 9600pro graphic card with latest 8.21.7 drivers. I've set graphics settings to 800x600 with everything as low as possible or turned off and yet I can't get smooth framerate. I get about 40-60fps at most, with 20-30 being the average and it drops below 15fps when there's some action.

Question is: what can I do to make it faster, or at least not dropping below 20fps.

shu

---

### Post by shu on 2006-01-27
It might be some major problem here. I just tested quake3 and it isn't smooth either. I get ~90fps, but it stalls every few seconds like if I had enormous ping, when I don't.

---

### Post by polpak on 2006-01-27
I haven't tried quake 3 yet, but AA works fine on my ATI 9800 xt

---

### Post by Tartin on 2006-01-28
Well, I've not tryed Americas Army but after following _[mlomker]("http://ubuntuforums.org/showthread.php?p=423589")_'s guide I got Quake 3 Arena to run really smooth on my laptop. Made a timedemo showing a total of 1260 frames in 3.8 seconds, that will be ~330 fps.
Intel Centrino 1.7ghz, 512mb, ATI Mobile Radeon 9700.

You should try following that guide too, it really helps!

---

### Post by shu on 2006-01-28
Well I have some progress. I returned from my preemption-enabled kernel to the stock one, and turned off few things running in my system, like gdesklets and beagle. Seems it helped, it isn't smooth yet, but it's not bothering me that much.

Anyway I only get around ~100fps on demo001 timedemo in quake3, while I get almost ~150fps with old geforce3 ti200 card.

Something is certainly wrong. Could you post your X.org section containing graphic card settings?

---

### Post by JDoza on 2006-01-29
Have you checked the forums on [www.americasarmy.com](www.americasarmy.com) ? There is a Guide for tweaking AA on there.(there was, might be gone)

I installed the new driver, 8.21.7 like you and every so often get a stutter in the video. I read on this [http://www.rage3d.com/board/forumdisplay.php?f=88](http://www.rage3d.com/board/forumdisplay.php?f=88) that the new driver does this. Hope this helps.

---

### Post by shu on 2006-01-29
Well, I think I have it working now. The problem lied in gdesklets which were causing frequent [every few seconds] stuttering and beagled which causing serious slowdowns now and then.

In my previous post I didn't notice that I reverted to 8.16.20 drivers not the 8.20.8, which explains low performance.

Right now I get around ~140fps in quake demos and america's army runs well keeping framerate over 30fps.

It's still sucks to play AA with 800x600 at low settings, but it seems I can't expect anything more.

---

