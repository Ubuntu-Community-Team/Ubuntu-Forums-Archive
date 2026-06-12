---
title: "rsync permission denied error"
date: 2010-06-19
forum: Desktop Environments
---

### Post by dave37 on 2010-06-19
Hi, I'm using rsync to keep my primary soho server and a backup soho server in sync.  All is working well except for one directory.  The directory OTHER has user mgrant and group house as full r+w access.  All the other directories are user mgrant and group mlgpc.  Those are rsyncing fine.  The OTHER directory causes rsync to report a permission denied (13) error.  Below is my rsync command and a snippet of the error.  The OTHER directory permissions on both servers are drwxrwx---

rsync command:
/usr/bin/rsync -av -r -p -t -o -g -l  --delete --log-file=/home/admindave/logs/rsync_home_backup.txt /media/backup/mlgpc /media/backup2

and an error snippet is:

2010/06/19 07:41:09 [1129] rsync: chgrp "/media/backup2/mlgpc/OTHER/W.A. McLeod Company Limited/Business Tax Info/GCT" failed: Permission denied (13)

After looking in to it more, it is how I'm mounting it in fstab.  I am specifying uid=name and gid=name, however the OTHER folder which is giving permission errors has different group name, how can I mount it so that the other directory is writable by rsync, that is, mount it so that both groups can access their files?

---

