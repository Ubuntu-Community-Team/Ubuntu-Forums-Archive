---
title: "System is Borked"
date: 2006-06-07
forum: Desktop Environments
---

### Post by pchachte on 2006-06-07
I was using checkinstall to install a kde application (libkexif, if I remember correctly) from source.  I remembered I needed to do something, so I pressed Control-C to stop it. When I did, all the icons on my gnome panels turned into red-Xs. Nothing on the system worked. I couldn't log out of emacs, because it wouldn't write any files to my home directory.  I managed to close everything and reboot using Alt-SysRq R S E I B.  

Now when I boot up, I can't log into my account, because it says my home directory is unavailable.

I can get to my home directory when I boot up in recovery mode, so the disk (and my home partition) must be fine.  I'm working off of my live cd at the moment and I am able to read documents from my home directory.  

I'm working off of a new install of dapper.

Here is a piece of my syslog showing what was happening just before, during, and after my computer crashed.

Thanks for your help!!!

Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/share/locale/pt/LC_MESSAGES/libkexif.mo^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/share/locale/pt/LC_MESSAGES^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/share/locale/pt^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/share/locale^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/share^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/lib/libkexif.so.1.0.0^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/lib/libkexif.so.1^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/lib/libkexif.so^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/lib/libkexif.la^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/lib/pkgconfig/libkexif.pc^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/lib/pkgconfig^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/lib^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/include/libkexif/kexifdialog.h^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/include/libkexif/kexifwidget.h^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/include/libkexif/kexifdata.h^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/include/libkexif/kexifutils.h^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/include/libkexif/libkexif_export.h^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/include/libkexif^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr/include^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup/usr^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup/no-backup^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/no-backup^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/var/tmp/plBjnLEfXinPIJHBBQOU/package^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/var/tmp/plBjnLEfXinPIJHBBQOU/installscript.sh^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/var/tmp/plBjnLEfXinPIJHBBQOU^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/var/tmp^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup/var^I#success
Jun  7 13:18:24 localhost rm: 0^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU/backup^I#success
Jun  7 13:18:24 localhost rm: 0^Iunlink^I/var/tmp/plBjnLEfXinPIJHBBQOU/newfiles.tmp^I#success
Jun  7 13:18:24 localhost rm: -1^Irmdir^I/var/tmp/plBjnLEfXinPIJHBBQOU^I#Directory not empty
Jun  7 13:18:24 localhost rm: -1^Iunlink^I/stuff/soft/libkexif-0.2.2/^I#No such file or directory
Jun  7 13:18:24 localhost rm: -1^Iunlink^I/stuff/soft/libkexif-0.2.2/checkinstall-debug*^I#No such file or directory
Jun  7 13:20:43 localhost kernel: [4449877.708000] Shorewall:net2all:DROP:IN=eth1 OUT= MAC=00:0f:1f:47:a4:6e:00:0b:23:ce:1f:61:08:00 SRC=60.11.125.37 DST=68.23.171.114 LEN=485 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=58011 DPT=1026 LEN=465
Jun  7 13:20:43 localhost kernel: [4449877.709000] Shorewall:net2all:DROP:IN=eth1 OUT= MAC=00:0f:1f:47:a4:6e:00:0b:23:ce:1f:61:08:00 SRC=60.11.125.37 DST=68.23.171.114 LEN=485 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=58011 DPT=1027 LEN=465
Jun  7 13:20:43 localhost kernel: [4449877.723000] Shorewall:net2all:DROP:IN=eth1 OUT= MAC=00:0f:1f:47:a4:6e:00:0b:23:ce:1f:61:08:00 SRC=60.11.125.37 DST=68.23.171.114 LEN=485 TOS=0x00 PREC=0x00 TTL=42 ID=0 DF PROTO=UDP SPT=58011 DPT=1026 LEN=465
Jun  7 13:20:52 localhost dhclient: DHCPREQUEST on eth1 to 192.168.0.1 port 67
Jun  7 13:20:52 localhost dhclient: DHCPACK from 192.168.0.1
Jun  7 13:20:52 localhost dhclient: execve (/lib/dhcp3-client/call-dhclient-script, ...): Permission denied
Jun  7 13:20:52 localhost dhclient: bound to 68.23.171.114 -- renewal in 235 seconds.
Jun  7 13:22:40 localhost kernel: [4449994.930000] SysRq : Keyboard mode set to XLATE
Jun  7 13:22:43 localhost kernel: [4449997.192000] SysRq : HELP : loglevel0-8 reBoot tErm Full kIll saK showMem Nice powerOff showPc unRaw Sync showTasks Unmount
Jun  7 13:22:43 localhost kernel: [4449997.539000] SysRq : Keyboard mode set to XLATE
Jun  7 13:22:45 localhost kernel: [4449999.215000] SysRq : Emergency Sync
Jun  7 13:22:45 localhost kernel: [4449999.218000] Emergency Sync complete
Jun  7 13:22:46 localhost exiting on signal 15
Jun  7 13:23:50 localhost syslogd 1.4.1#17ubuntu7: restart.
Jun  7 13:23:55 localhost mysqld_safe[6016]: started
Jun  7 13:23:55 localhost mysqld[6019]: ^G/usr/sbin/mysqld: Can't read dir of '/tmp/' (Errcode: 13)
Jun  7 13:23:55 localhost mysqld[6019]: ^G/usr/sbin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 13)
Jun  7 13:23:55 localhost mysqld[6019]: 060607 13:23:55 [ERROR] Aborting
Jun  7 13:23:55 localhost mysqld[6019]:
Jun  7 13:23:55 localhost mysqld[6019]: 060607 13:23:55 [Note] /usr/sbin/mysqld: Shutdown complete
Jun  7 13:23:55 localhost mysqld[6019]:
Jun  7 13:23:55 localhost mysqld_safe[6021]: ended
Jun  7 13:24:09 localhost /etc/init.d/mysql[6156]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jun  7 13:24:09 localhost /etc/init.d/mysql[6156]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jun  7 13:24:09 localhost /etc/init.d/mysql[6156]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jun  7 13:24:09 localhost /etc/init.d/mysql[6156]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jun  7 13:24:09 localhost /etc/init.d/mysql[6156]:
Jun  7 13:24:11 localhost postfix/master[6260]: daemon started -- version 2.2.10, configuration /etc/postfix
Jun  7 13:24:12 localhost hcid[6377]: Bluetooth HCI daemon
Jun  7 13:24:12 localhost hcid[6377]: Can't open system message bus connection: No reply within specified time
Jun  7 13:24:12 localhost sdpd[6382]: Bluetooth SDP daemon
Jun  7 13:24:12 localhost anacron[6437]: Anacron 2.3 started on 2006-06-07
Jun  7 13:24:12 localhost anacron[6437]: Normal exit (0 jobs run)
Jun  7 13:24:12 localhost /usr/sbin/cron[6467]: (CRON) INFO (pidfile fd = 3)
Jun  7 13:24:12 localhost /usr/sbin/cron[6468]: (CRON) STARTUP (fork ok)
Jun  7 13:24:12 localhost /usr/sbin/cron[6468]: (CRON) INFO (Running @reboot jobs)
Jun  7 13:24:42 localhost shutdown[6668]: shutting down for system reboot
Jun  7 13:24:42 localhost init: Switching to runlevel: 6
Jun  7 13:24:45 localhost postfix/master[6260]: terminating on signal 15
Jun  7 13:24:47 localhost sdpd[6382]: terminating...
Jun  7 13:24:47 localhost hcid[6377]: Exit.
Jun  7 13:24:48 localhost logger: Shorewall Stopped
Jun  7 13:24:48 localhost logger: Shorewall Cleared
Jun  7 13:24:48 localhost exiting on signal 15
Jun  7 13:36:51 localhost syslogd 1.4.1#17ubuntu7: restart.
Jun  7 13:36:55 localhost mysqld_safe[5972]: started
Jun  7 13:36:56 localhost mysqld[5975]: ^G/usr/sbin/mysqld: Can't read dir of '/tmp/' (Errcode: 13)
Jun  7 13:36:56 localhost mysqld[5975]: ^G/usr/sbin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 13)
Jun  7 13:36:56 localhost mysqld[5975]: 060607 13:36:56 [ERROR] Aborting
Jun  7 13:36:56 localhost mysqld[5975]:
Jun  7 13:36:56 localhost mysqld[5975]: 060607 13:36:56 [Note] /usr/sbin/mysqld: Shutdown complete
Jun  7 13:36:56 localhost mysqld[5975]:
Jun  7 13:36:56 localhost mysqld_safe[5977]: ended
Jun  7 13:37:10 localhost /etc/init.d/mysql[6112]: 0 processes alive and '/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping' resulted in
Jun  7 13:37:10 localhost /etc/init.d/mysql[6112]: ^G/usr/bin/mysqladmin: connect to server at 'localhost' failed
Jun  7 13:37:10 localhost /etc/init.d/mysql[6112]: error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Jun  7 13:37:10 localhost /etc/init.d/mysql[6112]: Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
Jun  7 13:37:10 localhost /etc/init.d/mysql[6112]:
Jun  7 13:37:12 localhost postfix/master[6216]: daemon started -- version 2.2.10, configuration /etc/postfix
Jun  7 13:37:12 localhost hcid[6333]: Bluetooth HCI daemon
Jun  7 13:37:13 localhost hcid[6333]: Can't open system message bus connection: No reply within specified time
Jun  7 13:37:13 localhost sdpd[6338]: Bluetooth SDP daemon
Jun  7 13:37:13 localhost anacron[6393]: Anacron 2.3 started on 2006-06-07
Jun  7 13:37:13 localhost anacron[6393]: Normal exit (0 jobs run)
Jun  7 13:37:13 localhost /usr/sbin/cron[6423]: (CRON) INFO (pidfile fd = 3)
Jun  7 13:37:13 localhost /usr/sbin/cron[6424]: (CRON) STARTUP (fork ok)
Jun  7 13:37:13 localhost /usr/sbin/cron[6424]: (CRON) INFO (Running @reboot jobs)
Jun  7 13:37:42 localhost ntpdate[6621]: can't find host ntp.ubuntu.com
Jun  7 13:37:42 localhost ntpdate[6621]: no servers can be used, exiting
Jun  7 13:37:42 localhost postfix/master[6216]: reload configuration /etc/postfix
Jun  7 13:38:05 localhost shutdown[6654]: shutting down for system reboot
Jun  7 13:38:05 localhost init: Switching to runlevel: 6
Jun  7 13:38:08 localhost postfix/master[6216]: terminating on signal 15
Jun  7 13:38:10 localhost sdpd[6338]: terminating...
Jun  7 13:38:10 localhost hcid[6333]: Exit.
Jun  7 13:38:11 localhost logger: Shorewall Stopped
Jun  7 13:38:11 localhost logger: Shorewall Cleared
Jun  7 13:38:11 localhost exiting on signal 15
Jun  7 13:42:39 localhost syslogd 1.4.1#17ubuntu7: restart.
Jun  7 13:42:44 localhost mysqld_safe[5966]: started
Jun  7 13:42:44 localhost mysqld[5969]: ^G/usr/sbin/mysqld: Can't read dir of '/tmp/' (Errcode: 13)
Jun  7 13:42:44 localhost mysqld[5969]: ^G/usr/sbin/mysqld: File '/var/log/mysql/mysql-bin.index' not found (Errcode: 13)
Jun  7 13:42:44 localhost mysqld[5969]: 060607 13:42:44 [ERROR] Aborting

