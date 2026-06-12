---
title: "Mount/unmount partitions"
date: 2010-09-21
forum: Desktop Environments
---

### Post by TaterBug on 2010-09-21
The following applies to a Dell Vostros 200 w/C2D 2G.

I have a multi-booted setup involving Win XP, 7, Ubuntu 10.04 and a few other flavors of Linux.  Sometime in the last week when I boot Ubuntu it now automatically mounts my Dell utility (sda1) and XP (sda2) partitions.  (The other partitions are within the sda3 extended partition.)  That's just a minor annoyance, however I can't unmount those partitions or mount any other partition including my /home (sda7) partition.  I have been able to temporarily circumvent by using GParted to mount /home and unmount the others.  When attempting to mount or unmount a partition (other than U 10.04 of course) I get an error message such as "mount: only root can mount /dev/sda6 on /media/sda6".
I can't think of any change I've made that could have affected this. 
I'm sure this is an easy fix but i can't find a fix within the menu system and as I'm a relative rookie with CLI I'm stuck.
Any help would be appreciated

---

### Post by deesto on 2010-09-21
> **TaterBug said:**
> The following applies to a Dell Vostros 200 w/C2D 2G.

I have a multi-booted setup involving Win XP, 7, Ubuntu 10.04 and a few other flavors of Linux.  Sometime in the last week when I boot Ubuntu it now automatically mounts my Dell utility (sda1) and XP (sda2) partitions.  (The other partitions are within the sda3 extended partition.)  That's just a minor annoyance, however I can't unmount those partitions or mount any other partition including my /home (sda7) partition.  I have been able to temporarily circumvent by using GParted to mount /home and unmount the others.  When attempting to mount or unmount a partition (other than U 10.04 of course) I get an error message such as "mount: only root can mount /dev/sda6 on /media/sda6".
I can't think of any change I've made that could have affected this. 
I'm sure this is an easy fix but i can't find a fix within the menu system and as I'm a relative rookie with CLI I'm stuck.
Any help would be appreciatedDo you get the same errors if you mount the partitions using 'sudo' (e.g., `sudo mount /dev/sda6 on /media/sda6`)?

---

### Post by TaterBug on 2010-09-21
After mucking around a bit I found that /etc/fstab contained references to those partitions with restrictive options.  My other Ubuntu and Mint flavors only referenced their own partition and swap.  After deleting the entries referring to the problem partitions and rebooting everything is back to normal.
Still don't know what I did to cause the problem.

---

