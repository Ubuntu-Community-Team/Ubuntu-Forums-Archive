---
title: "Writing to a mounted ntfs volume"
date: 2006-02-12
forum: Desktop Environments
---

### Post by josh34 on 2006-02-12
I am running the Ubuntu 5.10 live CD and I have mounted a ntfs partition on my windows drive and a fat32 partition on my backup drive. My question is how can I copy files from the fat32 partition to the ntfs partition, I have tried but it says the disk is read only?

Thanks,
Josh

---

### Post by RAOF on 2006-02-12
[QUOTE=josh34]I am running the Ubuntu 5.10 live CD and I have mounted a ntfs partition on my windows drive and a fat32 partition on my backup drive. My question is how can I copy files from the fat32 partition to the ntfs partition, I have tried but it says the disk is read only?

Thanks,
Josh[/QUOTE]
You cannot (safely) write to an ntfs partition from linux.  The filesystem drivers just aren't finished.

Your options are (in order of my recommendation):
1) Not be able to write to the ntfs partition (I recommend this)
2) Investigate 3rd party ntfs drivers - a google search for "captive ntfs" should bring up the Captive NTFS driver page, which last time I was interested seemed to be the best 3rd party NTFS writing drivers.
3) Recompile your kernel modules - you can activate **experimental** NFTS writing support.

Edit: I'm not sure how many of the above are available for use with a live cd.  You should be able to do 2), but I'm not sure.  And you'll need to re-do it each reboot.

---

