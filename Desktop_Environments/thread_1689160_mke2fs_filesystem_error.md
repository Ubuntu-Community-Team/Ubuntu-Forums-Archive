---
title: "mke2fs filesystem error"
date: 2011-02-16
forum: Desktop Environments
---

### Post by petebarchetta on 2011-02-16
Hello all,
I'm running a toughbook cf-m34 PIII with xubuntu 8.04.
anyway recently had issues with a usb stick, 1gb size

it refuses to format / create partition through the gparted app. when dropping to command line and doing a sudo fdisk -l it comes back with a
"error: unable to open /dev/sdb - unrecognised disk label"

suggesting somethings amiss

so when i run:
mke2fs -L red-disk /dev/sdb
it comes back with the error
"mke2fs: permission denied while trying to determine filesystem size"

---

### Post by mcduck on 2011-02-16
Your problem is that you are trying to format a drive (/dev/sdb) instead of a partition (/dev/sdb1, for example).

You have to first create a partition and then you can format it with a filesystem.

---

### Post by petebarchetta on 2011-02-17
hello, yes i see that. I know i am one step ahead of myself.
when i create the partitionin gparted it bombs out with a disklabel error thus meaning i cant create a partition. is there any way i can force a partition onto the drive without a disklabel?

---

### Post by mcduck on 2011-02-17
Shouldn't be a problem at all, I rarely label any partition. You don't need to force anything to do that. :D

---

### Post by petebarchetta on 2011-02-17
so i'm not running around in circles. can you advise of the command as i'm stuck on this one

---

### Post by mcduck on 2011-02-17
> **petebarchetta said:**
> so i'm not running around in circles. can you advise of the command as i'm stuck on this one

I thought you were using gparted? :D Make sure any existing aprtitions on the drive are unmounted when you try to modify the drive's partiitoning.

Anyway, if you want to do it from CLI, you need to use fdisk. mke2fs will not create a partition for you, only the filesystem (although fdisk should handle that as well).

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")

---

### Post by petebarchetta on 2011-02-18
the whole drive is unmounted. which is the odd bit. it should let me do something. i could understand that if i had say a file wondow open or an app doing something to the drive. but i cant even see it on my system.
sudo fdisk -l
brings up the error.
device manager see's it hanging off /dev/sdxxx
but when i try to do anything at terminal or through gparted it errors out

---

### Post by petebarchetta on 2011-03-15
Running gparted up again results in the same error of setting disklabel, I've installed testdisk onto the machine and it shows up on there, it shows a bad bock xenix???
Any ideas?

---

### Post by petebarchetta on 2011-03-28
information from testdisk is as follows,
partition 1 = sys=57
partition 2 = sys=DF
partition 3 = Xenix bad block
partition 4 = Sys=5B

any suggestions?
though WindozeXP it reports as RAW and wont format either

---

