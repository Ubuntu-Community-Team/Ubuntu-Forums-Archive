---
title: "sitill cannot connect to my box on ssh 22"
date: 2006-02-24
forum: Desktop Environments
---

### Post by Hotchilli on 2006-02-24
still cannot connect to my box from outside

root@asas:/home/bliss# netstat -a | grep ssh
tcp        0      0 *:ssh                   *:*                     LISTEN
unix  2      [ ACC ]     STREAM     LISTENING     1364   /tmp/ssh-XXjD8xlU/agent.586
root@***:/home/bliss# netstat -tln
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:20000           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:11372           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
tcp        0      0 192.168.1.94:53         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:119             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN
root@asas:/home/bliss# netstat -tld
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:20000                 *:*                     LISTEN
tcp        0      0 *:11372                 *:*                     LISTEN
tcp        0      0 *:10000                 *:*                     LISTEN
tcp        0      0 192.168.1.94:domain     *:*                     LISTEN
tcp        0      0 localhost:domain        *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 *:nntp                  *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN


post 22 forarded can ping can do trce ok but no ssh.

are any of these prcessess stoping ssh.???


ux
USER       PID %CPU %MEM   VSZ  RSS TTY      STAT START   TIME COMMAND
root         1  0.4  0.0  1492  512 ?        S    11:08   0:04 init
root         2  0.0  0.0     0    0 ?        SW   11:08   0:00 [keventd]
root         3  0.1  0.0     0    0 ?        SWN  11:08   0:02 [ksoftirqd_CPU0]
root         4  0.0  0.0     0    0 ?        SW   11:08   0:00 [kswapd]
root         5  0.0  0.0     0    0 ?        SW   11:08   0:00 [bdflush]
root         6  0.3  0.0     0    0 ?        SW   11:08   0:03 [kupdated]
root         7  0.0  0.0     0    0 ?        SW   11:08   0:00 [khubd]
root        11  0.0  0.0     0    0 ?        SW   11:08   0:00 [kreiserfsd]
root       210  0.0  0.0     0    0 ?        SW   11:08   0:00 [eth0]
root       321  0.0  0.0  1544  592 ?        S    11:08   0:01 /sbin/syslogd
root       327  0.0  0.1  2172 1312 ?        S    11:08   0:00 /sbin/klogd
root       333  0.0  0.2  2868 1696 ?        S    11:08   0:00 /usr/sbin/named
message    348  0.0  0.1  2084  904 ?        S    11:08   0:00 /usr/bin/dbus-daemon-1 --system
news       386  0.0  0.5 11332 3900 ?        S    11:09   0:00 /usr/lib/news/bin/innd -p 3
news       387  0.0  0.1  2444 1260 ?        S    11:09   0:00 /bin/sh /usr/lib/news/bin/rc.news
pkspxy     394  0.0  0.0  1488  416 ?        S    11:09   0:00 /usr/sbin/pkspxy -o -F /etc/pkspxy.cnews       402  0.0  0.4  4680 2944 ?        SN   11:09   0:00 /usr/bin/perl -w /usr/lib/news/bin/croot       488  0.0  0.1  2956 1140 ?        S    11:09   0:00 /usr/lib/postfix/master
root       494  0.0  0.0  1512  468 ?        S    11:09   0:00 /usr/sbin/smartd
postfix    502  0.0  0.1  2964 1168 ?        S    11:09   0:00 pickup -l -t fifo -u -c
postfix    503  0.0  0.1  2996 1200 ?        S    11:09   0:00 qmgr -l -t fifo -u -c
root       516  0.0  0.1  2860 1244 ?        S    11:09   0:00 /usr/sbin/sshd
daemon     543  0.0  0.0  1672  636 ?        S    11:09   0:00 /usr/sbin/atd
root       548  0.0  0.1  2144  836 ?        S    11:09   0:00 /usr/sbin/xinetd -pidfile /var/run/xroot       549  0.0  0.1  1748  736 ?        S    11:09   0:00 /usr/sbin/cron
root       555  0.0  0.8  8616 6180 ?        S    11:09   0:00 /usr/bin/perl /usr/share/usermin/minroot       556  0.0  0.8  8616 6180 ?        S    11:09   0:00 /usr/bin/perl /usr/share/webmin/miniroot       558  0.0  0.3  8896 2292 ?        S    11:09   0:00 /usr/bin/gdm
root       561  0.0  0.0  1484  476 tty1     S    11:09   0:00 /sbin/getty 38400 tty1
root       562  0.0  0.0  1484  476 tty2     S    11:09   0:00 /sbin/getty 38400 tty2
root       563  0.0  0.0  1484  476 tty3     S    11:09   0:00 /sbin/getty 38400 tty3
root       564  0.0  0.0  1484  476 tty4     S    11:09   0:00 /sbin/getty 38400 tty4
root       565  0.0  0.0  1484  476 tty5     S    11:09   0:00 /sbin/getty 38400 tty5
root       566  0.0  0.0  1484  476 tty6     S    11:09   0:00 /sbin/getty 38400 tty6
root       567  0.0  0.3  9244 2736 ?        S    11:09   0:00 /usr/bin/gdm
root       568  3.8  2.4 87476 17708 ?       R<   11:09   0:39 /usr/X11R6/bin/X :0 -nolisten tcp -dbliss      586  0.1  1.1 16216 8516 ?        S    11:09   0:01 /usr/bin/gnome-session
bliss      637  0.0  0.1  2428  804 ?        S    11:09   0:00 /usr/bin/ssh-agent /usr/bin/gnome-sebliss      639  0.5  1.1  9488 7864 ?        S    11:09   0:05 /usr/lib/gconf2/gconfd-2 5
bliss      644  0.0  0.1  2244 1024 ?        S    11:09   0:00 /usr/bin/gnome-keyring-daemon
bliss      646  0.0  0.3  5204 2644 ?        S    11:09   0:00 /usr/lib/bonobo-activation/bonobo-acbliss      648  0.0  0.2  3868 1612 ?        S    11:09   0:00 gnome-smproxy --sm-client-id defaultbliss      650  0.0  1.0 17236 7800 ?        S    11:09   0:00 /usr/lib/control-center/gnome-settinnews       660  0.0  0.1  2480 1308 ?        S    11:10   0:00 /bin/sh /usr/lib/news/bin/innwatch
bliss      856  0.2  1.0 11968 7284 ?        S    11:10   0:02 /usr/bin/metacity --sm-client-id=defbliss      863  0.4  1.6 18868 11716 ?       S    11:10   0:04 gnome-panel --sm-client-id default2
bliss      865  0.3  1.7 22784 12464 ?       S    11:10   0:03 nautilus --no-default-window --sm-clbliss      874  0.0  1.7 22784 12464 ?       S    11:10   0:00 nautilus --no-default-window --sm-clbliss      875  0.0  1.7 22784 12464 ?       S    11:10   0:00 nautilus --no-default-window --sm-clbliss      877  0.0  0.5  9508 3564 ?        S    11:10   0:00 /usr/lib/gnome-vfs2/gnome-vfs-daemonbliss      880  0.0  0.5  9508 3564 ?        S    11:10   0:00 /usr/lib/gnome-vfs2/gnome-vfs-daemonbliss      881  0.0  0.5  9508 3564 ?        S    11:10   0:00 /usr/lib/gnome-vfs2/gnome-vfs-daemonbliss      882  0.0  1.7 22784 12464 ?       S    11:10   0:00 nautilus --no-default-window --sm-clbliss      883  0.0  1.7 22784 12464 ?       S    11:10   0:00 nautilus --no-default-window --sm-clbliss      885  0.2  1.3 16584 9552 ?        S    11:10   0:02 /usr/lib/gnome-panel/wnck-applet --obliss      887  0.1  1.1 16768 7856 ?        S    11:10   0:01 /usr/lib/gnome-applets/mixer_applet2bliss      905  0.1  1.1 16568 8204 ?        S    11:10   0:01 /usr/lib/gnome-panel/clock-applet --bliss      907  0.0  0.9 14900 6820 ?        S    11:10   0:00 /usr/lib/gnome-panel/notification-arbliss      919  0.5  1.6 21724 11552 ?       R    11:10   0:05 gnome-terminal
bliss      920  0.0  0.0  2204  668 ?        S    11:10   0:00 gnome-pty-helper
bliss      922  0.0  0.1  2504 1404 ttyp1    S    11:10   0:00 bash
bliss      923  0.0  1.6 21724 11552 ?       S    11:10   0:00 gnome-terminal
bliss      925  0.0  1.6 21724 11552 ?       S    11:10   0:00 gnome-terminal
root       929  0.0  0.2  2536 1436 ttyp1    S    11:10   0:00 bash
bliss      952  6.4  4.2 47272 29944 ?       S    11:19   0:26 /usr/lib/mozilla/mozilla-bin
bliss      969  0.0  4.2 47272 29944 ?       S    11:19   0:00 /usr/lib/mozilla/mozilla-bin
bliss      970  0.0  4.2 47272 29944 ?       S    11:19   0:00 /usr/lib/mozilla/mozilla-bin
bliss      972  0.0  4.2 47272 29944 ?       S    11:19   0:00 /usr/lib/mozilla/mozilla-bin
news      1117  0.0  0.0  2020  500 ?        S    11:20   0:00 sleep 600
root      1132  0.0  0.1  2840  836 ttyp1    R    11:26   0:00 ps aux


many thanks

HC:-| :-|

---

### Post by lamego on 2006-02-24
What do you mean by "outside" ? Are you behind a router or something ?
Are you able to ssh locally ?
From a local point of view everything looks fine with your ssh.

---

### Post by Hotchilli on 2006-02-24
yes I can connect locally 
router has got port 22 forwarded

hc;)

---

