---
title: "crontab not working in hardy?"
date: 2009-02-10
forum: Desktop Environments
---

### Post by sartic on 2009-02-10
Is there any problem width cron in hardy? On feisty works as charm, but on hardy sometime or never it execute my command (i am using rsync to backup files on 2nd disk). If I execute this rsync line on xterm it works all time.

---

### Post by laceration on 2009-02-10
Have you added username to /etc/cron.allow?

---

### Post by sartic on 2009-02-10
it doesn't help

---

### Post by sartic on 2009-04-22
I tried now jaunty rc width gnome schedule works every time.
If cron doesn+t work what can I try next on hardy?

---

### Post by laceration on 2009-04-22
Crontab has a couple of things that can screw it up that you might check.
Is the path to the command in your crontab file?
The path is in your crontab's first line. 
```
crontab -l
```
If the path doesn't show in something like this

    PATH=/usr/sbin:/usr/bin:/sbin:/bin:/usr/local/bin
 
add it by editing your crontab:
```
crontab -e
```

also you might check if the command is like this
```
rsync
```
or 
```
usr/bin/rsync
```
always use the full path for cron job commands

---

### Post by sartic on 2009-04-29
/usr/bin/rsync

I tried that also..... not working still.

---

