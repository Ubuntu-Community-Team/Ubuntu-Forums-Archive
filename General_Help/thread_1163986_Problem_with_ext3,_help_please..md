---
title: "Problem with ext3, help please."
date: 2009-05-19
forum: General Help
---

### Post by vustovitskiy on 2009-05-19
Hi

   I have Ubuntu 8.10 and ext3 partition. Something occurred with system, I can't copy files from or to file-system, the ubuntu is just hangs up and caps lock indicator is flashing, and I have to switch off through the power button. The disk-check also hangs up the system. I tried to mount it as read-only, but the result was the same. I need only, the ability to copy some of my data from hard drive to USB disk, and then I can reinstall to 9.04 from scratch.

The hard drive seems work Ok, because Windows near Ubuntu works fine.

Thanks for help.

---

### Post by taurus on 2009-05-19
Can you boot your machine with Ubuntu LiveCD?  You can mount that ext3 partition and back up your personal files from the harddrive to an external drive so you can reinstall Ubuntu again.

---

### Post by vustovitskiy on 2009-05-19
> **taurus said:**
> Can you boot your machine with Ubuntu LiveCD?  You can mount that ext3 partition and back up your personal files from the harddrive to an external drive so you can reinstall Ubuntu again.

Yes I can, and I tried this, but the result the same. After few MB system "hangs" and I can only switch the power off.

---

### Post by taurus on 2009-05-19
From Ubuntu LiveCD, can you post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by vustovitskiy on 2009-05-19
> **taurus said:**
> From Ubuntu LiveCD, can you post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

=====================================================================
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc47fc47

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        3735     9028530    7  HPFS/NTFS
/dev/sda3            3736       30401   214194645    5  Extended
/dev/sda5           30141       30401     2096451   82  Linux swap / Solaris
/dev/sda6            3736       30140   212098099+  83  Linux

Partition table entries are not in disk order

==================================================================
df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M   96K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  172K 1007M   1% /dev
tmpfs                1007M   76K 1007M   1% /dev/shm
rootfs               1007M   23M  985M   3% /
/dev/sr0              699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                1007M   12K 1007M   1% /tmp
/dev/sdb1             998M  339M  660M  34% /media/disk
/dev/sda6             200G   96G   94G  51% /mnt

---

### Post by taurus on 2009-05-19
So you have mounted /dev/sda6 to /mnt.  It still crashes when you try to copy something off /dev/sda6--/mnt?  How did you mount /dev/sda6 to /mnt?

---

### Post by vustovitskiy on 2009-05-19
> **taurus said:**
> So you have mounted /dev/sda6 to /mnt.  It still crashes when you try to copy something off /dev/sda6--/mnt?  How did you mount /dev/sda6 to /mnt?

sudo mount -t ext3 /dev/sda6 /mnt

and also I tried readonly mode with -r option, the same result :(

---

### Post by vustovitskiy on 2009-05-19
> **taurus said:**
> So you have mounted /dev/sda6 to /mnt.  It still crashes when you try to copy something off /dev/sda6--/mnt?  How did you mount /dev/sda6 to /mnt?

And even not only during copy as appeared, also when trying to create archive, count size of the folder, even read file.

---

### Post by taurus on 2009-05-19
Maybe you want to run fsck for /dev/sda6.  You first need to unmount it since you can't fsck a partition while it is mounted.

```
sudo umount /dev/sda6
sudo fsck /dev/sda6
```

---

### Post by vustovitskiy on 2009-05-19
> **taurus said:**
> Maybe you want to run fsck for /dev/sda6.  You first need to unmount it since you can't fsck a partition while it is mounted.

```
sudo umount /dev/sda6
sudo fsck /dev/sda6
```

As far as I understand fsck is the same that I can run from the safe-mode loading, option check the hard drive, if it is than I have the same problem, it "hangs". And during the boot if I don't skip check disk, it will hangs as well :(

I tried to run 

   ```
badblock -sp1 /dev/sda6
```

it is ok, no bad blocks have been found, but I have the troubles with fsck, it hangs my laptop.

Any ideas?

---

### Post by vustovitskiy on 2009-05-20
It is totally sucks, i cant do anything, i can't copy files, i can't repair, i can't even work, because it hangs randomly :(

Anyone can help me please?

---

