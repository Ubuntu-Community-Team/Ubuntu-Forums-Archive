---
title: "linux mounting my hard drive ruined the data - any hope?"
date: 2009-06-09
forum: General Help
---

### Post by jeff00z28 on 2009-06-09
It is a 500b hard drive storing all of my music, applications, videos, etc. I didn't back it up anytime lately. I installed ubuntu and was using it fine, then i unplugged hte ubuntu hard drive and plugged in another hard drive to install windows and had the 500gb in as well, and after i installed windows linux would no longer detect/mount it. I threw it in a computer with xp and this is what i see now. I really dont want to download everythign from scratch especially with Oink not around anymore. Thanks.

[IMG]http://i39.tinypic.com/34zyf6u.jpg[/IMG]

---

### Post by justleen on 2009-06-09
Windows cant handle ext2/ext3. So it will see a disk, but doenst have a clue what to do with it.
If you need access from windows I'd advise you to install the Ext2 IFS driver, found here [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jeff00z28 on 2009-06-09
> **justleen said:**
> Windows cant handle ext2/ext3. So it will see a disk, but doenst have a clue what to do with it.
If you need access from windows I'd advise you to install the Ext2 IFS driver, found here [http://www.fs-driver.org/](http://www.fs-driver.org/)

thanks but it was actually originally formatted in ntfs. i got it to list the folders with this data recovery software. hopefully it works out, if not i will be hitting a lot of torrents

---

### Post by theozzlives on 2009-06-09
Did you safely remove the drive when in windows?

---

