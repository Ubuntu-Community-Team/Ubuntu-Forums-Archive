---
title: "FTP question"
date: 2008-12-07
forum: General Help
---

### Post by SINZAR on 2008-12-07
Hi,

I'm trying to add a folder from another hard disk into my FTP home directory. The goal is that since the primary disk is nearly full, I could upload to my second disk and download from it as well.

I created a symbolic link in the root ftp directory so the home folder looks like so:

5866865 lrwxrwxrwx  1 root root   21 2008-12-07 13:55 Disk2 -> /mnt/depository/Disk2
6520875 drwxrwxrwx  2 root root 4096 2008-12-07 13:39 Upload

Locally I can switch to the disk2 folder from the ftp home folder and see the test file inside, but when I connect to it using ftp and try to switch to that directory I get a 550 no such file or directory error message. Can anybody give me any tips on what I might be doing wrong?

Thanks.

---

### Post by SINZAR on 2008-12-08
Anybody with any guesses?

---

### Post by CrusaderAD on 2008-12-08
Sounds like a permission issue... check out the permissions with the chmod command. If you want to test it, run 

chmod 777

to open it up for yourself.

---

### Post by SINZAR on 2008-12-09
Gave it a try but still no luck. After a little more digging I found that the only way to solve this is to turn off chroot, which I don't want to do. My other option was to umount it from its current spot and remount it within the users home directory so I remounted it in /var/ftp/Disk2 and now all is working.

---

