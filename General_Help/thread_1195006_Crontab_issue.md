---
title: "Crontab issue"
date: 2009-06-23
forum: General Help
---

### Post by Sentinel-Being on 2009-06-23
Hey all...

I'm a newbie with most of this so please forgive me.... I am running a crontab on a job every day at 9am

* 9 * * * /home/me/scripts/DailyScript.sh > /dev/null 2>&1

The problem is that the job never seems to end. The script just keeps running. If I run the script manually it begins and ends correctly. When I run it in crontab it doesnt stop and eventually needs the pids killed. Any ideas?


```
#!/usr/bin/ksh


#######
#Run Reports
#######

/opt/LGTOnmc/bin/gstclreport -r "/Reports/NetWorker Backup Status/Daily Summary" -C "Group Start Time" "1 day" -u me -P pass -x csv -f /path/toDailySummary.csv &

wait %1
echo $?

/opt/LGTOnmc/bin/gstclreport -r "/Reports/NetWorker Backup Statistics/Client Summary"  -C "Save Time" "1 day" -u me -P pass -x csv -f /path/toClientSummary.csv &

wait %1
echo $?

/opt/LGTOnmc/bin/gstclreport -r "/Reports/NetWorker Backup Status/Group Details" -C "Group Start Time" "1 day" -u opsjxm -P pass01 -x csv -f /path/tomm_GroupDetails.csv &

wait %1
echo $?

/opt/LGTOnmc/bin/gstclreport -r "/Reports/NetWorker Backup Status/Group Summary by Client and Server" -C "Group Start Time" "1 day" -u opsjxm -P pass01 -x csv -f /path/tomm_ClientStatusOverTime.csv &

wait %1
echo $?

#######
#Truncate Tables
#######

mysql -hitdb2 -ume -ppass -e "truncate table mediamgmt.DailySummary" &

wait %1

mysql -hitdb2 -ume -ppass -e "truncate table mediamgmt.ClientSummary" &

wait %1

mysql -hitdb2 -ume -ppass -e "truncate table mediamgmt.mm_GroupDetails" &

wait %1

mysql -hitdb2 -ume -ppass -e "truncate table mediamgmt.mm_ClientStatusOverTime" &

wait %1

#######
#Import to MySQL
#######

mysqlimport --host=dbase --user=me --password=pass --ignore-lines=8 --fields-terminated-by="," --local mediamgmt /path/toDailySummary.csv &

wait %1


mysqlimport --host=dbase --user=me --password=pass --ignore-lines=10 --fields-terminated-by="," --local mediamgmt /path/toClientSummary.csv &

wait %1


mysqlimport --host=dbase --user=me --password=pass --ignore-lines=10 --fields-terminated-by="," --local mediamgmt /path/tomm_GroupDetails.csv &

wait %1


mysqlimport --host=dbase --user=me --password=pass --ignore-lines=11 --fields-terminated-by="," --local mediamgmt /path/tomm_ClientStatusOverTime.csv &

wait %1

```

---

### Post by geirha on 2009-06-23
> **Sentinel-Being said:**
> 
I'm a newbie with most of this so please forgive me.... I am running a crontab on a job every day at 9am

* 9 * * * /home/me/scripts/DailyScript.sh > /dev/null 2>&1


That will not run it just at 9 am, it will run it at 09:*. That is, 09:00, 09:01, 09:02, 09:03, 09:04 etc... Set the minute field to 0 to have it run at 9am only.

```
0 9 * * * /home/me/scripts/DailyScript.sh > /dev/null 2>&1
```

---

### Post by sedawk on 2009-06-23
As said before, the error was the asterisk in the first column.

But why are you starting every job in the background, only to
wait for it just in the next line?

Your script will look much simpler if you remove all the
"wait" lines and get rid of the background execution by
removing all the ampersands at the end of the lines.
(or do you intend to do parallel execution?)

---

### Post by Sentinel-Being on 2009-06-23
I was told to put the *Wait* and *&* commands in there for troubleshooting purposes. I edited the cron to reflect...

```
0 9 * * * /home/me/scripts/DailyScript.sh > /dev/null 2>&1
```

But it is still hanging out there.

---

### Post by tom17 on 2009-06-23
Try seeing what the output is so you can tell where in the script is is hanging:

```
0 9 * * * /home/me/scripts/DailyScript.sh > /home/me/scripts/DailyScript-Cron.out 2>&1
```

Also maybe put some more echo's in the script so you know *where* in the script it got to before hanging?

Just some ideas, first time I have ever tried helping some random person on here, hope it helps!

Tom...

---

### Post by sedawk on 2009-06-24
Your script doesn' contain any "ksh" specific stuff, so if you
switch to bash instead, I can tell you how to turn on more
debugging (I can't remember how to do it with ksh):

```

#!/bin/bash

set -x 

# Rest of script as before

```

As said before by someone else, do not use /dev/null - you need
that output for debugging!

One problem I can see already now is that you use commands
like "mysql" which might not be in the PATH that is used
by the minimalistic environment of cron. So you have to call
tools with an absolute path or you have to add directories
to the PATH variable in your script, e.g.:

```

#!/bin/bash

set -x 

PATH=/opt/mysql/bin:$PATH

# Rest of script as before

```

---

