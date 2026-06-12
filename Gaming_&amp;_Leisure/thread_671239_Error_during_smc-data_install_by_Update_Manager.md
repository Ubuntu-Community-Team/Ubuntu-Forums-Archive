---
title: "Error during smc-data install by Update Manager?"
date: 2008-01-18
forum: Gaming &amp; Leisure
---

### Post by aonegodman on 2008-01-18
Using the Update Manager I have received the following error and can't install.

Anyone else having this issue and is there a work around?


E: /var/cache/apt/archives/smc-data_1.4-1~gutsy1_all.deb: trying to overwrite `/usr/share/games/smc/music/story/default_story_1.ogg', which is also in package smc-music


Thanks!

---

### Post by disturbedite on 2008-01-18
this will solve your problem: (from term)
```
sudo dpkg --force-overwrite -i /var/cache/apt/archives/smc-data_1.4-1~gutsy1_all.deb
```

---

### Post by sub2007 on 2008-01-19
Seems you've externally installed the smc-music package, which provides the game music, but the new data package also provides the same music (most versions of the smc-data package don't provide music). The simplest fix is to remove smc-music from Synaptic, then try installing smc-data again.

---

