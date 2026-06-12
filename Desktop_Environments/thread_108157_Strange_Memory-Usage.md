---
title: "Strange Memory-Usage"
date: 2005-12-25
forum: Desktop Environments
---

### Post by daschl on 2005-12-25
hello folks :)

i tried to start jedit but this nice error message came up:

```

gromph@baenre:~$ jedit
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
GC Warning: Out of Memory!  Returning NIL!
Segmentation fault

```

so i checked my memory with free

```

gromph@baenre:~$ free
             total       used       free     shared    buffers     cached
Mem:        515792     501372      14420          0      54784     240360
-/+ buffers/cache:     206228     309564
Swap:       401616          0     401616

```

it says that only 14MB of my 512MB are free for usage

so i did a ps -aux and checked the memory usage for each program.

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   1560   528 ?        S    13:48   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   13:48   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   13:48   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   13:48   0:00 [khelper]
root         5  0.0  0.0      0     0 ?        S<   13:48   0:00 [kthread]
root         7  0.0  0.0      0     0 ?        S<   13:48   0:00 [kacpid]
root        97  0.0  0.0      0     0 ?        S<   13:48   0:00 [kblockd/0]
root       123  0.0  0.0      0     0 ?        S    13:48   0:00 [pdflush]
root       124  0.0  0.0      0     0 ?        S    13:48   0:00 [pdflush]
root       126  0.0  0.0      0     0 ?        S<   13:48   0:00 [aio/0]
root       125  0.0  0.0      0     0 ?        S    13:48   0:00 [kswapd0]
root       711  0.0  0.0      0     0 ?        S    13:48   0:00 [kseriod]
root      1934  0.0  0.0      0     0 ?        S    13:48   0:00 [khubd]
root      3101  0.0  0.0      0     0 ?        S    13:48   0:00 [kjournald]
root      3227  0.0  0.1   1664   572 ?        S<s  13:48   0:00 udevd --daemon
root      4412  0.0  0.0      0     0 ?        S    13:48   0:00 [khpsbpkt]
root      4935  0.0  0.0      0     0 ?        S    13:48   0:00 [kjournald]
root      5199  0.0  0.0      0     0 ?        S    13:48   0:00 [shpchpd_event]
root      5807  0.0  0.0      0     0 ?        S<   13:48   0:00 [ipw2200/0]
root      5952  0.0  0.0      0     0 ?        S    13:48   0:00 [pccardd]
root      5997  0.0  0.0      0     0 ?        S    13:48   0:00 [knodemgrd_0]
root      6898  0.0  0.0   1564   396 ?        Ss   13:48   0:00 /bin/dd bs 1 if
klog      6900  0.0  0.3   2576  1568 ?        Ss   13:48   0:00 /sbin/klogd -P
105       6913  0.0  0.2   2148  1092 ?        Ss   13:48   0:00 /usr/bin/dbus-d
hal       6926  0.0  0.7   5120  3808 ?        Ss   13:48   0:00 /usr/sbin/hald
hal       6931  0.0  0.1   1864   600 ?        S    13:48   0:00 hald-addon-acpi
hal       6941  0.0  0.1   1868   632 ?        S    13:48   0:01 hald-addon-stor
root      7352  0.0  0.4  10604  2576 ?        Ss   13:48   0:00 /usr/sbin/gdm
root      7371  0.0  0.5  10932  3024 ?        S    13:48   0:00 /usr/sbin/gdm
root      7419  3.2  7.5  41840 38788 ?        S    13:48   0:51 /usr/X11R6/bin/
hplip     7457  0.0  0.2  20808  1384 ?        Ssl  13:48   0:00 /usr/sbin/hpiod
dhcp      7488  0.0  0.2   2332  1136 ?        Ss   13:48   0:00 dhclient3 -pf /
hplip     7494  0.0  1.1   8828  5852 ?        S    13:48   0:00 python /usr/sbi
root      7595  0.0  0.1   1704   732 ?        Ss   13:48   0:00 /sbin/cardmgr
root      7704  0.0  0.1   1552   532 ?        SNs  13:48   0:00 /usr/sbin/power
root      7719  0.0  0.1   1920   812 ?        Ss   13:48   0:00 hcid: processin
root      7725  0.0  0.1   1612   556 ?        Ss   13:48   0:00 /usr/sbin/sdpd
root      7735  0.0  0.0      0     0 ?        S<   13:48   0:00 [krfcommd]
daemon    7767  0.0  0.1   1748   652 ?        Ss   13:48   0:00 /usr/sbin/atd
root      7780  0.0  0.1   1816   860 ?        Ss   13:48   0:00 /usr/sbin/cron
root      7816  0.0  0.0   1560   496 tty1     Ss+  13:48   0:00 /sbin/getty 384
root      7817  0.0  0.0   1556   492 tty2     Ss+  13:48   0:00 /sbin/getty 384
root      7818  0.0  0.0   1560   496 tty3     Ss+  13:48   0:00 /sbin/getty 384
root      7819  0.0  0.0   1560   492 tty4     Ss+  13:48   0:00 /sbin/getty 384
root      7820  0.0  0.0   1560   492 tty5     Ss+  13:48   0:00 /sbin/getty 384
root      7821  0.0  0.0   1556   488 tty6     Ss+  13:48   0:00 /sbin/getty 384
gromph    7846  0.0  1.8  18292  9308 ?        Ss   13:49   0:00 x-session-manag
gromph    7884  0.0  0.1   3124  1008 ?        Ss   13:49   0:00 /usr/bin/ssh-ag
gromph    7887  0.0  0.1   2572   744 ?        S    13:49   0:00 /usr/bin/dbus-l
gromph    7888  0.0  0.1   2144  1028 ?        Ss   13:49   0:00 dbus-daemon --f
gromph    7890  0.1  1.7  11588  8908 ?        S    13:49   0:01 /usr/lib/gconf2
gromph    7920  0.0  0.2   2324  1052 ?        S    13:49   0:00 /usr/bin/gnome-
gromph    7922  0.0  0.5   6324  2768 ?        Ss   13:49   0:00 /usr/lib/bonobo
gromph    7924  0.0  1.6  19160  8684 ?        S    13:49   0:00 /usr/lib/contro
gromph    7927  0.0  0.2   2712  1528 ?        S    13:49   0:00 /usr/lib/gamin/
gromph    7939  0.0  0.4   5920  2356 ?        S    13:49   0:00 xscreensaver -n
gromph    7963  0.2  1.5  13576  7776 ?        Ss   13:49   0:03 metacity --sm-s
gromph    7965  0.0  1.3  16984  6904 ?        Ss   13:49   0:00 gnome-volume-ma
gromph    7967  0.1  2.8  29788 14580 ?        Ssl  13:49   0:01 nautilus --sm-c
gromph    7969  0.1  2.3  20420 12260 ?        Ssl  13:49   0:02 gnome-panel --s
gromph    7971  0.0  1.5  37396  7908 ?        Ssl  13:49   0:00 gnome-cups-icon
gromph    7973  0.0  1.8  17944  9424 ?        Ss   13:49   0:00 update-notifier
gromph    7976  0.0  0.6   8352  3464 ?        Sl   13:49   0:00 /usr/lib/gnome-
gromph    7978  0.0  0.7  12012  3964 ?        S    13:49   0:00 /usr/lib/notifi
gromph    7981  1.2  2.1  19556 10948 ?        S    13:49   0:19 /usr/lib/gnome-
gromph    7983  0.0  1.7  18888  8936 ?        Sl   13:49   0:00 /usr/lib/gnome-
gromph    7993  0.0  0.1   2264   812 ?        S    13:49   0:00 /usr/lib/nautil
gromph    8001  0.0  1.4  17048  7608 ?        S    13:49   0:00 /usr/lib/gnome-
gromph    8003  0.2  1.7  18484  9072 ?        S    13:49   0:03 /usr/lib/gnome-
gromph    8005  0.0  1.6  17812  8336 ?        S    13:49   0:00 /usr/lib/gnome-
gromph    8007  0.0  2.1  20528 10868 ?        S    13:49   0:00 /usr/lib/gnome-
gromph    8009  0.0  1.8  21524  9536 ?        S    13:49   0:00 /usr/lib/gnome-
gromph    8019  4.1  7.2 106820 37140 ?        Sl   13:50   1:02 /usr/lib/mozill
gromph    8043  0.2  3.2  29000 16780 ?        S    13:50   0:03 gaim
root      8278  0.0  0.1   1824  1024 ?        SNs  13:53   0:00 /usr/sbin/acpid
cupsys    8311  0.0  0.6   6288  3276 ?        SNs  13:53   0:00 /usr/sbin/cupsd
syslog    8735  0.0  0.1   1764   792 ?        SNs  13:54   0:00 /sbin/syslogd -
gromph    8986  3.2  2.6  30968 13560 ?        Sl   14:06   0:17 gnome-terminal
gromph    8987  0.0  0.1   2268   704 ?        S    14:06   0:00 gnome-pty-helpe
gromph    8988  0.0  0.3   4640  2048 pts/0    Ss   14:06   0:00 bash
root      9144  0.9  0.5   5776  3040 pts/0    S    14:14   0:00 /usr/lib/gconf2
root      9148  0.0  0.2   2576  1364 ?        S    14:14   0:00 /usr/lib/gamin/
gromph    9155  0.0  0.2   3860  1040 pts/0    R+   14:15   0:00 ps aux

```
so approx. 30% of the total memory is used.
what happend to the other ~70%?

i think that's really strange
:confused:

tia
daschl

---

### Post by sciurus on 2005-12-25
[http://ubuntuforums.org/showthread.php?t=42988](http://ubuntuforums.org/showthread.php?t=42988)
[http://ubuntuforums.org/showthread.php?t=72466](http://ubuntuforums.org/showthread.php?t=72466)

---

