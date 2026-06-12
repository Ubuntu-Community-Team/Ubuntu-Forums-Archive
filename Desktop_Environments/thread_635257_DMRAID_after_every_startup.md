---
title: "DMRAID after every startup"
date: 2007-12-08
forum: Desktop Environments
---

### Post by adelodder on 2007-12-08
I have an onboard NVRAID for 4 SATA drives.

SATA drives 1 and 2 form a striped RAID. works fine after activating DMRAID and mounting it through fstab.

SATA drives 3 and 4 are two independent drives, but are falsely recognized as a mirrored RAID by DMRAID.

Every time I restart Ubuntu I have to use following commands to get my system how I want it:
```
sudo dmraid -an sil_aebidgcfdhbb
sudo mount -a
```

The first command removes what dmraid thinks to be a mirrored raid.

Can I automate this?

My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=7888c56f-9929-455e-8f90-93d92e4627f7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=10C43F4AC43F30F8 /media/hdb1     ntfs    defaults       1
# /dev/hdb5
UUID=B9954B914CD9790F /media/hdb5     ntfs    defaults       1
# /dev/sda5
UUID=119AB425A351B611 /media/sda5     ntfs    defaults       1
# /dev/sdb5
UUID=DA20D19AFB432F0D /media/sdb5     ntfs    defaults      1
# /dev/hdb6
UUID=474c7798-027e-48fb-86c9-4e1d755e958c none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

/dev/mapper/nvidia_ceedeifh5 	/mnt/movies 	ntfs 0 2

```

---

### Post by Zylar on 2008-01-16
My first thought would be to add those 2 lines to /etc/rc.local, without the sudo.  

Or put those 2 lines in a script and make it executable.  Then use System -> Preferences -> Sessions to add a startup program.

Good luck,

---

