---
title: "Crontab Not Executing Commands"
date: 2009-06-25
forum: General Help
---

### Post by kingnerd on 2009-06-25
Hey guys, sorry for bothering you, but I have the following file that I have imported into crontab several times (yes, I checked it with both crontab -e and crontab -l), and it is not executing the cp commands.  I also tried it with /home/user instead of the ., but that also did not work.  Any help would be greatly appreciated.

```
0 0,10,20 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup1.dat
0 1,11,21 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup2.dat
0 2,12,22 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup3.dat
0 3,13,23 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup4.dat
0 4,14 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup5.dat
0 5,15 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup6.dat
0 6,16 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup7.dat
0 7,17 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup8.dat
0 8,18 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup9.dat
0 9,19 * * * /bin/cp ./My\ Documents/Mine/server_level.dat ./My\ Documents/Mine/backup/backup10.dat
```

---

### Post by geirha on 2009-06-25
Cron will execute those commands from / (the root), so you definately need to provide the absolute path for those files.

Also, try adding the following at the end of each line:
```
 >>/tmp/backup.log 2>&1
```

This will send any output from the command to /tmp/backup.log, so check that file after it should've run.

---

### Post by kingnerd on 2009-06-25
> **geirha said:**
> Cron will execute those commands from / (the root), so you definately need to provide the absolute path for those files.

Also, try adding the following at the end of each line:
```
 >>/tmp/backup.log 2>&1
```

This will send any output from the command to /tmp/backup.log, so check that file after it should've run.

Still won't execute, and nothing in /tmp/backup.log afterwards.  If I copy and paste the command that I entered for cron to execute, it works fine.  (I also changed . to /home/user, and yes my username is user).  Any help would be appreciated.

---

### Post by geirha on 2009-06-25
How far into the future did you put your "test" job? You should make sure it is at least two minutes into the future, because cron will wait until the next minute to load the new crontab (after running crontab -e), so set the minute field to maybe 3 minutes into the future and see if it runs then.

---

### Post by kingnerd on 2009-06-25
> **geirha said:**
> How far into the future did you put your "test" job? You should make sure it is at least two minutes into the future, because cron will wait until the next minute to load the new crontab (after running crontab -e), so set the minute field to maybe 3 minutes into the future and see if it runs then.

I put it as * for testing, and at least 10 minutes have elapsed without execution.

---

### Post by geirha on 2009-06-25
Ok, so you have the following line for testing then, right?
```
* * * * * /bin/cp /home/user/My\ Documents/Mine/server_level.dat /home/user/My\ Documents/Mine/backup/backup1.dat >>/tmp/backup.log 2>&1
```

If it tries to execute the job at all, then at the very least an empty /tmp/backup.log should be created. Is it not created at all?

---

### Post by kingnerd on 2009-06-25
> **geirha said:**
> Ok, so you have the following line for testing then, right?
```
* * * * * /bin/cp /home/user/My\ Documents/Mine/server_level.dat /home/user/My\ Documents/Mine/backup/backup1.dat >>/tmp/backup.log 2>&1
```

If it tries to execute the job at all, then at the very least an empty /tmp/backup.log should be created. Is it not created at all?

When I nano it, it says new file, so I presume it is not being created at all.

---

### Post by geirha on 2009-06-25
That's odd. Is the cron dæmon actually running? and how does the crontab -l output look like with only that test job?
```

ps -ef | grep [c]ron
crontab -l

```

---

### Post by kingnerd on 2009-06-25
> **geirha said:**
> That's odd. Is the cron dæmon actually running? and how does the crontab -l output look like with only that test job?
```

ps -ef | grep [c]ron
crontab -l

```

Crontab -l returns the same line, but ps -ef | grep [c]ron, oddly enough, returns nothing.

---

### Post by geirha on 2009-06-25
> **kingnerd said:**
> Crontab -l returns the same line, but ps -ef | grep [c]ron, oddly enough, returns nothing.

Aha, so cron is not running. Try
```
sudo /etc/init.d/cron restart
```
Then run the ps-line again to confirm that it is running.

---

### Post by kingnerd on 2009-06-25
> **geirha said:**
> Aha, so cron is not running. Try
```
sudo /etc/init.d/cron restart
```
Then run the ps-line again to confirm that it is running.

Awesome... Thanks so much.  Works perfectly now (executes all commands, and created the log file).  I owe you one [-o<

---

