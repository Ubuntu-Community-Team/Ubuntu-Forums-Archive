---
title: "Is it possibe to change hard drive partition names/labels and keep all data"
date: 2009-03-05
forum: General Help
---

### Post by ozguitarplayer on 2009-03-05
hi
I would like to change the name/label of an extended partition that is loaded with data..can this be done safely and fairly easily or do I need  to use GPartEd to start again with partition names?

any advice is appreciated....

---

### Post by kanikilu on 2009-03-05
I believe you can change the labels in GParted without having to format or do anything drastic. I'm not sure if the devices have to be unmounted or not, though, so if that's the case, you'd have to use the Live CD or GParted Live CD if you want to change the label of the device Ubuntu is installed on.

---

### Post by Therion on 2009-03-05
You can't do much with a partition once it's mounted, so that means using a LiveCD.

Parted Magic is the new gParted:  [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by ajgreeny on 2009-03-05
If it's an ext3 partition you can do it with tune2fs as well ```
sudo tune2fs -L newname /dev/sdx#
```It is quick and works with no problem as far as I've seen.  I don't know if there is a similar utility for fat32 or ntfs partitions, but there may well be.

---

