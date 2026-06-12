---
title: "avgscan scheduled  but not running...."
date: 2009-02-20
forum: General Help
---

### Post by Mia_tech on 2009-02-20
guys, I added a job to my crontab file and it is an antivirus scan, but even though I'm using log file to see the result of scan, the log file is created but is blank, how do I know if indeed the antivirus is running? and why is the log file empty?... here's the line I added to my crontab file

> 00 2	* * 2	root	avgscan -scan /home/jorge -clean -report /home/jorge/avgscan.txt

---

### Post by dcstar on 2009-02-20
> **Mia_tech said:**
> guys, I added a job to my crontab file and it is an antivirus scan, but even though I'm using log file to see the result of scan, the log file is created but is blank, how do I know if indeed the antivirus is running? and why is the log file empty?... here's the line I added to my crontab file

Why is "root" there, is it some sort of command?

And do note "quote" code, use the proper code function.

---

### Post by Mia_tech on 2009-02-20
correct me if I'm wrong, but in crontab after dow you're suppose to put the user under which the command is expected to run

---

### Post by wowbagger53 on 2009-02-21
The format you have used is correct for entries in */etc/crontab*, but it is not recommended that you use */etc/crontab*. See [https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

If you do:

```
sudo crontab -e
```

... it will set up and allow you to edit a regular crontab file for root. In these use crontab files the username parameter is omitted.

Wrt the empty logfile, perhaps you could try putting the AVG command into a bash script, along with some other logging commands, to see what is happening.

The example you gave only runs on a Tuesday, but I presume that this is intentional.

HTH.

---

### Post by Mia_tech on 2009-02-21
yes it is only on Tuesday!

---

