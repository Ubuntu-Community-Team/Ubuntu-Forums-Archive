---
title: "[SOLVED] Mount ntfs drives automatically"
date: 2008-05-04
forum: Desktop Environments
---

### Post by vvvladut on 2008-05-04
I have two ntfs partitions which used to be mounted automatically in Ubuntu Gutsy. Now I have Kubuntu Hardy, and despite the fact that KDE actually appears to have a GUI interface for mouting drives automatically, where it even lets you specify the mount point, it just doesn't work.

Output of *sudo blkid* :

```
/dev/sda1: UUID="903418093417F148" TYPE="ntfs"
/dev/sda2: UUID="c42245df-09bb-4937-acf9-11091862859f" TYPE="ext3"
/dev/sda3: TYPE="swap" UUID="858eb9bc-66b3-47f2-9ce5-f3efdda713e6"
/dev/sdb1: UUID="0DC03DF22F1A337F" TYPE="ntfs"
```

Output of /etc/fstab:

```
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c42245df-09bb-4937-acf9-11091862859f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=858eb9bc-66b3-47f2-9ce5-f3efdda713e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I would like sda1 and sdb1 to be mounted automatically. Can anyone please tell me what lines I should add to fstab? I did find a few examples on this forum, but what scares me is that each time the parameters after the mountpoint were different...

---

### Post by vvvladut on 2008-05-04
I knew I should have searched these forums more carefully... After a bit more browsing, I found what is clearly the best solution: ntfs-config:

```
sudo apt-get install ntfs-config
```

It's a clever little program that sets up your fstab for you to automount your ntfs partitions at start up.

So thanks for your effort to everyone who replied to this thread...:P I'd mark it as solved, but that's no longer available...

---

### Post by Xiong Chiamiov on 2008-05-04
Marking as solved will be available again shortly, according to the powers that be.  I'm awaiting it eagerly.

This forum isn't particularly high-traffic, and we KDE users often get the shaft, since the people here mostly use GNOME.  You just have to wait a bit longer than you're used to.

---

