---
title: "filesystem backup"
date: 2005-12-19
forum: General Help
---

### Post by davebradford on 2005-12-19
i wud like to backup the following things on my ubuntu server weekly

/var/www/
/home/dave/
/etc/samba/smb.conf
/etc/apache2/apache2.conf

what is the easiest way of doing this?

---

### Post by doitashimashite on 2005-12-19
Make a one-liner script that makes a tarball and put that in crontab.

---

### Post by doitashimashite on 2005-12-19
Like this:

sudo gedit /etc/cron.weekly/backupthings

Insert the following lines (replace /tmp with the desired path where you want the backup file to land):

#!/bin/bash
#/etc/cron.weekly/backupthings
tar cvfz /tmp/backup`date +%Y%m%d`.tar.gz /var/www/ /home/dave/ /etc/samba/smb.conf /etc/apache2/apache2.conf

and save the file. The name of the backup file will contain the year, month and day.

Finally,

sudo chmod +x /etc/cron.weekly/backupthings

---

### Post by davebradford on 2005-12-19
that you i've set that up and it seems to be ok! what about if wanted to do a filesystem scan using clamav and run a command.. how can i do this dailty using crontab?

---

### Post by doitashimashite on 2005-12-19
I'd suggest write a similar script with the desired command and put that into the /etc/cron.daily directory.

---

### Post by doitashimashite on 2005-12-19
One more thing. The times at which these monthly / weekly / daily scripts are executed, are to be found in

/etc/crontab

Looks like this:

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
#

Each line starts with minute and hour. You can change them if you desire.

---

