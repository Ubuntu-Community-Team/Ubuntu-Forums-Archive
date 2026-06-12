---
title: "Make FAT32 partition on ext3 disk?"
date: 2005-12-20
forum: General Help
---

### Post by bigblop on 2005-12-20
I have a 20 GB disk where I have installed Ubuntu. Is there some way to make a FAT32 partition on this disk with eg 10 GB without erasing my Ubuntu installation?

I was wondering if I could use Partition Magic from winXP but am not sure that I dare to...

---

### Post by aysiu on 2005-12-20
Any partitioning program should work--just make sure the partition you're trying to resize isn't mounted **and** be sure to back up all your data, just in case.

---

### Post by bigblop on 2005-12-21
Ok then I can just do it from winxp.

On the 20 GB disk I would like to make 10 GB FAT32 that I will just do from within winxp.

Don't know what you mean that must not be mounted. When I access the disk from partition magic from winXP I guess its not mounted?

---

### Post by psusi on 2005-12-21
I do not trust partition magic any further than I can throw it.  All 4 times I have used it or seen someone else use it, it fried the disk.  

Boot up from the ubuntu livecd and use gparted to resize the existing partition and make a new one.

---

### Post by bigblop on 2005-12-21
Ok but officially it should be possible to use partition magic from winxp to do the job right?


I have never had a single problem with PQ and have been using it for years

---

### Post by BathroomNinja on 2005-12-21
'officially' is probably not the right word, but it should work, yes.  same with gparted.  The reason some are shakey about Partition Magic, is that some here have had bad experiences when PM tried to play with linux file systems.  I have personally never used it, so I have no opinion.  I have used gparted and it worked for what I used it for.

---

