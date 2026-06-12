---
title: "Mouting Data Drive at boot"
date: 2008-12-07
forum: General Help
---

### Post by techboywi on 2008-12-07
My system has two drives, one 20gb where the OS lives, and a data partition.  The data drive is still formatted in NTFS from when I ran windows.  I can usually get the drive to mount by logging in as root or a admin account and clicking on the drive through the Places menu, but I'd like to have the drive automatically mount when I reboot.  Here are my current settings

/etc/fstab
```

root@Xander:/home/techboywi# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=db9f2331-4344-4ff6-9135-b15d5048df34 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5  /media/Data
UUID=991692a5-7f7b-457a-924c-c5ab9308a6f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
tmpfs /dev/shm tempfs defaults,noexec,nosuid 0 0

```

/etc/mtab
```

root@Xander:/home/techboywi# cat /etc/mtab
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/techboywi/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=techboywi 0 0
/dev/sdb1 /media/Data fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

```

Leaving it as /media/Data is fine by me, I'd just like to automatically mount that at boot, so the information on that drive is always available.  Any help you can give would be much appreciated!

Thanks,
Bob

---

### Post by taurus on 2008-12-07
Install ntfs-config and use it to configure your ntfs partition.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by techboywi on 2008-12-07
Just a clarification, its not a partition, its a separate physical drive..

---

### Post by techboywi on 2008-12-07
> **taurus said:**
> Install ntfs-config and use it to configure your ntfs partition.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

Thanks, that did it!

---

