---
title: "mounting fat partition"
date: 2009-03-04
forum: General Help
---

### Post by theRightNee on 2009-03-04
hey everyone,

trying to mount a fat partition (labeled /dev/sda1) but it seems like it is not in the fstab file?

can someone tell me what i need to place in the fstab file so that the partition mounts NOT on boot, but when i need to mount it? thanks!

---

### Post by hexanol on 2009-03-04
Something like

```
/dev/sda1   **/mnt/something**   vfat   noauto,uid=**0**,gid=**0**,**utf8**,dmask=007,fmask=117,shortname=mixed   0   0

```

You *might* want to change the stuff I put in bold, especially the "uid" and "gid" values. For more information on fstab, type "man fstab".

---

### Post by theRightNee on 2009-03-15
hey
 

thank you for your help! i am now able to mount the partition to /mnt/spare...however, when i try to access files, i get an permissions error. i made sure to make it rwx for all users so what else could be the problem?

---

