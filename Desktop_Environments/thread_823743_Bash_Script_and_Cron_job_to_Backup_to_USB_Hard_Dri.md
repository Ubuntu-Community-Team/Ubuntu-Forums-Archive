---
title: "Bash Script and Cron job to Backup to USB Hard Drive"
date: 2008-06-09
forum: Desktop Environments
---

### Post by e30drift on 2008-06-09
I am having a devil of a time with this...

I have a workstation and 2 servers all running 8.04 desktop and 2 server editions respectively.
I have a USB hard drive attached to the workstation.
I want to use a bash script to Tar certain directories on the servers and back them up to the USB hard drive.

The problem is that I don't know much about Bash scripts and cron jobs.  

```
# tar -g /var/sdb1/Sunday/tar-incremental.log -zcvf /backup/today.tar.gz /var/www/html /home /etc
```

I can put that line in terminal and it will backup to the USB drive (sdb1), but when i try to run it on the 2 servers from terminal, of course it will not work as there is no connection to the workstation.  
I enabled Samba on all 3 boxes and shared out the USB drive with the appropriate permissions.
I do not know the appropriate syntax to throw in to that command.
Once I can confirm it works, i need help translating that to a bash script and cron jobs.

(edit):
I want to have daily backups, Sunday - Saturday, each backup job would be a seperate date.  
Here is the file structure that to help:
Root of drive
-Workstation
--Sunday
--Monday
...etc.
--Saturday
-Web
--Sunday
--Monday
...etc.
--Saturday
-MySQL
--Sunday
--Monday
...etc.
--Saturday


Any help would be much appriciated!

---

