---
title: "Why wont cron work?"
date: 2007-06-05
forum: Desktop Environments
---

### Post by mister_p_1998 on 2007-06-05
If I create a task to run Icepodder (castpodder as was) the event comes and goes, nothing runs, if I click on the task in Kcron and select "run now" , it works fine, whats up? Ive never got cron working yet EVER!

task as follows:

10 08 * * 1,2,3,4,5 steve /usr/bin/IcePodder

variable DISPLAY=:0

---

### Post by EndPerform on 2007-06-05
From what I see, this is only going to run at 8:10, Monday through Friday.  Check /var/log/syslog to see if it's being executed:

```
cat /var/log/syslog | grep /USR/SBIN/CRON
```

I also noticed you have your username in your cron command.  I'm not sure if that's necessary or not.  Here's my crontab, which I know is working:

```
0,5,10,15,20,25,30,35,40,45,50,55 * * * * /usr/bin/getmail
```

And I see the following in my /var/log/syslog:

```
Jun  5 11:25:01 scooby /USR/SBIN/CRON[19372]: (fubar) CMD (/usr/bin/getmail)
```

Also, double-check that it is actually enabled in Kcron.

---

