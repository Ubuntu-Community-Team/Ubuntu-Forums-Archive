---
title: "You are not privileged to unmount the volume"
date: 2009-06-08
forum: General Help
---

### Post by mrakesh85 on 2009-06-08
When I tried to umount  a windows partion by (right click < unmount)the above  message is coming. But when I use sudo umount /media/drivename command  it is unmounting that windows partion. and to mount a drive also I am  able to mount only through sudo mount /media/drivename command I am unable to mount by direct left click of mouse. This is happening only for two partions for remaining partion   I am able to mount by left click and unmount by right click<unmount. 

Thankyou
Rakesh

---

### Post by rogier.de.groot on 2009-06-08
Check that your user account has the right to mount/umount drives. It's in the user/group management tool somewhere.

---

### Post by mrakesh85 on 2009-06-08
> **rogier.de.groot said:**
> Check that your user account has the right to mount/umount drives. It's in the user/group management tool somewhere.

I have checked in users and groups < userprivilages ,acess to external storage devices automatically and mount the user specific file system both were ticked.

thank you
rakesh

---

### Post by rogier.de.groot on 2009-06-09
Is the partition you are trying to unmount an external storage device? If it's a Windows partition on a fixed hard drive, you'd have to edit /etc/fstab to prevent it being mounted with root privileges. I think. Why you'd want to is beyond me though.

---

