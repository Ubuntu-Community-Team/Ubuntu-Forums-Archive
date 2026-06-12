---
title: "shell script to auto-log stats"
date: 2009-03-04
forum: General Help
---

### Post by xandout on 2009-03-04
hey all first post!!
i have written a shell script to auto maticly log certain system stats but i need it to run say every 15 minutes, but not interrupt my work. also i need it to close the terminal window from which it runs.  im a n00b so i have no idea how to schedule things and this is my first script so im no pro.

```
#!/bin/bash			
# "Auto Log V1"
# "Script that logs system stats (date, logged in users, system uptime, and network status."

clear
################################ Set Variables #########################################

LOG_DIR=/var/log/autolog
NOW=$(date +"%b-%d-%y")
TIME=$(date)
FILE_NAME=sysinfo$NOW

################################ Execution ##############################################

cd $LOG_DIR			# "Change directories to 'autolog'."

date				# "Get Date"
who				# "Get logged in users"
uptime				# "Get System Uptime"
ifconfig			# "Get Network Status"
clear
echo >> $FILE_NAME		# "Place spaces between last log and this one"
echo >> $FILE_NAME
echo >> $FILE_NAME
echo >> $FILE_NAME
echo "~~~~~~~~~~~~~~~~~~~~~~~~~$TIME~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~" >> $FILE_NAME
date >> $FILE_NAME
who >> $FILE_NAME
uptime >> $FILE_NAME
echo >> $FILE_NAME
echo "__________________________________________________Network Stats______________________________________" >> $FILE_NAME
ifconfig >> $FILE_NAME
echo "_________________________###END OF LOG###____________________________________________________________" >> $FILE_NAME
exit

```

also any criticism is welcome

thank you

---

### Post by phinullfermata on 2009-03-04
I would use a cron job for that.  You can look up how to use it with
```
man cron
```
and you can edit the jobs that should run with cron with 
```
crontab -e
```

Good luck.

---

