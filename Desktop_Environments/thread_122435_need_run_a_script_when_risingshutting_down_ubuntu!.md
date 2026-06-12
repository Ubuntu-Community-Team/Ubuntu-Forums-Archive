---
title: "need run a script when rising/shutting down ubuntu!"
date: 2006-01-27
forum: Desktop Environments
---

### Post by lorap on 2006-01-27
hi, i just need to run some scripts on logging in and shutting down the os.
thanx
pavel

---

### Post by cwaldbieser on 2006-01-27
[QUOTE=lorap]hi, i just need to run some scripts on logging in and shutting down the os.
thanx
pavel[/QUOTE]
You can use "update-rc.d" to link the scripts once you write them.

---

### Post by lorap on 2006-01-30
ok
but what this means rc.d?
thanx

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=lorap]ok
but what this means rc.d?
thanx[/QUOTE]
It is an idea that stems from older UNIX systems.  The system can boot into different **run levels** and the scripts that are run during boot or shutdown are symbolically linked in special /etc/rc#.d folders.  Try
```

$ ls /etc/rc2.d

```
to get an idea of what I am talking about.  The links that start with "S"  are run at **S**tartup.  The links that start with "K" are run when the system is being **K**illed.  The order the links appear in is the order they are run in.

The "update-rc.d" command is just a convenient way to manage this.  There is also a graphical tool called BUM (Boot Up Manager) that has its own sub-forum.

---

