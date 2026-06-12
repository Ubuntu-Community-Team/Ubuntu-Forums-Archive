---
title: "partitions and mount points"
date: 2006-09-14
forum: Desktop Environments
---

### Post by jordilin on 2006-09-14
Let's say that I have the following partitions:
/dev/hda1
/dev/hda2
/dev/hda3
/dev/hda4
How does Linux know that every time I boot the OS /dev/hda1 must be mounted on /boot, /dev/hda2 on /, /dev/hda3 on /home, etc... Is there a file that tells this or sth?

---

### Post by monktbd on 2006-09-14
yes, you will find that file in /etc/fstab
so e.g.

> cat /etc/fstab

shows you how partitions will get mounted

---

### Post by jordilin on 2006-09-14
> **monktbd said:**
> yes, you will find that file in /etc/fstab
so e.g.



shows you how partitions will get mounted

Oops!! :oops: you are right!!! sometimes I happen to forget about the silliest things!!!

---

### Post by monktbd on 2006-09-14
> **jordilin said:**
> Oops!! :oops: you are right!!! sometimes I happen to forget about the silliest things!!!

tee-hee
and i was wondering when looking at your post count and join date how you managed for so long without knowing that.
(that actually would have been the best prove that ubuntu is very ready for the dekstop ;))

---

### Post by jordilin on 2006-09-14
> **monktbd said:**
> tee-hee
and i was wondering when looking at your post count and join date how you managed for so long without knowing that.
(that actually would have been the best prove that ubuntu is very ready for the dekstop ;))

It has been a shame for moments :oops:

---

