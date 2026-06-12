---
title: "tmpfs mounts using almost all available memory"
date: 2006-04-28
forum: Desktop Environments
---

### Post by chphilli on 2006-04-28
First off, I apologize if this has been covered already, but I don't see this referred to directly from Google searches, or searching through the forums here. (If this has been detailed elsewhere links would be appreciated.)

I just finished installing Breezy on an older machine (Dual 866Mhz P3, 256Mb), and noticed the following output from free:

```

chris@ezra:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           250        243          6          0         29        177
-/+ buffers/cache:         36        213
Swap:         2110          0       2110

```

The 6Mb "free" worries me a bit. Upon looking into the issue further, I noticed the following output from df:

```

chris@ezra:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/md0                18G   575M    17G   4% /
tmpfs                  132M      0   132M   0% /dev/shm
tmpfs                  132M    13M   119M  10% /lib/modules/2.6.12-9-386/volatile
/dev/hdb1              6.6G    16M   6.3G   1% /boot
/dev/hdd1               99G   135M    94G   1% /home
/dev/hdb2              6.9G    54k   6.6G   1% /tmp

```

So it looks like the two tmpfs mounts are claiming a very large portion of my installed memory? I don't know that this is a problem ( will Ubuntu use /dev/shm or /lib/modules/2.6.12-9-386/volatile for process that need memory? ), but it just seems strange to me. Is this something that I should be worried about or not? How will it impact performance of the machine? 

Just to show that there is really nothing running on this machine right now:

```

chris@ezra:~$ ps -A v
  PID TTY      STAT   TIME  MAJFL   TRS   DRS   RSS %MEM COMMAND
    1 ?        S      0:01     11    26  1409   484  0.1 init [2]
    2 ?        SN     0:00      0     0     0     0  0.0 [ksoftirqd/0]
    3 ?        S<     0:00      0     0     0     0  0.0 [events/0]
    4 ?        S<     0:00      0     0     0     0  0.0 [khelper]
    5 ?        S<     0:00      0     0     0     0  0.0 [kthread]
    7 ?        S<     0:00      0     0     0     0  0.0 [kacpid]
   64 ?        S<     0:00      0     0     0     0  0.0 [kblockd/0]
   92 ?        S      0:00      0     0     0     0  0.0 [pdflush]
   93 ?        S      0:00      0     0     0     0  0.0 [pdflush]
   95 ?        S<     0:00      0     0     0     0  0.0 [aio/0]
   94 ?        S      0:00      0     0     0     0  0.0 [kswapd0]
  680 ?        S      0:00      0     0     0     0  0.0 [kseriod]
  861 ?        S      0:00      0     0     0     0  0.0 [scsi_eh_0]
 1906 ?        S      0:00      0     0     0     0  0.0 [khubd]
 3330 ?        S      0:02      0     0     0     0  0.0 [md0_raid1]
 3385 ?        S      0:01      0     0     0     0  0.0 [kjournald]
 3483 ?        S<s    0:00      0    29  1626   564  0.2 udevd --daemon
 4695 ?        S      0:00      0     0     0     0  0.0 [kjournald]
 5494 ?        S      0:00      0     0     0     0  0.0 [kgameportd]
 6013 ?        Ss     0:00      0   389  1938  1124  0.4 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0
 6506 ?        Ss     0:00      0    16  1543   644  0.2 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 6532 ?        Ss     0:00      0    25  1538   400  0.1 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 6534 ?        Ss     0:00      0    18  2441  1564  0.6 /sbin/klogd -P /var/run/klogd/kmsg
 6546 ?        Ss     0:01      0    72  1683   740  0.2 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 6557 tty2     Ss+    0:00      0    10  1549   496  0.1 /sbin/getty 38400 tty2
 6558 tty3     Ss+    0:00      0    10  1545   492  0.1 /sbin/getty 38400 tty3
 6559 tty4     Ss+    0:00      0    32  1783   548  0.2 /usr/bin/tail -f /var/log/base-config-pkgsel.log
 7828 ?        Ss     0:00      0    12  1739   656  0.2 /usr/sbin/atd
 7883 ?        Ss     0:00      0    24  1783   764  0.2 /usr/sbin/cron
 9412 tty5     Ss+    0:00      0    10  1549   496  0.1 /sbin/getty 38400 tty5
 9415 tty6     Ss+    0:00      0    10  1549   496  0.1 /sbin/getty 38400 tty6
12312 ?        Ss     0:00      0   264  3307  1580  0.6 /usr/sbin/sshd
12339 tty1     Ss+    0:00      0    10  1541   492  0.1 /sbin/getty 38400 tty1
12891 ?        Ss     0:00      0   633  4510  1644  0.6 /usr/sbin/exim4 -bd -q30m
15022 ?        Ss     0:00      0    25  1746   800  0.3 /sbin/syslogd -u syslog
15131 ?        Ss     0:00      0   264  6051  1996  0.7 sshd: chris [priv]
15133 ?        R      0:00      0   264  6203  2084  0.8 sshd: chris@pts/1
15134 pts/1    Ss     0:00      0   606  5009  3112  1.2 -bash
15209 pts/1    R+     0:00      0    62  3597   884  0.3 ps -A v


```

---

