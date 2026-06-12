---
title: "HELP!!!! can't login to the desktop"
date: 2006-07-26
forum: Desktop Environments
---

### Post by underdog512 on 2006-07-26
I have a wierd and very serious problem.  I am running KDE on top of ubuntu, I have been for several months.  I have not had any problems until today.

When I restarted my computer, the kubuntu login screen comes up as usual however when I try to login, the screen goes blank for a few seconds and then the login screen comes back up and nothing happens.

I can login to failsafe mode.  I can also do a console login. 

Whats going on?!

HELP!!!!!

---

### Post by jimbren on 2006-07-26
try doing a console login and then restart kdm...but that is totally a stab in the dark.

```
sudo /etc/init.d/kdm restart
```

---

### Post by underdog512 on 2006-07-26
> **jimbren said:**
> try doing a console login and then restart kdm...but that is totally a stab in the dark.

```
sudo /etc/init.d/kdm restart
```

nope that didn't work

---

