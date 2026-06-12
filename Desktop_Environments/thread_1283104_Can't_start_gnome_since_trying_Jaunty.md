---
title: "Can't start gnome since trying Jaunty"
date: 2009-10-05
forum: Desktop Environments
---

### Post by rickwookie on 2009-10-05
Hi

I was happily running Ubuntu for a number of years but since trying to upgrade to Jauinty something went wrong and I could no longer log in to gnome.

I tried lots of things to get it to work again but then gave up for a while. Anyway, I thought that since Karmic is now in beta I'd give that a try to see if all the package updates would make my gnome desktop function again. Alas, since the new GDM now uses gnome, I then couldn't even get to the login prompt!

I managed to solve that problem by installing GDM-2.20 and setting that as my login manager, but still obviously I can't get gnome to work. I've installed xbuntu-desktop, and xfce won't start either, and I installed kubuntu-desktop and KDE does work, but I hate it.

If anyone could give me a pointer as to what log file I could check to try to see why gnome won't start (gnome failsafe also, well, fails!) I would really appreciate it.

---

### Post by rickwookie on 2009-10-05
If it's any use to anyone, here's the output of ps aux when gnome is trying to start (and doing nothing):
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   2780  1512 ?        Ss   09:19   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   09:19   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   09:19   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   09:19   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   09:19   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   09:19   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   09:19   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S<   09:19   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S<   09:19   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S<   09:19   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S<   09:19   0:00 [kintegrityd/0]
root        12  0.0  0.0      0     0 ?        S<   09:19   0:00 [kblockd/0]
root        13  0.0  0.0      0     0 ?        S<   09:19   0:00 [kacpid]
root        14  0.0  0.0      0     0 ?        S<   09:19   0:00 [kacpi_notify]
root        15  0.0  0.0      0     0 ?        S<   09:19   0:00 [kacpi_hotplug]
root        16  0.0  0.0      0     0 ?        S<   09:19   0:00 [ata/0]
root        17  0.0  0.0      0     0 ?        S<   09:19   0:00 [ata_aux]
root        18  0.0  0.0      0     0 ?        S<   09:19   0:00 [ksuspend_usbd]
root        19  0.0  0.0      0     0 ?        S<   09:19   0:00 [khubd]
root        20  0.0  0.0      0     0 ?        S<   09:19   0:00 [kseriod]
root        21  0.0  0.0      0     0 ?        S<   09:19   0:00 [kmmcd]
root        22  0.0  0.0      0     0 ?        S<   09:19   0:00 [bluetooth]
root        23  0.0  0.0      0     0 ?        S    09:19   0:00 [khungtaskd]
root        24  0.0  0.0      0     0 ?        S    09:19   0:00 [pdflush]
root        25  0.0  0.0      0     0 ?        S    09:19   0:00 [pdflush]
root        26  0.0  0.0      0     0 ?        S<   09:19   0:00 [kswapd0]
root        27  0.0  0.0      0     0 ?        S<   09:19   0:00 [aio/0]
root        28  0.0  0.0      0     0 ?        S<   09:19   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   09:19   0:00 [crypto/0]
root        33  0.0  0.0      0     0 ?        S<   09:19   0:00 [scsi_eh_0]
root        34  0.0  0.0      0     0 ?        S<   09:19   0:00 [scsi_eh_1]
root        35  0.0  0.0      0     0 ?        S<   09:19   0:00 [scsi_eh_2]
root        37  0.0  0.0      0     0 ?        S<   09:19   0:02 [scsi_eh_3]
root        40  0.0  0.0      0     0 ?        S<   09:19   0:00 [kstriped]
root        41  0.0  0.0      0     0 ?        S<   09:19   0:00 [kmpathd/0]
root        42  0.0  0.0      0     0 ?        S<   09:19   0:00 [kmpath_handlerd]
root        43  0.0  0.0      0     0 ?        S<   09:19   0:00 [ksnapd]
root        44  0.0  0.0      0     0 ?        S<   09:19   0:00 [kondemand/0]
root        45  0.0  0.0      0     0 ?        S<   09:19   0:00 [kconservative/0]
root        46  0.0  0.0      0     0 ?        S<   09:19   0:00 [krfcommd]
root       235  0.0  0.0      0     0 ?        S<   09:19   0:00 [khpsbpkt]
root       240  0.0  0.0      0     0 ?        S<   09:19   0:00 [knodemgrd_0]
root       264  0.0  0.0      0     0 ?        S<   09:19   0:00 [knodemgrd_1]
root       353  0.0  0.0      0     0 ?        S<   09:19   0:00 [kjournald]
root       403  0.0  0.0   2552  1136 ?        S    09:19   0:00 mountall --daemon --tmptime=0
root       416  0.0  0.0   2296   780 ?        S    09:19   0:00 upstart-udev-bridge --daemon
root       418  0.0  0.0   2760  1084 ?        S<s  09:19   0:00 udevd --daemon
root       545  0.0  0.0   2756   944 ?        S<   09:19   0:00 udevd --daemon
root       554  0.0  0.0   2756  1064 ?        S<   09:19   0:00 udevd --daemon
root       636  0.0  0.0      0     0 ?        S<   09:19   0:00 [kpsmoused]
root       681  0.0  0.0      0     0 ?        S<   09:19   0:00 [kgameportd]
root       766  0.0  0.0   2300   656 ?        S    09:19   0:00 mount -a -t cifs -o defaults //192.168.11.2/media /media/nasmedia
root       767  0.0  0.0   2004   736 ?        S    09:19   0:00 /sbin/mount.cifs //192.168.11.2/media /media/nasmedia -o rw
root       789  0.0  0.0      0     0 ?        S<   09:19   0:00 [kjournald]
root       856  0.0  0.0   2264   384 ?        Ss   09:19   0:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root       863  0.0  0.0   3960   964 ?        Ss   09:19   0:00 /sbin/mount.ntfs-3g /dev/sda3 /media/hda3 -o rw,locale=en_GB.UTF-8
root       886  0.0  0.0   3964   960 ?        Ss   09:19   0:00 /sbin/mount.ntfs-3g /dev/sda1 /media/hda1 -o rw,locale=en_GB.UTF-8
syslog     923  0.0  0.0  33888  1716 ?        Sl   09:19   0:00 rsyslogd -c4
root       924  0.0  0.0   1936   532 ?        Ss   09:19   0:00 dd if=/proc/kmsg of=/var/run/rsyslog/kmsg
root       931  0.0  0.0   3960   960 ?        Ss   09:19   0:00 /sbin/mount.ntfs-3g /dev/sda2 /media/hda2 -o rw,locale=en_GB.UTF-8
root      1019  0.0  0.0   1784   540 tty4     Ss+  09:20   0:00 /sbin/getty -8 38400 tty4
root      1021  0.0  0.0   1784   544 tty5     Ss+  09:20   0:00 /sbin/getty -8 38400 tty5
root      1033  0.0  0.0   1784   540 tty2     Ss+  09:20   0:00 /sbin/getty -8 38400 tty2
root      1034  0.0  0.0   1784   544 tty3     Ss+  09:20   0:00 /sbin/getty -8 38400 tty3
root      1036  0.0  0.0   1784   544 tty6     Ss+  09:20   0:00 /sbin/getty -8 38400 tty6
root      1038  0.0  0.0   2060   840 ?        Ss   09:20   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1045  0.0  0.0   2060   412 ?        Ss   09:20   0:00 atd
root      1046  0.0  0.0   2204   868 ?        Ss   09:20   0:00 cron
root      1223  0.0  0.0   5732  1024 ?        Ss   09:20   0:00 /usr/sbin/sshd
103       1242  0.0  0.0   3392  1600 ?        Ss   09:20   0:03 dbus-daemon --system --fork
avahi     1248  0.0  0.0   3120  1520 ?        Ss   09:20   0:00 avahi-daemon: running [Kylie.local]
avahi     1249  0.0  0.0   2988   524 ?        Ss   09:20   0:00 avahi-daemon: chroot helper
ntp       1273  0.0  0.0   4492  1264 ?        Ss   09:20   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 111:121 -g
107       1274  0.0  0.1   6440  4108 ?        Ss   09:20   0:00 hald --daemon=yes
root      1331  0.0  0.1  19872  3016 ?        Ssl  09:20   0:00 /usr/sbin/console-kit-daemon
root      1394  0.0  0.2   9732  4264 ?        Ss   09:20   0:00 NetworkManager
root      1395  0.0  0.0   3560  1212 ?        S    09:20   0:00 hald-runner
root      1397  0.0  0.1   4144  2092 ?        S    09:20   0:00 /usr/sbin/modem-manager
root      1444  0.0  0.0   5064  1660 ?        S    09:20   0:00 /sbin/wpa_supplicant -u -s
root      1478  0.0  0.0   3640  1140 ?        S    09:20   0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event1 /dev/input/event0
root      1485  0.0  0.0   3640  1140 ?        S    09:20   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1486  0.0  0.0   1836   544 ?        S    09:20   0:00 /bin/sh /usr/bin/mysqld_safe
root      1488  0.0  0.0   3640  1140 ?        S    09:20   0:00 hald-addon-storage: polling /dev/sr1 (every 2 sec)
root      1489  0.0  0.0   3640  1132 ?        S    09:20   0:00 hald-addon-storage: no polling on /dev/fd0 because it is explicitly disabled
107       1498  0.0  0.0   3460  1120 ?        S    09:20   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
mysql     1598  0.0  0.9 146240 19316 ?        Sl   09:20   0:04 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
root      1600  0.0  0.0   1752   536 ?        S    09:20   0:00 logger -t mysqld -p daemon.error
root      1712  0.0  1.3  30732 27876 ?        Ss   09:20   0:02 /usr/sbin/spamd --create-prefs --max-children 5 --helper-home-dir -d --pidfile=/var/run/spamd.pid
games     1884  0.0  0.0   6396   800 ?        Ss   09:20   0:00 /usr/sbin/ggzd
kernoops  1907  0.0  0.0   3564   908 ?        Ss   09:20   0:00 /usr/sbin/kerneloops
root      1924  0.0  0.1   5524  2524 ?        S    09:20   0:00 /usr/lib/devicekit-power/devkit-power-daemon
root      1981  0.0  1.2  30732 25924 ?        S    09:20   0:00 spamd child
root      1982  0.0  1.2  30732 25924 ?        S    09:20   0:00 spamd child
root      1983  0.0  0.0   9024  1700 ?        Ss   09:20   0:00 /usr/sbin/nmbd -D
root      1992  0.0  0.1  16016  2864 ?        Ss   09:20   0:00 /usr/sbin/smbd -D
root      2024  0.0  0.0  16016  1312 ?        S    09:20   0:00 /usr/sbin/smbd -D
spampd    2029  0.0  1.1  27624 23824 ?        Ss   09:20   0:00 /usr/bin/perl -T /usr/sbin/spampd --L --tagall --port=10025 --host=127.0.0.1 --relayport=10026 --relayhost=127.0.0.1 --pid=/var/run/spampd.pid --children=3 --user=spampd --group=spampd --logsock=unix
spampd    2034  0.0  1.1  27624 22960 ?        S    09:20   0:00 /usr/bin/perl -T /usr/sbin/spampd --L --tagall --port=10025 --host=127.0.0.1 --relayport=10026 --relayhost=127.0.0.1 --pid=/var/run/spampd.pid --children=3 --user=spampd --group=spampd --logsock=unix
spampd    2035  0.0  1.1  27624 22816 ?        S    09:20   0:00 /usr/bin/perl -T /usr/sbin/spampd --L --tagall --port=10025 --host=127.0.0.1 --relayport=10026 --relayhost=127.0.0.1 --pid=/var/run/spampd.pid --children=3 --user=spampd --group=spampd --logsock=unix
spampd    2036  0.0  1.1  27624 22816 ?        S    09:20   0:00 /usr/bin/perl -T /usr/sbin/spampd --L --tagall --port=10025 --host=127.0.0.1 --relayport=10026 --relayhost=127.0.0.1 --pid=/var/run/spampd.pid --children=3 --user=spampd --group=spampd --logsock=unix
root      2052  0.0  0.0  12252  1528 ?        Ss   09:20   0:00 /usr/sbin/winbindd
root      2065  0.0  0.0   2244   808 ?        Ss   09:20   0:00 /usr/sbin/dhcdbd --system
root      2070  0.0  0.0  12252  1284 ?        S    09:20   0:00 /usr/sbin/winbindd
root      2092  0.0  0.1   7064  2780 ?        Ss   09:20   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
rtkit     2150  0.0  0.0  22936  1144 ?        SNl  09:20   0:00 /usr/lib/rtkit/rtkit-daemon
root      2154  0.0  0.1   6348  3648 ?        S    09:20   0:00 /usr/lib/policykit-1/polkitd
root      2226  0.0  0.3  30608  7644 ?        Ss   09:20   0:00 /usr/sbin/apache2 -k start
root      2282  0.0  0.1   5368  2104 tty1     Ss   09:20   0:00 /bin/login --        
richard   2426  0.0  0.1   6812  4008 tty1     S    09:33   0:00 -bash
www-data  3186  0.0  0.1  30608  3756 ?        S    09:36   0:00 /usr/sbin/apache2 -k start
www-data  3187  0.0  0.1  30608  3756 ?        S    09:36   0:00 /usr/sbin/apache2 -k start
www-data  3188  0.0  0.1  30608  3756 ?        S    09:36   0:00 /usr/sbin/apache2 -k start
www-data  3189  0.0  0.1  30608  3756 ?        S    09:36   0:00 /usr/sbin/apache2 -k start
www-data  3190  0.0  0.1  30608  3756 ?        S    09:36   0:00 /usr/sbin/apache2 -k start
root     20158  0.0  0.1   5412  2816 ?        S    10:08   0:01 /usr/lib/devicekit-disks/devkit-disks-daemon
root     20162  0.0  0.0   5184   748 ?        S    10:08   0:00 devkit-disks-daemon: polling /dev/sr1 /dev/sr0
richard  20753  0.0  0.0   4216   756 ?        Ss   10:10   0:00 /usr/lib/libmenu-cache/libexec/menu-cached
root     23527  0.0  0.0  16744  1840 ?        Ss   10:45   0:00 /usr/sbin/gdm
root     23528  0.1  0.1  19440  3816 ?        R    10:45   0:00 /usr/sbin/gdm
root     23534  3.4  0.3  15404  7952 tty7     Rs+  10:45   0:04 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
richard  23607  0.0  0.1  33016  3492 ?        Sl   10:46   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
richard  23621  5.1  0.3  26248  6460 ?        Rsl  10:46   0:03 gnome-session
richard  23686  0.0  0.0   5028   608 ?        Ss   10:46   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
richard  23689  3.1  0.0   2868   920 ?        Ss   10:46   0:01 /bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
richard  23690  0.0  0.0   3484   696 ?        S    10:46   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
richard  23694  0.2  0.2  94520  4476 ?        Ssl  10:46   0:00 /usr/bin/pulseaudio --start
richard  23697  0.0  0.1  10956  2896 ?        S    10:46   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
richard  23699  6.3  0.2   8124  4788 ?        S    10:46   0:03 /usr/lib/libgconf2-4/gconfd-2
richard  23715  1.5  0.3  18432  7024 ?        S    10:46   0:00 metacity
richard  23719  1.0  0.6  30436 14352 ?        R    10:46   0:00 python /usr/share/system-config-printer/applet.py
richard  23721  0.8  0.3  17860  6704 ?        S    10:46   0:00 gnome-power-manager
richard  23722  0.4  0.4  22004  8340 ?        S    10:46   0:00 nm-applet --sm-disable
richard  23723  0.3  0.5  68980 11396 ?        Sl   10:46   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
richard  23729  0.3  0.2  18080  6080 ?        S    10:46   0:00 /usr/lib/notify-osd/notify-osd
richard  23731  0.2  0.4  96328  8996 ?        S    10:46   0:00 gnome-volume-control-applet
richard  23734  0.3  0.3  17752  6676 ?        S    10:46   0:00 bluetooth-applet
richard  23738  0.0  0.2  17324  5536 ?        S    10:46   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
richard  23743  0.3  0.1  18088  2596 ?        Ss   10:46   0:00 gnome-screensaver
richard  23752  0.0  0.0   3908  1828 ?        S    10:46   0:00 /usr/lib/xfconfd
richard  24115  0.2  0.1  32932  3548 ?        Ssl  10:46   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=21
richard  24122  0.4  0.5  45524 11036 ?        Sl   10:46   0:00 /usr/lib/evolution/2.28/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=18
richard  24437  0.0  0.3  23328  7412 ?        S    10:47   0:00 nautilus
richard  24438  0.0  0.0   2740  1008 tty1     R+   10:47   0:00 ps aux

```

---

### Post by Anarci on 2009-10-06
Are you using a propriety driver? A kernel upgrade broke my gnome recently when I upgraded to karmic beta.

You can also try going into recovery mode and doing a dpkg recovery to fix any possibly broken packages from the upgrade

---

### Post by rickwookie on 2009-10-06
No, I was using fglrx but now I'm using radeon or ati.

---

### Post by Anarci on 2009-10-07
Hmmm that makes me think that this might be the result of a bad upgrade, have you tried a fresh install of ubuntu or if you don't want to try that - A fresh install should be your last resort - You can wait 3 weeks until karmic is released and upgrade which might fix your problems.

If you don't feel like waiting you can always upgrade to karmic beta now. Just remember to backup

---

### Post by theZoid on 2009-10-07
Yeah, I just won't go the upgrade route anymore...clean install is too easy.

---

### Post by rickwookie on 2009-10-08
Yeah I'm sure it was a bad upgrade, that was to Jaunty.

But how to fix it is the question, surely there's a way to make it work without a fresh install. If the Jaunty release upgrade broke it, and it's still broken with the Karmic beta, then I doubt it will fix itself with the Karmic release.

Thanks anyway.

---

