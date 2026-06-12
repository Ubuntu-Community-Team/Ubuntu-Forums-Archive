---
title: "Installing Ubuntu over Fedora Core 5."
date: 2006-07-19
forum: Desktop Environments
---

### Post by jgrayson on 2006-07-19
I have been using Fedora for several years.  I would like to install Ubuntu to replace Fedora.   I have downloaded 6.06 and wanted to try to install it.   But Ubuntu wants to format it and repartion it.   Is there a way to install it over Fedora without losing all my current data???   With Mandrake and others I had the option to change without data loss.  

Thank you,

jgrayson

---

### Post by ajgreeny on 2006-07-19
I assume you have a separate /home partition in fedora.  If so then you can do a manual partiton when you get to that point, not accept the default. .You will need to mount your existing home partition as home in ubuntu but DO NOT FORMAT it in the table of partitions you have (I think there is a tick box against each partition).  That should do what you want.  You will also need a / partition (root) of perhaps 4 - 6 Gb and a swap partition of about twice your ram, and then proceed from there.

If you dont have a home partition in fedora, then you will either need to make one and move all your current /home/name contents to it before you install ubuntu.  I hope I've got all this right but if I have made any errors I'm sure someone will quickly put us both right.

Welcome to Ubuntu, it's great here!

---

### Post by Landoln on 2006-07-19
> **jgrayson said:**
> Is there a way to install it over Fedora without losing all my current data???

Like the previous post mentioned, you could do a manual partition and opt not to format the partitions.  I guess you could just not format the partition that you specify for / as long as you keep the same file system.  However, that would leave all of your old fedora system files, which could make your file system messy.  I would guess that the old system files wouldn't harm your ubuntu install except for wasting space, but I'm not sure.  

The best way to do it would be to have a /home partition, but if you don't already have one you may be not be able to do it without losing data.

---

### Post by jgrayson on 2006-07-19
Thank you both for the info.  I understand what you both are talking about.   I do have /home and another location /hdb2 that I don't want to lose.   I think I will move all the items I have into /hdb2 which is a seperate drive.  Then format the other.   I was just trying to avoid that if possible.  I don't want to messup or make a mess of my file system.  Now to remount /hdb2 I assume I need to just modify the fstab?   Then make sure I have correct permissions.   Does Ubnuntu have SELinux running as part of the kernel like fedora?   

jgrayson

---

### Post by Landoln on 2006-07-19
> Now to remount /hdb2 I assume I need to just modify the fstab?
You should be able to specify a mount point for any drives you want mounted during the ubuntu install if you choose to manually partition the drives.  For example, you could specify that /dev/hdb2 be mounted on /home and also specify that the partitioner should not format the partition.  If you really want to edit the fstab after you've installed, go for it, just make sure to copy any files (hidden or not) from the original /home to a temporary location and then to the newly mounted /home.

---

### Post by goobers on 2006-07-19
Just out of interest, what was your reason for switching from Fedora Core 5?

(I installed FC5 and Ubuntu when I upgraded from FC4 to see which I liked most, but ended up keeping Ubuntu due to the fact that it is much better supported and easier to use)

---

