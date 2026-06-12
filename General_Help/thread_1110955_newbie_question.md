---
title: "newbie question"
date: 2009-03-30
forum: General Help
---

### Post by alcav on 2009-03-30
Hi,

if I install ubunto on to a hdd which at the moment is used for b/up from an existing hdd,will Ubunto read the backed up files?.

Regards      Alan

---

### Post by chriskin on 2009-03-30
can you clarify what you want to do?

ubuntu will be able to see any files on any partition/drives.
sometimes it needs some working to make ubuntu able to edit them, not much to be honest though.

i just fail to undestand if you want to install ubuntu on another partition of the disk, or on the same. if it is in the same partition, everything will be lost while formating to ext3

---

### Post by 3Miro on 2009-03-30
> **alcav said:**
> Hi,

if I install ubunto on to a hdd which at the moment is used for b/up from an existing hdd,will Ubunto read the backed up files?.

Regards      Alan

Ubuntu will destroy all data on the partition where you install it (unless you are using wibi or something like that). Ubuntu will see all other data on all other partitions.

---

### Post by linux_tech on 2009-03-30
> **alcav said:**
> Hi,

if I install ubunto on to a hdd which at the moment is used for b/up from an existing hdd,will Ubunto read the backed up files?.

Regards      Alan

ubuntu should read the files ok. what format is the partition they are on?
If you install on the same drive, best to backup the files first as a precaution.

---

### Post by chriskin on 2009-03-30
> **linux_tech said:**
> ubuntu should read the files ok. what format is the partition they are on?
If you install on the same drive, best to backup the files first as a precaution.


excuse the off-topic post. 
i have your avatar printed as stickers. well mine has "GNU/Linux" where yours has just "linux" but it has the same design.


now back to topic..

Alan, in case you are going to install in tha same disk, partitioning with gparted will help you save both space for ubuntu and your files.
in case you need this option, ask for help and we will try

until then i can't see a reason for more of us replying the same thing :)

---

### Post by alcav on 2009-04-05
Thanks everyone for your help.I have a good idea how to do it now :o)

Alan

---

### Post by mikewhatever on 2009-04-06
> **3Miro said:**
> Ubuntu will destroy all data on the partition where you install it (unless you are using wibi or something like that). Ubuntu will see all other data on all other partitions.

This is a funny way to put it. If you think about it, Ubuntu isn't the one who clicks OK to format a partition. ;)

---

