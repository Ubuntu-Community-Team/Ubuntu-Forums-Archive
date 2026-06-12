---
title: "Jaunty turtle here not jackalope"
date: 2009-05-15
forum: General Help
---

### Post by silvagroup on 2009-05-15
Not sure what is going on but since upgrading to Jaunty I have a gone from a wonderful pc to the slowest piece imaginable, at times my pentium 1 with 64mg and 10 mg hard drive with windows 95 out performs my amd x2 w/3.5gb ram and over 1tb hd.

This was  not the case with 8.04 or 8.10.

The system will come to a complete halt for several minutes and all the windows that may be open go grey.

If I cam open sys monitor it doesn't show much going on as far as process and cpu usage, but resources shows cpu usage of almost 100%.

I also see many interruptible items specifically pdflush when this happens.

It is really horrible, any help in this would be greatly appreciated I need my system back.

Thank you in advance.

---

### Post by mikewhatever on 2009-05-15
Had you tolled us what process uses 100% of the CPU, it might have shed some light on the problem. If you don't know, post the output of the following command from Terminal.
**ps -aux**

---

### Post by silvagroup on 2009-05-15
Took twenty minutes to just post this.
Thanks for the help.
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   5244  1460 ?        Ss   13:11   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   13:11   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   13:11   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   13:11   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   13:11   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   13:11   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   13:11   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   13:11   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   13:11   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   13:11   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   13:11   0:00 [khelper]
root        12  0.0  0.0      0     0 ?        S<   13:11   0:00 [kstop/0]
root        13  0.0  0.0      0     0 ?        S<   13:11   0:00 [kstop/1]
root        14  0.0  0.0      0     0 ?        S<   13:11   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S<   13:11   0:00 [kintegrityd/1]
root        16  0.0  0.0      0     0 ?        S<   13:11   0:00 [kblockd/0]
root        17  0.0  0.0      0     0 ?        R<   13:11   0:00 [kblockd/1]
root        18  0.0  0.0      0     0 ?        S<   13:11   0:00 [kacpid]
root        19  0.0  0.0      0     0 ?        S<   13:11   0:00 [kacpi_notify]
root        20  0.0  0.0      0     0 ?        S<   13:11   0:00 [cqueue]
root        21  0.0  0.0      0     0 ?        S<   13:11   0:00 [ata/0]
root        22  0.0  0.0      0     0 ?        S<   13:11   0:01 [ata/1]
root        23  0.0  0.0      0     0 ?        S<   13:11   0:00 [ata_aux]
root        24  0.0  0.0      0     0 ?        S<   13:11   0:00 [ksuspend_usbd]
root        25  0.0  0.0      0     0 ?        S<   13:11   0:00 [khubd]
root        26  0.0  0.0      0     0 ?        S<   13:11   0:00 [kseriod]
root        27  0.0  0.0      0     0 ?        S<   13:11   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        S<   13:11   0:00 [btaddconn]
root        29  0.0  0.0      0     0 ?        S<   13:11   0:00 [btdelconn]
root        32  0.0  0.0      0     0 ?        S<   13:11   0:02 [kswapd0]
root        33  0.0  0.0      0     0 ?        S<   13:11   0:00 [aio/0]
root        34  0.0  0.0      0     0 ?        S<   13:11   0:00 [aio/1]
root        35  0.0  0.0      0     0 ?        S<   13:11   0:00 [ecryptfs-kthr]
root        38  0.0  0.0      0     0 ?        S<   13:11   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S<   13:11   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S<   13:11   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S<   13:11   0:00 [scsi_eh_3]
root        42  0.0  0.0      0     0 ?        S<   13:11   0:02 [scsi_eh_4]
root        43  0.0  0.0      0     0 ?        S<   13:11   0:00 [scsi_eh_5]
root        44  0.0  0.0      0     0 ?        S<   13:11   0:00 [kstriped]
root        45  0.0  0.0      0     0 ?        S<   13:11   0:00 [kmpathd/0]
root        46  0.0  0.0      0     0 ?        S<   13:11   0:00 [kmpathd/1]
root        47  0.0  0.0      0     0 ?        S<   13:11   0:00 [kmpath_handle]
root        48  0.0  0.0      0     0 ?        S<   13:11   0:00 [ksnapd]
root        49  0.0  0.0      0     0 ?        S<   13:11   0:00 [kondemand/0]
root        50  0.0  0.0      0     0 ?        S<   13:11   0:00 [kondemand/1]
root        51  0.0  0.0      0     0 ?        S<   13:11   0:00 [krfcommd]
root       224  0.0  0.0      0     0 ?        S<   13:11   0:00 [khpsbpkt]
root       272  0.0  0.0      0     0 ?        S<   13:11   0:00 [knodemgrd_0]
root       768  0.0  0.0      0     0 ?        S<   13:11   0:00 [scsi_eh_6]
root       769  0.0  0.0      0     0 ?        S<   13:11   0:00 [usb-storage]
root       781  0.0  0.0      0     0 ?        S<   13:11   0:00 [scsi_eh_7]
root       782  0.0  0.0      0     0 ?        S<   13:11   0:00 [usb-storage]
root       819  0.0  0.0      0     0 ?        D<   13:11   0:01 [kjournald]
root       955  0.0  0.0  16792   384 ?        S<s  13:11   0:00 /sbin/udevd --d
root      1795  0.0  0.0      0     0 ?        S<   13:11   0:00 [kpsmoused]
root      2183  0.0  0.0      0     0 ?        S<   13:11   0:00 [kjournald]
daemon    2395  0.0  0.0   8180   424 ?        Ss   13:11   0:00 /sbin/portmap
statd     2417  0.0  0.0  10300   568 ?        Ss   13:11   0:00 /sbin/rpc.statd
root      2422  0.0  0.0      0     0 ?        S<   13:11   0:00 [rpciod/0]
root      2423  0.0  0.0      0     0 ?        S<   13:11   0:00 [rpciod/1]
root      2428  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsiod]
root      2441  0.0  0.0  27120   316 ?        Ss   13:11   0:00 /usr/sbin/rpc.i
root      2520  0.0  0.0   3944   584 tty4     Ss+  13:11   0:00 /sbin/getty 384
root      2521  0.0  0.0   3944   584 tty5     Ss+  13:11   0:00 /sbin/getty 384
root      2526  0.0  0.0   3944   588 tty2     Ss+  13:11   0:00 /sbin/getty 384
root      2527  0.0  0.0   3944   588 tty3     Ss+  13:11   0:00 /sbin/getty 384
root      2528  0.0  0.0   3944   584 tty6     Ss+  13:11   0:00 /sbin/getty 384
root      2600  0.0  0.0   4604  1348 ?        Ss   13:11   0:00 /usr/sbin/acpid
syslog    2643  0.0  0.0  12376   708 ?        Ss   13:11   0:00 /sbin/syslogd -
root      2666  0.0  0.0   8204   584 ?        S    13:11   0:00 /bin/dd bs 1 if
klog      2668  0.0  0.1   8272  4872 ?        Ss   13:11   0:00 /sbin/klogd -P
108       2691  0.0  0.0  22088  1696 ?        Ss   13:11   0:00 /bin/dbus-daemo
root      2715  0.0  0.0  48940   924 ?        Ss   13:11   0:00 /usr/sbin/sshd
root      2774  0.0  0.0   4024   620 ?        S    13:11   0:00 /bin/sh /usr/bi
mysql     2816  0.1  0.5 161008 20032 ?        Sl   13:11   0:13 /usr/sbin/mysql
root      2817  0.0  0.0   3924   620 ?        S    13:11   0:00 logger -p daemo
root      3051  0.0  0.0 106872  2620 ?        Ssl  13:11   0:00 /usr/sbin/conso
clamav    3123  0.0  0.0  30092  1256 ?        Ss   13:11   0:00 /usr/bin/freshc
root      3290  0.0  0.0 133572  2628 ?        Sl   13:11   0:00 /usr/sbin/libvi
root      3381  0.0  0.0      0     0 ?        S<   13:11   0:00 [lockd]
root      3384  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd4]
root      3386  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd]
root      3387  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd]
root      3388  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd]
root      3389  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd]
root      3390  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd]
root      3391  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd]
root      3394  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd]
root      3395  0.0  0.0      0     0 ?        S<   13:11   0:00 [nfsd]
root      3412  0.0  0.0  18788   964 ?        Ss   13:11   0:00 /usr/sbin/rpc.m
nobody    3454  0.0  0.0  14804   608 ?        S    13:11   0:00 dnsmasq --stric
root      3516  0.0  0.0  37048  1284 ?        Ss   13:11   0:00 /usr/lib/postfi
root      3543  0.0  0.0  66292  1156 ?        Ss   13:11   0:00 /usr/sbin/winbi
root      3565  0.0  0.0  66292   940 ?        S    13:11   0:00 /usr/sbin/winbi
111       3566  0.0  0.1  36660  4840 ?        Ss   13:11   0:00 /usr/sbin/hald
root      3567  0.0  0.0  15944  1288 ?        S    13:11   0:00 hald-runner
root      3597  0.0  0.0  28484  1256 ?        S    13:11   0:00 hald-addon-inpu
root      3652  0.0  0.0  28484  1248 ?        S    13:11   0:00 hald-addon-stor
root      3653  0.0  0.0  28484  1252 ?        S    13:11   0:00 hald-addon-stor
root      3654  0.0  0.0  28484  1248 ?        S    13:11   0:00 hald-addon-stor
root      3655  0.0  0.0  28484  1252 ?        S    13:11   0:00 hald-addon-stor
root      3656  0.0  0.0  28484  1252 ?        S    13:11   0:00 hald-addon-stor
root      3657  0.0  0.0  28484  1256 ?        S    13:11   0:02 hald-addon-stor
root      3658  0.0  0.0  28484  1344 ?        S    13:11   0:03 hald-addon-stor
root      3659  0.0  0.0  28492  1240 ?        S    13:11   0:00 /usr/lib/hal/ha
111       3660  0.0  0.0  32392  1244 ?        S    13:11   0:00 hald-addon-acpi
root      3678  0.0  0.0  28356  1568 ?        Ss   13:11   0:00 /usr/sbin/bluet
root      3707  0.0  0.0 124216  1880 ?        Ss   13:11   0:00 /usr/sbin/gdm
root      3710  0.0  0.0 145248  3212 ?        S    13:11   0:00 /usr/sbin/gdm
root      3713 15.6  2.1 175164 74500 tty7     Ss+  13:11  23:39 /usr/X11R6/bin/
root      3738  0.0  0.0  70988  2396 ?        Ssl  13:11   0:00 /usr/sbin/Netwo
avahi     3758  0.0  0.0  31892  1472 ?        Ss   13:11   0:00 avahi-daemon: r
root      3760  0.0  0.0  21100  1196 ?        S    13:11   0:00 /sbin/wpa_suppl
avahi     3761  0.0  0.0  31764   444 ?        Ss   13:11   0:00 avahi-daemon: c
root      3763  0.0  0.0  69120  2860 ?        S    13:11   0:00 /usr/sbin/nm-sy
root      3790  0.0  0.0  68084  2116 ?        Ss   13:11   0:00 /usr/sbin/cupsd
root      3818  0.0  0.0  33296  1188 ?        Ss   13:11   0:00 /usr/bin/system
root      3870  0.0  0.1   8832  4600 ?        Ss   13:11   0:00 /usr/lib/win4li
root      3877  0.0  0.0  12420   388 ?        Ss   13:11   0:00 /usr/lib/win4li
nobody    3878  0.0  0.0  11640  1068 ?        S    13:11   0:04 /usr/lib/win4li
root      3880  0.0  0.0   6076   360 ?        S    13:11   0:00 /usr/lib/win4li
root      3901  0.0  0.0   9060  2840 ?        Ss   13:11   0:00 /usr/lib/win4li
daemon    3950  0.0  0.0  16524   440 ?        Ss   13:11   0:00 /usr/sbin/atd
root      3978  0.0  0.0  21052  1056 ?        Ss   13:11   0:00 /usr/sbin/cron
root      3994  0.0  0.0   6488  1012 ?        S    13:11   0:00 /sbin/dhclient
root      4022  0.0  0.0 121384  2628 ?        Ss   13:11   0:00 /usr/sbin/apach
www-data  4024  0.0  0.0 121116  2172 ?        S    13:11   0:00 /usr/sbin/apach
www-data  4025  0.0  0.0 344820  2612 ?        Sl   13:11   0:00 /usr/sbin/apach
www-data  4028  0.0  0.0 344820  2616 ?        Sl   13:11   0:00 /usr/sbin/apach
postfix   4303  0.0  0.0  39152  1232 ?        S    13:11   0:00 qmgr -l -t fifo
root      4313  0.0  0.1  90416  4984 ?        S    13:11   0:00 /usr/bin/timidi
root      4318  0.0  0.0   3944   584 tty1     Ss+  13:11   0:00 /sbin/getty 384
carlos    4337  0.0  0.0 159036  3040 ?        S    13:12   0:00 /usr/bin/gnome-
carlos    4349  0.0  0.2 175184  7976 ?        Ssl  13:12   0:00 /usr/bin/gnome-
carlos    4462  0.0  0.0  35940   632 ?        Ss   13:12   0:00 /usr/bin/ssh-ag
carlos    4465  0.0  0.0  23824   720 ?        S    13:12   0:00 /usr/bin/dbus-l
carlos    4466  0.0  0.0  22172  1764 ?        Ss   13:12   0:00 //bin/dbus-daem
carlos    4471  0.0  0.1 308028  3844 ?        Ssl  13:12   0:00 /usr/bin/pulsea
carlos    4472  0.0  0.0  68048  2704 ?        S    13:12   0:00 /usr/lib/pulsea
carlos    4474  0.0  0.1  47660  6464 ?        S    13:12   0:02 /usr/lib/libgco
carlos    4485  0.0  0.2 166180  7232 ?        Ss   13:12   0:00 /usr/bin/seahor
carlos    4488  0.0  0.0  41932  2388 ?        S    13:12   0:00 /usr/lib/gvfs/g
carlos    4494  0.0  0.0  71000  2592 ?        Ssl  13:12   0:01 /usr/lib/gvfs//
carlos    4501  0.1  0.3 227540 11272 ?        Ssl  13:12   0:09 /usr/lib/gnome-
carlos    4509  3.0  1.2 299104 42532 ?        S    13:12   4:38 /usr/bin/compiz
carlos    4510  0.2  0.7 338888 26816 ?        S    13:12   0:26 gnome-panel --s
carlos    4512  0.2  0.9 491208 32944 ?        S    13:12   0:21 nautilus --sm-c
carlos    4514  0.0  0.1 147224  3532 ?        Sl   13:12   0:00 /usr/lib/gvfs/g
carlos    4515  0.2  1.5 293168 54692 ?        S    13:12   0:19 python -u /usr/
carlos    4516  0.0  0.6 237684 23236 ?        S    13:12   0:00 /usr/bin/python
carlos    4517  0.0  0.4 191296 14196 ?        S    13:12   0:00 padevchooser
carlos    4518  0.0  0.0   4024   580 ?        S    13:12   0:00 /bin/sh /usr/bi
carlos    4522 26.8  1.1 278456 40136 ?        S    13:12  40:23 python -u /usr/
carlos    4526  0.0  0.0  55452  2848 ?        S    13:12   0:00 /usr/lib/gvfs/g
carlos    4531  0.0  0.4 217540 16080 ?        S    13:12   0:00 python /usr/sha
carlos    4533  0.0  0.2 146084  7292 ?        S    13:12   0:00 bluetooth-apple
carlos    4534  0.0  0.2 167644  7088 ?        S    13:12   0:00 tracker-applet
carlos    4535  0.0  0.4 193096 14036 ?        S    13:12   0:00 nm-applet --sm-
carlos    4537  0.0  1.0 369252 36056 ?        Sl   13:12   0:04 mono /usr/lib/t
carlos    4539  0.0  0.4 172176 14084 ?        S    13:12   0:00 /usr/lib/notify
carlos    4541  6.8  5.0 631920 173816 ?       Sl   13:12  10:17 /usr/lib/firefo
carlos    4542  0.0  0.4 238572 14872 ?        S    13:12   0:00 update-notifier
carlos    4545  0.0  0.2 427064  9392 ?        Sl   13:12   0:00 /usr/lib/evolut
carlos    4554  0.0  0.2 143564  9932 ?        S    13:12   0:00 /usr/lib/tracke
carlos    4557  0.0  0.1 153564  3724 ?        Ssl  13:12   0:00 /usr/lib/bonobo
carlos    4567  0.0  0.2 228416  8632 ?        Ss   13:12   0:00 gnome-power-man
carlos    4571  0.0  0.0   4024   572 ?        Ss   13:12   0:00 /bin/sh -c emer
carlos    4572  3.9  1.6 210208 56732 ?        S    13:12   5:58 emerald --repla
carlos    4597  0.0  0.0  46384  2984 ?        S    13:12   0:00 /usr/lib/gvfs/g
carlos    4599  0.0  0.0   4024   580 ?        S    13:12   0:00 /bin/sh /usr/bi
carlos    4602  2.7  0.4 237988 17108 ?        S    13:12   4:05 awn
carlos    4607  0.0  0.7 274680 24256 ?        S    13:13   0:01 python /usr/sha
carlos    4611  0.0  0.0  41936  2400 ?        S    13:13   0:00 /usr/lib/gvfs/g
carlos    4628  0.0  0.4 262624 15816 ?        S    13:13   0:00 /usr/lib/gnome-
carlos    4631  0.0  0.3 226384 12188 ?        S    13:13   0:00 /usr/lib/indica
carlos    4633  0.0  0.4 236996 14812 ?        S    13:13   0:00 /usr/lib/gnome-
carlos    4635  0.0  0.3 216936 11512 ?        S    13:13   0:00 /usr/lib/gnome-
carlos    4639  0.0  0.7 545452 24976 ?        Sl   13:13   0:00 /usr/lib/evolut
carlos    4641  0.0  0.4 241868 14952 ?        S    13:13   0:00 /usr/lib/fast-u
carlos    4643  0.0  0.4 270336 16304 ?        Sl   13:13   0:00 /usr/lib/gnome-
carlos    4649  0.0  0.2 342172  9248 ?        Sl   13:13   0:00 /usr/lib/evolut
root      4651  0.0  0.2  72672  8512 ?        S    13:13   0:00 /usr/bin/python
carlos    4843  0.2  0.1 163036  5644 ?        Ss   13:13   0:20 gnome-screensav
carlos    4951  0.0  0.2 154080  9924 ?        SN   13:13   0:00 /usr/lib/tracke
root     10277  0.8  0.0      0     0 ?        S    15:42   0:00 [pdflush]
carlos   10416  3.7  0.5 201020 17276 ?        Sl   15:42   0:00 gnome-terminal
carlos   10436  0.0  0.0  14412   780 ?        S    15:42   0:00 gnome-pty-helpe
carlos   10441  1.0  0.1  22772  4520 pts/0    Ss   15:42   0:00 bash
root     10495  1.7  0.0      0     0 ?        D    15:42   0:00 [pdflush]
root     10556  0.0  0.0      0     0 ?        S    15:42   0:00 [pdflush]
carlos   10557  0.0  0.0  16252  1152 pts/0    R+   15:42   0:00 ps -aux
carlos   13120  0.8  1.6 778820 57252 ?        Rl   13:32   1:07 evolution --com
root     13916  0.4  0.0  17724  1300 ?        Rs   13:34   0:31 /sbin/mount.ntf
carlos   17065  0.0  0.5 246872 20212 ?        S    14:48   0:00 python /usr/sha
carlos   17105  0.0  0.8 268792 30644 ?        S    14:49   0:01 python -u /usr/
postfix  18209  0.0  0.0  39104  1220 ?        S    14:51   0:00 pickup -l -t f

