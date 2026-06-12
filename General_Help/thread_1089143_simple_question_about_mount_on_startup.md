---
title: "simple question about mount on startup"
date: 2009-03-06
forum: General Help
---

### Post by jtharp on 2009-03-06
how can I set ubuntu to automatically mount a second hard drive on startup?

---

### Post by LegendofTom on 2009-03-06
You will have to add the following lines to /etc/fstab:

/dev/hda1 /media/win ntfs defaults 0 0

dev/hda1 is only an example, you will have to find what your second hdd is.

---

### Post by Rocket2DMn on 2009-03-06
If it is an external drive, they are typically mounted automatically.  If it is internal, please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
I will help you build the correct entry for fstab.
If you can identify which drive and partition you want, that would help, too.

---

### Post by dcstar on 2009-03-06
> **jtharp said:**
> how can I set ubuntu to automatically mount a second hard drive on startup?

Install the **pysdm** package and use System-Administration-Storage Device Manager.

---

### Post by jtharp on 2009-03-07
thanks for the help guys, pysdm seemed like the easiest method and it works great.  thanks!

---

