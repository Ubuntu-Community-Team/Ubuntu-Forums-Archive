---
title: "mysqldump fails"
date: 2009-06-24
forum: General Help
---

### Post by Alf Stockton on 2009-06-24
If I run
mysqldump --add-drop-table -u root phplist > /Backups/phplist.backup.sql
from the command line as root it works perfectly but.....not if I do the same command from root's crontab.
The command in crontab looks like
15 00 * * * mysqldump --add-drop-table -u root phplist > /Backups/phplist.backup.sql
Can someone please explain ?

---

### Post by Gunman1982 on 2009-06-24
When the cronjob is executed some paths are not set, so rather than executing mysqldump use the absolute path '/usr/bin/mysqldump' or wherever mysqldump is located. You can find that out by executing 'locate mysqldump' or 'whereis mysqldump'

---

