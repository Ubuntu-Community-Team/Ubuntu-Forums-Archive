---
title: "IS there a default partition editor for Kubuntu?"
date: 2009-03-28
forum: General Help
---

### Post by mahela007 on 2009-03-28
Is there an "out of the box" partition editor for kubuntu?

---

### Post by DGortze380 on 2009-03-28
neither ubuntu or kubuntu install with a partition editor... gparted is available on either live cd, and can be installed on either GUI with

sudo apt-get install gparted

fair warning: do not use this program on a mounted partition.

---

### Post by SuperSonic4 on 2009-03-28
I'd use [KDE Partition Manager]("http://www.kde-apps.org/content/show.php/KDE+Partition+Manager?content=89595") as a frontend to parted. There is a PPA for it which means once it's added you can use Adept or apt-get

---

