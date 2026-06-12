---
title: "trying to get cron to work..."
date: 2008-12-09
forum: General Help
---

### Post by enzo12345 on 2008-12-09
Hi.

I am trying to get a shell script to run every 10mins, I have takent hese steps:


I am using Ubuntu linux desktop.



```
crontab -e
```

added and saved this line to the file


```
# m h  dom mon dow   command
*/1 * * * * /home/enzo/Desktop/dlrecentuse.sh
```

restarted cron:


```
 sudo /etc/init.d/cron restart
```

nothing is happening, any ideas?

---

### Post by cmnorton on 2008-12-10
It looks like you have the right number of fields.

 Is this shell script protected executable?

Look in /var/log/syslog for cron entries. 

Looking in the logs saved me, when stuff would not execute and it was because I had one too many fields in /etc/crontab, which needs the username running the entry.

---

### Post by bodhi.zazen on 2008-12-10
The first field should be "*/10" without quotes.

Other then that, is the script executable ? Does it run from the command line ?

Since it is in /home , is your home on a separate partition mounted noexec ?

---

### Post by cmnorton on 2008-12-11
> **bodhi.zazen said:**
> The first field should be "*/10" without quotes.

Other then that, is the script executable ? Does it run from the command line ?

Since it is in /home , is your home on a separate partition mounted noexec ?

Thanks. Didn't even notice the " ".

---

