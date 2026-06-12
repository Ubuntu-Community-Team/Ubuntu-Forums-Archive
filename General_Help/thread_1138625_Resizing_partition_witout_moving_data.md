---
title: "Resizing partition witout moving data?"
date: 2009-04-26
forum: General Help
---

### Post by Frontierbacon on 2009-04-26
Hello

**is there any program for ubuntu that can resize a ntfs partition and just let the files be where they are?**

i have a harddisk with 4 partitions. i've deleted the first 3 on the harddisk, the 4th is full of data and i wanna resize it to take up the entire harddisk. problem is if i try to do this with gparted, it will automatically (cant choose not to) move ALL the data from the 4th partition to the left end of the harddisk.

this is unnessesary since its ntfs, and once im done with the resizing i have other files waiting on another hdd that i will fill the entire new partition up with. so its dosent really matter if the current data is in the start, or the waiting files. jhowever the data on the 4th partitio is some 400gb and i cba to wait 5 hours for it to be moved, not to mention unnessesary writings on the harddisk reducing life time

---

### Post by Frontierbacon on 2009-04-26
bump.
sry :P

---

### Post by unutbu on 2009-04-26
Yes, this is possible. Please open a terminal (Applications>Accessories>Terminal) and post the output of

```
sudo fdisk -l
sudo sfdisk -d > partition_table.txt
```

Post the partition_table.txt file as an attachment.
Indicate which partition you wish to resize.

---

