---
title: "Gparted Missed My Hard Drive.."
date: 2009-03-17
forum: General Help
---

### Post by S.A.A on 2009-03-17
I was trying to resize a NTFS partition with Gparted, when i tried to apply, it gave me an error.
Now, Gparted shows my entire hard as unallocated, but ubuntu is working fine, although that partition (that i tried to resize) can't be mounted any more.
Only if i try (sudo fdisk -l), it shows me the right partitions, Please tell me that i didn't lost that partition.
here is the output of (sudo mount /dev/sda5):
```
NTFS signature is missing.
Failed to mount '/dev/sda5': Invalid argument
The device '/dev/sda5' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

---

### Post by S.A.A on 2009-03-17
Hellow, Is any body Listening :( ?

---

### Post by cd-r80 on 2009-03-17
I had problems once with wrong jumper setting. ?! I saw my disk only with fdisk.

---

### Post by Yellow Pasque on 2009-03-17
> **S.A.A said:**
> Hellow, Is any body Listening :( ?
This is a forum of fellow volunteer users, not a real-time chat of paid tech support specialists. Please try to be a little more patient before bumping your threads. If you bump excessively (more than once a day), mods will generally lock your thread for a while and give you a warning.

EDIT: Sorry, I just saw that you have Ubuntu on that drive as well so using a Windows CD is not the fix. To understand the issue better, I suggest reading: [http://en.wikipedia.org/wiki/Master_boot_record#MBRs_and_disk_identity](http://en.wikipedia.org/wiki/Master_boot_record#MBRs_and_disk_identity)
I would recommend reinstalling GRUB: [http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/](http://roshan18.wordpress.com/2008/02/03/reinstalling-grub-boot-loader/)

---

### Post by S.A.A on 2009-03-17
Sorry for that, I'm Just very worry. and yes i have a windows cd, why ?

---

### Post by Yellow Pasque on 2009-03-17
Nvm about the Windows CD. It was misunderstanding on my part. I edited my post, read it again.

---

### Post by S.A.A on 2009-03-17
I don't think you understand me. i have xp on my pc, but on another healthy partition, the one that have been corrupted has my own files.

---

### Post by S.A.A on 2009-03-17
OK, i tried to install grub and this is what I've got:
```
grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1

Error 15: File not found

```

---

