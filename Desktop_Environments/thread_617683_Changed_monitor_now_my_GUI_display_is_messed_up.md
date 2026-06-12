---
title: "Changed monitor now my GUI display is messed up"
date: 2007-11-19
forum: Desktop Environments
---

### Post by boondocks on 2007-11-19
So I had a Ubuntu 7.10 Desktop system working just right for me.
It was using an old NEC MultiSync XV15+ monitor.  This monitor died.

I just received a NEC MultiSync 3FGe monitor.
Now it works fine at the console level.
But as soon as the GUI login appears the screen becomes fuzzy and incomprehensible.
I put in my id and password but the desktop is simply unreadable.

I can do a Ctrl-Alt-F2 and the console is just fine.

So how do I change the video settings to make it work with the NEC MultiSync 3FGe monitor?
(This monitor is in working condition.  I tested it with a Win XP system.)

---

### Post by taurus on 2007-11-19
You need to reconfigure your X server for that new monitor.  From a prompt, run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

