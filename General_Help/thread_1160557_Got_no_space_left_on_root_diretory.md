---
title: "Got no space left on root diretory"
date: 2009-05-15
forum: General Help
---

### Post by hugojmaia on 2009-05-15
Hi everybody, this is my first post on this forum. My problem is the following: I got 110mb of updates and I need to install them on Linux, the problem is, the root has only 2,5GB, it is already full and the updates can only be installed on root. Is there any way to make the root directory bigger or any way to install the updates on another directory? I'll be glad for any help.

---

### Post by Happy_Man on 2009-05-15
run ```
sudo apt-get clean
```

---

### Post by albinootje on 2009-05-15
> **Happy_Man said:**
> run ```
sudo apt-get clean
```

If this doesn't help, then please post the output of the following :
```

sudo fdisk -l
mount

```

---

### Post by hugojmaia on 2009-05-15
All commands did nothing, I need to get that directory bigger or set my default directory for installations and updates on another directory.

---

### Post by albinootje on 2009-05-15
> **hugojmaia said:**
> All commands did nothing, I need to get that directory bigger or set my default directory for installations and updates on another directory.

If you don't want to tell us anything at all about your hard drive partitioning, then I suggest to make a proper backup of your data, and use the "Partition Editor" to resize your / partition if possible.

See also : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck.

---

### Post by Happy_Man on 2009-05-15
Yeah, but what did ```
sudo fdisk -l
``` output?

---

