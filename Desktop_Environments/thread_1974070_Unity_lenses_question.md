---
title: "Unity lenses question"
date: 2012-05-05
forum: Desktop Environments
---

### Post by Ghost_Mazal on 2012-05-05
Lo all ,

I store my music and videos on an external drive and not in my home folder.
The unity lense doesn't show those files.

How can I make unity music and video lenses check and show files on the external drive ?

Thanx

---

### Post by ajgreeny on 2012-05-05
You probably need to mount the external disk and partitions somewhere in your /home using an extra line in /etc/fstab.

Tell us more about the details of where the external disk is normally mounted at the moment, and the filesystem (FAT32, NTFS, ext4) of the partition.  Also whether or not it is always attached.

---

### Post by Ghost_Mazal on 2012-05-05
> **ajgreeny said:**
> You probably need to mount the external disk and partitions somewhere in your /home using an extra line in /etc/fstab.

Tell us more about the details of where the external disk is normally mounted at the moment, and the filesystem (FAT32, NTFS, ext4) of the partition.  Also whether or not it is always attached.

It's mounted at /media/MediaDrive
NTFS
Not always connected

---

### Post by mc4man on 2012-05-05
The music lens will show whatever has been added/available in supported players, currently may just be rhythmbox & banshee in 12.04
So you need to address from that perspective

The video lens just looks in ~/Videos 
Support for other locations either directly or thru a symlink isn't yet enabled
[https://bugs.launchpad.net/unity-lens-videos/+bug/934589](https://bugs.launchpad.net/unity-lens-videos/+bug/934589)

---

### Post by madhi19 on 2012-05-05
Any way to edit the lenses to make it look at other folder or drive.

---

