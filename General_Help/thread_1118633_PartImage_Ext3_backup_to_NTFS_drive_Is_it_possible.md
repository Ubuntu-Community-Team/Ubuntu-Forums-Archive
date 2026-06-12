---
title: "PartImage: Ext3 backup to NTFS drive? Is it possible?"
date: 2009-04-07
forum: General Help
---

### Post by Pipps on 2009-04-07
Is it possible to use PartImage to backup a Ubuntu root (sda2) partition to an NTFS (sdd1) external drive?

I tried using [these instructions]("http://ubuntuforums.org/showthread.php?t=226402").

I used the following commands once PartImage had booted:

```

mkdir /backup
mount -t NTFS /dev/sdd1 /backup
partimage

```

All goes fine, until I hit 'enter' at the final prompt before the backup starts. Then, within 10 seconds of the backup procedure starting, I am told:

> Disk full! Can't write next volume file (backup01.001)
to .
Please enter another directory parth (without filename):

I hit 'Cancel'.

Then at the next prompt, I receive:
> Cannot create temp file []. No space left on device.

However, my image to be backed-up is only 2.5Gb, from a fresh Ubuntu installation, and the free space left on my external NTFS drive is 50Gb.

What could be going wrong here? Please help! Thank you.

---

