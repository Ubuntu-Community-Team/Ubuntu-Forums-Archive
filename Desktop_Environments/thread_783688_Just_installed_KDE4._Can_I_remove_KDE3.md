---
title: "Just installed KDE4. Can I remove KDE3?"
date: 2008-05-05
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2008-05-05
After installing KDE4, I noticed I have still have kde3 program packages. They aren't causing any problems but I would like to remove them because most of them are duplicates of kde4 packages, and they're a clutter. How would I completely remove kde3?

---

### Post by mutzinet on 2008-05-08
I thought about this at first when I had installed KDE4. But I end up starting kde3 every now and then because kde4 is sometimes a little buggy. I am waiting for kde4.1 before removing kde3.

---

### Post by Xiong Chiamiov on 2008-05-08
I don't think there is any automated way to do it yet.  My guess is that eventually the KDE4 packages will be transitioned back to the standard names with the -kde4, once 4 becomes stable.  I wouldn't recommend getting rid of KDE3, but if you really want to, I think you'll have to go through them manually in adept, unless you can figure out some fancy regex to use for apt-get.

---

### Post by XemeX on 2008-05-08
KDE4 uses some of the KDE3's apps so sometimes some elements of KDE4 may be removed.

---

### Post by benerivo on 2008-05-08
What about ```
sudo apt-get purge kubuntu-desktop
```If this was the command the cd installer used to get kde3 installed on the pc, then would thgis then make all kde3 apps 'autoremovable'?

EDIT - try removing kdelibs-data. All kde3 packages seem to rely on this, yet kde4-core doesn't.

---

