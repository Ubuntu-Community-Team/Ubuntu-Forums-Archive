---
title: "Ubuntu 9.04 sometimes hang on my Acer"
date: 2009-05-17
forum: General Help
---

### Post by mardangga on 2009-05-17
Hello everyone. 
I've problem with ubuntu Jaunty Jackalope on my Acer Travelmate 4720. Sometimes, it's hang (not responding). It's never happen when I'm using Ubuntu 8.10. I don't know what should I do. Is there anyone else who has the same problem with me? And how to fix it? 
Thx 4 u'r attention and sorry for my poor english.

---

### Post by mardangga on 2009-05-29
Hii everyone....
I've problem with Ubuntu 9.04 On my Acer Travelmate 4720.
It's always hang after I use it for a while. The screen was freeze, the keyboard is not working. But the mouse it's still can move. And the process inside I think it's still running.
Coz, I've test it. I download a files before ubuntu hang. When it's hang, the download progress is still 70%. So, I wait a while until I think it's already done. And then I turn off Linux by pressing the power button and turn it on again. 
I check my download progress, and the status is completed. So, I make conclusion, when my ubuntu hang (Screen freeze and keyboard no respond), the process is still running.
So, for anyone, please help me to fix this. I really2 need help.
Thx 4 u'r attention and sorry for my poor english.

---

### Post by baseface on 2009-05-29
how much ram do you have? and can you post the output of "ps aux".

---

