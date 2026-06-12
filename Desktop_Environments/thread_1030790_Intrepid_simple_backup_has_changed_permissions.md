---
title: "Intrepid simple backup has changed permissions"
date: 2009-01-04
forum: Desktop Environments
---

### Post by oygle on 2009-01-04
Noticed that after an upgrade to Intrepid, I no longer can browse the folders that simple backup creates. I can browse them as 'sudo' of course, but prior to the upgrade to 8.10, I was able to browse the paths.

Here is what the permissions were prior to the Intrepid upgrade

> drwxr-x---  2 root admin 4096 2008-12-18 21:17 2008-12-18_21.15.41.530559.******.ful


and now after the upgrade to Intrepid, the perms are

> drwxr-x---  2 root root  4096 2008-12-23 22:16 2008-12-23_22.10.47.173785.******.ful

as I'm a member of the 'admin' group, I was previously able to browse, view the backups, but now I can't, unless I run nautilus or konqueror as 'sudo'.

The packages are the same though ?

Oygle

---

### Post by oygle on 2009-01-05
Have retrieved a backup of the file /etc/sbackup.conf , from hardy, there are some differences ..

Hardy

> [general]
purge = 0
maxincrement = 2
lockfile = /var/lock/sbackup.lock
target = /var/backup
format = 1


Intrepid

> [general]
stop_if_no_target = 0
target = /var/backup
format = 1
purge = 0
maxincrement = 3
lockfile = /var/lock/sbackup.lock


The only _real_ difference though is the addition aof this line

> stop_if_no_target = 0


in Intrepid.  Possibly the cron job is running now as root, whereas before it was running as admin ??

The file '/etc/cron.daily/sbackup' is the same for both Hardy and Intrepid.

Hmm, line 183 in /usr/sbin/sbackupd in hardy is

> 	os.setgid( grp.getgrnam("admin").gr_gid )


and the same line in Intrepid is 

> 	os.setgid( grp.getgrnam("root").gr_gid )


with a comment above the Intrepid version ..

> # Due to no clarity on the 'admin' group, reverting to root group


Are other people having this problem ?  It means that, as I'm a member of the 'admin' group, I used to be able to browse the backups, but now I cannot, but are forced to become 'sudo'.

Oygle

---

