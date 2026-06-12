---
title: "/home fills up at 1 meg/sec"
date: 2009-05-04
forum: General Help
---

### Post by riktking on 2009-05-04
hi

im really stuck and have tried LOADS of solutions posted all over the forums. what is basically happening is the /home partition is filling up at about 1meg a second until basically the system freezes and a reboot is required. 

please help me as its driving me nuts!

thanks

riktking

---

### Post by ajgreeny on 2009-05-04
Whilst your home is growing try running either ```
top
``` to see what is happening or ```
ps aux
``` to see if a process is running.  It may give you a clue.

I presume you do not know which file or files are getting so huge as to fill up your home, but have a look at .xsession-errors, a hidden file in your home folder which can grow alarmingly if you have any x session problems with, for example, graphics.  Normally the file is about 2.3KB to start, but will grow occasionally if there are problems to about 60 or 70 KB, and can become huge over time.

---

