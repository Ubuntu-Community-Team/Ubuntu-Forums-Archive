---
title: "fsck during boot causes kernel panic on newest kernel, not older kernel."
date: 2008-12-04
forum: General Help
---

### Post by HousieMousie2 on 2008-12-04
fsck during boot causes kernel panic on newest kernel, not older kernel.

The forced check at boot, with the new kernel, doesn't seem to like my home partition, as it will have a kernel panic about 1/3 of the way through it.  The screen is scrambled, so I don't have any information from that screen as to what is happening/causing it.  fsck has successfully run on the root partition since the new kernel image was applied.

fsck runs on my home partition just fine from the older kernel and once that is done, I can then reboot to the new kernel without problems.

Booting the Live CD and running fsck on all partitions does not show any issues with my drives.

Where should I look to resolve this?  I am not seeing anything obvious in sys.log, syslog.0, dmesg...

---

### Post by taurus on 2008-12-04
Do you have a separate partition for /home and what filesystem does it use?

---

### Post by HousieMousie2 on 2008-12-04
Yes, it is /dev/sdc5.

blkid
```

/dev/sda1: UUID="3A585457585413CB" TYPE="ntfs"
/dev/sdb1: LABEL="HP_RECOVERY" UUID="0127-0A71" TYPE="vfat"
/dev/sdc1: UUID="a0f63e86-505d-4770-9d91-1a72f3c5d85b" SEC_TYPE="ext2" TYPE="ext3"
/dev/sdc2: UUID="274131bb-ed71-427a-94b9-3ef0388feeaf" TYPE="ext3"
/dev/sdb2: UUID="3EE87E06E87DBD29" LABEL="HP_PAVILION" TYPE="ntfs"
/dev/sdc5: UUID="97dfe958-e0dd-4777-a98d-d69a6a0a1b4e" TYPE="ext3" SEC_TYPE="ext2"
/dev/sdc6: TYPE="swap" UUID="8a7aaab4-ee5a-469e-909c-a9be5fe14f7c"

```

mtab
```
/dev/sdc2 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
/dev/sdc1 /boot ext3 rw,relatime 0 0
/dev/sdc5 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
```

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=274131bb-ed71-427a-94b9-3ef0388feeaf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=a0f63e86-505d-4770-9d91-1a72f3c5d85b /boot           ext3    relatime        0       2
# /dev/sda5
UUID=97dfe958-e0dd-4777-a98d-d69a6a0a1b4e /home           ext3    relatime        0       2
# /dev/sda6
UUID=8a7aaab4-ee5a-469e-909c-a9be5fe14f7c none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

```

As you can see, it gets the sda's and sdc's mixed up, but the UUIDs are correct.

---

### Post by taurus on 2008-12-04
What if you just change the last digit from 2 to 0 for /home, then fsck won't scan that partition anymore.  Also, I have my /home mounted with **defaults** instead of **relatime**.

---

### Post by HousieMousie2 on 2008-12-04
Do I need to change that anywhere else, or is fstab and mtab sufficient?

This is a good work around, but it doesn't really cure the ill... which is why is it having a nervous breakdown when fsck my /home when loading one kernel and not the other.

---

### Post by HousieMousie2 on 2009-09-07
:ks

---

### Post by HousieMousie2 on 2009-10-19
I did NOT at all like the idea of not allowing fsck to do what it is supposed to do... that is not a fix, it isn't even a good work around or temporary solution, in my opinion.

What has seemed to have solved the problem, since Linux gets the /dev/sdN# mixed up, is assigning labels.  fsck happily uses the labels and no longer depends on the /dev/sdN#'s to figure out which partition is which, so Linux can get every one of those wrong and fsck won't notice, since the labels are independent of that assigning scheme.

---

