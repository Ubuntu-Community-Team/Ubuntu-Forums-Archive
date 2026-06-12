---
title: "Wubi install is 10 times faster than regular dual boot installation"
date: 2012-02-03
forum: Desktop Environments
---

### Post by girishvjadhav on 2012-02-03
I installed ubuntu 11.04 64bit desktop version via wubi over windows server 2003 on my computer with i3 processor and 4 GB ram. A particular sql file used to execute like in 2-3 minutes on my wubi ubuntu install. 

Then I decided to dual boot the system and install 11.10 version of ubuntu on it. Without migrating the wubi install to hard disk, i did a complete new intallation after uninstalling the old wubi install. now the same sql execution is taking 20 minutes to execute. I tested it on a different wubi install just for curiosity and it took 2 minutes to run. the mysql version, and all other software stack were the same on both wubi install and dual boot install. 

What am I doing wrong? Why is it taking long time to execute on dual boot system?

All other softwares also seem to take some extra time to run on dual boot system. Has anyone else experienced the same issue?  How do I resolve this issue?

---

### Post by ajgreeny on 2012-02-03
Usually the other way around, however, you have changed the ubuntu version as well as the install type.

What about other activities that you carry out, which you say run slower;  how much slower, is that a factor of 10x. like your sql problem?

I would bet that your difficulty is down to your new partitioned installed dual boot being "faulty" in some way;  exactly what the problem might be is much more difficult to diagnose.

Check the CD or USB you used to install by booting to it again, hit return when you first see anything on screen, choose language and then check the install medium.  Also check the md5sum of the .iso file you burned against the published figure.
[UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by bcbc on 2012-02-03
Here is the answer: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1) Wubi is faster in some cases, slower in others. 

Still better to have a normal install (Wubi has a virtual disk - single file - so all your data etc. are stored in a single file; which makes it higher risk). It's great to try out Ubuntu though.

---

### Post by oldfred on 2012-02-03
From the link that bcbc posted.

> With SQLite, PostgreSQL, and FS-Mark the Wubi setup was dramatically  faster, which does raise concerns over data integrity with some operations likely  being carried out a-synchronously or batched.

---

### Post by bcbc on 2012-02-03
Wubi is set to sync all writes immediately, to avoid potential data loss or specifically ntfs corruption. Probably normal ubuntu is trying to manage these more efficiently using the journal to prevent errors in the case of hard shutdowns. (I'm speculating with little real knowledge about what goes on, but I tried to follow the links in the article to find out what problems they were alluding to and didn't find anything to clarify that statement).

I'd be interested to see how an ext2 file system compares with the same test, just to rule out inefficiencies introduced by journaling. Or just turn off journaling on the ext4 and see if it makes a difference.

---

### Post by girishvjadhav on 2012-02-08
I have to setup production environment for our product to run. MySql is the main part of our product. How can I make the existing MySql run faster on dual boot machine?

---

