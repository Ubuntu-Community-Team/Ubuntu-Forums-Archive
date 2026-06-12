---
title: "need help"
date: 2009-05-11
forum: General Help
---

### Post by thegrimr3mind on 2009-05-11
i have been having trouble downloading anything my package installer keeps saying only one software management tool is allowed to run at the same time but nothing else is running how can i fix this problem

---

### Post by baseface on 2009-05-11
```
ps aux | grep syn
```
then kill the package manager... if it reports back that one is running.

---

### Post by prem1er on 2009-05-11
You might be in the process of updating and trying to download a package.  That would cause this error.  Also if you are using apt-get at the same time, this would also cause this error.

---

### Post by thegrimr3mind on 2009-05-11
my update manager is giving me an error msg saying i need to run sudo dkpg or something

---

### Post by prem1er on 2009-05-11
> **thegrimr3mind said:**
> my update manager is giving me an error msg saying i need to run sudo dkpg or something

Just a little general help on the forums.  "Or something" is not useful for the people trying to help you.  Post as closely as possible to any problems or errors you are getting and it will be much easier for someone to help you.

---

### Post by thegrimr3mind on 2009-05-11
im new to ubuntu i cant stand Microsoft any more is there any way i can just close the software management programs

---

### Post by prem1er on 2009-05-11
> **baseface said:**
> ```
ps aux | grep syn
```
then kill the package manager... if it reports back that one is running.

Have you tried this yet?

---

### Post by shoby on 2009-05-11
I would suggest you to have some expert fix this issue... from the forums, you might not get the appropriate help/guide.

---

### Post by thegrimr3mind on 2009-05-11
how do i kill it i went to system monitor but im nut sure if its in there it says everything is sleeping

---

### Post by prem1er on 2009-05-11
Open up a terminal and type this.

```
ps aux | grep syn
```

---

### Post by thegrimr3mind on 2009-05-11
ok how do you open a terminal

---

### Post by thegrimr3mind on 2009-05-11
i did the terminal thing but that still hasnt fixed the problem

---

### Post by prem1er on 2009-05-11
It wouldn't fix anything.  Post the output of that command.

---

### Post by thegrimr3mind on 2009-05-11
will@will-desktop:~$ ps aux | grep syn
will      3344  0.0  0.1   3336   792 pts/0    R+   16:25   0:00 grep syn

---

### Post by baseface on 2009-05-11
ps aux | grep apt

---

### Post by thegrimr3mind on 2009-05-11
it is still saying theres another softwear management tool running

will@will-desktop:~$ ps aux | grep apt
will      3622  0.0  0.1   3336   800 pts/0    S+   16:38   0:00 grep apt

---

### Post by baseface on 2009-05-11
post the output of 
ps aux

---

