---
title: "Permissions/Access problem on External HDD"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Judicata on 2006-09-10
I've tried some solutions for this problem suggested in various forums and have yet to figure this out.

A regular user cannot write to (or edit files on) my external HDD.  When I try to sudo chmod through the command line it says permission is denied.  I've even created a root password and logged in a vc as root and tried it.  I've also tried sudo nautilus and, while it lets me click to change permissions, it immediate reverts back.  I've also tinkered with fstab to no avail (I even tried umask=777 in desperation). 

This wouldn't be a big deal, except my music collection is on there, and I do NOT want to run amarok (or whatever) as root every time I want to edit tags.

Anyone have experience with this?

---

### Post by Judicata on 2006-09-10
Ok, I did even more forum searching and figured this out.  Since my external drive is formatted in vfat, I can add/edit the following line to my /etc/fstab.

/dev/sda1  /mnt/external vfat  umask=0,defaults  0  1

The umask=0 allows all users read/write access, which I think is the best I can do without reformatting to ext3.

---

