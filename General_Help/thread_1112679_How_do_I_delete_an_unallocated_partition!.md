---
title: "How do I delete an unallocated partition!?"
date: 2009-03-31
forum: General Help
---

### Post by mattj7 on 2009-03-31
I messed up in the middle of installing ubuntu, and now I have this 8gb partition, meant for ubuntu, that is just sitting there unallocated like a piece of pie I can't eat.  How do i delete this partition?  I ran my live usb disk and opened the partition editor, but it would not give many any options on the unallocated partition...  I just want to delete it and get on with my life.  Any help?

---

### Post by zvacet on 2009-04-01
If it is unallocated then it is not partition.It is just free space.You can install Ubuntu on it if you want to.If you want to merge it with some of your existing partition then download [Gparted live CD.]("http://gparted.sourceforge.net/index.php")

---

### Post by hendra40 on 2009-04-01
You can download gparted from add/remove too.
This is other way to get gparted.

---

### Post by ad_267 on 2009-04-01
If it is unallocated space then you can just resize another partition to take up the space.

If there is a partition there then you need to make sure it's not mounted and you should be able to delete it using gparted.

---

### Post by jelle_ on 2009-04-01
you have to unmount the partition before you can resize it. this is difficult when running ubuntu. but you can boot from your ubuntu live-cd. it already contains gparted. now you can increase the size of ubuntu

---

