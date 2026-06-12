---
title: "Backing up Wine"
date: 2009-05-07
forum: General Help
---

### Post by Gideony on 2009-05-07
I'm pretty new to this linux thing, but I managed to get Wine working with Office 2007.  It took about three installs though, and I REALLY don't want to do it again.  I'm wanting to play with some different distros and was wondering if it was possible to back up the Wine data so I can just quickly move it to the new system.

If so... please provide rather complete instructions on how to back up and restore, I'm pretty new to this but really want to make Ubuntu work for me.

Thanks!

---

### Post by albinootje on 2009-05-07
> **Gideony said:**
> was wondering if it was possible to back up the Wine data so I can just quickly move it to the new system.


It's easy, you only have to back up the directory .wine in your home directory.

In Nautilus file manager press "ctrl-h" to make "hidden" files and directories visible. Right click on that directory, and choose "Create Archive".

---

### Post by Gideony on 2009-05-07
Okay....  trying this.  When I try to create an archive I get "permission denied"

When I try to just copy it to another drive I get this error "Error making symbolic link: Operation not permitted"

Any suggestions?

Thanks!

---

### Post by albinootje on 2009-05-07
> **Gideony said:**
>  When I try to create an archive I get "permission denied"

When I try to just copy it to another drive I get this error "Error making symbolic link: Operation not permitted"


Is the other drive an external drive ?
Can you post the output of the following in a terminal :
```

mount
cat /etc/fstab
sudo fdisk -l

```

---

### Post by Gideony on 2009-05-07
mount:
```

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gideon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gideon)
/dev/sdd1 on /media/Comicus type hfsplus (rw,nosuid,nodev,uhelper=hal)
/dev/sdc1 on /media/QUICK type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=gideon)
/dev/sdb2 on /media/Niebuhr type hfsplus (rw,nosuid,nodev,uhelper=hal)

```
I'm trying to put it on the "Quick" partition
fstab:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=73199fff-57d2-4c58-b12b-14129524c922 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=6166253b-d4a8-473f-a082-d3883c38af86 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
fdisk
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa347159f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       23699   190152704   af  Unknown
/dev/sda3           23715       30402    53710938   83  Linux
/dev/sda4           23699       23715      129883   82  Linux swap / Solaris

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976762583+  ee  GPT

Disk /dev/sdc: 8000 MB, 8000004096 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         973     7812472+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(972, 155, 63)

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6cc0e4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60802   488386552+  af  Unknown

```

Thanks alot!

---

### Post by Gideony on 2009-05-07
And I am trying to put it on an external drive, though I also tried just putting it on the desktop.  I can write to "Quick" (though not to Comicus... working on getting that working still)

---

### Post by albinootje on 2009-05-07
> **Gideony said:**
> And I am trying to put it on an external drive, though I also tried just putting it on the desktop.  I can write to "Quick" (though not to Comicus... working on getting that working still)

Thanks for the information.
Did you manage to create an archive now ?
You can also create an archive on the CLI like this :
```

cd /media/QUICK/
tar czvf wine-archived.tgz ~/.wine/

```
If you would do that, then the possible error message could possibly be clearer to be used to solve this problem.

"Comicus" uses hfs-plus, which needs to have the journal turned off before Linux can read/write to it afair.

---

### Post by Gideony on 2009-05-07
re: Comicus
Yeah, I've turned off journaling but I'm still not having any luck.  I'm playing with a few things, hopefully will get it going.

The archive seemed to create from the terminal (though still not from the GUI).  Thanks a lot!!!

---

