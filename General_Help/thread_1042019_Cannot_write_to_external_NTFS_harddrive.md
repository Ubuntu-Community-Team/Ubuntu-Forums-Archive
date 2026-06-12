---
title: "Cannot write to external NTFS harddrive"
date: 2009-01-17
forum: General Help
---

### Post by KhaaL on 2009-01-17
I'm trying to mount a external harddrive with write permissions without any success at all. I've tried 

```
$ sudo mount -v /dev/sdb1 /media/1touch/
```
and
```
$ sudo ntfs-3g /dev/sdb1 /media/1touch/ -o remove_hiberfile
```

Without much success (it will mount, but only as readonly).

even running nautilus as sudo results with the error message when i try to write somethint to the drive:

```
Error opening file '/media/1touch/178929 (copy).zip': Operation not supported
```

I'm running out of ideas what could be wrong here. my /etc/mtab is as follows....

```
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
/dev/sda6 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/robert/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=robert 0 0
/dev/sdc1 /media/KINGSTON vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdb1 /media/OneTouch4 fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
```

---

### Post by dcstar on 2009-01-17
> **KhaaL said:**
> I'm trying to mount a external harddrive with write permissions without any success at all. I've tried 
......

You should not need to manually mount anything, it should automount unless there is something wrong with the partition.

Run dmesg to see what it reports when you plug the drive in, and also do a **ntfsfix** on the partition.

---

### Post by KhaaL on 2009-01-19
I managed to solve the issue by mounting and un-mounting the device in windows XP. I'll try ntfsfix next time it happens :)

---

