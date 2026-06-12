---
title: "Change names of links in Places menu"
date: 2008-10-12
forum: Desktop Environments
---

### Post by mastakebob on 2008-10-12
I have 2 500gig internal drives in my Ubuntu 8.04.1 box.  They're mounted to ~/Movie and ~/TV, but they both show up in the Places dropdown menu as "500 GB Media".  They also show up on my desktop with that unhelpful name.  How can I change the displayed name to "Movie" and "TV"?  I imagine this has been answered before, but I can't seem to find any info on it.  Thanks for any help...

---

### Post by tom957 on 2008-10-12
I've wondered about the same thing.

---

### Post by mastakebob on 2008-10-15
A previous thread said something about the ~/.gtk-<forget exactly what the file name was> is the key, but when I look in that file, I just see a plain text list of media mounts.  So that wasn't much help.  When I tried dragging them into the places menu from Nautlius, it just changes to 500 gig media again, which isn't much help.  Do I have to mount them to /media and then just link to them from my home directory?  (I'm not at my home computer so I can't check that idea out quite yet)

---

### Post by vanadium on 2008-10-15
Your drives are probably mounted twice, once under /media and once under your home directory.

Anyway, I would mount internal drives under /mnt using /etc/fstab, then create a symlink to my home directory. You determine how you access the drive through the name of the symlink.

For external drives, I would be using the automatic mounting. In that case, Ubuntu will use a meaningful name if you label the partition. [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by mastakebob on 2008-10-15
Beautiful, worked like a charm.

Mounted both under /mnt/Movie or TV, then symlinked them to ~/Movie and ~/TV and then dragged those two symlinks to my "Places" in Nautilus.  They didn't immediately show up, but once i closed out of Nautilus and then reopened it, they were there.

---

