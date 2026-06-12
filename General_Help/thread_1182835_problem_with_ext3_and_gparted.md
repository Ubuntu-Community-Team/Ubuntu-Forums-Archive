---
title: "problem with ext3 and gparted"
date: 2009-06-09
forum: General Help
---

### Post by mafooba on 2009-06-09
Hi everybody, i am a new ubuntu linux user and i have a trouble when i try to resize (make bigger) an ext3 partition (where ubuntu 9.04 is installed) using gparted from an ubuntu livecd.

partitions have this layout:

NTFS||EXT3||SWAP||FREE SPACE||NTFS

The problem is that I cannot change "free space preceding" and "free space following" values (they remain in 0), then I can't resize ext3 partition.

Any idea for this?

Thanks a lot and sorry for my english ;)

greetings from Argentina.

---

### Post by Therion on 2009-06-09
The problem is that you can only expand (resize) a partition by using space that is immediately adjacent to it.  

Your problem is that you have a Swap partition on one side of your free space and and NTFS partition on the other side of it.

I'd delete the Swap partition, expand the Ext3 partition, and then re-create the Swap partition.

---

### Post by mrtomservo on 2009-06-09
I could be completely wrong, but maybe gparted doesn't like that you have a swap between the ext3 and free space.  Maybe you'll have to remove the swap temporarily and then resize your ext3, leaving enough room for you to re-create your swap partition.  :)

Hehehe, Therion beat me to the punch. :)

---

### Post by mafooba on 2009-06-09
thanks! i'll try your recomendations. 
Anyway, before, the layout was thus:

NTFS||free space||EXT3||SWAP||NTFS

But the result was the same,  "free space preceding" and "free space following" values stay unalterable. It means that gparted needs free space adjacent on right side?

thanx again.

---

### Post by michy99 on 2009-06-09
To get a better picture of your situation, please attach a screenshot from gparted or the output of```
sudo fdisk -l
```

---

### Post by mafooba on 2009-06-09
Ok, later at home (i am in work right now) i'll make these tests and publish the results.

thanks.

---

### Post by mafooba on 2009-06-10
> **Therion said:**
> Your problem is that you have a Swap partition on one side of your free space and and NTFS partition on the other side of it.

I'd delete the Swap partition, expand the Ext3 partition, and then re-create the Swap partition. partition.

i followed this steps and it works!
thanks to all

---

