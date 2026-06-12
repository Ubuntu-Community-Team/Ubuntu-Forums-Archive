---
title: "Removing KDE in Kubuntu."
date: 2008-07-30
forum: Desktop Environments
---

### Post by Benkrishman on 2008-07-30
I installed Kubuntu earlier to check out KDE 4.0.  After trying it out a little bit I decided I liked gnome more and would like to switch back.  Since I had just installed I figured it would probably just be easiest to reinstall with Ubuntu hardy.  I attempted to install but kept running into errors halfway through the install, it kept giving me the same i/o error even after trying multiple cd's and different downloads all giving me the same issue.  So I tried to install Kubuntu to see if the problem was my harddrive and it installed with no issues.  So now I figure it would be easiest to just install gnome(did this with apt-get ubuntu-desktop) and now I figured it would be a good idea to get rid of kde(except for any libraries I may need for kde programs).

What would be the best way of getting rid of KDE on Kubuntu Hardy?

---

### Post by Carl H on 2008-07-30
I'm not a KDE/Kubuntu man myself, but I'd guess that sudo apt-get remove kubuntu-desktop would be a good start.

---

### Post by Gourgi on 2008-07-30
i think 
```
apt-get remove kubuntu-desktop 
``` should be fine

---

### Post by Benkrishman on 2008-07-30
Thanks for the help, that did the trick.

---

