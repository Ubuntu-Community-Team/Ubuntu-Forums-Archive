---
title: "Would like more space on hard drive"
date: 2009-06-12
forum: General Help
---

### Post by DougieFresh4U on 2009-06-12
Looking at my screenshot posted, appears I have given way to much space to each partition. So I woulds like to free up some space so I can add another partition. Any help would be great. Remember now, I am no 'guru' so I need **simple instructions**.
Also note that when I boot up machine my grub list's 
Karmic at the top then
windows vista loader (win7)
then my jaunty install at the bottom of grub menu.
don't know if that helps

---

### Post by colau on 2009-06-12
> **DougieFresh4U said:**
> Looking at my screenshot posted, appears I have given way to much space to each partition. So I woulds like to free up some space so I can add another partition. Any help would be great. Remember now, I am no 'guru' so I need **simple instructions**.
Also note that when I boot up machine my grub list's 
Karmic at the top then
windows vista loader (win7)
then my jaunty install at the bottom of grub menu.
don't know if that helps
I am no sure,gparted may do the job this.

---

### Post by statistic on 2009-06-12
> **colau said:**
> I am no sure,gparted may do the job this.

More specifically I think colau is telling you to resize the partition.

In gparted, simply right click on the partition you wish to resize. If you see most of the options are blanked out, you probably need to unmount it, so do that first. Once it's unmounted, you can right-click and choose "resize/move" and just resize the partition. If it's your linux partition, then you can't do it while booted into it, so you can use a a live cd. You'll have to apt-get install gparted though, it doesn't ship on the live cds. Alternately you could learn to use the command line parted, but I'm not brave enough for that myself. :P

IMHO you should shrink your linux partition. Since linux plays pretty happily with most file systems, you can just mount all the other partitions (google adding windows partition in fstab) and store your data there. For easy access once they're mounted, look up symbolic links, they're like windows shortcuts.

---

