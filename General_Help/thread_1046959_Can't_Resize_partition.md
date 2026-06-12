---
title: "Can't Resize partition"
date: 2009-01-21
forum: General Help
---

### Post by leveliv on 2009-01-21
I get the error 

e2fsck -f -y -v /dev/sda1

then it asks if the fs is mounted or used by another program..so I ran 

sudo umount /dev/sda1

but it wasn't mounted
 
im trying to resize my partition so I can get some unallocated space.
 Im using the 8.04 Live CD to try and resize the partition.

---

### Post by talsemgeest on 2009-01-21
Try running ```
sudo e2fsck -f -y -v /dev/sda1
``` from the live cd and, if it gives you errors, post them.

---

### Post by leveliv on 2009-01-21
it just sits at this:

e2fsck 1.40.8 (13-Mar-2008)
Pass 1: Checking inodes, blocks, and sizes

---