### Post by thegrimr3mind on 2009-05-11
will@will-desktop:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3084   628 ?        Ss   16:20   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   16:20   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   16:20   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   16:20   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   16:20   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   16:20   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   16:20   0:01 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   16:20   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   16:20   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        R<   16:20   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   16:20   0:00 [khelper]
root        12  0.0  0.0      0     0 ?        S<   16:20   0:00 [kstop/0]
root        13  0.0  0.0      0     0 ?        S<   16:20   0:00 [kstop/1]
root        14  0.0  0.0      0     0 ?        S<   16:20   0:00 [kintegrityd/0]
root        15  0.0  0.0      0     0 ?        S<   16:20   0:00 [kintegrityd/1]
root        16  0.0  0.0      0     0 ?        S<   16:20   0:00 [kblockd/0]
root        17  0.0  0.0      0     0 ?        S<   16:20   0:00 [kblockd/1]
root        18  0.0  0.0      0     0 ?        S<   16:20   0:00 [kacpid]
root        19  0.0  0.0      0     0 ?        S<   16:20   0:00 [kacpi_notify]
root        20  0.0  0.0      0     0 ?        S<   16:20   0:00 [cqueue]
root        21  0.0  0.0      0     0 ?        S<   16:20   0:00 [ata/0]
root        22  0.0  0.0      0     0 ?        S<   16:20   0:00 [ata/1]
root        23  0.0  0.0      0     0 ?        S<   16:20   0:00 [ata_aux]
root        24  0.0  0.0      0     0 ?        S<   16:20   0:00 [ksuspend_usbd]
root        25  0.0  0.0      0     0 ?        S<   16:20   0:00 [khubd]
root        26  0.0  0.0      0     0 ?        S<   16:20   0:00 [kseriod]
root        27  0.0  0.0      0     0 ?        S<   16:20   0:00 [kmmcd]
root        28  0.0  0.0      0     0 ?        S<   16:20   0:00 [btaddconn]
root        29  0.0  0.0      0     0 ?        S<   16:20   0:00 [btdelconn]
root        30  0.0  0.0      0     0 ?        S    16:20   0:00 [pdflush]
root        31  0.0  0.0      0     0 ?        S    16:20   0:00 [pdflush]
root        32  0.0  0.0      0     0 ?        S<   16:20   0:00 [kswapd0]
root        33  0.0  0.0      0     0 ?        S<   16:20   0:00 [aio/0]
root        34  0.0  0.0      0     0 ?        S<   16:20   0:00 [aio/1]
root        35  0.0  0.0      0     0 ?        S<   16:20   0:00 [ecryptfs-kthr]
root        38  0.0  0.0      0     0 ?        S<   16:20   0:00 [scsi_eh_0]
root        39  0.0  0.0      0     0 ?        S<   16:20   0:00 [scsi_eh_1]
root        40  0.0  0.0      0     0 ?        S<   16:20   0:00 [scsi_eh_2]
root        41  0.0  0.0      0     0 ?        S<   16:20   0:00 [scsi_eh_3]
root        42  0.0  0.0      0     0 ?        S<   16:20   0:00 [kstriped]
root        43  0.0  0.0      0     0 ?        S<   16:20   0:00 [kmpathd/0]
root        44  0.0  0.0      0     0 ?        S<   16:20   0:00 [kmpathd/1]
root        45  0.0  0.0      0     0 ?        S<   16:20   0:00 [kmpath_handle]
root        46  0.0  0.0      0     0 ?        S<   16:20   0:00 [ksnapd]
root        47  0.0  0.0      0     0 ?        S<   16:20   0:00 [kondemand/0]
root        48  0.0  0.0      0     0 ?        S<   16:20   0:00 [kondemand/1]
root        49  0.0  0.0      0     0 ?        S<   16:20   0:00 [krfcommd]
root       708  0.0  0.0      0     0 ?        S<   16:20   0:00 [kjournald]
root       842  0.0  0.0   2224   400 ?        S<s  16:20   0:00 /sbin/udevd --d
root      1524  0.0  0.0      0     0 ?        S<   16:20   0:00 [kgameportd]
root      1527  0.4  0.0      0     0 ?        S<   16:20   0:23 [ath5k_pci]
root      2184  0.0  0.0   1808   464 tty4     Ss+  16:20   0:00 /sbin/getty 384
root      2185  0.0  0.0   1808   464 tty5     Ss+  16:20   0:00 /sbin/getty 384
root      2188  0.0  0.0   1808   464 tty2     Ss+  16:20   0:00 /sbin/getty 384
root      2190  0.0  0.0   1808   460 tty3     Ss+  16:20   0:00 /sbin/getty 384
root      2193  0.0  0.0   1808   464 tty6     Ss+  16:20   0:00 /sbin/getty 384
root      2264  0.0  0.0   2204   568 ?        Ss   16:20   0:00 /usr/sbin/acpid
syslog    2309  0.0  0.0   2040   612 ?        Ss   16:20   0:00 /sbin/syslogd -
root      2332  0.0  0.0   1968   456 ?        S    16:20   0:00 /bin/dd bs 1 if
klog      2334  0.0  0.0   3740   500 ?        Ss   16:20   0:00 /sbin/klogd -P
108       2357  0.0  0.1   2992  1288 ?        Ss   16:20   0:01 /bin/dbus-daemo
111       2394  0.0  0.5   6684  4260 ?        Ss   16:20   0:00 /usr/sbin/hald
root      2397  0.0  0.2  17448  2080 ?        Ssl  16:20   0:00 /usr/sbin/conso
root      2460  0.0  0.1   3328  1072 ?        S    16:20   0:00 hald-runner
root      2490  0.0  0.2   5176  1784 ?        S    16:20   0:00 hald-addon-inpu
root      2536  0.0  0.2   5180  1804 ?        S    16:20   0:01 hald-addon-stor
111       2538  0.0  0.2   5032  1760 ?        S    16:20   0:00 hald-addon-acpi
root      2556  0.0  0.2   3556  1548 ?        Ss   16:20   0:00 /usr/sbin/bluet
root      2593  0.0  0.2  15032  1748 ?        Ss   16:20   0:00 /usr/sbin/gdm
root      2595  0.0  0.4  15548  3256 ?        S    16:20   0:00 /usr/sbin/gdm
root      2600  8.0  8.6  87132 66336 tty7     Rs+  16:20   7:14 /usr/X11R6/bin/
root      2622  0.0  0.3  16552  2848 ?        Ssl  16:20   0:00 /usr/sbin/Netwo
root      2633  0.0  0.2   4276  1924 ?        S    16:20   0:00 /sbin/wpa_suppl
root      2634  0.0  0.4   7064  3120 ?        S    16:20   0:00 /usr/sbin/nm-sy
avahi     2646  0.0  0.1   2944  1488 ?        Ss   16:20   0:00 avahi-daemon: r
avahi     2647  0.0  0.0   2944   512 ?        Ss   16:20   0:00 avahi-daemon: c
root      2673  0.0  0.3   6496  2772 ?        Ss   16:20   0:00 /usr/sbin/cupsd
root      2704  0.0  0.1   4324  1152 ?        Ss   16:20   0:00 /usr/bin/system
daemon    2777  0.0  0.0   2096   452 ?        Ss   16:20   0:00 /usr/sbin/atd
root      2805  0.0  0.1   3480  1032 ?        Ss   16:20   0:00 /usr/sbin/cron
root      2899  0.0  0.0   1808   528 tty1     Ss+  16:20   0:00 /sbin/getty 384
will      2922  0.0  0.9  26492  7296 ?        Ssl  16:20   0:00 x-session-manag
will      2978  0.0  0.0      0     0 ?        Zs   16:20   0:00 [ssh] <defunct>
will      2981  0.0  0.0   3144   692 ?        S    16:20   0:00 /usr/bin/dbus-l
will      2982  0.0  0.1   3068  1268 ?        Ss   16:20   0:00 //bin/dbus-daem
will      2987  2.0  0.7 176596  5480 ?        Ssl  16:20   1:51 /usr/bin/pulsea
will      2988  0.0  0.3   7844  2632 ?        S    16:20   0:00 /usr/lib/pulsea
will      2990  0.0  0.5   7628  4492 ?        S    16:20   0:03 /usr/lib/libgco
will      3006  0.0  0.8  19276  6568 ?        Ss   16:20   0:00 /usr/bin/seahor
will      3009  0.0  0.2   5616  2124 ?        S    16:20   0:00 /usr/lib/gvfs/g
will      3014  0.0  1.1  29324  8772 ?        Ssl  16:20   0:01 /usr/lib/gnome-
will      3017  0.0  0.3  33864  2388 ?        SL   16:20   0:00 gnome-keyring-d
will      3023  0.0  0.3  29584  2320 ?        Ssl  16:20   0:00 /usr/lib/gvfs//
will      3029  0.0  0.0   1872   568 ?        S    16:20   0:00 /bin/sh /usr/bi
will      3090  1.0  2.7  29352 20804 ?        S    16:20   0:55 /usr/bin/compiz
will      3091  0.2  2.6  36984 20328 ?        S    16:20   0:14 gnome-panel
will      3092  0.1  3.2  70084 25328 ?        S    16:20   0:06 nautilus
will      3094  0.0  0.4  41760  3616 ?        Ssl  16:20   0:00 /usr/lib/bonobo
will      3099  0.0  1.8  27988 14368 ?        S    16:20   0:00 python /usr/sha
will      3102  0.0  1.6  23980 13024 ?        S    16:20   0:01 nm-applet --sm-
will      3116  0.0  1.5  23144 12280 ?        S    16:20   0:00 /usr/lib/notify
will      3117  0.0  1.1  25228  9064 ?        Ss   16:20   0:00 gnome-power-man
will      3124  0.0  1.4  23984 10872 ?        S    16:20   0:00 /usr/lib/gnome-
will      3127  0.0  0.3  14364  2968 ?        S    16:20   0:00 /usr/lib/gvfs/g
will      3144  0.0  0.4   7984  3560 ?        S    16:21   0:00 /usr/lib/gvfs/g
will      3146  0.0  0.4   8360  3116 ?        S    16:21   0:00 /usr/lib/gvfs/g
will      3150  0.0  1.8  27304 14404 ?        S    16:21   0:00 /usr/lib/fast-u
will      3153  0.0  1.9  44400 14768 ?        Sl   16:21   0:00 /usr/lib/gnome-
will      3156  0.0  1.2  23132  9912 ?        S    16:21   0:00 /usr/lib/indica
will      3164  0.0  0.2   5616  2232 ?        S    16:21   0:00 /usr/lib/gvfs/g
will      3167  0.0  0.0   1872   528 ?        S    16:21   0:00 /bin/sh /usr/bi
will      3169  0.1  1.8  24488 13844 ?        S    16:21   0:07 /usr/bin/gtk-wi
root      3184  0.0  0.1   2276  1000 ?        S    16:21   0:00 /sbin/dhclient
will      3251  0.1  0.7  17196  6060 ?        Ss   16:21   0:07 gnome-screensav
will      3256  0.0  1.5  44040 11740 ?        Sl   16:21   0:00 /usr/lib/evolut
will      3261  0.0  1.1  70888  8616 ?        Sl   16:21   0:00 /usr/lib/evolut
will      3324  0.0  1.9  34372 15216 ?        Sl   16:24   0:02 gnome-terminal
will      3325  0.0  0.0   2036   700 ?        S    16:24   0:00 gnome-pty-helpe
will      3326  0.0  0.4   5812  3092 pts/0    Ss+  16:24   0:00 bash
will      3642  0.2  1.7  24028 13508 ?        S    16:39   0:10 gksu --desktop
root      3646  0.2  7.5  72336 57600 ?        Ss   16:39   0:09 /usr/bin/python
will      4081  8.2 12.8 380380 98940 ?        Sl   16:56   4:30 /usr/lib/firefo
will      4174  0.0  0.0   1872   508 ?        S    16:57   0:00 /bin/sh /usr/bi
will      4175  0.0  0.0   1872   552 ?        S    16:57   0:00 /bin/sh ./songb
will      4180 17.7 12.2 449024 94396 ?        Sl   16:57   9:21 ././songbird-bi
will      5319  5.6  0.3   5760  3032 pts/1    Ss   17:50   0:00 bash
will      5335  0.0  0.1   2768  1032 pts/1    R+   17:50   0:00 ps aux
will@will-desktop:~$

---

### Post by Zoowey on 2009-05-11
I'm guessing it's telling you to run "sudo dpkg --configure -a" which I highly recommend you run.

So open a terminal and run "sudo dpkg --configure -a" without the quotes then restart your computer when it's done.

---