### Post by lisati on 2009-05-29
[http://ubuntuforums.org/showthread.php?p=7364670#post7364670](http://ubuntuforums.org/showthread.php?p=7364670#post7364670)

---

### Post by mardangga on 2009-05-29
> **baseface said:**
> how much ram do you have? and can you post the output of "ps aux".

My ram is 2 GB, and this is my "ps aux" output:

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.3  0.0   3084  1884 ?        Ss   12:27   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   12:27   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   12:27   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   12:27   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   12:27   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   12:27   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   12:27   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   12:27   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   12:27   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   12:27   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   12:27   0:00 [khelper]
root        12  0.0  0.0      0     0 ?        S<   12:27   0:00 [kstop/0]
root        13  0.0  0.0      0     0 ?        S<   12:27   0:00 [kstop/1]
root        14  0.0  0.0      0     0 ?        S<   12:27   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S<   12:27   0:00 [kintegrityd/1]
root        16  0.0  0.0      0     0 ?        S<   12:27   0:00 [kblockd/0]
root        17  0.0  0.0      0     0 ?        S<   12:27   0:00 [kblockd/1]
root        18  0.0  0.0      0     0 ?        S<   12:27   0:00 [kacpid]
root        19  0.0  0.0      0     0 ?        S<   12:27   0:00 [kacpi_notify]
root        20  0.0  0.0      0     0 ?        S<   12:27   0:00 [cqueue]
root        21  0.0  0.0      0     0 ?        S<   12:27   0:00 [ata/0]
root        22  0.0  0.0      0     0 ?        S<   12:27   0:00 [ata/1]
root        23  0.0  0.0      0     0 ?        S<   12:27   0:00 [ata_aux]
root        24  0.0  0.0      0     0 ?        S<   12:27   0:00 [ksuspend_usbd]
root        25  0.0  0.0      0     0 ?        S<   12:27   0:00 [khubd]
root        26  0.0  0.0      0     0 ?        S<   12:27   0:00 [kseriod]
root        27  0.0  0.0      0     0 ?        S<   12:27   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        S<   12:27   0:00 [btaddconn]
root        29  0.0  0.0      0     0 ?        S<   12:27   0:00 [btdelconn]
root        30  0.0  0.0      0     0 ?        S    12:27   0:00 [pdflush]
root        31  0.0  0.0      0     0 ?        S    12:27   0:00 [pdflush]
root        32  0.0  0.0      0     0 ?        S<   12:27   0:00 [kswapd0]
root        33  0.0  0.0      0     0 ?        S<   12:27   0:00 [aio/0]
root        34  0.0  0.0      0     0 ?        S<   12:27   0:00 [aio/1]
root        35  0.0  0.0      0     0 ?        S<   12:27   0:00 [ecryptfs-kthr]
root        38  0.0  0.0      0     0 ?        S<   12:27   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S<   12:27   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S<   12:27   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S<   12:27   0:00 [scsi_eh_3]
root        42  0.0  0.0      0     0 ?        S<   12:27   0:00 [scsi_eh_4]
root        43  0.0  0.0      0     0 ?        S<   12:27   0:00 [kstriped]
root        44  0.0  0.0      0     0 ?        S<   12:27   0:00 [kmpathd/0]
root        45  0.0  0.0      0     0 ?        S<   12:27   0:00 [kmpathd/1]
root        46  0.0  0.0      0     0 ?        S<   12:27   0:00 [kmpath_handle]
root        47  0.0  0.0      0     0 ?        S<   12:27   0:00 [ksnapd]
root        48  0.0  0.0      0     0 ?        S<   12:27   0:00 [kondemand/0]
root        49  0.0  0.0      0     0 ?        S<   12:27   0:00 [kondemand/1]
root        50  0.0  0.0      0     0 ?        S<   12:27   0:00 [krfcommd]
root       329  0.0  0.0      0     0 ?        S<   12:27   0:00 [khpsbpkt]
root       446  0.0  0.0      0     0 ?        S<   12:27   0:00 [knodemgrd_0]
root       782  0.0  0.0      0     0 ?        S<   12:27   0:00 [kjournald]
root       916  0.0  0.0   2224   576 ?        S<s  12:27   0:00 /sbin/udevd --d
root      1563  0.0  0.0      0     0 ?        S<   12:27   0:00 [tifm]
root      1604  0.0  0.0      0     0 ?        S<   12:27   0:00 [pccardd]
root      1642  0.0  0.0      0     0 ?        S<   12:27   0:00 [kpsmoused]
root      1653  0.0  0.0      0     0 ?        S<   12:27   0:00 [iwl3945/0]
root      1654  0.0  0.0      0     0 ?        S<   12:27   0:00 [iwl3945/1]
root      1664  0.0  0.0      0     0 ?        S<   12:27   0:00 [iwl3945]
root      2370  0.0  0.0   1808   528 tty4     Ss+  12:27   0:00 /sbin/getty 384
root      2371  0.0  0.0   1808   528 tty5     Ss+  12:27   0:00 /sbin/getty 384
root      2374  0.0  0.0   1808   532 tty2     Ss+  12:27   0:00 /sbin/getty 384
root      2377  0.0  0.0   1808   528 tty3     Ss+  12:27   0:00 /sbin/getty 384
root      2378  0.0  0.0   1808   528 tty6     Ss+  12:27   0:00 /sbin/getty 384
root      2445  0.0  0.0   2204  1084 ?        Ss   12:27   0:00 /usr/sbin/acpid
syslog    2490  0.0  0.0   2040   700 ?        Ss   12:27   0:00 /sbin/syslogd -
root      2513  0.0  0.0   1968   536 ?        S    12:27   0:00 /bin/dd bs 1 if
klog      2515  0.0  0.1   3868  2636 ?        Ss   12:27   0:00 /sbin/klogd -P
108       2538  0.1  0.0   3140  1448 ?        Ss   12:27   0:00 /bin/dbus-daemo
root      2579  0.0  0.0   1872   552 ?        S    12:27   0:00 /bin/sh /usr/bi
mysql     2698  0.0  0.8 127740 16916 ?        Sl   12:27   0:00 /usr/sbin/mysql
root      3044  0.0  0.0   5780  1772 ?        Ss   12:27   0:00 /usr/lib/postfi
root      3098  0.0  0.0  10600  1480 ?        Ss   12:27   0:00 /usr/sbin/winbi
root      3116  0.0  0.0  10600  1196 ?        S    12:27   0:00 /usr/sbin/winbi
111       3121  0.0  0.2   6812  4780 ?        Ss   12:27   0:00 /usr/sbin/hald
root      3124  0.0  0.1  17380  2580 ?        Ssl  12:27   0:00 /usr/sbin/conso
root      3187  0.0  0.0   3328  1140 ?        S    12:27   0:00 hald-runner
root      3217  0.0  0.0   5176  1796 ?        S    12:27   0:00 hald-addon-inpu
root      3229  0.0  0.0   5176  1860 ?        S    12:27   0:00 /usr/lib/hal/ha
root      3238  0.0  0.0   5172  1808 ?        S    12:27   0:00 /usr/lib/hal/ha
root      3252  0.0  0.0   5188  1780 ?        S    12:27   0:00 /usr/lib/hal/ha
111       3253  0.0  0.0   5032  1760 ?        S    12:27   0:00 hald-addon-acpi
root      3254  0.0  0.0   5180  1800 ?        S    12:27   0:00 hald-addon-stor
root      3287  0.0  0.0   3556  1672 ?        Ss   12:27   0:00 /usr/sbin/bluet
root      3323  0.0  0.0  15032  1776 ?        Ss   12:27   0:00 /usr/sbin/gdm
root      3324  0.0  0.1  15596  3336 ?        S    12:27   0:00 /usr/sbin/gdm
root      3331 18.5  3.8 160512 78288 tty7     Rs+  12:27   1:09 /usr/X11R6/bin/
root      3354  0.0  0.1  16552  2832 ?        Ssl  12:27   0:00 /usr/sbin/Netwo
root      3372  0.0  0.0   4276  1920 ?        S    12:27   0:00 /sbin/wpa_suppl
root      3374  0.0  0.1   7044  3124 ?        S    12:27   0:00 /usr/sbin/nm-sy
avahi     3378  0.0  0.0   2944  1508 ?        Ss   12:27   0:00 avahi-daemon: r
avahi     3379  0.0  0.0   2944   508 ?        Ss   12:27   0:00 avahi-daemon: c
root      3406  0.0  0.1   6108  2408 ?        Ss   12:27   0:00 /usr/sbin/cupsd
root      3434  0.0  0.0   4324  1160 ?        Ss   12:27   0:00 /usr/bin/system
root      3493  0.0  0.0   2032   884 ?        Ss   12:27   0:00 /usr/sbin/anacr
daemon    3509  0.0  0.0   2096   456 ?        Ss   12:27   0:00 /usr/sbin/atd
root      3537  0.0  0.0   3480  1040 ?        Ss   12:27   0:00 /usr/sbin/cron
root      3638  0.0  0.0   1808   532 tty1     Ss+  12:27   0:00 /sbin/getty 384
1000      3676  0.0  0.1  25668  3016 ?        S    12:28   0:00 /usr/bin/gnome-
1000      3689  0.0  0.3  26484  7324 ?        Ssl  12:28   0:00 x-session-manag
1000      3744  0.0  0.0   4784   604 ?        Ss   12:28   0:00 /usr/bin/ssh-ag
1000      3747  0.0  0.0   3144   692 ?        S    12:28   0:00 /usr/bin/dbus-l
1000      3748  0.0  0.0   3068  1268 ?        Ss   12:28   0:00 //bin/dbus-daem
1000      3753  0.0  0.2  94660  5340 ?        Ssl  12:28   0:00 /usr/bin/pulsea
1000      3754  0.0  0.1   7844  2632 ?        S    12:28   0:00 /usr/lib/pulsea
1000      3756  0.1  0.2   7632  4508 ?        S    12:28   0:00 /usr/lib/libgco
1000      3768  0.0  0.3  19284  6608 ?        Ss   12:28   0:00 /usr/bin/seahor
1000      3775  0.0  0.4  29652  9528 ?        Ssl  12:28   0:00 /usr/lib/gnome-
1000      3778  0.0  0.1   5616  2120 ?        S    12:28   0:00 /usr/lib/gvfs/g
1000      3784  0.0  0.1  29584  2372 ?        Ssl  12:28   0:00 /usr/lib/gvfs//
1000      3792  0.0  0.0   1872   564 ?        S    12:28   0:00 /bin/sh /usr/bi
1000      3849  1.0  1.2  34044 24964 ?        S    12:28   0:03 /usr/bin/compiz
1000      3850  0.6  0.9  36424 19984 ?        S    12:28   0:02 gnome-panel
1000      3851  0.2  0.8  54416 17400 ?        S    12:28   0:00 nautilus
1000      3853  0.0  0.1  41748  3484 ?        Ssl  12:28   0:00 /usr/lib/bonobo
1000      3855  0.0  0.0   1872   500 ?        Ss   12:28   0:00 /bin/sh -c emer
1000      3856  0.1  0.4  19548  9716 ?        S    12:28   0:00 emerald --repla
1000      3859  0.0  0.5  68540 12084 ?        Sl   12:28   0:00 /usr/lib/evolut
1000      3862  0.0  0.4  20184  9728 ?        S    12:28   0:00 bluetooth-apple
1000      3867  0.0  0.7  28176 14756 ?        S    12:28   0:00 update-notifier
1000      3871  0.1  0.7  26812 15724 ?        S    12:28   0:00 nm-applet --sm-
1000      3872  0.0  0.7  27988 14380 ?        S    12:28   0:00 python /usr/sha
1000      3874  0.0  0.4  25724  9736 ?        Ss   12:28   0:00 gnome-power-man
1000      3880  0.4  0.5  22884 12176 ?        S    12:28   0:01 /usr/lib/notify
1000      3886  0.0  0.5  23676 10400 ?        S    12:28   0:00 /usr/lib/gnome-
1000      3888  0.0  0.1   5940  2776 ?        S    12:28   0:00 /usr/lib/gvfs/g
1000      3944  0.0  0.1   7944  3632 ?        S    12:28   0:00 /usr/lib/gvfs/g
1000      3946  0.0  0.1   8320  3120 ?        S    12:28   0:00 /usr/lib/gvfs/g
1000      3950  0.0  0.6  27032 14160 ?        S    12:28   0:00 /usr/lib/fast-u
1000      3953  0.0  0.7  44524 15044 ?        Sl   12:28   0:00 /usr/lib/gnome-
1000      3955  0.0  0.4  23236  9924 ?        S    12:28   0:00 /usr/lib/indica
1000      3965  0.0  0.1   5616  2232 ?        S    12:28   0:00 /usr/lib/gvfs/g
1000      3990  0.2  0.1  16684  3096 ?        Ss   12:28   0:00 gnome-screensav
1000      3997  0.0  0.4  70892  8660 ?        Sl   12:28   0:00 /usr/lib/evolut
1000      4002  0.0  0.5  45068 11728 ?        Sl   12:28   0:00 /usr/lib/evolut
root      4019  0.0  0.0   2276  1024 ?        S    12:28   0:00 /sbin/dhclient
postfix   4094  0.0  0.0   5792  1684 ?        S    12:29   0:00 pickup -l -t fi
postfix   4096  0.0  0.0   5836  1728 ?        S    12:29   0:00 qmgr -l -t fifo
1000      4280 15.8  2.8 144456 58332 ?        Rl   12:30   0:35 /usr/lib/firefo
1000      4306  0.2  0.6  33540 14336 ?        Sl   12:30   0:00 gnome-terminal
1000      4307  0.0  0.0   2036   696 ?        S    12:30   0:00 gnome-pty-helpe
1000      4308  0.1  0.1   5976  3272 pts/0    Ss   12:30   0:00 bash
root      4327  0.0  0.0   1872   500 ?        S    12:32   0:00 /bin/sh -c nice
root      4328  0.0  0.0   1792   572 ?        SN   12:32   0:00 run-parts --rep
root      4339  0.0  0.0   1872   552 ?        SN   12:32   0:00 /bin/sh /etc/cr
root      4354  0.0  0.0   1804   432 ?        SN   12:32   0:00 sleep 1080
1000      4355  0.0  0.0   2768  1032 pts/0    R+   12:34   0:00 ps aux

---

### Post by mardangga on 2009-06-07
hello, is there someone who can help me?

---

### Post by Haxor on 2009-06-11
Hi,

I have an Acer Aspire 5630 which was working flawlessly with Intrepid Ibex. A week or so ago I decided to upgrade to Jaunty Jackalope and my problems began.
My computer also hangs when I leave it unattended for a while. Sometimes it happens after the screensaver had turned off the screen so I don´t know if my mouse responds or what.
Every time this happens I have to force the laptop to turn off and then restart my computer.
It has an Intel GMA950, 160 GB with jfs and 2 GB RAM.
I upgraded the kernel to improve the poor 3D performace.

Any ideas?

---