---

### Post by mikewhatever on 2009-05-15
There are two lines with rather high CPU usage, although none with near 100%.
> carlos 4522 **26.8** 1.1 278456 40136 ? S 13:12 40:23 python -u /usr/
root 3713 **15.6** 2.1 175164 74500 tty7 Ss+ 13:11 23:39 /usr/X11R6/bin/

The first looks like a python program, the second must be xserver. I wonder if you have an older Intel graphics card or an ATI one.
I realise it must have been hard to post all that, a **ps -aux > ~/Desktop/processes.txt** would have been a better way. This command will create a nicely formated text file on your desktop with the same list of running precesses.

---

### Post by silvagroup on 2009-05-16
Thanks, for the new command tried it works great, same results of course.
That's what's baffling, you look at the processes and there's  nothing going on, but mt system goes into a serious crawl, and everything on the screen goes gray.

Something I noticed in trying to resolve this, it happens mostly when video editing, (bad time for that to happen) and when I am using Evolution.

I am suspecting that the external drive I am using (My Book Home NTFS) maybe the issue?
Can't understand why though, it's hooked up using e-sata but the video editing still brings things to halt, except for audio, even from internal hard drive?

Rats, I am lost don't know, need some help with this one !!!!

Thanks

---

### Post by silvagroup on 2009-05-16
Just messing around tried Evo aaUSER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   5244  1912 ?        Ss   15:10   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   15:10   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   15:10   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   15:10   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   15:10   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   15:10   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   15:10   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   15:10   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   15:10   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   15:10   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   15:10   0:00 [khelper]
root        12  0.0  0.0      0     0 ?        S<   15:10   0:00 [kstop/0]
root        13  0.0  0.0      0     0 ?        S<   15:10   0:00 [kstop/1]
root        14  0.0  0.0      0     0 ?        S<   15:10   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S<   15:10   0:00 [kintegrityd/1]
root        16  0.0  0.0      0     0 ?        S<   15:10   0:00 [kblockd/0]
root        17  0.0  0.0      0     0 ?        S<   15:10   0:00 [kblockd/1]
root        18  0.0  0.0      0     0 ?        S<   15:10   0:00 [kacpid]
root        19  0.0  0.0      0     0 ?        S<   15:10   0:00 [kacpi_notify]
root        20  0.0  0.0      0     0 ?        S<   15:10   0:00 [cqueue]
root        21  0.0  0.0      0     0 ?        S<   15:10   0:00 [ata/0]
root        22  0.0  0.0      0     0 ?        R<   15:10   0:00 [ata/1]
root        23  0.0  0.0      0     0 ?        S<   15:10   0:00 [ata_aux]
root        24  0.0  0.0      0     0 ?        S<   15:10   0:00 [ksuspend_usbd]
root        25  0.0  0.0      0     0 ?        S<   15:10   0:00 [khubd]
root        26  0.0  0.0      0     0 ?        S<   15:10   0:00 [kseriod]
root        27  0.0  0.0      0     0 ?        S<   15:10   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        S<   15:10   0:00 [btaddconn]
root        29  0.0  0.0      0     0 ?        S<   15:10   0:00 [btdelconn]
root        30  0.0  0.0      0     0 ?        S    15:10   0:00 [pdflush]
root        31  0.0  0.0      0     0 ?        S    15:10   0:00 [pdflush]
root        32  0.0  0.0      0     0 ?        S<   15:10   0:04 [kswapd0]
root        33  0.0  0.0      0     0 ?        S<   15:10   0:00 [aio/0]
root        34  0.0  0.0      0     0 ?        S<   15:10   0:00 [aio/1]
root        35  0.0  0.0      0     0 ?        S<   15:10   0:00 [ecryptfs-kthrea]
root        38  0.0  0.0      0     0 ?        S<   15:10   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S<   15:10   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S<   15:10   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S<   15:10   0:00 [scsi_eh_3]
root        42  0.0  0.0      0     0 ?        S<   15:10   0:00 [scsi_eh_4]
root        43  0.0  0.0      0     0 ?        S<   15:10   0:00 [scsi_eh_5]
root        44  0.0  0.0      0     0 ?        S<   15:10   0:00 [kstriped]
root        45  0.0  0.0      0     0 ?        S<   15:10   0:00 [kmpathd/0]
root        46  0.0  0.0      0     0 ?        S<   15:10   0:00 [kmpathd/1]
root        47  0.0  0.0      0     0 ?        S<   15:10   0:00 [kmpath_handlerd]
root        48  0.0  0.0      0     0 ?        S<   15:10   0:00 [ksnapd]
root        49  0.0  0.0      0     0 ?        S<   15:10   0:00 [kondemand/0]
root        50  0.0  0.0      0     0 ?        S<   15:10   0:00 [kondemand/1]
root        51  0.0  0.0      0     0 ?        S<   15:10   0:00 [krfcommd]
root       263  0.0  0.0      0     0 ?        S<   15:10   0:00 [khpsbpkt]
root       467  0.0  0.0      0     0 ?        S<   15:10   0:00 [knodemgrd_0]
root       765  0.0  0.0      0     0 ?        S<   15:10   0:00 [scsi_eh_6]
root       766  0.0  0.0      0     0 ?        R<   15:10   0:00 [usb-storage]
root       780  0.0  0.0      0     0 ?        S<   15:10   0:00 [scsi_eh_7]
root       782  0.0  0.0      0     0 ?        R<   15:10   0:00 [usb-storage]
root       817  0.0  0.0      0     0 ?        S<   15:10   0:01 [kjournald]
root       953  0.0  0.0  16792   408 ?        S<s  15:10   0:00 /sbin/udevd --daemon
carlos    1220  4.6  0.5 201020 17208 ?        Sl   19:26   0:00 gnome-terminal
carlos    1246  0.0  0.0  14412   780 ?        S    19:26   0:00 gnome-pty-helper
carlos    1247  2.2  0.1  22672  4416 pts/0    Ss   19:26   0:00 bash
carlos    1353  0.0  0.0  16252  1148 pts/0    R+   19:26   0:00 ps -aux
carlos    1354  0.0  0.0      0     0 ?        R    19:26   0:00 [vino-server]
carlos    1355  0.0  0.0  97212   872 ?        R    19:26   0:00 /usr/lib/vino/vino-server --sm-config-prefix /vino-server-9ivgyA/ --sm-client-id 10b94425f653d826d5124241836311052900000043490030 --screen 0
root      1810  0.0  0.0      0     0 ?        S<   15:10   0:00 [kpsmoused]
postfix   3570  0.0  0.0  39104  2116 ?        S    18:45   0:00 pickup -l -t fifo -u -c
carlos   11876  0.0  0.1  75568  3796 ?        S    19:11   0:00 /usr/lib/gvfs/gvfsd-http --spawner :1.5 /org/gtk/gvfs/exec_spaw/2
root     15702  0.0  0.0      0     0 ?        S<   15:25   0:00 [kjournald]
daemon   15910  0.0  0.0   8180   580 ?        Ss   15:25   0:00 /sbin/portmap
statd    15932  0.0  0.0  10300   720 ?        Ss   15:25   0:00 /sbin/rpc.statd
root     15937  0.0  0.0      0     0 ?        S<   15:25   0:00 [rpciod/0]
root     15938  0.0  0.0      0     0 ?        S<   15:25   0:00 [rpciod/1]
root     15942  0.0  0.0      0     0 ?        S<   15:25   0:00 [nfsiod]
root     15956  0.0  0.0  27120   544 ?        Ss   15:25   0:00 /usr/sbin/rpc.idmapd
root     16035  0.0  0.0   3944   580 tty4     Ss+  15:25   0:00 /sbin/getty 38400 tty4
root     16036  0.0  0.0   3944   576 tty5     Ss+  15:25   0:00 /sbin/getty 38400 tty5
root     16039  0.0  0.0   3944   580 tty2     Ss+  15:25   0:00 /sbin/getty 38400 tty2
root     16042  0.0  0.0   3944   576 tty3     Ss+  15:25   0:00 /sbin/getty 38400 tty3
root     16043  0.0  0.0   3944   576 tty6     Ss+  15:25   0:00 /sbin/getty 38400 tty6
root     16116  0.0  0.0   4604  1272 ?        Ss   15:25   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog   16159  0.0  0.0  12376   708 ?        Ss   15:25   0:00 /sbin/syslogd -u syslog
root     16182  0.0  0.0   8204   600 ?        S    15:25   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog     16184  0.0  0.1   8272  4876 ?        Ss   15:25   0:00 /sbin/klogd -P /var/run/klogd/kmsg
108      16207  0.0  0.0  22088  1720 ?        Ss   15:25   0:00 /bin/dbus-daemon --system
root     16231  0.0  0.0  48940   936 ?        Ss   15:25   0:00 /usr/sbin/sshd
root     16290  0.0  0.0   4024   616 ?        S    15:25   0:00 /bin/sh /usr/bin/mysqld_safe
mysql    16332  0.0  0.5 161008 17760 ?        Sl   15:25   0:10 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root     16333  0.0  0.0   3924   620 ?        S    15:25   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root     16567  0.0  0.0 106872  2764 ?        Ssl  15:25   0:00 /usr/sbin/console-kit-daemon
clamav   16639  0.0  0.0  30076  1128 ?        Ss   15:25   0:00 /usr/bin/freshclam -d --quiet
root     16806  0.0  0.0 133572  2088 ?        Sl   15:26   0:00 /usr/sbin/libvirtd -d
root     16889  0.0  0.0      0     0 ?        S<   15:26   0:00 [lockd]
root     16890  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd4]
root     16891  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd]
root     16892  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd]
root     16893  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd]
root     16894  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd]
root     16895  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd]
root     16896  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd]
root     16897  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd]
root     16898  0.0  0.0      0     0 ?        S<   15:26   0:00 [nfsd]
root     16910  0.0  0.0  18788  1068 ?        Ss   15:26   0:00 /usr/sbin/rpc.mountd --manage-gids
nobody   16983  0.0  0.0  14804   584 ?        S    15:26   0:00 dnsmasq --strict-order --bind-interfaces --pid-file=/var/run/libvirt/network/default.pid --conf-file=  --listen-address 192.168.122.1 --except-interface lo --dhcp-range 192.168.122.2,192.168.122.254
root     17031  0.0  0.0  37048  1372 ?        Ss   15:26   0:00 /usr/lib/postfix/master
root     17058  0.0  0.0  66292  1216 ?        Ss   15:26   0:00 /usr/sbin/winbindd
root     17066  0.0  0.0  66292  1100 ?        S    15:26   0:00 /usr/sbin/winbindd
111      17081  0.0  0.0  36548  2860 ?        Ss   15:26   0:00 /usr/sbin/hald
root     17082  0.0  0.0  15936  1280 ?        S    15:26   0:00 hald-runner
root     17112  0.0  0.0  28484  1272 ?        S    15:26   0:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3
root     17169  0.0  0.0  28484  1288 ?        S    15:26   0:00 hald-addon-storage: polling /dev/sr2 (every 2 sec)
root     17170  0.0  0.0  28484  1280 ?        S    15:26   0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
root     17171  0.0  0.0  28484  1284 ?        S    15:26   0:00 hald-addon-storage: polling /dev/sde (every 2 sec)
root     17172  0.0  0.0  28484  1284 ?        S    15:26   0:00 hald-addon-storage: polling /dev/sdf (every 2 sec)
root     17173  0.0  0.0  28484  1280 ?        S    15:26   0:00 hald-addon-storage: polling /dev/sdg (every 2 sec)
root     17174  0.0  0.0  28484  1376 ?        S    15:26   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root     17175  0.0  0.0  28484  1284 ?        D    15:26   0:00 hald-addon-storage: polling /dev/sr1 (every 2 sec)
root     17176  0.0  0.0  28492  1224 ?        S    15:26   0:00 /usr/lib/hal/hald-addon-cpufreq
111      17177  0.0  0.0  32392  1228 ?        S    15:26   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root     17195  0.0  0.0  28356  1312 ?        Ss   15:26   0:00 /usr/sbin/bluetoothd
root     17224  0.0  0.0 124216  1852 ?        Ss   15:26   0:00 /usr/sbin/gdm
root     17226  0.0  0.0 145248  3144 ?        S    15:26   0:05 /usr/sbin/gdm
root     17232  9.9  1.4 152396 49624 tty7     Ss+  15:26  24:01 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root     17253  0.0  0.0  70988  2268 ?        Ssl  15:26   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root     17271  0.0  0.0  21100  1044 ?        S    15:26   0:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root     17273  0.0  0.0  69120  2552 ?        S    15:26   0:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
avahi    17277  0.0  0.0  31896  1432 ?        Ss   15:26   0:00 avahi-daemon: running [carlos-desktop.local]
avahi    17278  0.0  0.0  31764   452 ?        Ss   15:26   0:00 avahi-daemon: chroot helper
root     17309  0.0  0.0  68084  1880 ?        Ss   15:26   0:00 /usr/sbin/cupsd
root     17339  0.0  0.0  33296  1176 ?        Ss   15:26   0:00 /usr/bin/system-tools-backends
root     17399  0.0  0.1   8832  4612 ?        Ss   15:26   0:00 /usr/lib/win4linpro/bin/win4prod
root     17402  0.0  0.0   6488  1004 ?        S    15:26   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
root     17405  0.0  0.0  12420   388 ?        Ss   15:26   0:00 /usr/lib/win4linpro/bin/win4vncd
nobody   17406  0.0  0.0  11640  1068 ?        R    15:26   0:02 /usr/lib/win4linpro/bin/xrdp -nodaemon
root     17408  0.0  0.0   6076   344 ?        S    15:26   0:00 /usr/lib/win4linpro/bin/win4cdahubd
root     17437  0.0  0.0   9060  2848 ?        Ss   15:26   0:00 /usr/lib/win4linpro/bin/dhcpd -q -cf /var/run/win4linpro/dhcpd.conf vbinat0
daemon   17478  0.0  0.0  16524   448 ?        Ss   15:26   0:00 /usr/sbin/atd
root     17506  0.0  0.0  21052   992 ?        Ss   15:26   0:00 /usr/sbin/cron
root     17547  0.0  0.0 121384  2596 ?        Ss   15:26   0:00 /usr/sbin/apache2 -k start
www-data 17549  0.0  0.0 121116  2172 ?        S    15:26   0:00 /usr/sbin/apache2 -k start
www-data 17554  0.0  0.0 344820  2732 ?        Sl   15:26   0:00 /usr/sbin/apache2 -k start
www-data 17555  0.0  0.0 344820  2736 ?        Sl   15:26   0:00 /usr/sbin/apache2 -k start
root     17773  0.0  0.1  90416  5008 ?        S    15:26   0:00 /usr/bin/timidity -Os -iAD
root     17789  0.0  0.0   3944   580 tty1     Ss+  15:26   0:00 /sbin/getty 38400 tty1
postfix  17839  0.0  0.0  39152  1332 ?        S    15:26   0:00 qmgr -l -t fifo -u
carlos   18013  0.0  0.0 167232  3208 ?        S    15:36   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
carlos   18025  4.5  0.2 175172  7908 ?        Rsl  15:36  10:26 /usr/bin/gnome-session
carlos   18138  0.0  0.0  35940   648 ?        Ss   15:36   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
carlos   18141  0.0  0.0  23824   712 ?        S    15:36   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
carlos   18142  6.2  0.0  23232  2820 ?        Ss   15:36  14:26 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
carlos   18147  0.0  0.1 242492  4268 ?        Ssl  15:36   0:00 /usr/bin/pulseaudio --start
carlos   18148  0.0  0.0  68048  2692 ?        S    15:36   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
carlos   18150  3.2  0.2  48480  7232 ?        S    15:36   7:26 /usr/lib/libgconf2-4/gconfd-2
carlos   18161  0.0  0.1 166180  6592 ?        Ss   15:36   0:00 /usr/bin/seahorse-agent --execute /usr/bin/gnome-session
carlos   18164  0.2  0.0  41932  2336 ?        S    15:36   0:34 /usr/lib/gvfs/gvfsd
carlos   18170  0.0  0.0  71000  2348 ?        Ssl  15:36   0:01 /usr/lib/gvfs//gvfs-fuse-daemon /home/carlos/.gvfs
carlos   18179  1.4  0.2 227632 10028 ?        Rsl  15:36   3:24 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
carlos   18185  2.1  1.2 295608 43108 ?        S    15:36   5:02 /usr/bin/compiz.real --sm-client-id 102fd60a71d8cc9200124222908928041900000045150032 --ignore-desktop-hints --loose-binding core ccp
carlos   18187  0.9  0.7 331300 24224 ?        S    15:36   2:11 gnome-panel --sm-config-prefix /gnome-panel-rjJWjE/ --sm-client-id 10c2ef9e673faddba8124106774272702000000059720030 --screen 0
carlos   18188  0.0  0.7 486704 25828 ?        R    15:36   0:07 nautilus --sm-client-id 10c2ef9e673faddba8124106774273812500000059720031 --sm-client-state-file /home/carlos/.config/session-state/nautilus-1242511732.desktop
carlos   18190  0.0  0.0  81876  3152 ?        Sl   15:36   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
carlos   18192  0.3  0.3 427064 10688 ?        Sl   15:36   0:42 /usr/lib/evolution/2.26/evolution-alarm-notify --sm-config-prefix /evolution-alarm-notify-H5YC2A/ --sm-client-id 10c2ef9e673faddba8124106774185364000000059720019 --screen 0
carlos   18193  0.2  1.5 293152 53864 ?        S    15:36   0:28 python -u /usr/share/screenlets/Picframe/PicframeScreenlet.py
carlos   18194  0.0  0.5 231264 19300 ?        S    15:36   0:00 /usr/bin/python /usr/bin/fusion-icon --no-start
carlos   18195  0.3  0.3 191296 12060 ?        S    15:36   0:43 padevchooser
carlos   18197  0.0  0.0  55452  2756 ?        S    15:36   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
carlos   18198 13.4  1.1 278744 38488 ?        S    15:36  30:57 python -u /usr/share/screenlets/Sysmonitor/SysmonitorScreenlet.py
carlos   18199  0.0  0.0   4024   576 ?        S    15:36   0:00 /bin/sh /usr/bin/awn-autostart
carlos   18205  0.3  0.1 167644  6828 ?        S    15:36   0:42 tracker-applet
carlos   18206  0.3  0.3 193088 13080 ?        S    15:36   0:45 nm-applet --sm-disable
carlos   18210  0.0  0.8 268788 29264 ?        S    15:36   0:01 python -u /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py
carlos   18211  0.0  0.5 246868 19756 ?        S    15:36   0:00 python /usr/share/screenlets-manager/screenlets-daemon.py
carlos   18215 28.0 32.1 1855440 1104844 ?     Sl   15:36  64:39 evolution --sm-config-prefix /evolution-oi2sPx/ --sm-client-id 10b94425f653d826d5124242841317500900000043490049 --screen 0
carlos   18217  0.2  0.3 171984 12796 ?        S    15:36   0:39 /usr/lib/notify-osd/notify-osd
carlos   18243  0.0  0.1 153568  3852 ?        Ssl  15:36   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=21
carlos   18245  0.4  0.2 143472  9832 ?        S    15:36   0:57 /usr/lib/tracker/trackerd
carlos   18247  0.3  0.4 238664 14164 ?        S    15:36   0:44 update-notifier --startup-delay=60
carlos   18248  1.1  0.4 217540 16064 ?        S    15:36   2:40 python /usr/share/system-config-printer/applet.py
carlos   18254  0.2  0.2 146084  7088 ?        S    15:36   0:33 bluetooth-applet
carlos   18258  0.0  0.2 217132  9616 ?        S    15:36   0:02 /usr/lib/vino/vino-server
carlos   18264  0.4  0.2 228428  8716 ?        Ss   15:36   1:01 gnome-power-manager --sm-config-prefix /gnome-power-manager-nHJUBA/ --sm-client-id 10a761cc2d20c05a46124250835325306300000043510019 --screen 0
carlos   18277  0.0  0.0  46404  2632 ?        S    15:36   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
carlos   18281  0.0  0.0   4024   572 ?        Ss   15:36   0:00 /bin/sh -c emerald --replace
carlos   18282  0.0  0.3 164356 12768 ?        S    15:36   0:01 emerald --replace
carlos   18314  0.0  0.4 262624 15396 ?        S    15:36   0:00 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activate-iid=OAFIID:GNOME_GWeatherApplet_Factory --oaf-ior-fd=20
carlos   18316  1.3  0.6 236712 23572 ?        S    15:36   3:07 /usr/lib/indicator-applet/indicator-applet --oaf-activate-iid=OAFIID:GNOME_IndicatorApplet_Factory --oaf-ior-fd=28
carlos   18319  0.0  0.3 237000 13736 ?        S    15:36   0:00 /usr/lib/gnome-utils/gnome-dictionary-applet --oaf-activate-iid=OAFIID:GNOME_DictionaryApplet_Factory --oaf-ior-fd=26
carlos   18321  0.0  0.6 489148 23692 ?        Sl   15:36   0:00 /usr/lib/evolution/evolution-data-server-2.26 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=40
carlos   18324  0.0  0.3 216936 11732 ?        S    15:36   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=38
carlos   18326  0.4  0.4 241872 14276 ?        S    15:36   1:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=52
carlos   18329  0.0  0.4 270336 15284 ?        Sl   15:36   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=50
carlos   18332  0.0  0.0   4024   580 ?        S    15:36   0:00 /bin/sh /usr/bin/avant-window-navigator
carlos   18376  0.3  0.4 234832 14680 ?        S    15:36   0:50 awn
carlos   18382  0.0  0.3 342172 10424 ?        Sl   15:36   0:00 /usr/lib/evolution/2.26/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=34
carlos   18387  0.3  0.6 274788 22488 ?        S    15:36   0:44 python /usr/share/avant-window-navigator/applets/mimenu/mimenu.py --uid=1234994500 --window=75497523 --orient=0 --height=48
carlos   18392  0.0  0.0  41936  2308 ?        S    15:36   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
carlos   18656  0.5  0.2 154092  9924 ?        SN   15:36   1:13 /usr/lib/tracker/tracker-indexer
carlos   18722  0.9  0.1 163160  5636 ?        Ss   15:36   2:08 gnome-screensaver
root     19503  0.0  0.2  72664  8504 ?        S    15:37   0:00 /usr/bin/python /usr/lib/system-service/system-service-d
root     21218  0.0  0.0  17568  1136 ?        Ss   15:38   0:01 /sbin/mount.ntfs-3g /dev/sdc1 /media/TETRADRIVE -o rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8
root     22882  0.0  0.0  23824   708 ?        S    15:39   0:00 dbus-launch --autolaunch 874b0c51c06521573ebb7d3a49af6711 --binary-syntax --close-stderr
root     22883  0.0  0.0  21256   776 ?        Ss   15:39   0:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --sessiond went gray did command:

