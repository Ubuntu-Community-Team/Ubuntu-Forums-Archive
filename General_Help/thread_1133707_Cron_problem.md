---
title: "Cron problem"
date: 2009-04-23
forum: General Help
---

### Post by formula on 2009-04-23
Hi all,

I try to setup a cron job that will run as root. I did this:

sudo crontab -e 

and then typed in:

43 10 * * *  /var/www/ct/automysqlbackup.sh


It doesn't run. Why? and where I can see the log why it didn't run?

any ideas?

Many thanks!

---

### Post by Nepherte on 2009-04-23
Is the cron daemon running? Is the file /var/www/ct/automysqlbackup.sh executable?

---

### Post by formula on 2009-04-23
> **Nepherte said:**
> Is the cron daemon running? Is the file /var/www/ct/automysqlbackup.sh executable?
it is executable, I can run it from the terminal but how do I know if the daemon is running?

---

