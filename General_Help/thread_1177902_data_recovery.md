---
title: "data recovery"
date: 2009-06-03
forum: General Help
---

### Post by heyitsaustin123 on 2009-06-03
I have a ntfs 160gb external HDD that is full of about 20gb of music a bunch of movies and all my stuff for school. I was trying to make a partition in gparted. It didn't say new under partition so I thought I had to create a partition table. Well I didn't see where it said that I would lose all my files instantly so I continued, and then gparted froze so I closed it.And now when i try to mount the drive it says "unable to mount location" "can't load file". I have no idea what to do. Is there anything i can do to get my files back. I looked around on google and the forums but didn't find much Any help is greatly appreciated. Thank-you in advance.

---

### Post by blueridgedog on 2009-06-03
If you think the partition table is corrupt, you can try and recover it with testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can install it with ```
sudo apt-get install testdisk
```

You can do a quick scan with testdisk and see if it can see the ntfs partition.

If you think the partition was overwritten, then a product like formost may help:  [http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

---

### Post by QIII on 2009-06-03
I'm with blueridgedog on TestDisk.

I've recovered a lot of data for people who accidentally push the "big red button" (including myself!)

---

### Post by colau on 2009-06-03
> **blueridgedog said:**
> if you think the partition table is corrupt, you can try and recover it with testdisk: [http://www.cgsecurity.org/wiki/testdisk](http://www.cgsecurity.org/wiki/testdisk)

you can install it with ```
sudo apt-get install testdisk
```

you can do a quick scan with testdisk and see if it can see the ntfs partition.

If you think the partition was overwritten, then a product like formost may help:  [http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)
+1

---

### Post by heyitsaustin123 on 2009-06-03
> **blueridgedog said:**
> If you think the partition table is corrupt, you can try and recover it with testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You can install it with ```
sudo apt-get install testdisk
```

You can do a quick scan with testdisk and see if it can see the ntfs partition.

If you think the partition was overwritten, then a product like formost may help:  [http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Thank-you so much! I thought i lost all my data. Thank-you Thank-you Thank-you!

---

