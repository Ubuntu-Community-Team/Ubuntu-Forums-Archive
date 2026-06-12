---
title: "How to fully remove KDE?"
date: 2005-08-13
forum: Desktop Environments
---

### Post by phibxr on 2005-08-13
I installed KDE to check for improvements from the 3.0-era, but when I tried to uninstall it, it seemed like I was only able to remove separate packages, even though I begun with a "complete removal"  of the KDE-meta package.

I'm running Ubuntu 5.04 Hoary on iMac G4 700MHz.

---

### Post by PeP on 2005-08-13
if you remove kde-core kdebase libqt3 and kdelibs4, almost all kde packages will diseapear

---

### Post by yongyi on 2005-08-13
also,u can try this:
sudo apt-get --purge remove kdelibs4 libarts1

---

