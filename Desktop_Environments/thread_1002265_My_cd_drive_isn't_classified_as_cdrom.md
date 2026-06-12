---
title: "My cd drive isn't classified as cdrom"
date: 2008-12-04
forum: Desktop Environments
---

### Post by nintendude7cubed on 2008-12-04
i need to install something off of a cd. The problem is that when it looks for the cd, it looks in cdrom and for some reason, my disk isn't read from there... Is there a way to put the disk into that folder so it reads properly? The cd is there and i can get to the files, its just that it goes into the media folder next to the cdrom folder...

---

### Post by taurus on 2008-12-04
If you want to mount your CD to somewhere else, you need to change the mount point in /etc/fstab from /media/cdrom (or /media/cdrom0) to wherever you want it.  And don't forget to create the new mount point or it won't be able to mount it.

---

