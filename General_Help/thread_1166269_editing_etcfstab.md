---
title: "editing /etc/fstab"
date: 2009-05-21
forum: General Help
---

### Post by The Switch Blade on 2009-05-21
I want to add my Storage drive as a permanent device.

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=56682c83-fcbf-4915-b037-9177abb55cf9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63482991-a509-4d2f-bfa1-3f52d215ad5a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```



sudo fdisk -l
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b037b03

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9598    77095903+  83  Linux
/dev/sda2            9599       10011     3317422+   5  Extended
/dev/sda5            9599       10011     3317391   82  Linux swap / Solaris

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
16 heads, 63 sectors/track, 1240341 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb7931725

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4162     1240338   623033208    7  HPFS/NTFS
```



df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              73G   13G   57G  19% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  224K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  148K  1.5G   1% /dev
tmpfs                 1.5G  188K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sdb1             595G  211G  385G  36% /media/Storage
```

What do I do?

---

### Post by logos34 on 2009-05-21
Use ntfs-config gui:

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron))

---

### Post by uidb4056 on 2009-05-21
You need to add this to your fstab, you should edit it running in terminal:

sudo gedit /etc/fstab

```
# Entry for /dev/sdb1 :
/dev/sdb1 /media/Storage ntfs-3g defaults,locale=en_US.UTF-8 0 1
```Be sure you have installed ntfs-3g, you can search for it in synaptic or install running in terminal:

sudo apt-get install ntfs-3g

---

### Post by logos34 on 2009-05-21
> **uidb4056 said:**
> Be sure you have installed ntfs-3g, you can search for it in synaptic or install running in terminal:

sudo apt-get install ntfs-3g

ubuntu comes with ntfs-3g already installed.  It's the -config gui that's needed, or else manually edit fstab as you suggest

---

