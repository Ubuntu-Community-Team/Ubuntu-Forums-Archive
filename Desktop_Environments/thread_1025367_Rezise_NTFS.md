---
title: "Rezise NTFS"
date: 2008-12-30
forum: Desktop Environments
---

### Post by Sin@Sin-Sacrifice on 2008-12-30
So I tried gparted to resize my ntfs partition so I can make more space for a ubuntu studio install and well... look at pic 1 and 2. In the first note that there's 152 GB empty on it (sda1). So I figured on just letting winblows have about 120 GB just in case I find another game that I can't run on wine. Well.. note in screen shot 2 that it's telling me that the maximum size is 258 GB and the minimum size is 6 MB left. It will not let me resize. No matter what I do. Is there another way, maybe through the command line, that I could resize this partition?

---

### Post by hawker525 on 2008-12-31
Is the volume unmounted? if not, resizing or changing of any kind is impossible. I recommend using a livecd for that. Also, I tried that once and it took about 65 hours to resize it.


Maarten

---

### Post by hawker525 on 2008-12-31
This might also be handy:
```
sudo cfdisk
```

---

