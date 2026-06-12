---
title: "what's  wrong?"
date: 2008-12-28
forum: General Help
---

### Post by luofeiyu on 2008-12-28
my  computer    run   very  very  slow!
what's  wromg?

pt@pt-laptop:~$ ps aux
USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
root 1 0.5 0.3 2844 1688 ? Ss 15:17 0:01 /sbin/init
root 2 0.0 0.0 0 0 ? S< 15:17 0:00 [kthreadd]
root 3 0.0 0.0 0 0 ? S< 15:17 0:00 [migration/0]
root 4 0.0 0.0 0 0 ? S< 15:17 0:00 [ksoftirqd/0]
root 5 0.0 0.0 0 0 ? S< 15:17 0:00 [watchdog/0]
root 6 0.0 0.0 0 0 ? S< 15:17 0:00 [events/0]
root 7 0.0 0.0 0 0 ? S< 15:17 0:00 [khelper]
root 41 0.0 0.0 0 0 ? S< 15:17 0:00 [kblockd/0]
root 44 0.0 0.0 0 0 ? S< 15:17 0:00 [kacpid]
root 45 0.0 0.0 0 0 ? S< 15:17 0:00 [kacpi_notify]
root 137 0.0 0.0 0 0 ? S< 15:17 0:00 [kseriod]
root 175 0.0 0.0 0 0 ? S 15:17 0:00 [pdflush]
root 176 0.0 0.0 0 0 ? S 15:17 0:00 [pdflush]
root 177 0.0 0.0 0 0 ? S< 15:17 0:00 [kswapd0]
root 218 0.0 0.0 0 0 ? S< 15:17 0:00 [aio/0]
root 1499 0.0 0.0 0 0 ? S< 15:17 0:00 [ksuspend_usbd]
root 1502 0.0 0.0 0 0 ? S< 15:17 0:00 [khubd]
root 1562 0.0 0.0 0 0 ? S< 15:17 0:00 [ata/0]
root 1569 0.0 0.0 0 0 ? S< 15:17 0:00 [ata_aux]
root 2297 0.0 0.0 0 0 ? S< 15:17 0:00 [scsi_eh_0]
root 2299 0.0 0.0 0 0 ? S< 15:17 0:00 [scsi_eh_1]
root 2347 0.0 0.0 0 0 ? S< 15:17 0:00 [scsi_eh_2]
root 2349 0.0 0.0 0 0 ? S< 15:17 0:00 [scsi_eh_3]
root 2743 0.0 0.0 0 0 ? S< 15:17 0:00 [kjournald]
root 2968 0.1 0.1 2404 948 ? S<s 15:17 0:00 /sbin/udevd --d
root 3248 0.0 0.0 0 0 ? S< 15:18 0:00 [led_workqueue]
root 3288 0.0 0.0 0 0 ? S< 15:18 0:00 [kmmcd]
root 3312 0.0 0.0 0 0 ? S< 15:18 0:00 [pccardd]
root 3325 0.0 0.0 0 0 ? S< 15:18 0:00 [kpsmoused]
root 4638 0.0 0.1 2932 740 ? Ss 15:18 0:00 /usr/sbin/pppd
root 4791 0.0 0.1 1716 512 tty4 Ss+ 15:18 0:00 /sbin/getty 384
root 4792 0.0 0.1 1716 508 tty5 Ss+ 15:18 0:00 /sbin/getty 384
root 4796 0.0 0.1 1716 512 tty2 Ss+ 15:18 0:00 /sbin/getty 384
root 4797 0.0 0.1 1716 512 tty3 Ss+ 15:18 0:00 /sbin/getty 384
root 4799 0.0 0.1 1716 512 tty6 Ss+ 15:18 0:00 /sbin/getty 384
root 4974 0.0 0.2 2456 1360 ? Ss 15:18 0:00 /usr/sbin/acpid
root 5014 0.0 0.0 0 0 ? S< 15:18 0:00 [kondemand/0]
syslog 5079 0.0 0.1 1936 648 ? Ss 15:18 0:00 /sbin/syslogd -
root 5135 0.0 0.1 1872 540 ? S 15:18 0:00 /bin/dd bs 1 if
klog 5137 0.0 0.4 3300 2168 ? Ss 15:18 0:00 /sbin/klogd -P
108 5159 0.0 0.2 2828 1292 ? Ss 15:18 0:00 /usr/bin/dbus-d
root 5175 0.0 0.3 4580 1968 ? Ss 15:18 0:00 /usr/sbin/Netwo
root 5189 0.0 0.2 3388 1164 ? Ss 15:18 0:00 /usr/sbin/Netwo
root 5202 0.0 0.2 4112 1112 ? Ss 15:18 0:00 /usr/bin/system
avahi 5231 0.0 0.2 2760 1388 ? Ss 15:18 0:00 avahi-daemon: r
avahi 5232 0.0 0.0 2760 472 ? Ss 15:18 0:00 avahi-daemon: c
root 5283 0.0 0.1 1772 520 ? S 15:18 0:00 /bin/sh /usr/bi
mysql 5325 0.0 3.2 127092 16328 ? Sl 15:18 0:00 /usr/sbin/mysql
root 5327 0.0 0.1 1700 556 ? S 15:18 0:00 logger -p daemo
root 5487 0.1 1.3 12436 6768 ? Ss 15:18 0:00 /opt/PostgreSQL
daemon 5515 0.0 1.1 12436 5864 ? S 15:18 0:00 /opt/PostgreSQL
daemon 5516 0.0 1.1 12436 5864 ? S 15:18 0:00 /opt/PostgreSQL
daemon 5517 0.0 1.1 12436 5864 ? S 15:18 0:00 /opt/PostgreSQL
daemon 5518 0.0 1.1 12436 5864 ? S 15:18 0:00 /opt/PostgreSQL
daemon 5519 0.0 1.1 12436 5864 ? S 15:18 0:00 /opt/PostgreSQL
root 5526 0.0 0.4 5920 2272 ? Ss 15:18 0:00 /usr/sbin/cupsd
postgres 5558 0.1 1.0 23628 5568 ? S 15:18 0:00 /opt/PostgreSQL
postgres 5559 0.0 0.1 10392 880 ? Ss 15:18 0:00 postgres: logge
postgres 5561 0.0 0.2 23628 1032 ? Ss 15:18 0:00 postgres: write
postgres 5562 0.0 0.1 23628 972 ? Ss 15:18 0:00 postgres: wal w
postgres 5563 0.0 0.2 23764 1116 ? Ss 15:18 0:00 postgres: autov
postgres 5564 0.0 0.2 10388 1020 ? Ss 15:18 0:00 postgres: stats
privoxy 5589 0.0 0.2 2728 1052 ? Ss 15:18 0:00 /usr/sbin/privo
113 5601 0.7 1.9 12436 9792 ? S 15:18 0:01 /usr/sbin/&#12304;T×O×R&#12305;
root 5646 0.0 0.1 2020 764 ? Ss 15:18 0:00 /usr/sbin/dhcdb
111 5665 0.2 0.8 6260 4340 ? Ss 15:18 0:00 /usr/sbin/hald
root 5668 0.0 0.4 7764 2336 ? Ssl 15:18 0:00 /usr/sbin/conso
root 5730 0.0 0.2 3236 1060 ? S 15:18 0:00 hald-runner
root 5743 0.0 0.2 3300 1056 ? S 15:18 0:00 hald-addon-inpu
111 5759 0.0 0.1 2204 904 ? S 15:18 0:00 hald-addon-acpi
root 5778 0.0 0.2 3304 1036 ? S 15:18 0:00 hald-addon-stor
root 5798 0.0 0.2 3052 1228 ? Ss 15:18 0:00 /usr/sbin/hcid
root 5804 0.0 0.0 0 0 ? S< 15:18 0:00 [btaddconn]
root 5805 0.0 0.0 0 0 ? S< 15:18 0:00 [btdelconn]
root 5811 0.0 0.2 2900 1024 ? S 15:18 0:00 /usr/lib/blueto
root 5815 0.0 0.2 2964 1216 ? S 15:18 0:00 /usr/lib/blueto
root 5820 0.0 0.0 0 0 ? S< 15:18 0:00 [krfcommd]
root 5845 0.0 0.3 14424 1680 ? Ss 15:18 0:00 /usr/sbin/gdm
root 5853 0.0 0.6 14892 3132 ? S 15:18 0:00 /usr/sbin/gdm
root 5881 1.3 6.0 39244 30812 tty7 Ss+ 15:18 0:02 /usr/bin/X :0 -
daemon 5884 0.0 0.0 1984 420 ? Ss 15:18 0:00 /usr/sbin/atd
root 5898 0.0 0.1 2104 892 ? Ss 15:18 0:00 /usr/sbin/cron
root 6034 0.0 0.1 1716 508 tty1 Ss+ 15:18 0:00 /sbin/getty 384
pt 6077 0.2 0.9 7732 4604 ? S 15:18 0:00 /usr/lib/libgco
pt 6079 0.0 0.4 14532 2120 ? S 15:18 0:00 /usr/bin/gnome-
pt 6080 0.0 1.5 29372 7740 ? Ssl 15:18 0:00 x-session-manag
pt 6129 0.0 0.0 0 0 ? Z 15:18 0:00 [sci] <defunct>
pt 6137 0.0 1.3 23612 7044 ? Ss 15:18 0:00 /usr/bin/seahor
pt 6141 0.0 0.2 2700 1104 ? Ss 15:18 0:00 dbus-daemon --f
pt 6142 0.6 3.6 48288 18652 ? Sl 15:18 0:00 gnome-settings-
pt 6150 0.0 1.1 28712 5764 ? Sl 15:18 0:00 /usr/bin/pulsea
pt 6153 0.0 0.4 5676 2208 ? S 15:18 0:00 /usr/lib/pulsea
pt 6162 0.0 0.5 15628 2676 ? Ss 15:19 0:00 gnome-screensav
pt 6167 0.0 0.1 1772 536 ? S 15:19 0:00 /bin/sh /usr/bi
pt 6169 0.7 4.3 51832 22108 ? S 15:19 0:00 gnome-panel --s
pt 6170 0.7 5.3 82524 26940 ? S 15:19 0:00 nautilus --no-d
pt 6177 0.0 0.6 32128 3212 ? Ssl 15:19 0:00 /usr/lib/bonobo
pt 6186 0.0 0.4 5636 2144 ? S 15:19 0:00 /usr/lib/gvfs/g
pt 6210 0.0 0.3 29048 1884 ? Ssl 15:19 0:00 /usr/lib/gvfs//
pt 6242 1.4 2.8 21636 14328 ? S 15:19 0:01 /usr/bin/compiz
pt 6243 0.0 1.1 15064 5920 ? S 15:19 0:00 bluetooth-apple
pt 6246 0.1 2.6 38800 13564 ? S 15:19 0:00 update-notifier
pt 6252 0.0 2.0 54628 10404 ? Sl 15:19 0:00 /usr/lib/evolut
pt 6253 0.0 1.1 15696 5700 ? S 15:19 0:00 tracker-applet
pt 6255 0.0 2.0 30904 10364 ? SNl 15:19 0:00 trackerd
pt 6260 0.2 2.3 25812 12076 ? S 15:19 0:00 nm-applet --sm-
pt 6261 0.0 0.9 21108 4712 ? Ss 15:19 0:00 /usr/lib/gnome-
pt 6264 0.1 2.4 24548 12292 ? S 15:19 0:00 python /usr/sha
pt 6266 0.1 2.0 26264 10416 ? Ss 15:19 0:00 gnome-power-man
pt 6271 0.0 1.9 39416 9956 ? Sl 15:19 0:00 /usr/lib/evolut
pt 6281 0.0 1.3 67280 6636 ? Sl 15:19 0:00 /usr/lib/evolut
pt 6293 0.0 0.4 5632 2176 ? S 15:19 0:00 /usr/lib/gvfs/g
pt 6345 0.0 0.5 22332 2672 ? S 15:19 0:00 /usr/lib/gvfs/g
pt 6355 0.1 2.6 42952 13288 ? Sl 15:19 0:00 /usr/lib/gnome-
pt 6357 0.1 2.3 24552 11676 ? S 15:19 0:00 /usr/lib/fast-u
pt 6367 0.0 0.0 1772 484 ? Ss 15:19 0:00 /bin/sh -c /usr
pt 6368 0.0 0.0 1772 504 ? S 15:19 0:00 /bin/sh /usr/bi
pt 6370 0.1 1.8 31136 9436 ? S 15:19 0:00 /usr/bin/gtk-wi
pt 6462 0.6 3.2 64632 16260 ? Sl 15:20 0:00 gnome-terminal
pt 6464 0.0 0.1 2796 760 ? S 15:20 0:00 gnome-pty-helpe
pt 6465 0.3 0.6 6280 3484 pts/0 Rs 15:20 0:00 bash
pt 6509 0.0 0.1 2644 1008 pts/0 R+ 15:20 0:00 ps aux

---

### Post by p_quarles on 2008-12-28
Well, that's incredibly difficult to read without any formatting, but it doesn't *look* like anything there is taking up too much CPU time. Try running:
```
free -m
```
and post the results here.

---

### Post by luofeiyu on 2008-12-28
pt@pt-laptop:~$ free   -m
             total       used       free     shared    buffers     cached
Mem:           495        476         18          0         13        221
-/+ buffers/cache:        241        253
Swap:          956          0        956
what's  wrong?how  to  do ?
thank  you

---

### Post by cariboo on 2008-12-28
When pasting output in a reply, click the new reply button and use the advanced editor, the code tags are created by clicking the **#** sign.

From the output of ps ax it looks like you have both mysql and postgreSQL running, but mysql is not running properly. Try shutting mysql down by typing in a terminal:

```
sudo /etc/init.d/mysql stop
```

To see if that makes a difference. Another way to see which application is using all your resources is to run:

```
top
```

in a terminal.

Jim

---

