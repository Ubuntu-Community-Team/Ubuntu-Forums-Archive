---
title: "Slow login after upgrade from 6.06 to 6.06.1"
date: 2006-08-17
forum: Desktop Environments
---

### Post by peteruta on 2006-08-17
I just did an update today Aug 17th on 2 boxes. 
Sun Microsystems AMD workstation 
Toshiba Tecra M2

The Sun box went without a hitch.
The Toshiba went ok as well, but when I login, it takes 3 min after I press enter for my password. 

The CPU is not loaded 3-5% only
Nothing of note in any of the system logs or user logs
No errors for X, etc...

Has anyone see this? Once I get logged in, all works as it should, no problems.

PS and Top shots:

Here is a PS during the problem.

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 08:23 ?        00:00:01 init [2]
root         2     1  0 08:23 ?        00:00:00 [migration/0]
root         3     1  0 08:23 ?        00:00:00 [ksoftirqd/0]
root         4     1  0 08:23 ?        00:00:00 [watchdog/0]
root         5     1  0 08:23 ?        00:00:00 [events/0]
root         6     1  0 08:23 ?        00:00:00 [khelper]
root         7     1  0 08:23 ?        00:00:00 [kthread]
root         9     7  0 08:23 ?        00:00:00 [kblockd/0]
root        10     7  0 08:23 ?        00:00:00 [kacpid]
root       159     7  0 08:23 ?        00:00:00 [pdflush]
root       160     7  0 08:23 ?        00:00:00 [pdflush]
root       161     1  0 08:23 ?        00:00:00 [kswapd0]
root       162     7  0 08:23 ?        00:00:00 [aio/0]
root       750     7  0 08:23 ?        00:00:00 [kseriod]
root      1677     7  0 08:23 ?        00:00:03 [kacpid-work-0]
root      1865     7  0 08:23 ?        00:00:00 [khubd]
root      1887     1  0 08:23 ?        00:00:00 [khpsbpkt]
root      1915     1  0 08:23 ?        00:00:00 [knodemgrd_0]
root      1981     1  0 08:23 ?        00:00:02 [kjournald]
root      2204     1  0 08:23 ?        00:00:00 /sbin/udevd --daemon
root      3085     1  0 08:23 ?        00:00:00 [pccardd]
root      3141     1  0 08:23 ?        00:00:00 [pccardd]
daemon    3641     1  0 08:24 ?        00:00:00 /sbin/portmap
root      3932     1  0 08:24 ?        00:01:05 [ktoshkeyd]
root      3950     1  0 08:24 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    4045     1  0 08:24 ?        00:00:00 /sbin/syslogd -u syslog
root      4104     1  0 08:24 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4106     1  0 08:24 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmsg
hplip     4466     1  0 08:24 ?        00:00:00 /usr/sbin/hpiod
cupsys    4537     1  0 08:24 ?        00:00:21 /usr/sbin/cupsd
104       4565     1  0 08:24 ?        00:00:02 /usr/bin/dbus-daemon --system
108       4580     1  0 08:24 ?        00:00:07 /usr/sbin/hald
root      4581  4580  0 08:24 ?        00:00:00 hald-runner
108       4586  4581  0 08:24 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4646  4581  0 08:24 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
108       4660  4581  0 08:24 ?        00:00:01 /usr/lib/hal/hald-addon-storage
108       4661  4581  0 08:24 ?        00:00:01 /usr/lib/hal/hald-addon-storage
root      4677     1  0 08:24 ?        00:00:01 /sbin/dhcdbd --system
root      4699     1  0 08:24 ?        00:00:00 /usr/sbin/NetworkManager --pid-file=/var/run/NetworkManager/Netroot      4713     1  0 08:24 ?        00:00:00 /usr/sbin/NetworkManagerDispatcher --pid-file=/var/run/NetworkM113       4762     1  0 08:24 ?        00:00:00 /usr/sbin/exim4 -bd -q30m
root      4895     1  0 08:24 ?        00:00:01 /usr/sbin/powernowd -q
root      4922     1  0 08:24 ?        00:00:00 /usr/sbin/sshd
root      4981     1  0 08:24 ?        00:00:00 /usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive
root      5076     1  0 08:25 ?        00:00:00 hcid: processing events
root      5083     1  0 08:25 ?        00:00:00 /usr/sbin/sdpd
root      5094     1  0 08:25 ?        00:00:00 [krfcommd]
root      5107     1  0 08:25 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
daemon    5142     1  0 08:25 ?        00:00:00 /usr/sbin/atd
root      5155     1  0 08:25 ?        00:00:00 /usr/sbin/cron
root      5258     1  0 08:25 tty1     00:00:00 /bin/login --
root      5259     1  0 08:25 tty2     00:00:00 /sbin/getty 38400 tty2
root      5260     1  0 08:25 tty3     00:00:00 /sbin/getty 38400 tty3
root      5261     1  0 08:25 tty4     00:00:00 /sbin/getty 38400 tty4
root      5262     1  0 08:25 tty5     00:00:00 /sbin/getty 38400 tty5
root      5263     1  0 08:25 tty6     00:00:00 /sbin/getty 38400 tty6
root      5623     7  0 08:31 ?        00:00:00 [kacpid-work-1]
petem     5839     1  0 08:34 ?        00:00:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
petem     7602     1  0 08:51 ?        00:00:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
root      7945     7  0 08:57 ?        00:00:00 [kacpid-work-2]
root      7946     7  0 08:57 ?        00:00:00 [kacpid-work-3]
petem    15070  5258  0 14:19 tty1     00:00:00 -bash
root     15071 15070  0 14:19 tty1     00:00:00 -bash
petem    15207     1  0 14:20 ?        00:00:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
dhcp     17587  4677  0 15:11 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhclient/dhclient-eth0.leases -proot     17994  4922  0 15:17 ?        00:00:00 sshd: petem [priv]
petem    17996 17994  0 15:17 ?        00:00:00 sshd: petem@pts/0
petem    17997 17996  0 15:17 pts/0    00:00:00 -bash
root     18118 17997  0 15:19 pts/0    00:00:00 -bash
petem    18359     1  0 15:23 ?        00:00:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
root     18797     1  0 15:31 ?        00:00:00 /usr/sbin/gdm
root     18798 18797  0 15:31 ?        00:00:00 /usr/sbin/gdm
root     18803 18798  1 15:31 tty7     00:00:12 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolistepetem    19357     1  1 15:43 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 31
petem    19380 18798  2 15:43 ?        00:00:00 x-session-manager
petem    19422 19380  0 15:43 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-spetem    19426     1  0 15:43 ?        00:00:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
petem    19425     1  0 15:43 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
petem    19429     1  0 15:43 ?        00:00:00 /usr/bin/gnome-keyring-daemon
petem    19431     1  2 15:43 ?        00:00:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activapetem    19433     1  3 15:43 ?        00:00:00 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iipetem    19437 19433  0 15:43 ?        00:00:00 [xrdb] <defunct>



