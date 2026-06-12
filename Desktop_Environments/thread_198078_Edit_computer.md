---
title: "Edit computer:/// ???"
date: 2006-06-16
forum: Desktop Environments
---

### Post by chrilleh on 2006-06-16
I have got my Dapper 6.0.6 x64 up and running. I have mounted my old ntfs disk and they have strange labels that i want to change, but i dont know where to look to edit.

In what config files do i edit the content of "Computer". As you can see in the attached screenshot, there are all the disks with strange names. How do i configure this?

---

### Post by Fatjoint on 2006-06-16
[QUOTE=chrilleh]I have got my Dapper 6.0.6 x64 up and running. I have mounted my old ntfs disk and they have strange labels that i want to change, but i dont know where to look to edit.

In what config files do i edit the content of "Computer". As you can see in the attached screenshot, there are all the disks with strange names. How do i configure this?[/QUOTE]

Go to Applications -> Terminal and type this at the prompt:         cat /etc/fstab

Then copy and paste the results into a reply.

---

### Post by chrilleh on 2006-06-16
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /home           ext3    defaults        0       2
/dev/sda4       /media/sda1     ext3    defaults        0       2
/dev/sda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/western1 ext3    defaults        0       0
/dev/hdd1       /media/western2 ext3    defaults        0       0

/dev/sdb1       /media/oldwin   ntfs    nls=utf8,umask=0222     0       0
/dev/sdb5       /media/scratch  ntfs    nls=utf8,umask=0222     0       0
/dev/sdb6       /media/230gb    ntfs    nls=utf8,umask=0222     0       0


# chroot 32-bit
/home /chroot32/home none bind 0 0
/tmp /chroot32/tmp none bind 0 0
/dev /chroot32/dev none bind 0 0
/proc /chroot32/proc proc defaults 0 0
/media/cdrom0 /chroot32/media/cdrom0 none bind 0 0
/usr/share/fonts /chroot32/usr/share/fonts none bind 0 0

```

---

