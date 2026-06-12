---
title: "Running Unison in Crontab"
date: 2009-01-05
forum: General Help
---

### Post by aidan.whitehouse on 2009-01-05
Ok, I have trawled all possible forums and tried lots of different syntaxes but can I get unison to work in crontab???

I have the following line in Crontab for user xxx:

```
*/1 * * * 1-5 /usr/bin/unison -batch -fastcheck true -ui text /home/xxx/.unison/backup > /home/xxx/Desktop/CrontabError.log
```

I have set it up to run every minute for the purposes of trying to get it to work, but when I get it working, it will run overnight.

cron.log shows that this was attempted:

```
Jan  5 22:46:01 yyy /USR/SBIN/CRON[7650]: (xxx) CMD (/usr/bin/unison -batch -fastcheck true -ui text /home/xxx/.unison/backup > /home/xxx/Desktop/CrontabError.log)
```

but the sync does not happen and I just get a blank output file.  Running the same command in terminal is successful.

The sync is between the local PC and a Samba share which mounts quite happily for user xxx at startup.  I have also tried putting a similar line in crontab for root, but I get the same result

Anybody got any ideas?

---

