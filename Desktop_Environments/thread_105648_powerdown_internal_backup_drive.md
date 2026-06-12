---
title: "powerdown internal backup drive"
date: 2005-12-18
forum: Desktop Environments
---

### Post by linuxted on 2005-12-18
Can't seem to get a backup drive to stay powered down when I start the computer.  I've tried added the following scrip to /etc/init.d and created a symbolic link to it in /etc/rc2.d 

# This is to keep noise/power/heat low by powering off the backup
# drive

#umount /dev/hdb
/sbin/hdparm -y /dev/hdb

But alas, this doesn't appear to work.

Any ideas mucho appreciado :)

---

### Post by dcstar on 2005-12-18
[QUOTE=linuxted]Can't seem to get a backup drive to stay powered down when I start the computer.  I've tried added the following scrip to /etc/init.d and created a symbolic link to it in /etc/rc2.d 

# This is to keep noise/power/heat low by powering off the backup
# drive

#umount /dev/hdb
/sbin/hdparm -y /dev/hdb

But alas, this doesn't appear to work.

Any ideas mucho appreciado :)[/QUOTE]
Edit your /etc/hdparm.conf file, you should be able to do better there.

---

