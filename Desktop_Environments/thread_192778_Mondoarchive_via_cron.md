---
title: "Mondoarchive via cron"
date: 2006-06-09
forum: Desktop Environments
---

### Post by pietrob71 on 2006-06-09
I have a script -> /usr/bin/backup

--------------------------------------------------------------------------------------------------
rsync -a --delete /var/www /home/max/backup/
mysqldump --all-database --opt > /home/max/backup/mysql_backup.sql
rsync -a --delete /var/mail/virtual /home/max/backup/

umount -f /dev/cdrw
mondoarchive -OVegFw 4 -9 -I /home/max/backup/ -d /dev/cdrw
--------------------------------------------------------------------------------------------------

from my shell with "sudo backup" everythings work fine and I obtain a CD with my backup

This is my root crontab

0 3 * * *     /usr/bin/backup

At 3:00 am of every day the script is executed, because I can see the correct day and time of mysql_backup.sql, but the line of mondoarchive is not executed and cd is not burned.

Then I have find on google this howto:

[http://cod.homelinux.org/C/documentation/mondo-with-cron/mondo-with-cron.html]("http://cod.homelinux.org/C/documentation/mondo-with-cron/mondo-with-cron.html")

I have tried to follow this howto but when I type: "grep mondo /var/spool/at/*"

the system tell me: "grep: /var/spool/at/*: No such file or directory"

I hope someone can help me.

Thanks in advance

Pietro

---

