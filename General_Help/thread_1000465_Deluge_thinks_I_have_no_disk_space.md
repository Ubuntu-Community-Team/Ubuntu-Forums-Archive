---
title: "Deluge thinks I have no disk space"
date: 2008-12-02
forum: General Help
---

### Post by wightghost on 2008-12-02
I'm running Intrepid and have finally settled on Deluge for torrents.  This morning, when I tried to start or add a torrent I got the message:

[I]There is not enough free disk space to complete your download.
This torrents will be paused
Space Needed: 126.6 MiB
Available Space: 0.0 KiB[/I]

This, I know, is wrong because there is 28Gb of space on the partition when the torrents are being saved to.  Everything was fine until this morning.  The only change I've made since yesterday is to install VirtualBox but can't imagine that would make any difference.
Can anyone help?
Thanks

---

### Post by plucky on 2008-12-03
Open a terminal and post output of ```
sudo fdisk -l
df -h
```


Have you emptied the Trash lately?

---

### Post by wightghost on 2008-12-03
Thanks Plucky,
I tried clearing all the torrents and then reloading them into Deluge.  Seems to be working fine now.  Weird....

Thanks again

---

