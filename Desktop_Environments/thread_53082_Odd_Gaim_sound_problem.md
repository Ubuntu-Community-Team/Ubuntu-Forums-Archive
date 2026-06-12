---
title: "Odd Gaim sound problem"
date: 2005-07-30
forum: Desktop Environments
---

### Post by NeoChaosX on 2005-07-30
Hey all. I've having a weird problem with sound in Gaim, and not sure what's going on. When I have Gaim on for awhile, sound eventually stops working in the app. A few minutes later, sound in all other apps stops working, too! When I check the GNOME System Monitor, I find that there's a whole lot of extra Gaim processes listed. When I close the first one, the sounds that were supposed to play in Gaim play all at once, and my sound device is free again. 

Does anyone know what's going on here? Is this a bug others here have encountered, and is it limited just to the Ubuntu package of Gaim?

---

### Post by brian g on 2005-07-30
> When I have Gaim on for awhile, sound eventually stops working in the app. A few minutes later, sound in all other apps stops working, tooi have this problem on occasion.
i will have to check the system monitor next time it happens.

---

### Post by NeoChaosX on 2005-09-04
Just had this problem again.  ](*,) 

Am I and brian g the only one suffering from this problem?

---

### Post by scunc_dvl on 2006-09-22
Try this: 
 Gaim doesn't know about ALSA, but just select *Command* in the dropdown of the sounds preferences and type *aplay %s*

reasoning:
I found this problem to be simply, programs like XMMS and Gaim are using different sound systems that simply don't mix well.

I switched both those programs to use ALSA, and things seem pretty smooth right now, with an additional tweak to XMMS to use MMap mode (That's the most obscure setting and a guess)

On different configurations, other things may work better like *playsound %s*.

---

