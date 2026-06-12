---
title: "Date format in a crontab"
date: 2005-11-03
forum: Desktop Environments
---

### Post by kenironside on 2005-11-03
Hi,

I'm sorry if this is in the wrong place. I have a line in my root crontab that works fine if I execute from the command line but won't work when it is put into the root crontab.

The crontab line is:
* * * * * /bin/cp /var/log/fetchmail/fetchmail.log /var/log/fetchmail/fetchmail_`date +%Y%m%d`.log

1. If I execute this from the command line it works as expected.
2. I have checked that it has a carriage return after it in the crontab - it has - it is not the last line and every other line executes fine.
3. If I replace the _`date +%Y%m%d` with a simple word - it executes OK.

Is there some reason that the date format doesn't work in a crontab?

Thanks, Ken

---

### Post by kenironside on 2005-11-03
Solved it myself - I put the command in a script (it works) and called the script from crontab.

---

