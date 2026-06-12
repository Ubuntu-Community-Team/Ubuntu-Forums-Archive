---
title: "Fstab Drive Mounting Weirdness"
date: 2007-12-30
forum: Desktop Environments
---

### Post by radioraheem on 2007-12-30
I recently setup a new machine and hooked up two existing drives from the old computer.  All three drives are SATA, but one of the older two drives have some weird permissions that I can't seem to correct sudo or otherwise.

sudo fdisk -l  :
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00042804

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00041fcf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14593   117218241   83  Linux

```

sda1 and sdb1 seem to mount and work without a problem, but as for sdc1...

sudo mount /dev/sdc1 /home/user/stuff

Now the user (not using sudo) can go into the stuff directory, but cd'ing into any directory under that gives "Permission denied" errors.

ls -lah on the subdirectories shows this on every file name:

```

?--------- ? ? ? ?                ? File 1
?--------- ? ? ? ?                ? File 2

```

sudo chown -R user:user      runs without returning an error, but does not change any of the files with the above ? permissions.

My fstab is using a pretty standard (as I understand it anyway) setup:

```
/dev/sdc1	/home/user/stuff	    ext3	     defaults	  0	   1
```

dmesg doesn't show anything weird when trying to mount the drive.  I can sudo copy these files to a different drive and then chown/chmod them to a working permission set, but that's the only way I can get access to them.

I figure I'm just exhausted from the holidays and I'm missing something small.  Anyone have any ideas?  

Many thanks in advance for the help!

---

