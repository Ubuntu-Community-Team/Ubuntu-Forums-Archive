---
title: "KDE 4.1 freezes on disk icon starting up"
date: 2008-07-29
forum: Desktop Environments
---

### Post by supernaut on 2008-07-29
Hi,

I previously had a beta of KDE 4.1 installed on Ubuntu, since it updated to final via apt this morning, it refuses to start up, freezing on the disk icon requiring X to be killed. Any ideas?

---

### Post by edvar on 2008-07-29
It happened to me when I upgraded to KDE 4.1 RC1. 

You'll have to remove all KDE4 packages on Synaptics and install the package kubuntu-kde4-desktop. Also select the plasma packages for some plasma fun afterwards.

For some reason a direct upgrade of KDE 4.1 has always been dodgy.

---

### Post by ramaswamyps on 2008-07-29
try deleting/moving  .kde in home folder to /mnt
and restart

---

