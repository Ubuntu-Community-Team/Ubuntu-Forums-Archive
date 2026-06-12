---
title: "Back up my hard drive??"
date: 2008-12-19
forum: General Help
---

### Post by jakenbake42 on 2008-12-19
I am running Ubuntu 8.10 and would like to back up my harddrive automatically and routinely onto my external usb drive. Also, I would like the files to be fully accessible [so I can access them on different operating systems without any additional software]
Thanks in advance!

---

### Post by jerome1232 on 2008-12-19
I think I'd recommend rsync, as it can make incremental backups (only backs up what has changed) and much much more. It's installed in Ubuntu by default.

To make it run on a routine you'd have to make a small simple script and schedule it to run on a schedule in cron.


here is a great guide to look over.
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by xjcannonx on 2008-12-19
I have had a good experience with 'simple backup solution' just search for sbackup in the repos, its easy and will do everything you need it to

---

### Post by DamonChyld on 2008-12-19
I vote for [Partimage]("http://www.partimage.org/Main_Page") ;)

---

