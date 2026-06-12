---
title: "Error 22 after deleting all partitions"
date: 2009-05-22
forum: General Help
---

### Post by vexxis526 on 2009-05-22
Upgrading from 9.04 BETA to 9.04 using the update manager and alternate CD both were not working on my Dell machine, so I regrettably deleted every partition that I could and created a partition table over sda1 in which I had problems deleting. I was hoping that I could boot from my Dell Windows XP re-installation disc, install from there, then either keep XP on the machine or reformat with 9.04, but I keep getting error 22 every time after the BIOS loads. 

I tried to lauch the Windows recovery console and enter the fixmbr command there, but when I put the Windows disc in, nothing happened. Unless I am doing something wrong, it seems that I can't boot from any discs, as the error 22 message stays on the screen no matter what. Any help is greatly appreciated, as I would love to have this machine working with either Ubuntu or XP for the weekend. I will try my best to supply any information that is needed to help fix the problem. Thanks.

---

### Post by x33a on 2009-05-22
i think you deleted your recovery partition too. hence, you are unable to initiate the recovery process.

to install ubuntu again, put the ubuntu cd in the drive and check it for errors. if it passes the check, then proceed with installation. if it fails the check, you'll have to download and burn another iso and check its md5 for errors.

---

### Post by vexxis526 on 2009-05-22
> **x33a said:**
> i think you deleted your recovery partition too. hence, you are unable to initiate the recovery process.

to install ubuntu again, put the ubuntu cd in the drive and check it for errors. if it passes the check, then proceed with installation. if it fails the check, you'll have to download and burn another iso and check its md5 for errors.

That is what seems to be the problem. Even when I put the disc in, the error message still stays there and nothing happens. I'm going to try it soon and let you know what happens. Thanks.

---

