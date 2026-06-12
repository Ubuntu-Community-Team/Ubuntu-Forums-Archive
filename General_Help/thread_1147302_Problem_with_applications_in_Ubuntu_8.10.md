---
title: "Problem with applications in Ubuntu 8.10"
date: 2009-05-03
forum: General Help
---

### Post by gspinn on 2009-05-03
Hi all. I`m new in Linux. I use Ubuntu 8.10 becouse of hardware problems but this is not important. I have a problem with the os. When i start Firefox,Skype i think any program the coputer get so slo. I barely can move my mouse. And my cpu stays always in 20% usage. Is that normal. I use Intel Celeron 340 3Ghz, 1.5Gb ddr ram and Ati radeon X300se. I think thats good for every day usage. I hope that somebody can help me or tell me why is this proble. Thanks.

p.s. Sorry for the bad english.

---

### Post by spiderbatdad on 2009-05-03
```
ps aux
```might help to show you what is running and using cpu. Not sure why you're having such a slow down when launching apps. execpt opening and launching those apps generally shoots cpu way up for a few seconds. It may be that your graphics card requires extra effort to display the gui.

---

### Post by gspinn on 2009-05-03
I havent enabled any efects in the appirience menu if this is what you mean. Thank youfor the fast reply

---

### Post by spiderbatdad on 2009-05-03
Not what I was suggesting.

Applications >> Accessories >> Terminal.
type in:
```
ps aux
```Paste output here if you like.

---

### Post by gspinn on 2009-05-03
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.3  0.1   3056  1896 ?        Ss   22:41   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   22:41   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   22:41   0:00 [migration/0]
root         4  0.2  0.0      0     0 ?        S<   22:41   0:01 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   22:41   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   22:41   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   22:41   0:00 [khelper]
root        46  0.0  0.0      0     0 ?        S<   22:41   0:00 [kintegrityd/0]
root        48  0.1  0.0      0     0 ?        S<   22:41   0:01 [kblockd/0]
root        50  0.0  0.0      0     0 ?        S<   22:41   0:00 [kacpid]
root        51  0.0  0.0      0     0 ?        S<   22:41   0:00 [kacpi_notify]
root       128  0.0  0.0      0     0 ?        S<   22:41   0:00 [cqueue]
root       132  0.0  0.0      0     0 ?        S<   22:41   0:00 [kseriod]
root       169  0.0  0.0      0     0 ?        S    22:41   0:00 [pdflush]
root       170  0.0  0.0      0     0 ?        S    22:41   0:00 [pdflush]
root       171  0.0  0.0      0     0 ?        S<   22:41   0:00 [kswapd0]
root       211  0.0  0.0      0     0 ?        S<   22:41   0:00 [aio/0]
root      1083  0.0  0.0      0     0 ?        S<   22:41   0:00 [kstriped]
root      1090  0.0  0.0      0     0 ?        S<   22:41   0:00 [ksnapd]
root      1258  0.0  0.0      0     0 ?        S<   22:42   0:00 [ksuspend_usbd]
root      1262  0.0  0.0      0     0 ?        S<   22:42   0:00 [khubd]
root      1290  3.0  0.0      0     0 ?        S<   22:42   0:19 [ata/0]
root      1292  0.0  0.0      0     0 ?        S<   22:42   0:00 [ata_aux]
root      1717  0.0  0.0      0     0 ?        S<   22:42   0:00 [scsi_eh_0]
root      1718  0.0  0.0      0     0 ?        S<   22:42   0:00 [scsi_eh_1]
root      1719  0.0  0.0      0     0 ?        S<   22:42   0:00 [scsi_eh_2]
root      1720  0.0  0.0      0     0 ?        S<   22:42   0:00 [scsi_eh_3]
root      2038  0.3  0.0      0     0 ?        S<   22:42   0:02 [scsi_eh_4]
root      2041  0.0  0.0      0     0 ?        S<   22:42   0:00 [scsi_eh_5]
root      2143  0.0  0.0      0     0 ?        S<   22:42   0:00 [scsi_eh_6]
root      2145  0.3  0.0      0     0 ?        S<   22:42   0:01 [usb-storage]
root      2267  0.0  0.0      0     0 ?        S<   22:42   0:00 [kjournald]
root      2443  0.2  0.0   2528  1024 ?        S<s  22:42   0:01 /sbin/udevd --d
root      2745  0.0  0.0      0     0 ?        S<   22:42   0:00 [btaddconn]
root      2751  0.0  0.0      0     0 ?        S<   22:42   0:00 [btdelconn]
root      2900  0.0  0.0      0     0 ?        S<   22:42   0:00 [cx88 tvaudio]
root      4144  0.0  0.0      0     0 ?        S<   22:42   0:00 [kjournald]
root      4409  0.0  0.0   1780   524 tty4     Ss+  22:42   0:00 /sbin/getty 384
root      4410  0.0  0.0   1780   528 tty5     Ss+  22:42   0:00 /sbin/getty 384
root      4417  0.0  0.0   1780   524 tty2     Ss+  22:42   0:00 /sbin/getty 384
root      4418  0.0  0.0   1780   524 tty3     Ss+  22:42   0:00 /sbin/getty 384
root      4419  0.0  0.0   1780   524 tty6     Ss+  22:42   0:00 /sbin/getty 384
root      4594  0.0  0.0   2308  1232 ?        Ss   22:42   0:00 /usr/sbin/acpid
root      4631  0.0  0.0      0     0 ?        S<   22:42   0:00 [kondemand/0]
syslog    4714  0.0  0.0   2012   672 ?        Ss   22:42   0:00 /sbin/syslogd -
root      4769  0.0  0.0   1940   540 ?        S    22:42   0:00 /bin/dd bs 1 if
klog      4771  0.1  0.1   3796  2628 ?        Ss   22:42   0:00 /sbin/klogd -P
108       4794  0.1  0.0   3072  1300 ?        Ss   22:42   0:00 /bin/dbus-daemo
avahi     4816  0.0  0.0   2888  1488 ?        Ss   22:42   0:00 avahi-daemon: r
avahi     4817  0.0  0.0   2888   496 ?        Ss   22:42   0:00 avahi-daemon: c
root      4849  0.0  0.1   4244  1688 ?        Ss   22:42   0:00 /usr/sbin/atiev
root      4878  0.0  0.1   6436  2364 ?        Ss   22:42   0:00 /usr/sbin/cupsd
111       5046  0.1  0.2   6460  4500 ?        Ss   22:43   0:00 /usr/sbin/hald
root      5049  0.0  0.1  16388  2564 ?        Ssl  22:43   0:00 /usr/sbin/conso
root      5112  0.0  0.0   3364  1140 ?        S    22:43   0:00 hald-runner
root      5133  0.0  0.0   3436  1052 ?        S    22:43   0:00 hald-addon-inpu
111       5148  0.0  0.0   2296   896 ?        S    22:43   0:00 hald-addon-acpi
root      5151  0.0  0.0   3440  1060 ?        S    22:43   0:00 hald-addon-stor
root      5154  0.0  0.0   3440  1060 ?        S    22:43   0:00 hald-addon-stor
root      5157  0.0  0.0   3440  1060 ?        S    22:43   0:00 hald-addon-stor
root      5160  0.0  0.0   3440  1060 ?        S    22:43   0:00 hald-addon-stor
root      5172  0.1  0.0   3440  1060 ?        S    22:43   0:00 hald-addon-stor
root      5213  0.0  0.1   3488  1680 ?        Ss   22:43   0:00 /usr/sbin/bluet
root      5237  0.0  0.0      0     0 ?        S<   22:43   0:00 [krfcommd]
root      5262  0.0  0.1  14636  2476 ?        Ssl  22:43   0:00 /usr/sbin/Netwo
root      5267  0.0  0.0   4244  1324 ?        S    22:43   0:00 /sbin/wpa_suppl
root      5270  0.0  0.1   6780  2960 ?        S    22:43   0:00 /usr/sbin/nm-sy
root      5300  0.0  0.1  14240  1788 ?        Ss   22:43   0:00 /usr/sbin/gdm
root      5339  0.0  0.0   4336  1152 ?        Ss   22:43   0:00 /usr/bin/system
daemon    5373  0.0  0.0   2068   456 ?        Ss   22:43   0:00 /usr/sbin/atd
root      5402  0.0  0.0   2252   956 ?        S    22:43   0:00 /sbin/dhclient
root      5403  0.0  0.0   3412  1028 ?        Ss   22:43   0:00 /usr/sbin/cron
root      5505  0.0  0.0   1780   520 tty1     Ss+  22:43   0:00 /sbin/getty 384
root      5575  0.0  0.2  14784  3232 ?        S    22:43   0:00 /usr/sbin/gdm
root      5580  6.1  3.6  67808 55928 tty7     Rs+  22:43   0:34 /usr/X11R6/bin/
root      5602  0.0  3.6  67808 55928 tty7     S+   22:43   0:00 /usr/X11R6/bin/
koko      5624  0.0  0.1  14700  2048 ?        S    22:44   0:00 /usr/bin/gnome-
koko      5635  0.0  0.3  24896  5736 ?        Ssl  22:44   0:00 x-session-manag
koko      5694  0.0  0.0   3124   688 ?        S    22:44   0:00 /usr/bin/dbus-l
koko      5695  0.0  0.0   3036  1212 ?        Ss   22:44   0:00 //bin/dbus-daem
koko      5698  0.3  0.2  28944  4260 ?        Ssl  22:44   0:01 /usr/bin/pulsea
koko      5701  0.0  0.1   7532  2532 ?        S    22:44   0:00 /usr/lib/pulsea
koko      5703  0.7  0.3   7724  4684 ?        S    22:44   0:03 /usr/lib/libgco
koko      5709  0.0  0.4  17728  6308 ?        Ss   22:44   0:00 /usr/bin/seahor
koko      5711  0.0  0.1   5556  2156 ?        S    22:44   0:00 /usr/lib/gvfs/g
koko      5718  0.0  0.1  29196  2032 ?        Ssl  22:44   0:00 /usr/lib/gvfs//
koko      5722  0.0  0.2  13916  3636 ?        S    22:44   0:00 /usr/lib/gnome-
koko      5727  0.2  0.6  32968 10276 ?        Ssl  22:44   0:01 /usr/lib/gnome-
koko      5728  0.8  0.8  21420 12700 ?        S    22:44   0:04 metacity
koko      5733  1.7  1.4  39116 22864 ?        S    22:44   0:09 gnome-panel
koko      5737  1.1  1.9  81700 30944 ?        S    22:44   0:06 nautilus --no-d
koko      5739  0.1  0.2  32432  3460 ?        Ssl  22:44   0:00 /usr/lib/bonobo
koko      5751  0.3  0.1  21216  3064 ?        Ss   22:44   0:01 gnome-screensav
koko      5760  0.1  0.1  14296  2992 ?        Sl   22:44   0:00 /usr/lib/gvfs/g
koko      5762  0.0  0.1   5536  2176 ?        S    22:44   0:00 /usr/lib/gvfs/g
koko      5766  0.0  0.6  23904 10004 ?        S    22:44   0:00 /usr/lib/gnome-
koko      5769  0.0  0.1   5556  2208 ?        S    22:44   0:00 /usr/lib/gvfs/g
koko      5771  0.0  0.1  22192  2764 ?        S    22:44   0:00 /usr/lib/gvfs/g
koko      5776  0.2  0.7  25072 12388 ?        S    22:44   0:01 nm-applet --sm-
koko      5778  0.1  0.8  26848 13932 ?        S    22:44   0:00 update-notifier
koko      5779  0.0  0.3  15560  5568 ?        S    22:44   0:00 tracker-applet
koko      5782  0.1  0.6  31400 10040 ?        Sl   22:44   0:00 /usr/lib/evolut
koko      5787  0.1  0.8  25472 12976 ?        S    22:44   0:00 python /usr/sha
koko      5788  0.0  0.5  17848  7776 ?        S    22:44   0:00 bluetooth-apple
koko      5795  0.1  0.8  27460 13784 ?        S    22:44   0:00 /usr/lib/fast-u
koko      5798  0.2  1.0  37812 15688 ?        Sl   22:44   0:01 /usr/lib/gnome-
koko      5801  0.3  0.6  30900 10456 ?        SNl  22:44   0:01 trackerd
koko      5804  0.0  0.5  24080  8972 ?        Ss   22:44   0:00 gnome-power-man
koko      5834  3.8  2.1  76380 33392 ?        Rl   22:45   0:17 skype
root      5851  0.0  0.0   3900  1108 ?        Ss   22:45   0:00 /sbin/mount.ntf
root      5905  0.1  0.0   3900  1168 ?        Ss   22:45   0:00 /sbin/mount.ntf
root      5931  0.8  1.0  22888 16132 ?        S    22:45   0:03 /usr/bin/python
koko      5969 11.6  3.7 183464 58324 ?        Sl   22:46   0:47 /usr/lib/firefo
root      5973  0.2  0.0   4044  1200 ?        Ss   22:46   0:01 /sbin/mount.ntf
koko      6286 11.0  1.5  99936 23716 ?        Sl   22:52   0:00 gnome-terminal
koko      6288  0.0  0.0   2912   760 ?        S    22:52   0:00 gnome-pty-helpe
koko      6289  4.6  0.2   5908  3272 pts/0    Ss   22:52   0:00 bash
koko      6306  0.0  0.0   2744  1008 pts/0    R+   22:52   0:00 ps aux

```

---

