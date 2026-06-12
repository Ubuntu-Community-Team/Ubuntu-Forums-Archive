---
title: "[SOLVED] /var/log/ File Ownerships"
date: 2008-12-31
forum: General Help
---

### Post by WestCoastSuccess on 2008-12-31
I was trying to free up some space on my root partition and decided to archive a bunch of files in /var/log, expecting the system would create new log files (which it didn't), however when I extracted them and returned them to /var/log, ownership reverted to user, and now the system isn't writing to the logs.

Can anyone have a quick look at the following files and tell me who the owner/group is and what the default permissions are (ie: ls -l /var/log):

auth.log
kern.log
syslog
daemon.log
dpkg.log
messages

Many thanks!

---

### Post by SuperSonic4 on 2008-12-31
Admin group for all except dpkg which is root. Full codes below:

```
-rw-r----- 1 syslog adm    44769 2008-12-31 20:59 auth.log
-rw-r----- 1 syslog adm   997301 2008-12-31 18:57 kern.log
-rw-r----- 1 syslog adm   179540 2008-12-31 20:55 syslog
-rw-r----- 1 syslog adm   525152 2008-12-31 18:57 daemon.log
-rw-r----- 1 root   adm  1243771 2008-12-31 19:28 dpkg.log     
-rw-r----- 1 syslog adm   668021 2008-12-31 20:55 messages 
```

---

### Post by WestCoastSuccess on 2008-12-31
Many thanks, SuperSonic4!

---

