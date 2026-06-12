---
title: "Crontab not found"
date: 2009-03-12
forum: General Help
---

### Post by sunrex on 2009-03-12
> crontab -e
bash: crontab: command not found


This is on a VPS, I'm trying to setup a restarter.sh that will check the server every 60 seconds and restart when down.

I've never messed with crontab before so I could be wrong here..

Also, will crontab automatically run every time the OS/PC is restarted or will I have to do this every single time?.

Thank you!.

---

### Post by rybl on 2009-03-12
What does the command [FONT="Courier New"]which crontab[/FONT] return?  I think the default is [FONT="Courier New"]/usr/bin/crontab[/FONT].

---

### Post by sunrex on 2009-03-12
> **rybl said:**
> What does the command [FONT="Courier New"]which crontab[/FONT] return?  I think the default is [FONT="Courier New"]/usr/bin/crontab[/FONT].

root@103:/# which crontab
root@103:/# cd /
root@103:/# which crontab
root@103:/#

---

### Post by &amp;wP*!) on 2009-03-12
> **sunrex said:**
> This is on a VPS, I'm trying to setup a restarter.sh that will check the server every 60 seconds and restart when down.

I've never messed with crontab before so I could be wrong here..

Also, will crontab automatically run every time the OS/PC is restarted or will I have to do this every single time?.

Thank you!.
[B]
/usr/sbin/cron[/B] is the daemon that must run. Type
```
ps -ef | grep cron
```
If there is no **/etc/crontab** or **/etc/cron.d**, your administrator might have prevented you from using that. For more infomartion, **man cron**.

---

### Post by sunrex on 2009-03-12
root@103:/var/www/TAS# ps -ef | grep cron
root     22504 11439  0 18:31 pts/0    00:00:00 grep cron
root@103:/var/www/TAS#
root@103:/var/www/TAS#

---

### Post by sorochan on 2010-04-26
sudo apt-get install cron

---

