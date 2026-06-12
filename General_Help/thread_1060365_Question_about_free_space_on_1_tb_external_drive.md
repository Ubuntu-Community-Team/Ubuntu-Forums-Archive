---
title: "Question about free space on 1 tb external drive"
date: 2009-02-04
forum: General Help
---

### Post by Charlotte18 on 2009-02-04
I have a 1tb external hard drive. It was originally an ntfs drive, and I re-formatted it to ext3. 

When the drive was ntfs and empty, the properties showed 931.4 gb free and 93.6 mb used. Now that the drive is ext3 and also empty, it shows 870.1 gb free and 46.8 gb used.

What's going on with ext3? Something seems very wrong.

---

### Post by blazemore on 2009-02-04
Use gparted to fully delete the partition.
Close right out of gparted, then open it again and create a NEW partition, formatted as ext3

---

### Post by Charlotte18 on 2009-02-04
Thanks, I found the problem.

Ext3 reserves superuser space, and without setting this space manually, mkfs sets it by default to 5% of the total capacity.

I found that I can set a lower percentage manually with the command:
```
mksf.ext3 -m 1 /dev/sdd
```
This sets the percentage to 1% instead of 5.

---

### Post by blazemore on 2009-02-04
Well hey I learned something new. I thought it might be bad bits left over from an inproperly mounted NTFS.

---

