---
title: "slocate seg fault"
date: 2005-02-03
forum: Desktop Environments
---

### Post by lykoszine on 2005-02-03
Subject: Cron <root@beast> test -e /usr/sbin/anacron || run-parts --report /etc/cron.daily
Date: Thu,  3 Feb 2005 06:26:28 +0000 (GMT)

/etc/cron.daily/slocate:
/etc/cron.daily/slocate: line 12: 21670 Segmentation fault      /usr/bin/updatedb

Anybody got any ideas on this one? Thanks

---

### Post by Levander on 2005-02-03
[QUOTE=lykoszine]

Anybody got any ideas on this one? Thanks[/QUOTE]


Try deleting the locate database file manually, then recreate it again?  I know you can run the same script manually that cron runs to create and update the database, but don't remember the name of it.

---

### Post by lykoszine on 2005-02-04
[QUOTE=Levander]Try deleting the locate database file manually, then recreate it again?  I know you can run the same script manually that cron runs to create and update the database, but don't remember the name of it.[/QUOTE]
 Same as unfortunately. Seg fault on line 12.
Likewise if I remove ---purge with apt-get and resintall.

      1 #! /bin/sh
      2
      3 if [ -x /usr/bin/slocate ]
      4 then
      5         if [ -f /etc/updatedb.conf ]
      6         then
      7                 /usr/bin/updatedb
      8         else
      9                 /usr/bin/updatedb -f proc
     10         fi
     11         chown root.slocate /var/lib/slocate/slocate.db
     12 fi
~

that is cron.daily/slocate

---

