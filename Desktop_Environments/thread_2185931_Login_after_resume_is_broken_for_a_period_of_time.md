---
title: "Login after resume is broken for a period of time"
date: 2013-11-05
forum: Desktop Environments
---

### Post by moxford2 on 2013-11-05
Laptop goes to sleep.
Open it up, get the locked prompt, put in password....always fails.
Enter again, fails.
Enter again, works.

Laptop goes to sleep.
Open it up.  
Let it sit for 20 seconds.
Enter password, which works.

Something blows, and is not being resumed properly BEFORE the desktop/login prompt is shown.  Thus, I get failures trying to login until daemonX/processX/whatever is fully ready.

How can I fix this?  Laptop running Ubuntu 13.10, did the same thing on 13.04 

Thanks.

---

### Post by Toz on 2013-11-05
Hello and welcome to the forums.

Attempt a suspend and on resume have a look at the end of /var/log/auth.log and post back any relevant log entries about a password attempt.

Also, can you post back the contents of your /var/log/pm-suspend.log file like:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated

as well as the results of:
```
cat /var/log/syslog | grep PM:
```

Lets see if there is anything in the log files to help identify the cause.

---