What ever that all means.
Thank again !!!

---

### Post by silvagroup on 2009-05-18
After too many days messing around with Jaunty, shutding down things and third party drivers and not using external drive, nothing has helped the situation.
I am afraid that Jaunty is just a major cpu hog and if that is the case that makes it useless.

I am going to try it on a seperate partiton on my laptop and see if it's the same there before I totaly junk Jaunty.

---

### Post by Don1500 on 2009-05-18
> **silvagroup said:**
> After too many days messing around with Jaunty, shutding down things and third party drivers and not using external drive, nothing has helped the situation.
I am afraid that Jaunty is just a major cpu hog and if that is the case that makes it useless.

I am going to try it on a seperate partiton on my laptop and see if it's the same there before I totaly junk Jaunty.

That may be the answer for you, but check back. One thing I know about Ubuntu, if you have a problem today, tomorrow it may be gone.

---

### Post by silvagroup on 2009-05-19
The install on the laptop runs great, very low cpu usage.
I have stopped all startup processes removed evo and everyhing my little pea brain can figure out and still both cores way over 60%.
i am backing everything up and going to do a re-install some how the desktops gotten messed up horribly, I hope.
Will report back w/results.

---

### Post by silvagroup on 2009-05-20
After trying many things including a complete system re-installation I have learned that there is aproblem with Evolution, but I think it's more OS related.

