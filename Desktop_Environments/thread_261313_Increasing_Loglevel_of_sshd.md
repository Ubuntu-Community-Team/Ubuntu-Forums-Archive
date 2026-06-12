---
title: "Increasing Loglevel of sshd"
date: 2006-09-20
forum: Desktop Environments
---

### Post by kihai on 2006-09-20
Hi folks,
just stumbled upon a apparently simple task - but can't find out, how to get done with it.

I'm running a LTSP System (Edubuntu) with 300+ users logging in weekly and for reporting purposes I log their login activity with a script that evaluates auth.log. 
Only problem is that sshd (the daemon that writes LTSP log entries to auth.log) doesn't log the logout times, only the login times.
Now I wanna be able to see exactly when a user logs in AND out, so I tried to increase the loglevel in /etc/ssh/sshd_config from INFO to VERBOSE, but nothing changed. Will try it with DEBUG but will have to wait until everyone is logged out, so I can restart the sshd.

Any of you have any other advice on how I can get the desired logging of both logins and logouts???

---

### Post by kihai on 2006-12-20
Don't want to seem curious, I'm just really wondering: Is there NOBODY on this forum who has had any idea on this for THREE MONTHS??????? (By the way: problem still isn't solved)

---

### Post by mannheim on 2006-12-20
On my system, auth.log does contain info from sshd about both login and logout:
```
Dec 20 13:22:25 my-machine sshd[12345]: Accepted publickey for john from 122.344.566.788 port 53048 ssh2
Dec 20 13:22:25 my-machine sshd[12347]: (pam_unix) [COLOR="Blue"]session opened[/COLOR] for user john by (uid=0)
Dec 20 13:22:30 my-machine sshd[12347]: (pam_unix) [COLOR="Blue"]session closed[/COLOR] for user john

```
I have "LogLevel INFO"

You could try asking the question in the Servers and Security section of these forums.

---

