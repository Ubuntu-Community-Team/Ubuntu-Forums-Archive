---
title: "Hibernation and Swap partition"
date: 2009-06-20
forum: General Help
---

### Post by cybrosh on 2009-06-20
Can't resume from hibernation : 

free :

```
Swap:      4195792          0    4195792

```

sudo fdisk -l :
```
/dev/sda4           12019       12542     4195800   82  Linux swap / Solaris
Partition 4 does not end on cylinder boundary.

```

sudo vol_id /dev/sda4

```
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=7a006064-efb0-4fce-b954-47dad7b8b426
ID_FS_UUID_ENC=7a006064-efb0-4fce-b954-47dad7b8b426
ID_FS_LABEL=
ID_FS_LABEL_ENC=

```

cat /etc/initramfs-tools/initramfs.conf
```
#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

#
# BUSYBOX: [ y | n ]
#
# Use busybox if available.
#

BUSYBOX=y

#
# COMPCACHE_SIZE: [ "x K" | "x M" | "x G" | "x %" ]
#
# Amount of RAM to use for RAM-based compressed swap space.
#
# An empty value - compcache isn't used, or added to the initramfs at all.
# An integer and K (e.g. 65536 K) - use a number of kilobytes.
# An integer and M (e.g. 256 M) - use a number of megabytes.
# An integer and G (e.g. 1 G) - use a number of gigabytes.
# An integer and % (e.g. 50 %) - use a percentage of the amount of RAM.
#
# You can optionally install the compcache package to configure this setting
# via debconf and have userspace scripts to load and unload compcache.
# 

COMPCACHE_SIZE=""

#
# NFS Section of the config.
#

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# DEVICE: ...
#
# Specify the network interface, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

```

And.... cat /etc/initramfs-tools/conf.d/resume says :

```
cat: /etc/initramfs-tools/conf.d/resume: No such file or directory

```

So where do I put the "resume" ??????

Also, here's the fstab : 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/dev/sda4       none  
```

What do I do?

---

### Post by philinux on 2009-06-20
Your fstab looks unfamiliar. Here's mine.

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
UUID=40558149-061d-43bc-9068-9c34dbdfa6c7 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=39759482-7d7a-4398-b338-2cdf7ed2e99d /home           ext3    relatime        0       2
# swap was on /dev/sda2 during installation
/dev/sda2                                 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by cybrosh on 2009-06-20
I know...it's a dual boot notebook(vista as the primary). 

Still...what do I do?

---

### Post by Legace on 2009-06-20
A Wubi installation of Ubuntu does not support hibernation ([http://en.wikipedia.org/wiki/Wubi_(Ubuntu)#Limitations](http://en.wikipedia.org/wiki/Wubi_(Ubuntu)#Limitations)).

Do a full installation of Ubuntu from the Live CD to get hibernation **and** to make Ubuntu run faster :)

---

### Post by cybrosh on 2009-06-20
:( Thanks

---

