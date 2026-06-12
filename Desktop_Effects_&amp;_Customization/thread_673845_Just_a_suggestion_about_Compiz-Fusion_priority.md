---
title: "Just a suggestion about Compiz-Fusion priority"
date: 2008-01-21
forum: Desktop Effects &amp; Customization
---

### Post by VictorR on 2008-01-21
Working on my computer (Ubuntu 7.10 with Compiz-Fusion on Athlon XP 2600+) and listening to music on Beep Media Player, I found that when I close program windows (effect - burn) music stops for a moment. After some search I have found a simple solution, which I think can be useful for someone.
I have reduced nice value for Compiz-Fusion by 5 adding the "nice -n 5" command to its launcher in the Sessions menu.
The whole procedure:
1. go to System -> Preferences -> Sessions
2. add the above command in front of the Compiz launcher, in my case it looks like:
   nice -n 5 compiz --replace --indirect-rendering

Now the fire and smoke of burning maximized windows does not affect my media player :)

Reducing the priority by 5 causes some side-effects with other software, so it is better to reduce it by 1 instead.

---

