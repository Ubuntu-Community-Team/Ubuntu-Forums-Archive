---
title: "HDD Recovery"
date: 2008-12-28
forum: General Help
---

### Post by kaska1 on 2008-12-28
Hi all, I have a Hard drive connected to a NAS drive via the usb port on the nas unit. The hd inside the NAS unit failed recently, so I had to remove and attach the external usb drive to a laptop to view those files. Naturally, I chose to install ubuntu on the laptop. After I replaced the hd inside the NAS drive, I tried mounting the USB HD. But it wouldn't allow me to mount it, saying that the fsystem is incorrect, even though its in ext3. So anyway being a newb that i am, i typed mkfs.ext3. And i proceeded since it didn't even warn me that i'd lose all my files. 

Anyway, 20% into the formatting, i realize i'd lose all my files, so i stopped it. So now i am wondering whats the best way to proceed to recover all those files back? Is it possible to recover the files with the directory structures still in tact? 
I'd really appreciate it if someone can help me get all those files back. Thanks!!!

---

### Post by kaska1 on 2008-12-28
bump

---

### Post by linux_tech on 2008-12-28
here is a good overview of several different programs for this task-
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Testdisk & photorec are a well known and well documented data recovery programs-
[http://www.cgsecurity.org/wiki/Main_Page](http://www.cgsecurity.org/wiki/Main_Page)

---

### Post by Sef on 2008-12-28
Get [Knoppix]("http://knoppix.com").   If it can read the hard drive, it may be able to recover the files.  I have used it on hard drives that don't boot up.

---