I can temporarily resolve the Evo problem but it comes back.

My wife who doessn't use Evolution is now experiencing the same problem with Jauunty on her system cpu usage 75-80% with the syetem just sitting at idle.

She is also running on a totally different pc platform than I am.

So far the lapto is doing OK.

Something much deeper is going on here and I don't know how to get to the root of it or where to even begin to look.

---

### Post by Psychopump on 2009-05-20
This is very strange indeed silvagroup, especially as your wife's machine has the same issue without using Evolution. (I think we can therefore safely rule out Evolution as the culprit)

I run Jaunty (LinuxMint Gloria) on my laptop which has lower specs than yours with no issues at all. When idling my CPU is running at around 2%, with system monitor, firefox and deluge running it sits at 12%.

I am sorry that I cannot assist in troubleshooting this problem, as my knowledge is lacking. But if I can help by posting any data from my machine as a comparison, please let me know!

Good luck!

---

### Post by XCan on 2009-05-20
You never answered the question from mikewhatever, regarding whether you're using an older Intel or ATI graphics chip. For all I know, Jaunty is a bitch when it comes to especially the Intel chips.

---

### Post by Psychopump on 2009-05-20
> **XCan said:**
> You never answered the question from mikewhatever, regarding whether you're using an older Intel or ATI graphics chip. For all I know, Jaunty is a bitch when it comes to especially the Intel chips.

