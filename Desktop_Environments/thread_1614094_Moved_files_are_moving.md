---
title: "Moved files are moving"
date: 2010-11-05
forum: Desktop Environments
---

### Post by pbhill on 2010-11-05
I have a 500GB USB hard drive that I use for storing music and video files.
Occasionally I need to do some housekeeping and move some individual files to different folders. Mostly I drag and drop for convenience. This hasn't been a problem until recently when I find that any changes I have made are reversed when I reopen the folders. The permissions seem to be correct. What is causing this?

---

### Post by Barriehie on 2010-11-06
> **pbhill said:**
> I have a 500GB USB hard drive that I use for storing music and video files.
Occasionally I need to do some housekeeping and move some individual files to different folders. Mostly I drag and drop for convenience. This hasn't been a problem until recently when I find that any changes I have made are reversed when I reopen the folders. The permissions seem to be correct. What is causing this?

That was happening with a couple of my drives and I had to change the mount options to sync in /etc/fstab instead of async.

---

### Post by pbhill on 2010-11-06
> **Barriehie said:**
> That was happening with a couple of my drives and I had to change the mount options to sync in /etc/fstab instead of async.

Thanks Barriehie. This is beyond my level of knowledge. Could you or someone elaborate a bit?

---

### Post by Barriehie on 2010-11-06
> **pbhill said:**
> Thanks Barriehie. This is beyond my level of knowledge. Could you or someone elaborate a bit?

;)

 I'll try!  So at boot time there's a file that's read that tell the kernel how to mount attached devices.  It's [color=green]/etc/fstab[/color], it's not a complicated file but it has several fields defining actions, permissions, etc. for devices. My backup USB attached HD has this line, (the blue one):

```

[color=blue]/dev/sdc1 /mnt/backup  ext3    rw,nodev,nosuid,auto,sync       0       1[/color]

Field 1 - the device - /dev/sdc1
Field 2 - the mount point - /mnt/backup
Field 3 - FileSystem type - ext3
Field 4 - mount options - In this case: Read/Write, nodev means can't use a file as the device, nosuid means don't dset SUID/SGID on here, auto means mount it automatically at boot time, and sync means write changes without waiting for the system to determine when it's not busy.  
Field 5 - dump flag to tell whether or not the backup the partition
Filed 6 - fsck flag to determine whether or not to check at boot time, this can be modified via tune2fs.
```

Been awhile since I 'configured' my fstab file but the link I used is [here](http://www.tuxfiles.org/linuxhelp/fstab.html) and I'm sure there are plenty more!

If you're mounting it manually from the CLI you'll have to see the manpages on mount for that one.  I only mount a couple of USB flashdrives every so often and my use of the mount command is no more complicated than:
```
mount -t ext3 /dev/sdd1 /media/USB
``` and then:
```

eject USB<number in the volume label>
```

HTH,
Barrie

---

### Post by pbhill on 2010-11-06
I'll give fstab a try.
But meanwhile, an interesting new development... the same USB drive has now changed all it's permissions to root.  I've never had this happen before. Wierd.

---

### Post by Barriehie on 2010-11-06
> **pbhill said:**
> I'll give fstab a try.
But meanwhile, an interesting new development... the same USB drive has now changed all it's permissions to root.  I've never had this happen before. Wierd.

Back up the original first!

---

