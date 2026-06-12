---
title: "Drive Partitioning...."
date: 2009-05-17
forum: General Help
---

### Post by Dante1217 on 2009-05-17
alright, i just installed Ubuntu today, and i have it on my partitioned HDD. i belive it is split into 2 partitions one has windows xp and one ubuntu. i want to erase ALL my windows partition.. how would i go about doing so? i have downloaded fdisk and wine to run it, but im all out od cd's and only have dvds and fdisk doesnt support dvd format. so untill i can go buy some disks, is there another way that does not invove that?

---

### Post by HermanAB on 2009-05-17
Hmm???  Use gparted.

---

### Post by nandemonai on 2009-05-17
Fdisk and partition editor (gparted) come with Ubuntu by default ;)

No need to use Windows software.

---

### Post by Legace on 2009-05-17
Just open Terminal, and type in **sudo gparted**
If you don't have GParted installed, install it by:
```
sudo apt-get install gparted
```

---

### Post by Ravernomina on 2009-05-17
just boot into your live cd go into system>admin>partition editor find the partion marked NTFS delete it. Then expand your ubuntu partition so u can reap the benefits :)

---

