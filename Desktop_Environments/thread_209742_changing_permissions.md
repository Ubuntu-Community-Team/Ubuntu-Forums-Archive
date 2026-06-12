---
title: "changing permissions"
date: 2006-07-05
forum: Desktop Environments
---

### Post by doormans on 2006-07-05
I recently added an external usb hard drive and  want to be able to backup files to it.  get an error message stating that it only has read permissions and no write. How do  change the permissions to read and write for this? thanks

---

### Post by kpkeerthi on 2006-07-05
Can you post what is the result of ```
$ sudo fdisk -l
$ mount
```. We can proceed from there.

---

### Post by aysiu on 2006-07-05
Sounds as if it's NTFS or something...

---

### Post by doormans on 2006-07-05
Got it fixed. I had it formatted with ntsf. Thanks for the help and quick replys.=D>

---

