---
title: "Copy MySQL Database"
date: 2009-02-04
forum: General Help
---

### Post by caseyp80 on 2009-02-04
My motherboard crapped out on me, and my hard drive seems to be at least somewhat corrupted, however I can access files from it when I plug it in to another computer, just won't boot.  How can I copy my MySQL database to a fresh install of an Ubuntu LAMP server without having a command line interface to that MySQL database?
Thanks for any advice!

---

### Post by mb_webguy on 2009-02-04
Assuming you have the drive plugged in so you can access the files, and that you have a standard installation of MySQL...

Stop MySQL with "sudo /etc/init.d/mysql stop".  Make a backup of the current (clean) MySQL data directory with "sudo cp -Rp /var/lib/mysql /var/lib/mysql.backup".  Then copy the old data directory from the old drive with "sudo cp -Rp /mountpoint/var/lib/mysql /var/lib/mysql", where "mountpoint" is the path to the mount.  Now restart MySQL with "sudo /etc/init.d/mysql start".  With any luck, MySQL should restart, and you should have your old databases back.

(Btw, make sure you use the "R" and "p" options for the cp commands in order to copy the entire directory contents and retain the existing owner, group, and permissions.)

---

