---
title: "/etc/init.d/mysql start [fail]"
date: 2009-05-07
forum: General Help
---

### Post by hpartidas on 2009-05-07
Hello all,

After endless searching, the closest [post]("http://ubuntuforums.org/showthread.php?t=666689") I found that kinda helped me out was on this site so i figured I'd see if anyone can help me out here.

MySQL won't start for me for some reason. When I first installed it, it worked great! no issues at all, after a reboot when ever i tried running mysql it would fail.

Here is what syslog is throwing back at me:

```
May  7 08:52:50 desktop mysqld_safe[13452]: started
May  7 08:52:50 desktop mysqld[13455]: 090507  8:52:50 [Warning] Can't create test file /var/lib/mysql/desktop.lower-test
May  7 08:52:50 desktop mysqld[13455]: 090507  8:52:50 [Warning] Can't create test file /var/lib/mysql/desktop.lower-test
May  7 08:52:50 desktop mysqld[13455]: 090507  8:52:50 [Warning] One can only use the --user switch if running as root
May  7 08:52:50 desktop mysqld[13455]:
May  7 08:52:50 desktop mysqld[13455]: 090507  8:52:50  InnoDB: Operating system error number 13 in a file operation.
May  7 08:52:50 desktop mysqld[13455]: InnoDB: The error means mysqld does not have the access rights to
May  7 08:52:50 desktop mysqld[13455]: InnoDB: the directory.
May  7 08:52:50 desktop mysqld[13455]: InnoDB: File name ./ibdata1
May  7 08:52:50 desktop mysqld[13455]: InnoDB: File operation call: 'open'.
May  7 08:52:50 desktop mysqld[13455]: InnoDB: Cannot continue operation.
May  7 08:52:50 desktop mysqld_safe[13462]: ended
May  7 08:53:04 desktop /etc/init.d/mysql[13616]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
May  7 08:53:04 desktop /etc/init.d/mysql[13616]: Could not open required defaults file: /etc/mysql/debian.cnf
May  7 08:53:04 desktop /etc/init.d/mysql[13616]: Fatal error in defaults handling. Program aborted
May  7 08:53:04 desktop /etc/init.d/mysql[13616]: 

```I checked the permissions, but the /usr/lib/mysql directory belongs to mysql user and to the mysql group.

Does anyone have any idea what might be going on here?

---

### Post by ubuser_7 on 2009-05-07
How about the file: /etc/mysql/debian.cnf that its complaining about?

---

### Post by moving on 2009-08-21
i have same error,
i'm try to set permissions 777 for /etc/mysql/debian.cnf, but it's not helping.

Any other idea?

---

### Post by moving on 2009-08-21
oops, i'm find solution - /etc/init.d/apparmor stop

---

