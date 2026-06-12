---
title: "Crontab entry does not work."
date: 2008-07-28
forum: Desktop Environments
---

### Post by aravinda_sh on 2008-07-28
Hi All,
I have cron tab entry like this. Why I am not getting it executed and send a mil to me.
PATH=/usr/sbin:/usr/bin:/sbin:/bin
01 04 * * * cd </var/www/bugzilla> ; ./collectstats | sendmail "Bugs status" [email]aravinda.sh@gmail.com[/email]
01 05 * * * cd </var/www/bugzilla>; ./automysqlbackup | sendmail "Bugzilla backup" [email]aravinda.sh@gmail.com[/email]

I have this cron tab entry in /var/www/bugzilla directory. I could see these scripts getting executed and send a mail to me.

collectstats is a perl script collectstats.pl
and automysqlbackup is shell script automysqlbackup.sh.

Please some can help me on this.

Aravinda SH

---

### Post by spupy on 2008-07-28
Well, use the full names of the scripts in the cron entry.
Like "collectstats.pl" instead of "collectstats".

---

### Post by aravinda_sh on 2008-07-28
> **spupy said:**
> Well, use the full names of the scripts in the cron entry.
Like "collectstats.pl" instead of "collectstats".
Yes I did. To verify I added the following line
* * * * *  /bin/echo "Hello World" and then restarted using the command 
sudo /etc/init.d/sysklogd restart

After a minute I typed "**mail**", I get message saying "No mail for root".

I suspect my crontab is not working.

---

### Post by spupy on 2008-07-28
> **aravinda_sh said:**
> Yes I did. To verify I added the following line
* * * * *  /bin/echo "Hello World" and then restarted using the command 
sudo /etc/init.d/sysklogd restart

After a minute I typed "**mail**", I get message saying "No mail for root".

I suspect my crontab is not working.

So the commands you use work themselves, but in crontab they don't? In that case you really need to check your syntax.
Instead of doing a "cd" to the folder containing the script and then calling the script, try to invoke the script using its whole path, like:
```
/var/www/bugzilla/collectstats.pl
```

---

### Post by aravinda_sh on 2008-07-29
> **spupy said:**
> So the commands you use work themselves, but in crontab they don't? In that case you really need to check your syntax.
Instead of doing a "cd" to the folder containing the script and then calling the script, try to invoke the script using its whole path, like:
```
/var/www/bugzilla/collectstats.pl
```
Thank you very much and it worked.

---

