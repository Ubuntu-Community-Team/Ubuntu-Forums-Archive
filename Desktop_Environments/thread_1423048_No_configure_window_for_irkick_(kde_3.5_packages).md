---
title: "No configure window for irkick (kde 3.5 packages)"
date: 2010-03-06
forum: Desktop Environments
---

### Post by mahoul on 2010-03-06
I installed kdelirc-kde3 (ppa packages) and lirc-x. When I launch irkick and right click on its icon -> configure, nothing happens.

Is any way of debugging irkick output?

---

### Post by mahoul on 2010-03-06
Solved.
Added environment vars listed [**here**]("https://wiki.kubuntu.org/Kubuntu/Kde3/Karmic#Executing%20KDE3.5%20applications%20from%20another%20DE") to $HOME/.profile
After re-logging it's working like a charm.

:p

---

