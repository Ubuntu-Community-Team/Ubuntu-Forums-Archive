---
title: "shuttered and lower fps compared to windows"
date: 2006-11-24
forum: Gaming &amp; Leisure
---

### Post by jadziadax on 2006-11-24
](*,) 

on windows and quake3 the 'video' seems noticably smoother and the fps higher. the exact number of fps doesn't seem to be the most important issue. but the screen doesn't seem to refresh as smoothly, it shutters a bit on every turn of the mouse to another view(similar to the effect of video being out of sync with a monitor's refresh). it's not only 'inefficient' but tiring as well.

fixable without waiting for new drivers or moving to windows?

ps. the 'radeon' driver behaves the same and seems to give even lower fps

---

### Post by Ferrat on 2006-11-24
> **jadziadax said:**
> ](*,) 

on windows and quake3 the 'video' seems noticably smoother and the fps higher. the exact number of fps doesn't seem to be the most important issue. but the screen doesn't seem to refresh as smoothly, it shutters a bit on every turn of the mouse to another view(similar to the effect of video being out of sync with a monitor's refresh). it's not only 'inefficient' but tiring as well.

fixable without waiting for new drivers or moving to windows?

ps. the 'radeon' driver behaves the same and seems to give even lower fps

Are you using the protarian drivers from ATi.com?

Have your installed them and recompiled the kernel evt?

---

### Post by jadziadax on 2006-11-24
yes been using it for some time, it doesn't look good either with ati's fglrx or the 'radeon' driver.

---

### Post by Ferrat on 2006-11-25
> **jadziadax said:**
> yes been using it for some time, it doesn't look good either with ati's fglrx or the 'radeon' driver.

Haven't tried Q3 but Doom 3 flows good both the intro grafics and the game, are you using OSS sound driver? 

check that 3d rendering works 

With "fglrxinfo" and "glxinfo | grep render" 

to see that nothing say no or mesa

---

### Post by jadziadax on 2006-11-25
i think you misunderstood. i'm using 3d accel successfully for years. the problem is with something i believe is usually referred as "tearing", the video/screen not being in full sync with the refresh rate of the monitor or sth similar to that.

the root of the problem seem to have been that q3 doesn't support r_swapinterval on unix, a setting that forces vertical sync. 

luckily "driconf" seems to be able to force it for all applications. i'm not sure it 100% solved it, but i think it looks better now.

ps. maybe the problem wouldn't appear if it wasn't a TFT monitor

---

