---
title: "Changing label of hard drive"
date: 2009-04-08
forum: General Help
---

### Post by Idefix82 on 2009-04-08
I just want to make sure: if I change the label of an external Ext3 hard drive using e2label, is there any risk of losing the data on the drive?
Thanks in advance!

---

### Post by kpkeerthi on 2009-04-08
Do it from a Live CD and make sure the drive is not mounted. I have done that and data were intact.

---

### Post by coffeecat on 2009-04-08
I've often changed an ext3 label of an internal partition using e2label without it affecting the data, so I imagine the same would be true of an external drive. But, no guarantees! :p

By the way, and I only learnt this recently, you can change partition labels of all supported filesystems using the later versions of Gparted. You have to install Gparted, of course, but nice to use a GUI. Iirc you couldn't do this with the Hardy version, but you certainly can with the Jaunty version, and I'm not sure about Intrepid.

---

### Post by coffeecat on 2009-04-08
> **kpkeerthi said:**
> Do it from a Live CD and make sure the drive is not mounted.

Actually, you don't need to unmount the partition. And I don't understand why you would want to use a live CD. It works fine from an ordinary installation.

---

### Post by Idefix82 on 2009-04-08
Thanks, that's what I wanted to hear! In my case, unmounting the partition is no problem without the live cd. Thanks again!

---

