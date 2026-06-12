---
title: "fstab error - no boot"
date: 2005-12-08
forum: General Help
---

### Post by Benchrest on 2005-12-08
I added a line to fstab that prevents me from booting. I need to edit the fstab from live cd I believe to delete the line. My problem is I don't understand the MKDIR and MOUNT commands I think I need to use. My system has xp on the master drive (HDA) and Ubuntu is on a slave (HDB) . But I don't know if I should reference HDB1,2,3,4 etc. for the mount.
I have tried:
I called the mount point ubuntu, but I'm not sure where this mount point really is.
sudo mkdir /ubuntu
sudo mount /dev/hdb1 /mnt/ubuntu ext2

Perhaps I need reference to some educational material as I am lost. I do have another Ubuntu system networked to this one but I don't think it can see the drive with xp booted. xp cannot see the ubuntu partitions.

---

### Post by taurus on 2005-12-08
If you want to mount it on /mnt/ubuntu, then you need to create it as 

sudo mkdir /mnt/ubuntu

since /ubuntu is NOT the same as /mnt/ubuntu...

sudo mount -t ext2 /dev/hdb1 /mnt/ubuntu
(means mount the first partition on the second harddrive as ext2 filesystem on /mnt/ubuntu...)

---

### Post by jliedeka on 2005-12-08
I'm not sure what the default partitioning scheme is because I have never used it.  However, /dev/hdb1 is a good guess for the root partition.  You can make a temporary mount point wherever you like for it.  /mnt/ubuntu is a good spot.  Once you mount it (as above) you should be able to cd to /mnt/ubuntu/etc and edit fstab.

---

### Post by fordfan753 on 2005-12-08
I'm not sure if you can create directories using the live cd, so here's what I'd do, and yeah, it might seem slightly dodgy but hey! it's a live cd ;)

```
cd /home/*user*/
sudo mount -t ext2 /dev/*device_name* Desktop
```

This will temporarily mount your partition to the Desktop folder in your home directory, slightly dodgy, but it isn't really used for much in the live disc anyway.

To find out what your device name is have a look at the output from ```
sudo fdisk -l /dev/hda
```

90% of the time it will be using hda, but you may have to try other, ie hdb, hdc, hdd, and if using sata sometimes sda, sdb, sdc, sdd.

---

### Post by Benchrest on 2005-12-08
I want to thank you all for your help. I've got the system running again!

I tried the mount command from taurus and it failed. Thinking it maybe another partition than HDB1 I tried 2-5. 2-4 said they didn't exist. 5 had the wrong filetype. I changed to VFAT and it mount. It was the windows partition I created to pass data back and forth. So I knew I had the command format correct. Fordfan753 suggestion to use fdisk pointing to HDB was the key. Showed my partition is HDB6. I was then home free. Had to use CHOWN to gain ownership to edit. Thanks again. Rich

PS I forgot to unmount but I think it's ok. Need to remember that.

---

