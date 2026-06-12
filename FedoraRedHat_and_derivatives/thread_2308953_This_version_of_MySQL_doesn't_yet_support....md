---
title: "This version of MySQL doesn't yet support..."
date: 2016-01-06
forum: Fedora/RedHat and derivatives
---

### Post by andrew102 on 2016-01-06
I am running MySQL version 5.1 on CentOS. I keep backups using a mysqldump script to save the database to the local file system.

I was restoring form the backup to the same server on a different schema name. This is the error I come across:

ERROR 1235 (42000) at line 197: This version of MySQL doesn't yet support 'multiple triggers with the same action time and event for one table'

And occurs on multiple lines. Why would a mysqldump from 5.1 and a restore to 5.1 trigger this error message?

---

