---
title: "Resizing FAT32 Partition"
date: 2009-06-15
forum: General Help
---

### Post by JustAnotherVagueAnon on 2009-06-15
I have a FAT32 partition on a separate drive with data on it. I want to make it smaller so I can make another partition on it. There's plenty of room, but can I safely make it smaller without losing any data? I'm using GPartEd but I don't know how fragmented the data is, so it could be spread out near the end. Does GPartEd know how to resize this without losing any data that may be near the "end"?

---

### Post by bodhi.zazen on 2009-06-15
In general you should defragment first, although it is not required.

In general you can resize without losing data, although it is always a possibility.

In general, if it is important to you, back it up.

---

### Post by JustAnotherVagueAnon on 2009-06-15
Ok, thanks. How can I defrag FAT32 with Ubuntu?

---

### Post by synapsys on 2009-06-15
Not that I know of..... maybe you can use the ultimate boot cd for windows.....

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

---

### Post by SuperZ on 2009-06-15
Im pretty sure you can do this with Gparted... Somone please correct me if Im wrong.

---

### Post by Polaris96 on 2009-06-15
If the data is small, burn it all to a DVD or two.   I have resized UNIX'y filesystems with parted and never had a problem.  I'd probably give it a try with FAT32 as long as I had a backup.

Consider wiping out the drive and re-making everything using lvm2.  If you do that, you get a lot of flexibility in resizing and the added bonus of snapshots for data protection.

---

