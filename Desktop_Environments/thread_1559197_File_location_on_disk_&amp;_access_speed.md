---
title: "File location on disk &amp; access speed"
date: 2010-08-23
forum: Desktop Environments
---

### Post by allaboutsam on 2010-08-23
On a modern system--Lucid, SATA 3.0--does the location of a file on the physical disk make an appreciable difference to its access speed? If so, is there a (safe) way to put a file in a particular place on the disk?

I ask because I would like to reserve some space on disk to remain unused without messing with the partition table. My thought was to do this by using dd to create some large files (4 Gb each, or so) containing zeros. But obviously I would like to put them on the slowest part of the disk, as they won't be used for anything.

Of course, maybe there is a better way of doing this...

Thanks,
allaboutsam

---

### Post by Confucius! on 2010-08-23
I am not sure you are going to see a big access speed increase. This should really be setup when you partition your disk. I dont think creating 4GB files is the way to go because you cannot control where they get stored on the disk. I think the best way to do this is to do a backup and then boot to a live CD. Then using gpart shrink you partition from left to right. Make sure you have enough space for you current Ubuntu install are you are going to be in trouble. After completed run the command sudo "fdisk -lu /dev/sdx" x being the disk you are working on. Then look under start to see where you partitions starts. It should not say one or you did it backwards. This is very risky and I would make sure you have a good backup.

---

### Post by allaboutsam on 2010-08-26
Thanks--that's sort of what I thought. Two tidbits:

First, I forgot to mention that I am using an encrypted LVM. It is unclear to me whether it is possible to specify the physical location of a volume within an LVM, encrypted or otherwise.

Second, before I read your reply I did go ahead and stuff the volume with 4Gb files using dd. I noticed when doing so that the write speed got slower as it went along, then faster for the last few files. I tested the read speed of a sample of the files, and the write speed was an excellent predictor of the read speed (R-squared = 0.97). So I'm guessing that the read/write speed indicates where on the disk the OS put the file.

In the end what I did was to fill all the free space with 4Gb files, then delete ten of the files, starting with the ones with the fastest read/write speeds, to free up the fastest 40Gb worth of disk space. Or such is my hypothesis, anyway!

---