Top
-----------------------------------------------------------------


root@jasmin:/var/log# top

top - 15:45:29 up  7:22,  3 users,  load average: 0.13, 0.29, 0.32
Tasks:  83 total,   1 running,  81 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.7% us,  0.7% sy,  0.0% ni, 97.4% id,  0.0% wa,  0.3% hi,  1.0% si
Mem:   2073800k total,   734596k used,  1339204k free,    80400k buffers
Swap:  2104472k total,        0k used,  2104472k free,   532144k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
19444 root      16   0  2200 1100  856 R  0.7  0.1   0:00.59 top
 3932 root      19   4     0    0    0 S  0.3  0.0   1:06.25 ktoshkeyd
    1 root      16   0  1564  528  460 S  0.0  0.0   0:01.68 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.75 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.16 kblockd/0
   10 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kacpid
  159 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  160 root      15   0     0    0    0 S  0.0  0.0   0:00.51 pdflush
  161 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  162 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  750 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod
 1677 root      11  -5     0    0    0 S  0.0  0.0   0:03.52 kacpid-work-0
 1865 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1887 root      15   0     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt
 1915 root      15   0     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0
 1981 root      15   0     0    0    0 S  0.0  0.0   0:02.20 kjournald
 2204 root      13  -4  2432  920  368 S  0.0  0.0   0:00.86 udevd
 3085 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3141 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pccardd
 3641 daemon    16   0  1668  336  256 S  0.0  0.0   0:00.00 portmap
 3950 root      15   0  2680 1792  652 S  0.0  0.1   0:00.87 acpid
 4045 syslog    16   0  1764  672  548 S  0.0  0.0   0:00.10 syslogd
 4104 root      16   0  1684  500  412 S  0.0  0.0   0:00.10 dd
 4106 klog      18   0  2412 1340  388 S  0.0  0.1   0:00.10 klogd
 4466 hplip     16   0  4672  860  640 S  0.0  0.0   0:00.00 hpiod
 4537 cupsys    16   0  4208 1884 1384 S  0.0  0.1   0:21.37 cupsd
 4565 messageb  16   0  2324  924  688 S  0.0  0.0   0:02.86 dbus-daemon
 4580 haldaemo  16   0  6932 5532 1564 S  0.0  0.3   0:07.50 hald
 4581 root      17   0  2720  996  848 S  0.0  0.0   0:00.11 hald-runner
 4586 haldaemo  16   0  2004  872  764 S  0.0  0.0   0:00.07 hald-addon-acpi
 4646 haldaemo  15   0  2008  796  692 S  0.0  0.0   0:00.16 hald-addon-keyb
 4660 haldaemo  16   0  2012  864  760 S  0.0  0.0   0:01.06 hald-addon-stor
 4661 haldaemo  16   0  2008  864  760 S  0.0  0.0   0:01.17 hald-addon-stor
 4677 root      15   0  1952  884  716 S  0.0  0.0   0:01.07 dhcdbd
 4699 root      16   0 20324 2036 1676 S  0.0  0.1   0:00.77 NetworkManager
 4713 root      16   0  2932 1292 1052 S  0.0  0.1   0:00.03 NetworkManagerD
 4762 Debian-e  16   0  5220  964  692 S  0.0  0.0   0:00.00 exim4
 4895 root      21   5  1552  260  192 S  0.0  0.0   0:01.02 powernowd
 4922 root      16   0  4764 1064  756 S  0.0  0.1   0:00.00 sshd
 4981 root      16   0  2212  788  656 S  0.0  0.0   0:00.00 xinetd
 5076 root      16   0  1972  708  616 S  0.0  0.0   0:00.00 hcid






Thanks

Peter

---

