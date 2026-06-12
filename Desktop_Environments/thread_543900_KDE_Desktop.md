---
title: "KDE Desktop"
date: 2007-09-05
forum: Desktop Environments
---

### Post by Bratna on 2007-09-05
I just installed Kubuntu on my system I am using as a CS Source server. I don't have it hooked up to a keyboard mouse or monitor. I configure everything using SSH. When I run a ps awx I see that there are alot of things running that are taking recourses from the server. What I was thinking is that if I don't let the OS load KDE I will save some recourses but I dont know how to change what loads when the os starts.  Here is a list of what is running with  the cs server shut down. Any help would be great. 



 1 ?        Ss     0:01 /sbin/init
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S<     0:00 [events/0]
    6 ?        S<     0:00 [khelper]
    7 ?        S<     0:00 [kthread]
   30 ?        S<     0:00 [kblockd/0]
   31 ?        S<     0:00 [kacpid]
   32 ?        S<     0:00 [kacpi_notify]
   94 ?        S<     0:00 [kseriod]
  119 ?        S      0:00 [pdflush]
  120 ?        S      0:00 [pdflush]
  121 ?        S<     0:00 [kswapd0]
  122 ?        S<     0:00 [aio/0]
 1928 ?        S<     0:00 [ksuspend_usbd]
 1929 ?        S<     0:00 [khubd]
 2097 ?        S<     0:00 [ata/0]
 2098 ?        S<     0:00 [ata_aux]
 2234 ?        S<     0:00 [kjournald]
 2433 ?        S<s    0:00 /sbin/udevd --daemon
 3402 ?        S<     0:00 [kgameportd]
 3854 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 3855 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 3858 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 3859 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 3860 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 3861 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4107 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 4209 ?        Ss     0:00 /sbin/syslogd
 4263 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4265 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4286 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 4302 ?        Ss     0:02 /usr/sbin/hald
 4303 ?        S      0:00 hald-runner
 4309 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
 4317 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event1
 4322 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event3
 4325 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event4
 4328 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event5
 4340 ?        S      0:06 hald-addon-storage: polling /dev/hdc
 4353 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 4368 ?        Ssl    0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
 4385 ?        Ss     0:00 avahi-daemon: registering [csserver.local]
 4386 ?        Ss     0:00 avahi-daemon: chroot helper
 4400 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
 4477 ?        Ss     0:00 /usr/sbin/hpiod
 4480 ?        S      0:00 python /usr/sbin/hpssd
 4530 ?        S      0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=3
 4576 ?        Ss     0:00 /usr/sbin/sshd
 4617 ?        Ss     0:00 /usr/sbin/hcid -x -s
 4634 ?        S<     0:00 [krfcommd]
 4669 ?        Ss     0:00 /usr/sbin/atd
 4683 ?        Ss     0:00 /usr/sbin/cron
 4740 ?        Ss     0:00 /usr/bin/kdm
 4773 tty7     Ss+    0:03 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-JLK3iu
 4795 ?        S      0:00 -:0
 4840 ?        S      0:05 /usr/bin/kdm_greet
 5029 ?        SNs    0:00 /usr/sbin/cupsd
 5323 pts/2    Ss     0:00 -bash
 5459 pts/2    R+     0:00 ps awx

---

### Post by trippinnik on 2007-09-06
I did a search in the forums and got this for you: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
it explains how to use a console program that enables startup services.  You'll want to disable kdm.

---

