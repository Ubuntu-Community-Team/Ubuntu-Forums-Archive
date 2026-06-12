---
title: "Cron Backup not Working"
date: 2009-05-07
forum: General Help
---

### Post by MetaCipher on 2009-05-07
I have several cron scripts that run daily, hourly, and every 5 minutes to perform backups and other functions. The problem is that the backups that create .tars are empty. While the backups that create other files are just fine. The obvious answer is yes, the crontab was edited as root (sudo crontab -e). The second obvious answer is yes, the scripts do work as if you run them as a normal user or root. The /backup/ folder is chmoded correctly (as the files are getting made). Here's my crontab:

```

# m h  dom mon dow   command
0 1 * * *   /cron/backup
0 */1 * * *   /cron/recentbackup
*/5 * * * *   /cron/email_auto_retrieve
*/5 * * * *   /cron/webcalendar
0 1 * * *   /cron/log

```

The problem scripts are backup and recentbackup. Here's the contents of one file, and one of the lines that creates an empty tar.

/cron/backup/
```

#!/bin/sh

tar -cvvf /backup/users/`eval date +%Y%m%d`.tar /share/users/
tar -cvvf /backup/extern/users/`eval date +%Y%m%d`.tar /share/users/

exit 0

```

Any help is appreciated. Thanks.

Edit:
My log (sudo grep CRON /var/log/syslog) doesn't display 1 am, when the backups run, unfortunately. It only goes back about 2 hours - is there a way to change this?

Also, forgot to mention. Using Ubuntu 9.04 Server 64bit.

---

### Post by MetaCipher on 2009-05-08
In an effort to debug I directed the two backup scripts not working to a text file, and suddenly the scripts started to work (which seems really odd).

Here's my crontab now:
```

0 1 * * *   /cron/backup > /home/tim/test.txt

```

---

