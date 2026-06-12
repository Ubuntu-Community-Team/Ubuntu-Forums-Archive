---
title: "Mass query (cache) denied in /var/log/syslog"
date: 2009-01-03
forum: General Help
---

### Post by solitudex86 on 2009-01-03
Just noticed, that I'm getting MASS non stop of this in my syslog. Any ideas? I tried google. Below is what I am getting non stop.

```

Jan  2 23:15:24 conghosted named[4206]: client 65.54.237.139#18155: query (cache) 'totalmed.com/A/IN' denied
Jan  2 23:15:25 conghosted named[4206]: client 69.64.194.12#38470: query (cache) 'totalmed.com/MX/IN' denied
Jan  2 23:15:25 conghosted named[4206]: client 207.68.176.68#43812: query (cache) 'totalmed.com/A/IN' denied
Jan  2 23:15:26 conghosted named[4206]: client 65.55.178.25#39007: query (cache) 'totalmed.com/MX/IN' denied
Jan  2 23:15:26 conghosted named[4206]: client 207.68.176.68#61712: query (cache) 'totalmed.com/A/IN' denied
Jan  2 23:15:29 conghosted named[4206]: client 69.64.194.11#58695: query (cache) 'ns1.totalmed.com/AAAA/IN' denied
Jan  2 23:15:29 conghosted named[4206]: client 69.64.194.11#55623: query (cache) 'ns2.totalmed.com/AAAA/IN' denied
Jan  2 23:15:29 conghosted named[4206]: client 65.55.178.25#57416: query (cache) 'totalmed.com/A/IN' denied
Jan  2 23:15:30 conghosted named[4206]: client 207.68.176.72#47670: query (cache) 'totalmed.com/A/IN' denied
Jan  2 23:15:31 conghosted named[4206]: client 207.68.176.74#12635: query (cache) 'totalmed.com/A/IN' denied
Jan  2 23:15:31 conghosted named[4206]: client 144.232.70.21#40082: query (cache) 'totalmed.com/MX/IN' denied
Jan  2 23:15:33 conghosted named[4206]: client 144.232.70.21#55433: query (cache) 'totalmed.com/MX/IN' denied
Jan  2 23:15:35 conghosted named[4206]: client 65.55.178.23#36121: query (cache) 'totalmed.com/A/IN' denied
Jan  2 23:15:36 conghosted named[4206]: client 207.68.176.69#38721: query (cache) 'totalmed.com/A/IN' denied
Jan  2 23:15:37 conghosted named[4206]: client 144.232.70.21#38401: query (cache) 'totalmed.com/MX/IN' denied
Jan  2 23:15:37 conghosted named[4206]: client 144.232.70.21#17545: query (cache) 'totalmed.com/MX/IN' denied
Jan  2 23:15:37 conghosted named[4206]: client 144.232.70.21#43229: query (cache) 'totalmed.com/MX/IN' denied
Jan  2 23:15:37 conghosted named[4206]: client 144.232.70.21#38401: query (cache) 'totalmed.com/MX/IN' denied
Jan  2 23:15:44 conghosted named[4206]: client 69.64.194.12#38470: query (cache) 'ns1.totalmed.com/A6/IN' denied
Jan  2 23:15:46 conghosted named[4206]: client 69.64.194.12#38470: query (cache) 'ns2.totalmed.com/A6/IN' denied


```

---

### Post by LateNiteTV on 2009-01-03
can you please post the output of:
```
ps aux
```

---

