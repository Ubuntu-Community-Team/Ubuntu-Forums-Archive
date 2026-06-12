---
title: "mount ext3 trouble"
date: 2005-11-15
forum: Desktop Environments
---

### Post by Hairy_Palms on 2005-11-15
i have a problem, the ext3 partition that i use as a partiton to store all my music/films/pictures so that windows and linux can access it is having trouble with breezy, its mount point is /media/media but i can only write to it as root.
its fstab line is /dev/hdc3       /media/media    ext3    defaults,user,rw        0       0
windows access it fine and so does suse, but ubuntu, is saying i cant write to it as my user only as root.

---

### Post by MDoten on 2005-12-08
Hey,

I was having that problem before too. What I did was use the line:

/dev/hdb1    /media/stuff    ext3    defaults        0       0

Before mounting the drive or doing anything else, I went into the /media directory and created the stuff directory. After creating it, I set the permissions as 777, which allowed me, as a user, to write to the hard drive.

Hope that helps. :smile:

---