My system has an Intel chip and runs quite nicely.
(Maybe there are some differences in Mint that improve performance?)

---

### Post by silvagroup on 2009-05-22
Sorry for the non responsiveness, but I've been trying to get the new install of Jaunty going.
And I am not pleased at all.

Solved evolution problem, but that was just partially related, it was not the primary culprit.

I am not using Intel chipsets, it's an HP amdx2 w/nvidia 3.5gb ram and over 1tb hd space.

The re-install was working and just today it started up with the high cpu use again and while trying to copy some audio files it started getting errors about not finding the files and just stopped copying and stayed there showing file operation but nothing happening for over an hour.
Couldn't find a process to stop so I restarted system and when I logged back in all my desktop setting were wiped out. And so far it's a plain vanilla install.

Haven't had much time to even look at my wifes system yet, wanted to figure out mine first.

I am thinking it's Jaunty because both systems with Intrepid were sweet, Jaunty is just plain broke!!!

The laptop so far is ok as long as I want to tether my laptop, I can't get wifi to work so I have to use wired connection.

In the long run I am far from impressed with Jaunty, from my experience I would liken it to upgrading from XP to Vista. Well that's not 100% accurate Vista at least works as expected.

---

### Post by silvagroup on 2009-07-03
It appears that Ubuntu doesn't have an empty safety net, that I know of.
After a few months the same started happening to my laptop, it turned out that my disks were getting full, and the systems just kind of goes wacky after that, all kinds of weird things happen begining with excessive cpu use.
Moral to the story, keep you eye on the disk usage and don't get under maybe about 5%.

---

