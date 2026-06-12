---
title: "HELP!!! Partition table got whacked"
date: 2005-09-12
forum: Desktop Environments
---

### Post by JayDB on 2005-09-12
I am an idiot! Let's get that out of the way right off the bat. I admit it. 

I have a dual-boot system and I was mucking around on the W98 side of things and the partition software buggered me up totally. Now, I can't boot into anything.

My primary hd is 30 gig and pure W98. However, the partition is relatively undefined now and all anything sees is 30 gig of nothing (should be 5 individual partitions of varying sizes).

My secondary hd is 80 gig and has a swap drive (2 gig), an Ubuntu install, and a FAT32 partition. 

When I boot FreeDos, FDISK shows the second drive as having non-DOS and  FAT32 ( which I am able to access as drive D: ). FDISK shows the first drive as a DOS drive, but it is an inaccessible C:.

I tried the Ubuntu install cd, hoping I could "fix" the install and maybe recover the GRUB info and therefore restore the MBR. No such luck, as "fixing" an install was not an option.

I tried the Ubuntu live cd, hoping for more of the same. No such luck there either.

I tried SystemRestore, but I could not find any way to "reset" the partitions without formatting them.

Does anyone have any suggestions? Or have I just lost two disk drives????

Thank You in advance.

---

### Post by az on 2005-09-12
Boot into the install cd and make your way to the partitioner.  Then go to the F2 shell and use parted to recover lost partitions.

Read the parted online documentation first...

---

### Post by JayDB on 2005-09-12
Thank you for the advice azz. I will give it a try tonight. 

parted to the RESCUE!

---

