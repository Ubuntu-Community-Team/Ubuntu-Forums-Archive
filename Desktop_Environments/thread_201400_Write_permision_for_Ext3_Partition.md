---
title: "Write permision for Ext3 Partition"
date: 2006-06-21
forum: Desktop Environments
---

### Post by BeatBoxRocker on 2006-06-21
I have a partition with Ext3 filesystem, the problem is that only root is allowed to write in this partition. I have tried several configurations in fstab and I have changed the attributes of the mount point (chmod 777 & 775) but i dont know what I should do to make it work... ](*,) 

This is the line of my fstab:
/dev/hda5 /media/hda5 ext3 atime,auto,rw,nodev,exec,nosuid,user 0 0

Thanks in advance! Saludos.

---

### Post by jvl on 2006-06-21
man chown

---

### Post by aysiu on 2006-06-21
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by BeatBoxRocker on 2006-06-22
Thanks for the help! I didnt know why but the existing mount point didnt want to work but solved creating a new one with the right permissions.

Saludos!

---

