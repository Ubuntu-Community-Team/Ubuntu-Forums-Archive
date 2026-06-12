---
title: "remove to trash"
date: 2009-01-29
forum: General Help
---

### Post by karimla131 on 2009-01-29
hi i use ubuntu 8.10 and i have a problem  when i delete any folder or file it say can not delete to the trash do you want to delete it from immediately ??
my hard desk is sata 160 G
so can anyone help please

---

### Post by redilyn on 2009-01-29
By any chance is this hard drive formated as NTFS?

Just tested on my ntfs partition and can not move to trash.

I think you need to use a linux fs such as ext3

---

### Post by karimla131 on 2009-01-29
yes it is ntfs driver so how can i linux fs

---

### Post by russu52 on 2009-01-29
make sure the drive you want to format is unmounted first:
terminal>
sudo umount /dev/sdb1 where sdb1 is the drive you want to format.

then:
sudo mkfs.ext3 /dev/sdb1 to format the drive to ext3

---

### Post by redilyn on 2009-01-29
The good news is it is easy to change your partition to ext3.

The bad news is you will have to delete your partitions and recreate them as ext3.

Depending on how long you have been using ubuntu and how many personal files you have on your hard drive this may not be a viable option.

Unfortunately i do not know of any way to convert from ntfs to ext3 or any other linux file system.

The big thing you need to decide is:

-Do you really need to ability to put files into the trash?
-Can you afford a reinstall of ubuntu?

Also, The drive you are talking about. Is ubuntu installed on it?

---

### Post by karimla131 on 2009-01-29
any way thank you

---

### Post by russu52 on 2009-01-29
> **karimla131 said:**
> any way thank you

it didn't work?

---

### Post by redilyn on 2009-01-29
Russu52, You gave him a command to format his drive without even asking if there was anything on it that he needed.

Lets hope it didnt work. :)

---

### Post by mb_webguy on 2009-01-29
Hrm... I'm using Intrepid, and the "Move to Trash" option in Nautilus works just fine on my ntfs drive.  Maybe it has something to do with how the drive is being mounted (e.g. uid, gid, and/or permissions)?

---

