---
title: "how can i add a free disk space to ubuntu after deleting microsoft?"
date: 2005-03-13
forum: Desktop Environments
---

### Post by lorap on 2005-03-13
i want to remove microsoft,how can i do that from ubuntu and then use that free space?
thanks.
pavel

---

### Post by az on 2005-03-13
That depends.

You may delete the first partition and move the ubuntu partition to that space.  If it is small, it _may_ be problematic.  If the Ubuntu partition is smaller, you should not have a problem.  You can then enlarge your ubuntu partition.

All of this can be done with parted or any program that uses parted (gparted or qtparted)

I have never run the Ubuntu live cd.   If it has gparted or qtparted on it, use that, since you cannot partition a disk if there are mounted partitions on it.  If not,m use Knoppix (any version from the last three years will do it...)

You may even use your warty install disk to delete, move and resize your partitions.

If I may also suggest you start trying out the Hoary preview.  If you can live without the extra space for a little while, now would be a good time to file some bug reports.  Basically, if you have an hour or two to kill, install Hoary on top of windows and look for bugs.  Make a point of finding one and reporting it (as long as it is not already been reported...)  When your are done, free up the space and move Warty back.


Do not forget to change your fstab and grub menu.list settings to make the root partition point to the correct partition afterwards!

---

### Post by lorap on 2005-03-14
good morning!
that's what i've thought to do.
i think that's the best solution install hoary.
i'll do my best to find out and report the bugs i would recognize.
thanks:-)
pavel

---

