---
title: "hard drive problems"
date: 2009-04-26
forum: General Help
---

### Post by jamesdcarroll on 2009-04-26
A few days ago the automatic disk check started and found a bunch of errors. Whenever it asked me if I wanted to let it fix the filesystem I let it, and now the drive seems to be unreadable.  I've looked around to see what the next steps would be, but I would appreciate your insights. 

First, as I boot, there are a ton of "DRDY" errors that from what I've read would seem to indicate a physical problem. But when I go into GPartEd it picks it up and knows the size. When I ask it to check it fails with "Is this a zero length partition and quits. Folks always seem interested in the following:

fdisk -l =>
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35f535f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29835   239649606   83  Linux
/dev/sda2           29836       30401     4546395    5  Extended
/dev/sda5           29836       30401     4546363+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4046d95f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38346   308014213+  83  Linux
/dev/sdb2           38347       38913     4554427+   5  Extended
/dev/sdb5           38347       38913     4554396   82  Linux swap / Solaris

```

and fstab =>
```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
/dev/sdb5 swap swap defaults 0 0
```

But I don't think that's right as I'm running from LiveCD. The drive that's having the problem (/dev/sdb1) used to be where I had ubuntu installed (as well as all my data). /dev/sda1 used to be basically an empty drive that I'm trying to reinstall to with 2 partitions so that I can "dd" everything to it an hopefully save what I have. I've got another thread on that and I'm messin' it up pretty good. :)

If there's anything else I can provide let me know. Any tips would be great as well, but if you have any "Whatever you do, DON'T do that!!!" would appreciated too.

---

### Post by jamesdcarroll on 2009-04-26
I reinstalled and made the extra partition that I wanted for the 'dd' attempt.  I noticed that even though I didn't touch it, the install process decided to format the swap partition on the drive that is having trouble. 

Here is what my fstab looks like now:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71b05d5c-f4d1-40cb-8a97-8c62342b9ee7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=1aef1eda-d3a0-4785-8852-aab7f06e7bab /home           ext3    relatime        0       2
# /dev/sda5
UUID=eff2e5cc-9ebc-4f35-a697-7d975e8e7c1c none            swap    sw              0       0
# /dev/sdb5
UUID=babe5591-a48f-4284-8dd9-62f51888c54e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Is there a way to update this manually to have it see my troubled partition?

Thanks

---

