---
title: "Problem with processes using 100% of cpu"
date: 2006-02-17
forum: Desktop Environments
---

### Post by guitonoklops9 on 2006-02-17
I am new to Ubuntu and linux ...

I have succesfully installed Ubuntu 5.1 on my computer:

Dell Dimension 8300
Pentium 4 3.4 ghz
512 MB Ram
15 GB HD
Onboard Video: AGP 8x

When viewing the System Monitor I find that my cpu is constantly running at 100%.  I don't know enough about system processes yet to identify the problem.  I wouldn't mind a recommendation on where I can learn about this.  

Any help would be greatly appreciated!

Here is a copy of "*ps aux*"

luke@ubuntu:~$ ps aux
USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
root 1 1.9 0.1 1560 528 ? S 14:05 1:17 init [2]
root 2 0.0 0.0 0 0 ? SN 14:06 0:00 [ksoftirqd/0]
root 3 0.0 0.0 0 0 ? S< 14:06 0:02 [events/0]
root 4 0.0 0.0 0 0 ? S< 14:06 0:00 [khelper]
root 5 0.0 0.0 0 0 ? S< 14:06 0:00 [kthread]
root 7 0.0 0.0 0 0 ? S< 14:06 0:00 [kacpid]
root 70 0.0 0.0 0 0 ? S< 14:07 0:00 [kblockd/0]
root 101 0.0 0.0 0 0 ? S 14:07 0:00 [pdflush]
root 102 0.0 0.0 0 0 ? S 14:07 0:03 [pdflush]
root 104 0.0 0.0 0 0 ? S< 14:07 0:00 [aio/0]
root 103 0.0 0.0 0 0 ? S 14:07 0:00 [kswapd0]
root 689 0.0 0.0 0 0 ? S 14:07 0:00 [kseriod]
root 921 0.0 0.0 0 0 ? S< 14:07 0:00 [ata/0]
root 924 0.0 0.0 0 0 ? S 14:07 0:00 [scsi_eh_0]
root 925 0.0 0.0 0 0 ? S 14:07 0:00 [scsi_eh_1]
root 1870 0.0 0.0 0 0 ? S 14:07 0:00 [khubd]
root 3004 0.1 0.0 0 0 ? S 14:08 0:05 [kjournald]
root 3187 0.1 0.1 1660 568 ? S<s 14:09 0:04 udevd--daemon
root 4714 0.0 0.0 0 0 ? S 14:12 0:00 [kjournald]
dhcp 5970 0.0 0.2 2332 1132 ? Ss 14:16 0:00 dhclient3 -pf /
root 6524 0.0 0.1 1824 1024 ? Ss 14:18 0:00 /usr/sbin/acpid
syslog 6539 0.0 0.1 1764 760 ? Ss 14:18 0:00 /sbin/syslogd -
root 6556 0.0 0.0 1564 392 ? Ss 14:18 0:01 /bin/dd bs 1 if
klog 6558 0.4 0.3 2456 1564 ? Ss 14:18 0:13 /sbin/klogd -P
105 6571 0.0 0.2 2144 1044 ? Ss 14:18 0:00 /usr/bin/dbus-d
root 6625 0.0 0.4 10604 2576 ? Ss 14:19 0:00 /usr/sbin/gdm
root 6626 0.0 0.5 10932 3016 ? S 14:19 0:01 /usr/sbin/gdm
root 6677 20.6 5.0 41428 26116 ? R 14:19 10:57/usr/X11R6/bin/
cupsys 6697 0.8 0.6 6288 3288 ? Ss 14:19 0:27/usr/sbin/cupsd
hplip 6723 0.0 0.2 12612 1284 ? Ssl 14:19 0:00 /usr/sbin/hpiod
hplip 6730 0.1 1.1 8824 5844 ? S 14:20 0:03 python /usr/sbi
root 6923 0.0 0.1 1920 812 ? Ss 14:21 0:00 hcid: processin
root 6929 0.0 0.1 1608 552 ? Ss 14:21 0:00 /usr/sbin/sdpd
root 6939 0.0 0.0 0 0 ? S< 14:21 0:00 [krfcommd]
daemon 6971 0.0 0.1 1752 656 ? Ss 14:21 0:00 /usr/sbin/atd
root 6984 0.0 0.1 1812 852 ? Ss 14:21 0:00 /usr/sbin/cron
root 7016 0.0 0.0 1560 488 tty1 Ss+ 14:22 0:00 /sbin/getty 384
root 7017 0.0 0.0 1560 496 tty2 Ss+ 14:22 0:00 /sbin/getty 384
root 7020 0.0 0.0 1560 492 tty3 Ss+ 14:22 0:00 /sbin/getty 384
root 7023 0.0 0.0 1560 496 tty4 Ss+ 14:22 0:00 /sbin/getty 384
root 7024 0.0 0.0 1560 492 tty5 Ss+ 14:22 0:00 /sbin/getty 384
root 7025 0.0 0.0 1556 492 tty6 Ss+ 14:22 0:00 /sbin/getty 384
luke 7046 1.1 1.7 18028 9228 ? Ss 14:24 0:34x-session-manag
luke 7084 0.0 0.1 3124 1004 ? Ss 14:24 0:00 /usr/bin/ssh-ag
luke 7087 0.0 0.1 2576 748 ? S 14:24 0:00 /usr/bin/dbus-l
luke 7088 0.0 0.2 2144 1032 ? Ss 14:24 0:00 dbus-daemon--f
luke 7090 3.6 1.6 11332 8680 ? S 14:24 1:44 /usr/lib/gconf2
luke 7093 0.0 0.2 2328 1056 ? S 14:25 0:00 /usr/bin/gnome-
luke 7097 0.3 0.5 6312 2788 ? Ss 14:25 0:10 /usr/lib/bonobo
luke 7099 1.3 1.4 13276 7400 ? Ss 14:25 0:38 /usr/bin/metaci
luke 7101 0.6 1.7 19440 8960 ? S 14:25 0:19 /usr/lib/contro
luke 7107 2.8 0.2 2708 1408 ? S 14:26 1:19 /usr/lib/gamin/
luke 7121 0.4 0.4 5920 2360 ? S 14:26 0:13 xscreensaver -n
luke 7126 2.3 2.3 20632 12088 ? Ssl 14:27 1:04 gnome-panel--s
luke 7128 3.5 2.7 30496 13996 ? Ssl 14:27 1:37 nautilus --no-d
luke 7151 0.6 1.6 37708 8576 ? Ss 14:27 0:17gnome-cups-icon
luke 7156 0.9 1.4 13700 7532 ? S 14:28 0:26 /usr/lib/notifi
luke 7168 0.0 0.6 8348 3436 ? Sl 14:28 0:01 /usr/lib/gnome-
luke 7180 0.0 0.1 2264 808 ? S 14:29 0:00 /usr/lib/nautil
luke 7185 1.3 1.9 18568 9876 ? S 14:29 0:33 /usr/lib/gnome-
luke 7194 0.5 1.7 19440 9028 ? Sl 14:29 0:13 /usr/lib/gnome-
luke 7212 1.0 1.8 21568 9676 ? S 14:30 0:25 /usr/lib/gnome-
luke 7217 1.5 2.2 20924 11548 ? S 14:31 0:37 /usr/lib/gnome-
luke 7237 0.2 1.5 17104 7784 ? S 14:32 0:06 /usr/lib/gnome-
luke 7709 35.9 2.6 38076 13652 ? Sl 15:10 0:39 gnome-terminal
luke 7722 0.2 0.1 2268 704 ? S 15:11 0:00 gnome-pty-helpe
luke 7723 2.4 0.3 4628 2012 pts/0 Ss 15:11 0:01 bash
luke 7744 0.0 0.2 3860 1048 pts/0 R+ 15:12 0:01 ps aux
luke@ubuntu:~$

---

### Post by GeneralZod on 2006-02-17
```

top

```

is a far better method of measuring this than ps -aux, as processes are sorted by CPU usage.  Try it out! :)

To answer your question, though, it looks like gnome-terminal is the culprit, here.

---

### Post by guitonoklops9 on 2006-02-17
ok ... "top" sounds good.

to resolve my problem with gnome-terminal should i just run:

kill gnome-terminal

? (just a guess)

---

