---
title: "Show desktop"
date: 2013-05-12
forum: Desktop Environments
---

### Post by The musmula on 2013-05-12
Hello!

about two months ago I installed ubuntu 12.10 on my pc, a few weeks ago I upgraded to 13.04. I had some problems with the cpu, but I solved them. when I used 12.10 I messed up compiz, sooo... when I hovered the lower left corner of my display my desktop was shown, this was no problem at first, then I upgraded and... when I hover that corner again it shows my desktop again BUT when I hover it one more time it brings up the app I last used, BUT in black-white.

Is there a way to get rid of this, because I technically cannot enable the fade to desktop plugin while using unity, but somehow it happened, and I got a problem because when i get back to ccsm the fade to desktop plugin is deactivated.

Could someone help me please?

(sorry for my bad english)

well... so far the problem is getting worse, the black and white windows are appearing even when I just move from one window to another

I really need help before I cant read threads, so plz hurry

---

### Post by stinkeye on 2013-05-13
As you upgraded, it may be worthwhile to set compiz back to defaults.
```
dconf reset -f /org/compiz/
```

Then reload unity...
```
setsid unity
```

---

### Post by The musmula on 2013-05-13
THANKS! A LOT!

that solved the problem, thank you

---

