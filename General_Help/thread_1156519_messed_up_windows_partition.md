---
title: "messed up windows partition"
date: 2009-05-11
forum: General Help
---

### Post by ispy on 2009-05-11
I screwed around with a few settings to tweak my windows partition, and now it won't mount so I can get the files from it.

any ideas?

here's my fstab (including my pitiful attempts at getting it to mount)

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=63871790-84de-4259-a206-914c23624c07 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5029533e-f80c-4640-a538-b9ba22aed809 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

#Windows
/dev/sda1	/media/Windows	vfat	uid=1000,umask=000	2
```

---

### Post by ispy on 2009-05-11
UPDATE:

OK, so after running sudo mkdir /media/Windows (duh! *slaps forehead*) I get this error.

```
:~$ sudo mount /dev/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



```

Help?

---

### Post by geraldvillorente on 2009-05-11
try this one:
Create a directory first for your device to mount to..
```

sudo mkdir /media/windows

```
then, mount your target device to /media/windows
```

sudo mount -t vfat /dev/sda1 /media/windows

```
or with the -o force option 
```

sudo mount -t vfat /dev/sda1 /media/windows -o force

```

---

