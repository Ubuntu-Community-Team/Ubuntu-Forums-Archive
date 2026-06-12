---
title: "Auto logoff user after 15 minutes idle time"
date: 2009-05-27
forum: General Help
---

### Post by amadeus266 on 2009-05-27
I am setting up Ubuntu on some of my workstations and need them to be PCI DSS compliant. Specifically, I would like the user to be automatically logged off after 15 minutes of inactivity. I already have one system completely set up including joined to Win2K3 Active Directory for authentication. I have the users being logged off the server after 15 minutes and need to do the same on the workstation running Ubuntu.

---

### Post by amadeus266 on 2009-05-28
I have read many posts about other people reporting that their Ubuntu computers are logging them off automatically and wanting to know how to stop that behavior. I want to do the opposite. Any ideas? Anyone???

---

### Post by KhurramM on 2009-05-28
[http://www.cyberciti.biz/tips/howto-linux-kill-and-logout-users.html](http://www.cyberciti.biz/tips/howto-linux-kill-and-logout-users.html)

and,

[http://www.linuxquestions.org/questions/linux-security-4/how-do-i-automatically-logout-after-a-period-of-inactivity-271831/](http://www.linuxquestions.org/questions/linux-security-4/how-do-i-automatically-logout-after-a-period-of-inactivity-271831/)

might help u.

---

### Post by amadeus266 on 2009-05-28
Thanks, I will give it a go.

---

### Post by amadeus266 on 2009-06-04
The previous suggestions didn't work for me. I am now trying timeoutd but it isn't working either. It appears that my setting are correct...
```
# /etc/timeouts: user login/idle/session time limits.  See timeouts(5).
#
# Format:  TIMES:TTYS:USERS:GROUPS:MAXIDLE:MAXSESS:MAXDAY:WARN
#   or:    TIMES:TTYS:USERS:GROUPS:LOGINSTATUS
#
# Some examples:
#
# dopey is not allowed to login
#Al:*:dopey:*:NOLOGIN
#
# cas gets unlimited use
#Al:*:cas:*:0:0:0:0
#
# fred is allowed 20 minutes idle, 240 mins per session, and 480 mins per day
# on ttyS3
#Al:ttyS3:fred:*:20:240:480:10
#
# everyone else is allowed only 120min/session, 240/day
#Al:ttyS3:*:*:20:120:240:5
# everyone can log in at any time but will be logged out when idle for 15 minutes
Al:*:*:*:15:::2
```
But in my log files I get the following:
```
Jun  4 09:16:55 yosemite3 timeoutd[10061]: Could not open tty7 for checking line discipline - idle limits will be enforced.
Jun  4 09:16:55 yosemite3 timeoutd[10061]: User administrator exceeded idle limit (idle for 2583 minutes, max=15). 
Jun  4 09:16:55 yosemite3 timeoutd[10061]: Could not write logoff message to tty7.
```

---

