---
title: "Unity crash leaves me stranded - PRECISE"
date: 2012-05-08
forum: Desktop Environments
---

### Post by thatsmyboy on 2012-05-08
Just did a "fresh" install of Precise (12.04) over a lucid LTS box. It's a Dell C521 with Nvidia graphics (which I think may be part of the problem). I'm not sure which driver I'm using , so information to locate that would be welcome. as it stands I'm stuck looking at the desktop and navigating from there to applications - more likely clicking a document to launch the associated app. the Unity 2D fallback works okay , but I'm pretty frustrated about this install. I guess what I really wanted was to keep all my users, but ditch the programs, drivers, interface for something new (latest LTS). even the users aren't linked properly, but that's a different question it seems.

If it helps, when I first booted up I got an error stating that I should upgrade 'compiz-core'.

---

### Post by Peter09 on 2012-05-09
That sounds like you did not complete the upgrade properly.
 
Try doing the.....
 
```
sudo update
sudo upgrade
```
 
thing ... to make sure you are fully up to date.

---

### Post by thatsmyboy on 2012-05-09
I already went ahead with apt-get update, apt-get upgrade. I ended up deactivating the restricted nvidia driver which seems to work well for my use. For those who want to know how it's under "system settings > Additional drivers" A search for "driver" in dash should do the trick.

---

