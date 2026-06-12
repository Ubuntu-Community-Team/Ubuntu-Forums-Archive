---
title: "USB key lots of space missing!"
date: 2009-04-07
forum: General Help
---

### Post by triplemaya on 2009-04-07
Just bought a snazzy new USB key, 16gb, but the disk usage analyser reports it as 11.2gb, and at that I've filled it up with 11.2 gig's worth of stuff, and the os says its full.
But fdisk -l reports
Disk /dev/sdb: 16.0 GB, 16022241280 bytes
82 heads, 18 sectors/track, 21201 cylinders
Units = cylinders of 1476 * 512 = 755712 bytes
Disk identifier: 0xd26791a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               6       21202    15642688    c  W95 FAT32 (LBA)

whatmI doing wrong? :@(

---

### Post by mb_webguy on 2009-04-07
I haven't had this problem with a USB pendrive before, but I have with a couple of different SD cards.  For some reason, even though the system detects the card as the correct size, it detects it as full long before it should be.

I've found that reformatting the card fixes the problem.  It should also work in your situation.  Just copy all of the information back off of the drive (since formatting will destroy any information on it), open up GParted, and reformat the thing (as FAT32, of course).

---

### Post by triplemaya on 2009-04-07
Many thanks, that did the trick. Wonder why it was a problem, it was a DIESEL too.

---

### Post by Fenris_rising on 2009-04-07
I had similar problems recently. I think part of my problem was deleting items on the stick but removing the stick without following the proper procedure so that what I had deleted although unseen in a window was still present and taking up space. I always unmount properly now and the space is reported correctly.

regards

Fenris

---

