---
title: "I need a bit of help with MythTV please..."
date: 2006-10-03
forum: Desktop Environments
---

### Post by someguyouknow on 2006-10-03
I need to know if i can reset the MySQL host for MythTV
I get this error when i try to enter the mythtv-setup and frontend.
i think i changed something even though i shouldnt have.
what config file do i need to get rid of?


```
QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-10-03 12:51:25.881 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-10-03 12:51:25.960 Unable to connect to database!
2006-10-03 12:51:25.961 Driver error was [1/2005]:
QMYSQL3: Unable to connect
Database error was:
Unknown MySQL server host 'NameHere' (1)
```

---

### Post by someguyouknow on 2006-10-12
anybody?
I tried purging mysql but that didnt work either...

---

### Post by Aberrix on 2006-10-12
It looks like it doesn't know where to connect; 

```
Unknown MySQL server host 'NameHere' (1)
```

There should be a hostname to the SQL server instead of 'NameHere'

where ever that is in your config.

---

### Post by someguyouknow on 2006-10-12
Thanks... i found the config in /home/mythtv/.mythtv/mysql.txt
all seems well now... at least with that problem

---

### Post by Aberrix on 2006-10-12
> **someguyouknow said:**
> Thanks... i found the config in /home/mythtv/.mythtv/mysql.txt
all seems well now... at least with that problem

awesome, glad it worked for you!

---

### Post by lonce on 2006-10-12
LOL I was just about to respond and say the same thing as Aberrix.  Good call on that.  Hope it works for you.

---

### Post by someguyouknow on 2006-10-12
Yep, all it well thanks.
lol i have been working on mythtv for weeks and it finally works.
i feel accomplished.

---

