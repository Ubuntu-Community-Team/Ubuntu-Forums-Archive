---
title: "Mounting Partition Problems"
date: 2006-09-18
forum: Desktop Environments
---

### Post by topheth on 2006-09-18
This will seem silly to some, but I'm new to Ubuntu and cannot figure this out.

I've a FAT32 partition I wish to access.
The created file is /media/fat32_part and I have permissions.

However, whenever I go to System->Administration->Disks and mount this partition to that location, permissions change to root only and I cannot write to partition.

So how does one do this?  

Thank you in advance.

---

### Post by artinla on 2006-09-18
sudo chown <your username> /media/fat32_part
then
just sudo nautilus and change the permissions to whatever you want.

---

### Post by topheth on 2006-09-18
Thank you for the reply...

However, how do I mount a partition without it changing file owner to root?

I try:  sudo mount /dev/hdb1 /media/fat32_part

and it changes file owner to root.

---

