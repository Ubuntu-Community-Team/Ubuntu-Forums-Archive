---
title: "Config file for USB drives?"
date: 2009-03-28
forum: General Help
---

### Post by mjpatey on 2009-03-28
If permanent drives are configured by /etc/fstab, what's the config file for removable USB drives?

---

### Post by cariboo on 2009-03-28
You can see all mounted drives in /etc/mtab eg:

```
 cat /etc/mtab
/dev/sdc1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/sdc3 /home ext3 rw,relatime 0 0
/dev/mapper/nvidia_ifdejefh1 /home/storage ext3 rw,relatime 0 0
/dev/sdd1 /home/backups ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/sde1 /media/external ext3 rw 0 0
```

In the above print out, my external usb drive is /dev/sde1

Jim

---

### Post by mjpatey on 2009-03-28
Thanks, Jim!  Is there some file like fstab that will allow me to edit the characteristics of the drive?  I'm having a problem with permissions.  For some reason, the drive's permissions have changed to "read-only" for Root, and for my main user, I can read and write folders, but only "access" files, not write them.

When I try to change the permissions to give myself write permission on files, it seems to allow me to make the change, but when I go back and check, it's set back to the previous state.

When I run "fsck.vfat" on the drive (it's formatted to FAT32), it tells me I'm only allowed 1-2 FATs, not 251, and stops there.

Does any of this make more sense to you than it does to me?

---

