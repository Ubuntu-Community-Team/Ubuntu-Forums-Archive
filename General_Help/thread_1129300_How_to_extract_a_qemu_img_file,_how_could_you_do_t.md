---
title: "How to extract a qemu img file, how could you do this?"
date: 2009-04-18
forum: General Help
---

### Post by dragos240 on 2009-04-18
I want to put a debian system on my flash drive, don't tell me how to do it or anything, I just want to know how to extract an img file. How can I do this?

---

### Post by kevstar31 on 2009-04-18
mkdir /mnt/diskimg/
mount -t *filesytemtype* -o loop *diskimg* /mnt/diskimg/

---

### Post by dragos240 on 2009-04-18
> **kevstar31 said:**
> mkdir /mnt/diskimg/
mount -t *filesytemtype* -o loop *diskimg* /mnt/diskimg/

What is an img file's fstype? I know what a filesystem type is, like vfat, ext2, etc, but what is an img file's?

---

### Post by kevstar31 on 2009-04-19
it depends on the image do you know what command was used to write the image or can you post a link to it?

---

### Post by dragos240 on 2009-04-19
> **kevstar31 said:**
> it depends on the image do you know what command was used to write the image or can you post a link to it?

qemu-img create virtualharddrive.img 5G -f qcow

---

