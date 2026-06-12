---
title: "boot weirdness after moving /usr"
date: 2005-12-18
forum: General Help
---

### Post by tafsiri on 2005-12-18
Hi,

I previously had the /, /usr and /home directories on different partitions. After moving /usr to be on the same partition as / i have been getting buffer i/o errors on startup, they look like this. 

[4294800.003000] Buffer I/O error on device dm-4, logical block 123479

I get about 50 or so of these things, after which the computer boots up just fine and everything seems to work (nothing bad has happened yet). I tried checking all my partitions with fsck and badblocks, but they report no error. The method i used to move the partition was to create a new directory in / copy all the stuff from the old /usr into this directory. Unmount the old /usr and remove its entry in fstab and then rename the new directory (now on the same partition as /) to usr.  These errors come during the enterpise volume management part of the boot. Have i missed somthing crucial in moving the /usr. The drive is fairly new (about 6 months old) and i would be surprised if it were failing already. By the way i am using reiserFS as a filesystem on all my partitions (in case this is relevant).

thanks

---

