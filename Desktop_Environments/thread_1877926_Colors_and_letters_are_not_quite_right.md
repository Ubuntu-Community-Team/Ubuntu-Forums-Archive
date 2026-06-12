---
title: "Colors and letters are not quite right"
date: 2011-11-08
forum: Desktop Environments
---

### Post by oscarivera9 on 2011-11-08
Hi, I have problems when using the Gnome 3 desktop environment with Ubuntu 11.10, maybe someone else has encountered what I have and/or can guide me in the right direction.  When I use Unity, everything is fine, just as it is also fine if I use Gnome Classic, or Xfce.  When I log in with Gnome, the top panel is kind of pink (instead of black) and the letters on it are not quite legible.  I can sort of read my name, but that's about it.  I know that's not how it's supposed to be and I would like to really check out the new Gnome 3 Desktop Environment, but at this point I haven't been able to do so.
I am using an ATI Radeon HD 5770 graphics card with the Catalyst 11.8 driver.

---

### Post by oscarivera9 on 2011-12-06
No one really answered me when I originally posted this thread a few weeks ago, but in case anyone encounters the problems that I did, I am posting again to say that the problem's been fixed.
I was using the fglxr proprietary driver and when I tried to use the recommended open source driver, which is what I'm using right now, the problems went away.  I never had a problem with Unity, the only problem was when I would try to use Gnome 3 which I am currently using without any problems whatsoever. 
So for anyone experiencing graphics problems with Gnome 3, if you are using the proprietary ATI Radeon driver, switch to the open source driver to fix the problem.

Thanks

---

### Post by typhoon_tip on 2011-12-06
Probably nobody answer because there are so many threads in this forum about the subject. ATI and FGLRX driver are incompatible with Gnome 3 as of today:
[http://ati.cchtml.com/show_bug.cgi?id=99](http://ati.cchtml.com/show_bug.cgi?id=99)

Situation will be solved in January 2012 seems, but hopefully in 11.12 version too due to be out in current month.

---

