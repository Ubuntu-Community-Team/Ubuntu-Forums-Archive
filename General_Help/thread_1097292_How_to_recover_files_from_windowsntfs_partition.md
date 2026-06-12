---
title: "How to recover files from windows/ntfs partition?"
date: 2009-03-15
forum: General Help
---

### Post by elymic on 2009-03-15
Hi all,

I'm posting my question here, shortly after an unsuccessful removal of dozens of viruses from my data (ntfs) partition and an eventual total loss of the windows os. I have been accessing my data partition mostly under Windows xp, although I had a separate partition with xubuntu. Then the antivirus informed me of a virus attack over my os, and soon after - while running a thorough scan - windows failed to function. Now when booted from the xubuntu partition and try to I look for my data or even for the windows partition I can't find it anywhere... the nearest thing the I could find is sda1, sda2 etc., but they are all tagged as "blocked device" (with an "x" sign on the icon). I desperately need to find a way to clean up my data partition from the viruses, while running it under xubuntu. Other relevant threads suggest to use clamAV but in my situation it cannot reach the correct partition from the reason mentioned. Hoe is this possible? and how can I at least view my infected files? I know they are there, because when I boot from GPartEd, it's showing that the data partition contains 80Gb. What do you pros recommend in such a case?

Thanks a lot!

Michael

p.s. I am not that concerned about the windows partition, it's only the data partition that I am interested in saving from the viruses.

---

### Post by TCSnyder on 2009-03-15
you can use this command to see attached devices

```
df -h
```

find your hard drive and try to force mount it

use

```
sudo mount /dev/sd* /media/harddrive/ -o force
```

you will have to make the /media/harddrive directory first and replace sd* with your hard drive device name.

---

### Post by bodhi.zazen on 2009-03-15
Moved to general help as it seems more a data recovery question then anything else.

See this link : [http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by elymic on 2009-03-25
forcing the mount for the data partition works very well, but it has to be typed every time the laptop starts up (either from suspend mode or after a restart). How can I permanently mount the partition?
thanks

---

### Post by bodhi.zazen on 2009-03-25
To fix this you need to boot windows and unmount the partition properly.

You should also know that, although rare, forcing a mount can cause data loss.

If you no longer run windows, I suggest you pull the data and reformat the partition to a linux native file system.

---

### Post by mal_conductor on 2009-03-29
Use testdisk and/or photorec.

Here are my notes:  Hope it helps.

[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

