---
title: "Installation partition problem - Please help!"
date: 2009-05-24
forum: General Help
---

### Post by Pipps on 2009-05-24
I have the following file system on my single local hard disc:

dsa1         ntfs         windows         56GB
unallocated                               6GB    
sda2         ext3         /boot           94MB
sda3         swap         (sda5)          2MB
sda4         ext3         Ubuntu          10MB

I would like to install another separate Ubuntu installation on the unallocated partition. However, when I try to do this by botting in Live USB mode, I go through the installation procedure as normal, but I receive the following message:

> "No root file system is defined. Please correct this from the partitioning menu

I then opened Gparted in Live USB mode. I clicked on the 'unnallocated' partition, and then clicked 'New', but I received the following error message:

> "It is not possible to create more than 4 primary partitions. If you want more partitions you should first create an extended partition. Such a partition can contain other partitions. Because an extended partition is also a primary partition it might be necessary to remove a primary partition first."

**So my question**
How do I create a new ext3 file system on this 6GB unallocated partition, under these circumstances?

---

### Post by Super TWiT on 2009-05-24
Try creating an extended partition like it recommended. I did this once, and couldn't remember exactly what I did. Also, a separate partition isn't required for the /boot.  However, if stuff is already installed there, it may not work.

---

### Post by nandemonai on 2009-05-24
You can only have 4 primary partitions on a disk, extended partitions included.

If those 4 partitions are primary ones then you're out of luck I'm afraid.

You'd need to delete one, create an extended partition then can use as many logical partitions inside the extended one as you like.

---

