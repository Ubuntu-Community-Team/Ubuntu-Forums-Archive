---
title: "(no) Authentication to mount"
date: 2010-01-11
forum: Desktop Environments
---

### Post by manolomanolo on 2010-01-11
Hi to all.

I have got an NTFS partition (as shown by GParted) labelled "COMMON" which is not automatically mounted.
Also, when I try to access to it, I am asked superuser password before letting nautilus mount and list it into my accessible partitions.

The strange thing is that I also have a FAT32 partition (as shown by GParted) labelled "WIN7" and I can directly access to it: it is automatically mounted at startup and also no authentication is required.

[IMG]http://img246.imageshack.us/img246/6188/selection002.png[/IMG]

How to access to the COMMON partition just as accessing to the WIN7 partition? Thanks.

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f2821b42-2df9-461b-a040-7bbe3084bb43 /               ext4    errors=remount-ro 0       1
# /COMMON was on /dev/sda3 during installation
UUID=1B14-0211  /COMMON         vfat    utf8,umask=007,gid=46 0       1
# /WIN7 was on /dev/sda4 during installation
UUID=5513-BEBE  /WIN7           vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda2 during installation
UUID=667a70d3-6777-46ae-9269-3f90cfa4caed none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

After accessing both partitions the mtab is:
```
cat /etc/mtab 
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sda4 /WIN7 vfat rw,utf8,umask=007,gid=46 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/manolo/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=manolo 0 0
/dev/sda3 /media/COMMON fuseblk rw,nosuid,nodev,allow_other,default_permissions,blksize=4096 0 0

```

Ubuntu 9.10 - Kernel 2.6.31-17-generic

---

### Post by sisco311 on 2010-01-11
The third field in fstab describes the type of the filesystem:
```
UUID=1B14-0211  /COMMON         **ntfs**    utf8,umask=007,gid=46 0       1
```

---

### Post by manolomanolo on 2010-01-11
So?

---

### Post by sisco311 on 2010-01-11
> **manolomanolo said:**
> So?

Edit the file:
```
gksu gedit /etc/fstab
```
and replace vfat with ntfs in the partition's fstab entry:
```
UUID=1B14-0211  /COMMON         **ntfs **   utf8,umask=007,gid=46 0    2
```

---

### Post by manolomanolo on 2010-01-11
Sisco, thanks for your suggestion.

I understand that the file system type is NTFS while on the other hand is said to be "vfat" on fstab, but quite the same happens with the FAT32 file system which also is said to be "vfat" on fstab.

So, why do you think that changing vfat to ntfs would make things better?
And also, why "vfat" does work for the FAT32 partition?

Thanks for your time.

---

### Post by Morbius1 on 2010-01-11
Could you please post the output of the following command:
[B]
sudo blkid -c /dev/null[/B]

---

