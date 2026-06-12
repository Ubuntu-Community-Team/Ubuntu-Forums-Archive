---
title: "backup-manager and mysql"
date: 2006-08-11
forum: Desktop Environments
---

### Post by gmarton on 2006-08-11
Hi
In /etc/backup-manager.conf there is a way to type database names needing backup. I came across a problem today where one of those databases on in the config file was dropped and backup-manager stopped when it could not find it.

Is there a way to have backup manager find available databases without constantly editing the configureation file?

> ##############################################################
# Backup method: MYSQl
#############################################################
# This method is dedicated to MySQL databases.
# You should not use the tarball method for backing up database
# directories or you may have corrupted archives.
# Enter here the list of databases
export BM_MYSQL_DATABASES="mysql otherdatabase"

Thanks

---

### Post by indytim on 2006-08-11
I can't speak to backing up MySQL with Backup Manager.  I use phpMyAdmin to backup both the structure and the content of my MySQL databases.  It works on re-builds of the MySQL server (in the event....:roll: ).

IndyTim

---

