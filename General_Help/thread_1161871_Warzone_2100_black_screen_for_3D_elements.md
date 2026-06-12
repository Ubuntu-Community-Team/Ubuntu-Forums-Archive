---
title: "Warzone 2100 black screen for 3D elements"
date: 2009-05-17
forum: General Help
---

### Post by objem on 2009-05-17
I am able to run Warzone 2100 fine but when starting any new game, the 3D elements only flash for half a second and then the whole battlefield becomes black. The radar and other parts of the screen are fine and I can press escape and use the menu's. 

I have tried enabling/disabling compiz. Used 2 versions of the game (version in jaunty repo and compiled from latest source), and also tried rolling back my video driver. Although I can play other 3D games with no problems (ppracer and scorched 3D).

It may be specific to jaunty 64 bit as I have only seen one other report of this problem by another linux user after googling.

---

### Post by jsday187 on 2009-06-11
Exactly same thing for me too. Intel 965GM X3100. Jaunty amd64. Warzone2100 2.2.0
Quick flash of graphics then nothing but the build buttons. Compiz is NOT installed on my computer AT ALL in case anyone was going to say that was the problem.

****

---

### Post by prokher on 2009-06-16
As far as I see, bug is posted [here]("https://bugs.launchpad.net/ubuntu/+source/warzone2100/+bug/374531").

---

### Post by rodolfonio on 2009-07-08
> **objem said:**
> It may be specific to jaunty 64 bit as I have only seen one other report of this problem by another linux user after googling.

Exactly the same problem in Ubuntu 8.10 32 bit, my laptop is a Toshiba without any graphic card.

---

### Post by Ekeluo on 2009-07-18
This is also happens on a presario a900 with integrated intel X3100 graphics.

---

### Post by objem on 2009-07-22
Solved! Warzone now plays fine with the landscape and everything.

I have been following this thread:
[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

Which explains how to improve performance of intel graphics drivers under jaunty (I use the bleeding edge method). Only today after an update the game ran OK. I read somewhere in the changlelogs that they enabled DRI2 in the drivers again and I think this might have made it work. :D

---

