---
title: "Examining File Progress"
date: 2008-01-14
forum: Desktop Environments
---

### Post by geekcliff on 2008-01-14
Anyone Know what that annoying box is that says Examining File Progress, that keeps popping up in kubuntu?

---

### Post by p_quarles on 2008-01-14
Is this specific to Kubuntu 7.10, or have you experienced it in other versions? If the former, it may be the desktop search daemon that was added to the latest version. What's the output of this?:
```
ps aux | grep strigi
```

---

### Post by geekcliff on 2008-01-14
> **p_quarles said:**
> Is this specific to Kubuntu 7.10, or have you experienced it in other versions? If the former, it may be the desktop search daemon that was added to the latest version. What's the output of this?:
```
ps aux | grep strigi
```

Not had this problem before 7.10, the output of that code was 5303  0.0  0.1   2984   764 pts/1    R+   13:26   0:00 grep strigi

---

### Post by p_quarles on 2008-01-14
Oops! Try:
```
ps aux | grep strigi*
```
I think its process is actually called something like "strigi-daemon." If the output is exactly the same, post the output of the simple:
```
ps aux
```

---

### Post by geekcliff on 2008-01-14
> **p_quarles said:**
> Oops! Try:
```
ps aux | grep strigi*
```
I think its process is actually called something like "strigi-daemon." If the output is exactly the same, post the output of the simple:
```
ps aux
```

First one, 5318  0.0  0.1   2988   772 pts/1    S+   13:30   0:00 grep

---

### Post by geekcliff on 2008-01-14
> **p_quarles said:**
> Oops! Try:
```
ps aux | grep strigi*
```
I think its process is actually called something like "strigi-daemon." If the output is exactly the same, post the output of the simple:
```
ps aux
```

