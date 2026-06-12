---
title: "[SOLVED] issue with mounting drive"
date: 2008-12-04
forum: General Help
---

### Post by psmaster on 2008-12-04
I let my brother on my computer for a couple of hours, and now I can not mount my 40GB HDD, and he will not tell me what he did to screw it up!

When I try to mount it, it gives me:
```

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

```

Please help, I have all my projects on that drive!

---

### Post by taurus on 2008-12-04
Is it internal or external harddrive?  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```
And next time, create a new account for him, one without sudo privilege so he won't be able to edit system files.

---

### Post by psmaster on 2008-12-04
internal HDD
```

psmaster@conquest:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0a1d0a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0d9d0d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4864    39070048+   7  HPFS/NTFS
psmaster@conquest:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eb673970-d7db-4df8-a336-cabfa386e42b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ad3b320d-61e9-4f43-9ebb-c040fc667ed3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
psmaster@conquest:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   15G  122G  11% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  208K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.9M  502M   1% /dev
tmpfs                 505M  660K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-9-generic/volatile

```

---

### Post by psmaster on 2008-12-05
/bump

---

### Post by capscrew on 2008-12-06
> When I try to mount it, it gives me:
Code:

mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)



Doesn't the above error code mean the mount point has changed?  Betcha your bro changed or deleted your mount point.  :-(

---

### Post by psmaster on 2008-12-06
ok, I got it fixed.
I mounted it to /media/40GB and changed to mount point of the drive to that when it was mounted.
Thanks for all your help ;)

---

