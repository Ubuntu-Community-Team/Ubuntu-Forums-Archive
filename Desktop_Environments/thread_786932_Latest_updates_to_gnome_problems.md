---
title: "Latest updates to gnome problems"
date: 2008-05-08
forum: Desktop Environments
---

### Post by 2WhEElTeRRoRisT on 2008-05-08
After those gnome updates a few days ago my laptop now won't start up the desktop. I can log in with no problems. My cursor will change from the default to the one I changed it to and that is as far as it will go. The background stays that orange color, the background image never appears. More importantly, none of the desktop panels will load. I can't even get anything to show up on a right click. That is why I figure that it just must not be loading at all. I don't know that much about fixing linux problems. I know there has to be a way to fix this, but I don't know how. Right now I am forced to log into my Enlightenment instead to even be able to use the computer. If anybody has any tips for me that would be great. THanks.

---

### Post by sebvajda on 2008-05-09
It's probably [a known problem ]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434")with gnome-keyring segfault'ing if root disk is tagged as removable storage by hal.

You can try this possible [workaround]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434/comments/62") that worked for me.

---