Simple one, USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.3   2952  1852 ?        Ss   12:55   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   12:55   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   12:55   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        SN   12:55   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   12:55   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   12:55   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   12:55   0:00 [khelper]
root        26  0.0  0.0      0     0 ?        S<   12:55   0:00 [kblockd/0]
root        27  0.0  0.0      0     0 ?        S<   12:55   0:00 [kacpid]
root        28  0.0  0.0      0     0 ?        S<   12:55   0:00 [kacpi_notify]
root        88  0.0  0.0      0     0 ?        S<   12:55   0:00 [kseriod]
root       109  0.0  0.0      0     0 ?        S    12:55   0:00 [pdflush]
root       110  0.0  0.0      0     0 ?        S    12:55   0:00 [pdflush]
root       111  0.0  0.0      0     0 ?        S<   12:55   0:00 [kswapd0]
root       163  0.0  0.0      0     0 ?        S<   12:55   0:00 [aio/0]
root      1964  0.0  0.0      0     0 ?        S<   12:55   0:00 [ksuspend_usbd]
root      1965  0.0  0.0      0     0 ?        S<   12:55   0:00 [khubd]
root      2116  0.0  0.0      0     0 ?        S<   12:55   0:00 [ata/0]
root      2117  0.0  0.0      0     0 ?        S<   12:55   0:00 [ata_aux]
root      2337  0.0  0.0      0     0 ?        S<   12:55   0:00 [kjournald]
root      2542  0.0  0.2   3032  1380 ?        S<s  12:56   0:00 /sbin/udevd --d
root      3386  0.0  0.0      0     0 ?        S<   12:56   0:00 [kpsmoused]
root      3513  0.0  0.0      0     0 ?        S<   12:56   0:00 [pegasus]
root      3537  0.0  0.0      0     0 ?        S<   12:56   0:00 [kgameportd]
root      4002  0.0  0.1   1696   516 tty4     Ss+  12:56   0:00 /sbin/getty 384
root      4003  0.0  0.0   1692   512 tty5     Ss+  12:56   0:00 /sbin/getty 384
root      4005  0.0  0.1   1696   516 tty2     Ss+  12:56   0:00 /sbin/getty 384
root      4006  0.0  0.1   1692   516 tty3     Ss+  12:56   0:00 /sbin/getty 384
root      4007  0.0  0.1   1692   516 tty1     Ss+  12:56   0:00 /sbin/getty 384
root      4008  0.0  0.0   1692   512 tty6     Ss+  12:56   0:00 /sbin/getty 384
root      4084  0.0  0.0      0     0 ?        S<   12:56   0:00 [kondemand/0]
syslog    4144  0.0  0.1   1912   696 ?        Ss   12:56   0:00 /sbin/syslogd -
root      4197  0.0  0.1   1832   528 ?        S    12:56   0:00 /bin/dd bs 1 if
klog      4199  0.0  0.2   2484  1392 ?        Ss   12:56   0:00 /sbin/klogd -P
105       4220  0.0  0.2   2904  1092 ?        Ss   12:56   0:00 /usr/bin/dbus-d
root      4236  0.0  0.3  12556  2028 ?        Ssl  12:56   0:00 /usr/sbin/Netwo
root      4250  0.0  0.2   3280  1284 ?        Ss   12:56   0:00 /usr/sbin/Netwo
root      4263  0.0  0.1   3088   816 ?        Ss   12:56   0:00 /usr/bin/system
root      4264  0.0  0.2   2776  1260 ?        S    12:56   0:00 dbus-daemon --s
108       4283  0.0  0.8   5964  4172 ?        Ss   12:56   0:00 /usr/sbin/hald
root      4284  0.0  0.1   3092  1012 ?        S    12:56   0:00 hald-runner
108       4324  0.0  0.1   2156   892 ?        R    12:56   0:00 hald-addon-keyb
108       4332  0.0  0.1   2152   892 ?        S    12:56   0:00 /usr/lib/hal/ha
root      4411  0.0  0.4   5804  2164 ?        Ss   12:56   0:00 /usr/sbin/cupsd
108       4414  0.0  0.2   3260  1184 ?        S    12:56   0:00 hald-addon-stor
avahi     4628  0.0  0.2   2732  1368 ?        Ss   12:56   0:00 avahi-daemon: r
avahi     4629  0.0  0.0   2732   456 ?        Ss   12:56   0:00 avahi-daemon: c
root      4643  0.0  0.1   1996   892 ?        Ss   12:56   0:00 /usr/sbin/dhcdb
root      4665  0.0  0.2   2924  1176 ?        Ss   12:56   0:00 /usr/sbin/hcid
root      4678  0.0  0.1   2764   976 ?        S    12:56   0:00 /usr/lib/blueto
root      4681  0.0  0.0      0     0 ?        S<   12:56   0:00 [krfcommd]
root      4689  0.0  0.2   2836  1208 ?        S    12:56   0:00 /usr/lib/blueto
root      4712  0.0  0.2  13096  1456 ?        Ss   12:56   0:00 /usr/sbin/gdm -
root      4715  0.0  0.5  13652  2924 ?        S    12:56   0:00 /usr/sbin/gdm -
root      4720  9.5  7.1  41540 36844 tty7     SLs+ 12:56   3:25 /usr/bin/X :0 -
daemon    4770  0.0  0.0   1956   424 ?        Ss   12:56   0:00 /usr/sbin/atd
root      4784  0.0  0.1   2336   912 ?        Ss   12:56   0:00 /usr/sbin/cron
dhcp      4832  0.0  0.2   2420  1164 ?        S    12:56   0:00 /sbin/dhclient
cliff     4908  0.0  0.1   1756   540 ?        Ss   12:56   0:00 /bin/sh /usr/bi
cliff     4982  0.0  0.1   4432   540 ?        Ss   12:56   0:00 /usr/bin/ssh-ag
cliff     4985  0.0  0.1   2704   644 ?        S    12:56   0:00 /usr/bin/dbus-l
cliff     4986  0.0  0.1   2776   916 ?        Ss   12:56   0:00 /usr/bin/dbus-d
root      5016  0.0  0.0   1540   148 ?        S    12:56   0:00 start_kdeinit -
cliff     5017  0.0  0.8  26024  4384 ?        Ss   12:56   0:00 kdeinit Running
cliff     5020  0.0  0.6  25844  3100 ?        S    12:56   0:00 dcopserver [kde
cliff     5023  0.0  1.2  27252  6620 ?        S    12:56   0:00 klauncher [kdei
cliff     5025  0.0  2.6  32548 13776 ?        S    12:56   0:01 kded [kdeinit] 
cliff     5030  0.0  0.0   1676   368 ?        S    12:56   0:00 kwrapper ksmser
cliff     5032  0.0  1.6  27532  8512 ?        S    12:56   0:00 ksmserver [kdei
cliff     5033  0.1  2.3  30808 11932 ?        S    12:56   0:02 kwin [kdeinit] 
cliff     5035  0.1  2.5  31884 13296 ?        S    12:56   0:04 kdesktop [kdein
cliff     5038  0.0  1.0  26220  5376 ?        S    12:56   0:00 kio_file [kdein
cliff     5041  0.0  2.4  32356 12792 ?        S    12:56   0:01 kio_uiserver [k
cliff     5056  0.1  1.3  20672  6772 ?        S    12:56   0:02 /usr/bin/artsd
cliff     5059  0.0  1.5  27232  7856 ?        S    12:56   0:00 kaccess [kdeini
cliff     5064  0.0  2.4  31772 12716 ?        S    12:56   0:00 kmix [kdeinit] 
cliff     5065  0.0  3.2  30548 16820 ?        S    12:56   0:01 katapult -sessi
cliff     5069  0.6  8.3 136292 43280 ?        Sl   12:56   0:12 amarokapp -sess
cliff     5076  0.0  0.4   8136  2208 ?        S    12:56   0:00 aspell -a -S -C
cliff     5081  1.0  4.3  43752 22520 ?        S    12:57   0:21 kicker [kdeinit
cliff     5091  0.0  2.0  35356 10516 ?        S    12:57   0:00 knotify [kdeini
cliff     5092  0.0  3.6  39880 18904 ?        S    12:57   0:00 konqueror [kdei
cliff     5097  0.0  2.2  31084 11844 ?        S    12:57   0:00 /usr/bin/python
cliff     5100  0.0  2.2  33900 11424 ?        S    12:57   0:00 knetworkmanager
cliff     5101  0.0  3.6  39872 18904 ?        S    12:57   0:00 konqueror [kdei
cliff     5104  0.3  2.8  33980 14744 ?        S    12:57   0:06 adept_notifier
cliff     5105  0.0  1.8  28420  9728 ?        S    12:57   0:00 klipper [kdeini
cliff     5107  0.0  2.2  22820 11732 ?        S    12:57   0:00 python /usr/sha
cliff     5156  0.0  0.5   5688  2872 ?        S    12:59   0:00 /usr/lib/libgco
cliff     5239  0.0  0.1   1756   528 ?        S    13:22   0:00 /bin/sh /usr/bi
cliff     5251  0.0  0.1   1752   528 ?        S    13:22   0:00 /bin/sh /usr/li
cliff     5255 18.8 10.4 158808 54028 ?        Sl   13:22   1:48 /usr/lib/firefo
cliff     5278  0.5  4.8  90212 25200 ?        S    13:26   0:01 xfce4-terminal
cliff     5285  0.0  0.1   2664   740 ?        S    13:26   0:00 gnome-pty-helpe
cliff     5286  0.1  0.6   5780  3096 pts/1    Ss   13:26   0:00 bash
cliff     5324  0.0  0.1   2624  1004 pts/1    R+   13:32   0:00 ps aux

---

### Post by p_quarles on 2008-01-14
Hmm. Nothing there seems to be off at all.

Does the error message give you *any* other information? Without any, I'd just be blindly guessing.

---

### Post by geekcliff on 2008-01-15
> **p_quarles said:**
> Hmm. Nothing there seems to be off at all.

Does the error message give you *any* other information? Without any, I'd just be blindly guessing.

Its not actualy an error message, more a status box, it seems to be scanning the waste bin, but gets stuck.

---

