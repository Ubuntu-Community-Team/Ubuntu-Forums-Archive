---
title: "mysql FAT sharing problems!"
date: 2008-12-12
forum: General Help
---

### Post by gontofe on 2008-12-12
This has been asked before in various places, but I haven't found a good answer yet!

I dual boot Windows Vista and Ubuntu Intrepid, and want to run mysql on both, working from the same databases. I have moved the mysql data folder onto an external FAT hard drive, which I mount in linux as follows:

```
/dev/sdb1 /media/DOCUMENTS1 vfat rw,exec,auto,users,uid=1000,gid=1000,umask=007 0 0
```

I have installed mysql in linux, and everything works fine. However, I have tried to point the pqth in /etc/mysql/my.cnf to the relevant folder on the FAT drive, when I restart, I get the following error:

```
081212 17:26:17 [Warning] Can't create test file /media/DOCUMENTS1/data/mike-laptop.lower-test
081212 17:26:17 [Warning] Can't create test file /media/DOCUMENTS1/data/mike-laptop.lower-test
081212 17:26:17  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
```

If I try to go about it differently, keeping the original path in the my.cnf file, simply creating a symbolic link to the FAT data folder in place of /var/lib/mysql, I get:
```
081212 17:29:01 [Warning] Can't create test file /var/lib/mysql/mike-laptop.lower-test
081212 17:29:01 [Warning] Can't create test file /var/lib/mysql/mike-laptop.lower-test
081212 17:29:01  InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to
InnoDB: the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'create'.
InnoDB: Cannot continue operation.
```

I've made sure the user 'mysql' is added to group '1000', but it still doesn't make any difference.

What am I missing??

---

### Post by gnu2tux on 2008-12-12
Mysql runs as group 124, not 1000, so I would imagine you have a problem right there. However there are a few other snafus to be aware of - VFAT (or FAT32) doesn't actually support permissions like Linux does, so mapping the permissions is a pretty nasty thing to do and you're likely to end up in no end of pain.

IMO, you're going about this the wrong way. If you wanna access your MySQL db in Windows, install a free Ext2/3 driver for Windows and read your Mysql db from your Linux partition. That way the permissions can be retained.

Try something like Ext2 IFS for Windows: [URL="http://www.fs-driver.org/"]http://www.fs-driver.org/
[/URL]

---

### Post by gontofe on 2008-12-12
True, but I added it to the group 1000, because I didn't want to mount my drive only to be accessible to mysql alone... I thought it would make more sense to ensure the 1000 group had rwx access and that mysql belonged to that group, no?

---

### Post by gontofe on 2008-12-15
All sorted! The problem was actually with apparmor. To solve, I edited /etc/apparmor.d/usr.sbin.mysqld, replacing the following lines:
```
  /var/lib/mysql/ r,
  /var/lib/mysql/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
```
To reflect the new path in /etc/mysql/my.cnf.

When restarting the server I still got an error:
```

 * Starting MySQL database server mysqld                                                                                               [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```
But this was solved by looking at [http://ubuntuforums.org/showthread.php?t=112505]("http://ubuntuforums.org/showthread.php?t=112505"), with the command ```
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY '<password>' WITH GRANT OPTION;
``` Replace <password> with the debian-sys-maint password from /etc/mysql/debian.cnf.

---

