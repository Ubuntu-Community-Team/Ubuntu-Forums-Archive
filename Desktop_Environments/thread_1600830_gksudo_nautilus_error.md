---
title: "gksudo nautilus error"
date: 2010-10-19
forum: Desktop Environments
---

### Post by Werm on 2010-10-19
I get this error in terminal when running the command:

(nautilus:2026): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed


Can this be caused by another separate disk being full? Not the primary... I have no problems doing what I need to do but I would like to know if this is an "issue" or just because one disk is full. Thanks

root@werm-desktop:/etc/X11# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             132G   36G   90G  29% /
none                  2.0G  272K  2.0G   1% /dev
none                  2.0G  100K  2.0G   1% /dev/shm
none                  2.0G  380K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
**/dev/sdc1             597G  596G  393M _100%_ /media/Movies**
/dev/sdb1             233G  165G   69G  71% /media/Storage
/dev/sdd1             3.8G  823M  3.0G  22% /media/A954-BB0A

---