### Post by solitudex86 on 2009-01-03
Here is the output, what I was just told though, was someone used one of my IP's as their nameserver.

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2844  1692 ?        Ss    2008   0:14 /sbin/init
root         2  0.0  0.0      0     0 ?        S<    2008   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<    2008   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<    2008   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<    2008   0:01 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<    2008   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<    2008   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<    2008   0:02 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<    2008   0:13 [events/0]
root        10  0.0  0.0      0     0 ?        S<    2008   0:13 [events/1]
root        11  0.0  0.0      0     0 ?        S<    2008   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<    2008   0:01 [kblockd/0]
root        47  0.0  0.0      0     0 ?        S<    2008   0:02 [kblockd/1]
root        68  0.0  0.0      0     0 ?        S<    2008   0:00 [kseriod]
root       139  0.0  0.0      0     0 ?        S     2008   0:07 [pdflush]
root       140  0.0  0.0      0     0 ?        S     2008   0:33 [pdflush]
root       141  0.0  0.0      0     0 ?        S<    2008   0:02 [kswapd0]
root       181  0.0  0.0      0     0 ?        S<    2008   0:00 [aio/0]
root       182  0.0  0.0      0     0 ?        S<    2008   0:00 [aio/1]
root      1109  0.0  0.1   9132  2636 ?        Ss    2008   0:00 /usr/sbin/console-kit-daemon
root      1279  0.0  0.0      0     0 ?        S<    2008   0:00 [ksuspend_usbd]
root      1287  0.0  0.0      0     0 ?        S<    2008   0:00 [khubd]
root      1288  0.0  0.0      0     0 ?        S<    2008   0:00 [ata/0]
root      1295  0.0  0.0      0     0 ?        S<    2008   0:00 [ata/1]
root      1301  0.0  0.0      0     0 ?        S<    2008   0:00 [ata_aux]
root      1318  0.0  0.0      0     0 ?        S<    2008   0:00 [scsi_eh_0]
root      1319  0.0  0.0      0     0 ?        S<    2008   0:00 [scsi_eh_1]
root      1320  0.0  0.0      0     0 ?        S<    2008   0:00 [scsi_eh_2]
root      1329  0.0  0.0      0     0 ?        S<    2008   0:00 [scsi_eh_3]
root      1812  0.0  0.0      0     0 ?        S<    2008   0:00 [scsi_eh_4]
root      1813  0.0  0.0      0     0 ?        S<    2008   0:00 [scsi_eh_5]
root      2171  0.0  0.0      0     0 ?        S<    2008   2:25 [kjournald]
root      2361  0.0  0.0   2224   652 ?        S<s   2008   0:00 /sbin/udevd --daemon
root      3687  0.0  0.0      0     0 ?        S<    2008   0:00 [kjournald]
root      4088  0.0  0.0   1716   508 tty4     Ss+   2008   0:00 /sbin/getty 38400 tty4
root      4089  0.0  0.0   1716   508 tty5     Ss+   2008   0:00 /sbin/getty 38400 tty5
root      4091  0.0  0.0   1716   508 tty2     Ss+   2008   0:00 /sbin/getty 38400 tty2
root      4094  0.0  0.0   1716   512 tty3     Ss+   2008   0:00 /sbin/getty 38400 tty3
root      4095  0.0  0.0   1716   512 tty6     Ss+   2008   0:00 /sbin/getty 38400 tty6
syslog    4137  0.0  0.0   1936   684 ?        Ss    2008   5:02 /sbin/syslogd -u syslog
root      4156  0.0  0.0   1872   540 ?        S     2008   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4158  0.0  0.0   2996  1856 ?        Ss    2008   0:00 /sbin/klogd -P /var/run/klogd/kmsg
bind      4206  0.0  0.6  49120 13180 ?        Ssl   2008  11:51 /usr/sbin/named -u bind
root      4232  0.0  0.0   5316  1016 ?        Ss    2008   1:05 /usr/sbin/sshd
ntp       4256  0.0  0.0   4124  1220 ?        Ss    2008   1:32 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 108:113 -g
daemon    4489  0.0  0.0   1984   420 ?        Ss    2008   0:00 /usr/sbin/atd
root      4500  0.0  0.0   2104   888 ?        Ss    2008   0:04 /usr/sbin/cron
root      4541  0.0  0.0   1716   508 tty1     Ss+   2008   0:00 /sbin/getty 38400 tty1
root      6392  0.0  0.0   3628   960 ?        S     2008   0:00 /usr/sbin/vsftpd
root      6829  0.0  0.3  24344  7812 ?        Ss    2008   0:43 /usr/sbin/apache2 -k start
109       6864  0.0  0.0   2568   936 ?        Ss    2008   0:00 /usr/bin/dbus-daemon --system
www-data  9588  0.0  0.2  24708  5572 ?        S    Jan02   0:00 /usr/sbin/apache2 -k start
root     17546  0.0  0.0   3296  1224 ?        Ss    2008   0:05 SCREEN
root     17547  0.0  0.0   3252  1752 pts/1    Ss    2008   0:00 /bin/bash
www-data 19751  0.0  0.4  26040  8924 ?        S    Jan02   0:00 /usr/sbin/apache2 -k start
www-data 19753  0.0  0.4  25780  8592 ?        S    Jan02   0:00 /usr/sbin/apache2 -k start
snmp     20962  0.0  0.1   8700  3820 ?        S    Jan02   0:02 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid 127.0.0.1
root     21223  0.0  0.0   1772   532 ?        S    Jan02   0:00 /bin/sh /usr/bin/mysqld_safe
mysql    21347  0.0  0.8 128440 17552 ?        Sl   Jan02   0:04 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root     21349  0.0  0.0   1976   644 ?        S    Jan02   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
www-data 23860  0.0  0.4  25792  8596 ?        S    Jan02   0:00 /usr/sbin/apache2 -k start
www-data 27282  0.0  0.4  26748  9212 ?        S    Jan02   0:00 /usr/sbin/apache2 -k start
www-data 27309  0.0  0.4  26044  8840 ?        S    Jan02   0:00 /usr/sbin/apache2 -k start
www-data 27311  0.0  0.2  24708  5556 ?        S    Jan02   0:00 /usr/sbin/apache2 -k start
root     27351  0.2  0.5  30012 11392 pts/1    S+    2008  98:21 ./ghost++
root     29252  0.0  0.0   5396  1748 ?        Ss   Jan02   0:00 /usr/lib/postfix/master
postfix  29256  0.0  0.0   5444  1808 ?        S    Jan02   0:00 qmgr -l -t fifo -u
postfix  29280  0.0  0.1   5772  2444 ?        S    Jan02   0:00 tlsmgr -l -t unix -u -c
www-data 29351  0.0  0.2  24344  4516 ?        S    Jan02   0:00 /usr/sbin/apache2 -k start
www-data 29371  0.0  0.2  24344  4396 ?        S    00:32   0:00 /usr/sbin/apache2 -k start
postfix  29372  0.0  0.0   5404  1644 ?        S    00:34   0:00 pickup -l -t fifo -u -c
root     29396  0.0  0.1   8056  2520 ?        Ss   00:57   0:00 sshd: root@pts/0 
root     29398  0.0  0.0   3240  1752 pts/0    Ss   00:57   0:00 -bash
root     29410  0.0  0.0   2580   964 pts/0    R+   00:57   0:00 ps aux
www-data 29490  0.0  0.4  27140  9776 ?        S    Jan01   0:00 /usr/sbin/apache2 -k start

```

---

### Post by solitudex86 on 2009-01-03
Solved, I just killed named service. Although I dunno about the other guy that has me set as his NS.

---

### Post by Kevbert on 2009-01-03
It's got something to do with hotmail/MSN. If you type in terminal
```
whois 65.54.237.139
```
you'll get information on that address.

---

