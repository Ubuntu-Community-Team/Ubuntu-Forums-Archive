---
title: "Errant cron results"
date: 2009-02-17
forum: General Help
---

### Post by pjpalmq on 2009-02-17
Greetings,

HISTORY:
I had my crontab executing fine. The scripts it called out worked fine. Due to my not being able to install AutoCAD using WINE (which works fine on my laptop) I decided to start from scratch and rebuild my desktop.  (WINE & AutoCAD issue still not resolved - save for another day).

Now:
When I execute these scripts in a shell they work just fine and produce the desired results. When my crontab executes the scripts the scripts run but produce one empty tar ball and one partial tar ball. Obviously not what I want as a backup.

File permissions on the scripts are set to execute.

My ubuntu release is:

Distributor ID: Ubuntu
Description: Ubuntu 8.10
Release: 8.10
Codename: intrepid

My crontab looks like this:

59 23 2-31 * * /home/pjpalmq/backup/backup.scr
59 23 1 * * /home/pjpalmq/backup/bigbackup.scr

The script (backup.scr) looks like this:

#!/bin/bash
now=`date`
mkdir /Backup/Linux/Nightly/"$now"
touch /Backup/Linux/Nightly/"$now"/"$now"
tar -cvf /Backup/Linux/Nightly/"$now"/My\ Documents.tar /home/pjpalmq/My\ Documents
tar -cvf /Backup/Linux/Nightly/"$now"/Mail.tar /Mail
end=`date`
touch /Backup/Linux/Nightly/"$now"/"$end"

I have also updated my scripts so that all commands have full path's specified as well as files.

Thanks so much for any ideas.

Peter

---

