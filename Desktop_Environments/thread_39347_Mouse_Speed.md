---
title: "Mouse Speed"
date: 2005-06-04
forum: Desktop Environments
---

### Post by ZakZak on 2005-06-04
I really like to have a very sensitive mouse (to keep wrist movement to a minimum).  Under Windows, I always have the "Speed" slider set all the way to the right (and "Acceleration" set to Low).  This setting is pretty much perfect for me.

Under Ubuntu, in System | Preferences | Mouse, on the Motion tab, I have set the "Sensitivity" all the way to the right and have played with the "Acceleration" slider, but I can't find a setting that is at all comfortable for me.  The mouse is always either too slow or too jumpy (by jumpy, I mean it will suddenly go from slow to fast - causing me to miss what I'm aiming for).

I've tried multiple mice on multiple Ubuntu systems and this is always a problem for me (but never in Windows).  Is there anything I can do to make my mouse faster without the huge accuracy loss I get when playing with the Acceleration?

-Zak

---

### Post by Curlydave on 2005-06-04
Try this: Keep the acceleration setting fixed. Does adjusting the sensitivity slider actually do anything? Now, play with the Acceleration slider some more... It's more like sensitivity than acceleration, right? 

I think that the mouse settings are bugged, and that might be your problem.

---

### Post by ZakZak on 2005-06-05
Okay, I think you're right.  The sensitivity slider doesn't appear to have any effect at all while the acceleration slider definitely has a very pronounced effect.  It always makes the mouse either way too slow or way way too "jumpy".

So, is there something I should do?

Thanks,
-Zak

---

### Post by Curlydave on 2005-06-05
Yea, download the source code and fix the bug.  :?

---

### Post by graigsmith on 2005-06-20
i dont think theres a bug in it.  if its too jumpy, you need to turn up the sensitivity, and turn down the acceleration.

---

### Post by Laibcoms on 2007-12-25
Hmm...

I have a problem with the mouse speed.  Regardless what setting I try, there is always an area within Ubuntu that the mouse suddenly goes back to its default speed.  Then after I leave that area, it goes back to my own speed.

I played with Sensitivity and Accelaration, same results.  Could this be a bug?  It usually happens when I move mouse between windows and when moving my mouse passing by menus.

---

### Post by Kache on 2008-01-04
Here's my quick Ubuntu Mouse Properties Guide for ya, since I had this problem and played with the settings so much, haha:

The acceleration is more like "speed" and the sensitivity is more like "mouse-will-be-slowed-if-under-this-speed." Yeah, the descriptions aren't very clear. I think the best way to think of it is:

**Sensitivity** is the threshold speed at which the mouse will start accelerating fast/moving full speed. If set to zero, the mouse will move all the time with no acceleration adjustment. *(perfect mouse distance to pixel distance ratio)* and the mouse will move on a "grid." *(You can see that at zero, if your acceleration is high enough, that means your pointer will start to skip pixels no matter how slow you move your mouse. Also, putting sensitivity in the middle sucks because you constantly pass above and below that threshold.)*

**Acceleration** is much more like "pointer speed." It dictates how far will the pointer move past the threshold for the distance you move your mouse. It doesn't seem to affect the speed when you're below the threshold much, if at all. *(It's most evident that this is the case when you break the "slow zone" speed threshold, either by moving the mouse fast enough, or setting the sensitivity to zero, as said above.)*

Everything else is a combination of the two.

::edit::
wow, there may be a better solution for this. Look up synaptics, xorg.conf, and syndaemon. I'm gonna read up on this stuff...

Now I'm just gonna blabber on a bit...

Strictly speaking, the sensitivity is a really basic acceleration implementation, and it's not even very intuitive. Not that I know how to, but I'd think one quick way to improve the Ubuntu mouse is to make the transition through the sensitivity speed threshold a lot smoother.

Another fix could be to use Microsoft's old method. Windows used to have a speed and acceleration bar that was just velocity+acceleration *(that worked more like you would expect acceleration to work)* and a movement smoother option. I also like a fast mouse (maxed speed in XP/Vista), and I used to set the velocity low and acceleration high so I still get my high speed when I'm moving fast, but I get accuracy when I slow down. I figured other people would use the inverse, where speed was higher, and acceleration was low, so they could move the mouse accurately at slow speeds while still keeping max speed down. I suspect that Window's new mouse speed is just that- n inversely related velocity+acceleration.

---

