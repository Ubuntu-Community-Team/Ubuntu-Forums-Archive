---
title: "How can i disable the ugly window-animations in 9.04?"
date: 2009-04-19
forum: General Help
---

### Post by BazookaAce on 2009-04-19
Hi, 

I'm currently using 9.04 beta, and i'm sick of the ugly animations that comes (sadly) to life when i'm minimizing windows. 

**How can i disable this monster?** 

**Q:** What animations are you talking about? 
**A:** The black squares that looks like - yeah you guessed it - crap. 
 _                                                                         _

---

### Post by Bakon Jarser on 2009-04-19
System > Preferences > Appearance.  Click the visual effects tab and click none.

---

### Post by BazookaAce on 2009-04-19
Already done. I don't have Compiz installed. I've checked most of the apperance-settings, but i can't find a way to disable this.

---

### Post by stoneage on 2009-04-19
Ummm, I don't think that is an animation.

---

### Post by BazookaAce on 2009-04-19
Yes it is? Don't you guys have it? Or are you "still" on 8.xx?

---

### Post by ibuclaw on 2009-04-19
Does this help? [http://ubuntuforums.org/showthread.php?t=299760](http://ubuntuforums.org/showthread.php?t=299760)

I use compiz, so I can't remember the metacity minimise effect. But it may look better if you enable metacity compositing. Which to do is to run:
```
gconftool -s /apps/metacity/general/compositing_manager true --type=bool
```
But that will only work if you have a graphics card that supports it.

Regards
Iain

---

### Post by CatKiller on 2009-04-19
I believe that they used to be controlled by gconf-editor settings at

/desktop/gnome/interface/enable_animations
/apps/metacity/general/reduced_resources
/apps/panel/enable_animations

Perhaps they still are (but I'm still on 8.10 :))

---

### Post by BazookaAce on 2009-04-19
Found it!

gconf-editor-->/desktop/gnome/interface/enable_animations (uncheck it)

Edit: Thanks guys! We did find it at the same time. Kinda creepy :P

---

### Post by stoneage on 2009-04-21
> **BazookaAce said:**
> Yes it is? Don't you guys have it? Or are you "still" on 8.xx?

I am still on 8.10........didn't know that..........learning all the time....

..thanks..

---

