---
title: "floppy,"
date: 2005-11-16
forum: Desktop Environments
---

### Post by tom_d on 2005-11-16
Hi I am having trouble using the floppy, I finally mounted the floppy and now I get this message root@whitedragon:/home/tom# mount /media/floppy
mount: you must specify the filesystem type
root@whitedragon:/home/tom#
how do I fix this ?   thanks in advance   tom_d

---

### Post by Ampersand on 2005-11-16
Try 
```
mount -t vfat /media/floppy
```

---

