---
title: "Howto clone an unbootable system to a new partition?"
date: 2006-05-26
forum: Desktop Environments
---

### Post by celiapgt on 2006-05-26
Hello,

I have this problem which I want to solve, if possible, with a package-cloning technique:

I removed my master hard disk from the computer for a while for some reasons, without formatting or else. I have Win200 (hda1) +  Ubuntu 5.1 (hda2) in two partitions. Then I added a slave hard disk, bigger, with three partitions (hdb1, hdb2, and hdb3; this latter partition has EXT3 filesystem).

When I reboot my PC having both disks on it, GrUB replied with Error 18: ... something about cylinders, sectors and heads that don't match BIOS info. I read in Google's found pages that kernel image is to big and far from sector 1 in my master hard disk.  I cannot modify this BIOS info (no passwords, but BIOS doesn't allow me to edit these setting, nor in Auto mode nor User defined mode).

I took advantage of partition hd3 to reinstall a fresh new Ubuntu 5.1, and now I want to package-cloning my system to these new partiton, so I can recover the many packages (and data, also) I added after I installed Ubuntu for the first time. I  can reach the data, because the hda2 partition is not corrupted.

My second Ubuntu 5.1 (in partition hdb3) is running ok, with a /boot in a recently created hda4 partition, in master hd. GrUB boots perfectly well this second Ubuntu, whose kernel is as big as the first Ubuntu! What is wrong with my first Ubuntu, the one with precious data?

First question: is there a technique to achieve this?
Second one: is this the right aproach to solve this problem?

I'd greatly appreciate any help.

---