---

### Post by joelito on 2006-06-07
Try booting to safe mode and when you get to the shell type: 
```
chown -R yourname:yourname /home/yourname
```

Restart and try logging in...


What I think it happened was that somehow your file were suddenly converted to be root's

---

### Post by pchachte on 2006-06-07
Thanks, but that didn't work. 

The permissions for my users are all fine.  I can add a few more details about my problem. 

First, when I try to boot up, gdm does not start up. I get thrown into my terminal. 

Second, when I try to log in from the terminal, the error I get is: can't cd to /home/charles.

Any other ideas?

---

### Post by pchachte on 2006-06-07
The other thing I notice is that when I exit from safe mode, mysql fails to start because it can not connect to the host. My guess is that my problem is associated with my hostname, but I have no idea where to go from here. 

Any ideas?

---

### Post by bodhi.zazen on 2006-06-17
My system is also borked.

I was running Drapper Beta, updated to LTS.

Now when I boot GDM fails and I drop into a CLI. I cannot log in a my usual user and get an error "No Shell".

Log in as root, multiple problems. First I have no network (I am posting from a backup system). When I type ifup eth0 I get the error message you posted here.

As you have I chown -R user:user /home/user. I have re-set my shell from the CLI. No good.

Still borked.

Did you ever get an answer?

I suppoze I can re-install and restore home from backup, but still would like to know what happened and if I will still have porblems.

Thank you.

---

### Post by malv83 on 2006-06-20
I also did a ctrl-C out of checkinstall and my system is in the same state as yours.

---

### Post by steabert on 2006-06-22
If you can work in recovery mode, what does /etc/fstab say?

---

### Post by Pierre Senellart on 2006-09-07
This can be fixed by executing "chmod 755 /" as root. cf 

[https://launchpad.net/distros/ubuntu/+source/checkinstall/+bug/45763](https://launchpad.net/distros/ubuntu/+source/checkinstall/+bug/45763)

---

### Post by bodhi.zazen on 2006-09-07
> **Pierre Senellart said:**
> This can be fixed by executing "chmod 755 /" as root. cf 

[https://launchpad.net/distros/ubuntu/+source/checkinstall/+bug/45763](https://launchpad.net/distros/ubuntu/+source/checkinstall/+bug/45763)

Interesting. That Ubuntu install is long gone for me.

---

