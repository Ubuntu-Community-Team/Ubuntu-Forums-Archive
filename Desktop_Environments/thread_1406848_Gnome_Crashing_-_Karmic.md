---
title: "Gnome Crashing - Karmic"
date: 2010-02-14
forum: Desktop Environments
---

### Post by NiGhtMarEs0nWax on 2010-02-14
Hi, Gnome keeps crashing on me whenever my CPU spikes, usually when starting up a virtual machine or watching a flash video, my cpu will spike to 100%, Gnome then crashes and I get logged out.

Is there any logs I can check? or if I can monitor what's happening? I would really like to get this resolved because it's resulting in data corruption.

im using Ubuntu Karmic.

---

### Post by NiGhtMarEs0nWax on 2010-02-15
Bump.




After looking through the authentication log I noticed this repeatedly. I wonder if it's related? I would post lines from other logs from the same times, but I don't really know what I'm looking for.

> Feb 14 18:39:00 SPOONS gnome-keyring-daemon[20864]: dbus failure unregistering from session: Connection is closed

I can reproduce the crash if needed, and post the relevant logs.



Please help! Thanks.

---

### Post by Satoru-san on 2010-02-15
can you please paste these:

```
dmesg | tail -n 30
ps aux
```

do the dmesg after it crashes, adn the ps aux before.

Also you could please paste the /var/log/Xorg.0.log after X crashes and you get terminal. To do these though you will have to put them on a flash drive.

```
dmesg > /mnt/usb/dmesg.txt
cp /var/log/Xorg.0.log /mnt/usb
```

---

### Post by NiGhtMarEs0nWax on 2010-02-15
Ok, I'm expecting a flash drive to be delivered to me in the next day or two, I ordered one over the weekend.


I'll PM you when I've reposted on this thread, Thanks man.

---

### Post by Satoru-san on 2010-02-15
> **NiGhtMarEs0nWax said:**
> I'll PM you when I've reposted on this thread, Thanks man.
No need to do that, I look at all the forums all day long.

---

### Post by NiGhtMarEs0nWax on 2010-02-23
Hey sorry for the late reply, took a couple of weeks for my flash drive to be delivered. :)

**ps:** (done before crash)

```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   3424  1396 ?        Ss   15:59   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   15:59   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   15:59   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   15:59   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   15:59   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   15:59   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   15:59   0:00 [cpuset]
root         8  0.0  0.0      0     0 ?        S<   15:59   0:00 [khelper]
root         9  0.0  0.0      0     0 ?        S<   15:59   0:00 [netns]
root        10  0.0  0.0      0     0 ?        S<   15:59   0:00 [async/mgr]
root        11  0.0  0.0      0     0 ?        S<   15:59   0:00 [kintegrityd/0]
root        12  0.0  0.0      0     0 ?        S<   15:59   0:00 [kblockd/0]
root        13  0.0  0.0      0     0 ?        S<   15:59   0:00 [kacpid]
root        14  0.0  0.0      0     0 ?        S<   15:59   0:00 [kacpi_notify]
root        15  0.0  0.0      0     0 ?        S<   15:59   0:00 [kacpi_hotplug]
root        16  0.0  0.0      0     0 ?        S<   15:59   0:00 [ata/0]
root        17  0.0  0.0      0     0 ?        S<   15:59   0:00 [ata_aux]
root        18  0.0  0.0      0     0 ?        S<   15:59   0:00 [ksuspend_usbd]
root        19  0.0  0.0      0     0 ?        S<   15:59   0:00 [khubd]
root        20  0.0  0.0      0     0 ?        S<   15:59   0:00 [kseriod]
root        21  0.0  0.0      0     0 ?        S<   15:59   0:00 [kmmcd]
root        22  0.0  0.0      0     0 ?        S<   15:59   0:00 [bluetooth]
root        23  0.0  0.0      0     0 ?        S    15:59   0:00 [khungtaskd]
root        26  0.0  0.0      0     0 ?        S<   15:59   0:01 [kswapd0]
root        27  0.0  0.0      0     0 ?        S<   15:59   0:00 [aio/0]
root        28  0.0  0.0      0     0 ?        S<   15:59   0:00 [ecryptfs-kthrea]
root        29  0.0  0.0      0     0 ?        S<   15:59   0:00 [crypto/0]
root        33  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_0]
root        34  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_1]
root        35  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_2]
root        36  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_3]
root        37  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_4]
root        39  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_5]
root        41  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_6]
root        43  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_7]
root        48  0.0  0.0      0     0 ?        S<   15:59   0:00 [kstriped]
root        49  0.0  0.0      0     0 ?        S<   15:59   0:00 [kmpathd/0]
root        50  0.0  0.0      0     0 ?        S<   15:59   0:00 [kmpath_handlerd]
root        51  0.0  0.0      0     0 ?        S<   15:59   0:00 [ksnapd]
root        52  0.0  0.0      0     0 ?        S<   15:59   0:00 [kondemand/0]
root        53  0.0  0.0      0     0 ?        S<   15:59   0:00 [kconservative/0]
root        54  0.0  0.0      0     0 ?        S<   15:59   0:00 [krfcommd]
root       306  0.0  0.0      0     0 ?        S<   15:59   0:00 [khpsbpkt]
root       307  0.0  0.0      0     0 ?        S<   15:59   0:00 [usbhid_resumer]
root       308  0.0  0.0      0     0 ?        S<   15:59   0:00 [scsi_eh_8]
root       309  0.0  0.0      0     0 ?        S<   15:59   0:00 [usb-storage]
root       315  0.0  0.0      0     0 ?        S<   15:59   0:00 [knodemgrd_0]
root       405  0.0  0.0      0     0 ?        S<   15:59   0:00 [kjournald2]
root       466  0.0  0.0   2772   392 ?        S<s  15:59   0:00 udevd --daemon
root       569  0.0  0.0      0     0 ?        S<   15:59   0:00 [kgameportd]
root       768  0.0  0.0      0     0 ?        S<   15:59   0:00 [hd-audio0]
root       954  0.0  0.0   1852   448 ?        Ss   15:59   0:00 dd bs=1 if=/proc/kmsg of=/var/run/rsyslog/kmsg
syslog     956  0.0  0.0  34804  1160 ?        Sl   15:59   0:00 rsyslogd -c4
102        984  0.0  0.0   3152  1396 ?        Ss   15:59   0:00 dbus-daemon --system --fork
avahi      995  0.0  0.0   2824  1260 ?        Ss   15:59   0:00 avahi-daemon: running [SPOONS.local]
107        996  0.0  0.1   6276  2232 ?        Ss   15:59   0:00 hald --daemon=yes
root       997  0.0  0.2  18680  3124 ?        Ssl  15:59   0:00 NetworkManager
avahi      998  0.0  0.0   2824   272 ?        Ss   15:59   0:00 avahi-daemon: chroot helper
root      1016  0.0  0.1   3908  1684 ?        S    15:59   0:00 /usr/sbin/modem-manager
root      1045  0.0  0.1  19412  2452 ?        Ssl  15:59   0:00 /usr/sbin/console-kit-daemon
root      1052  0.0  0.0      0     0 ?        S<   15:59   0:00 [kjournald]
root      1141  0.0  0.0   3344   972 ?        S    15:59   0:00 hald-runner
root      1151  0.0  0.0      0     0 ?        S<   15:59   0:00 [cifsoplockd]
root      1171  0.0  0.0   4784  1036 ?        S    15:59   0:00 /sbin/wpa_supplicant -u -s
root      1302  0.0  0.0   1704   456 tty4     Ss+  15:59   0:00 /sbin/getty -8 38400 tty4
root      1304  0.0  0.0   1704   456 tty5     Ss+  15:59   0:00 /sbin/getty -8 38400 tty5
root      1309  0.0  0.0   1704   456 tty2     Ss+  15:59   0:00 /sbin/getty -8 38400 tty2
root      1310  0.0  0.0   1704   456 tty3     Ss+  15:59   0:00 /sbin/getty -8 38400 tty3
root      1312  0.0  0.0   1704   456 tty6     Ss+  15:59   0:00 /sbin/getty -8 38400 tty6
root      1323  0.0  0.0   1976   568 ?        Ss   15:59   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon    1346  0.0  0.0   1964   296 ?        Ss   15:59   0:00 atd
root      1347  0.0  0.0   2092   756 ?        Ss   15:59   0:00 cron
root      1397  0.0  0.0   3420  1052 ?        S    15:59   0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
107       1413  0.0  0.0   3264   932 ?        S    15:59   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      1419  0.0  0.0   3420  1144 ?        S    15:59   0:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
root      1425  0.0  0.0   3420  1020 ?        S    15:59   0:00 hald-addon-input: Listening on /dev/input/event3 /dev/input/event1 /dev/input/event0
113       1876  0.0  0.0   6568   584 ?        Ss   15:59   0:00 /usr/sbin/exim4 -bd -q30m
root      1919  0.0  0.0   8600  1024 ?        Ss   15:59   0:00 /usr/sbin/nmbd -D
root      1923  0.0  0.1  15280  1692 ?        Ss   15:59   0:00 /usr/sbin/smbd -D
root      1924  0.0  0.0  15280   552 ?        S    15:59   0:00 /usr/sbin/smbd -D
root      1983  0.0  0.0  11684   764 ?        Ss   15:59   0:00 /usr/sbin/winbindd
root      1984  0.0  0.0  11684   604 ?        S    15:59   0:00 /usr/sbin/winbindd
root      2016  0.0  0.0   6688  1280 ?        Ss   15:59   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
timidity  2395  0.0  0.1  16144  1776 ?        S    15:59   0:00 /usr/bin/timidity -Os -iAD
root      2403  0.0  0.0   1704   456 tty1     Ss+  15:59   0:00 /sbin/getty -8 38400 tty1
root      2415  0.0  0.0   2144   608 ?        S    15:59   0:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth1.pid -lf /var/lib/dhcp3/dhclient-0032f797-e904-41a0-9a95-4063060a831a-eth1.lease -cf /var/run/nm-dhclient-eth1.conf eth1
root      2452  0.0  0.1   8616  2964 ?        Ss   15:59   0:00 gdm-binary
root      2528  0.0  0.1   5128  2152 ?        S    15:59   0:00 /usr/lib/devicekit-power/devkit-power-daemon
1000      2739  0.0  0.2  40728  3172 ?        Sl   16:05   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
root      2837  0.0  0.0      0     0 ?        S<   16:05   0:00 [cifsd]
root      2929  0.0  0.1   5308  2908 ?        S    16:05   0:00 /usr/lib/devicekit-disks/devkit-disks-daemon
root      2930  0.0  0.0   4828   568 ?        S    16:05   0:00 devkit-disks-daemon: polling /dev/sr0 /dev/sdc
root      2956  0.0  0.1   5840  3068 ?        S    16:05   0:00 /usr/lib/policykit-1/polkitd
root      3066  0.0  0.0   2768   464 ?        S<   16:05   0:00 udevd --daemon
root     18783  0.0  0.0  20892   520 ?        S    16:57   0:00 /usr/bin/truecrypt --core-service
root     18785  0.0  0.0 136860  1252 ?        Ssl  16:57   0:00 /usr/bin/truecrypt --core-service
root     18792  0.3  0.0      0     0 ?        S<   16:57   0:03 [loop0]
root     18795  0.0  0.0      0     0 ?        S<   16:57   0:00 [kdmflush]
root     18796  0.0  0.0   2768   468 ?        S<   16:57   0:00 udevd --daemon
root     18818  0.0  0.0   2152   628 ?        S    16:57   0:00 upstart-udev-bridge --daemon
root     18831  0.0  0.0      0     0 ?        S<   16:57   0:00 [kcryptd_io]
root     18832  2.5  0.0      0     0 ?        S<   16:57   0:30 [kcryptd]
root     18845  1.5  0.0   3996   956 ?        Ss   16:57   0:19 /sbin/mount.ntfs /dev/mapper/truecrypt9 /media/truecrypt9 -o rw,uid=1000,gid=1000,umask=077
root     18962  0.0  0.0  20808   532 ?        S    16:57   0:00 /usr/bin/truecrypt --core-service
root     18964  0.0  0.0 136912  1308 ?        Ssl  16:57   0:00 /usr/bin/truecrypt --core-service
root     18974  0.0  0.0      0     0 ?        S<   16:57   0:00 [loop1]
root     18984  0.0  0.0      0     0 ?        S<   16:57   0:00 [kdmflush]
root     18985  0.0  0.0      0     0 ?        S<   16:57   0:00 [kcryptd_io]
root     18986  0.0  0.0      0     0 ?        S<   16:57   0:00 [kcryptd]
root     19000  0.0  0.0   3864   708 ?        Ss   16:57   0:00 /sbin/mount.ntfs /dev/mapper/truecrypt10 /media/truecrypt10 -o rw,uid=1000,gid=1000,umask=077
1000     19214  0.0  0.2  40728  3460 ?        Sl   16:59   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
root     20199  0.0  0.0      0     0 ?        S    17:02   0:00 [pdflush]
root     20243  0.0  0.2   8544  3396 ?        S    17:02   0:00 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Display1
root     20244  6.3  3.0  83860 47532 tty9     Rs+  17:02   0:56 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-ZMpk0l/database -nolisten tcp
gdm      20278  0.0  0.0   3384   712 ?        S    17:02   0:00 /usr/bin/dbus-launch --exit-with-session
root     20297  0.0  0.2  12892  4392 ?        S    17:02   0:00 /usr/lib/gdm/gdm-session-worker
1000     20329  0.0  0.2  40728  3532 ?        Sl   17:02   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
1000     20344  0.0  0.4  25460  6540 ?        Ssl  17:02   0:00 gnome-session
1000     20387  0.0  0.0   4712   608 ?        Ss   17:02   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
1000     20390  0.0  0.0   3100  1296 ?        Ss   17:02   0:00 /bin/dbus-daemon --fork --print-pid 8 --print-address 10 --session
1000     20391  0.0  0.0   3384   708 ?        S    17:02   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session gnome-session
1000     20395  0.4  0.3  94184  4644 ?        Ssl  17:02   0:04 /usr/bin/pulseaudio --start
1000     20398  0.0  0.1  10636  2912 ?        S    17:02   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
1000     20400  0.0  0.3   7820  4832 ?        S    17:02   0:00 /usr/lib/libgconf2-4/gconfd-2
1000     20406  0.0  0.5  96740  8948 ?        Ssl  17:02   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
1000     20412  0.0  0.4  22552  7328 ?        Ss   17:02   0:00 seahorse-daemon
1000     20414  0.0  0.1   5760  2172 ?        S    17:02   0:00 /usr/lib/gvfs/gvfsd
1000     20421  0.0  0.1  29796  2456 ?        Ssl  17:02   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/axeface1111/.gvfs
1000     20438  0.0  0.4  17488  6320 ?        S    17:02   0:00 /usr/lib/notify-osd/notify-osd
1000     20439  0.0  0.0   1752   556 ?        S    17:02   0:00 /bin/sh /usr/bin/compiz
1000     20503  1.6  1.8  37132 28344 ?        S    17:02   0:14 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --sm-client-id 10c26f08dcccaa4a00126694457883984300000203440029 move resize place decoration animation ccp
1000     20504  0.1  1.2  43040 19364 ?        S    17:02   0:01 gnome-panel
1000     20505  0.3  2.0  99128 31952 ?        Rl   17:03   0:02 nautilus
1000     20507  0.0  0.2  39360  3356 ?        S    17:03   0:00 /usr/lib/gvfs/gvfs-gdu-volume-monitor
1000     20518  0.0  1.8  68488 29004 ?        Sl   17:03   0:00 pidgin
1000     20519  0.0  0.0   4492  1472 ?        S    17:03   0:00 /bin/bash /home/axeface1111/.Startup-Scripts/Gnome_Terminal_Startup_With_Sleep.sh
1000     20520  0.0  0.0   1752   492 ?        S    17:03   0:00 /bin/sh /usr/bin/awn-autostart
1000     20525  0.0  0.7  34728 10876 ?        Sl   17:03   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
1000     20530  0.0  0.0   1752   480 ?        Ss   17:03   0:00 /bin/sh -c /usr/bin/compiz-decorator
1000     20531  0.1  0.6  20380  9664 ?        S    17:03   0:00 /usr/bin/gtk-window-decorator
1000     20534  0.0  0.7  95192 11356 ?        S    17:03   0:00 gnome-volume-control-applet
1000     20535  0.0  0.3  16624  5608 ?        S    17:03   0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
1000     20536  0.0  0.4  17236  6488 ?        S    17:03   0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
1000     20537  0.0  0.7  34352 12040 ?        S    17:03   0:00 nm-applet --sm-disable
1000     20539  0.0  0.4  17216  6960 ?        S    17:03   0:00 gnome-power-manager
1000     20554  0.0  0.1   6532  2208 ?        S    17:03   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
1000     20556  0.0  0.1  17380  2600 ?        Ss   17:03   0:00 gnome-screensaver
1000     20559  0.0  0.2  40644  3476 ?        Ssl  17:03   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=22
1000     20579  0.0  0.1   6212  2796 ?        S    17:03   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.9 /org/gtk/gvfs/exec_spaw/0
1000     20597  0.0  0.6  29668 10156 ?        S    17:03   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=18
1000     20599  0.0  0.8  32240 12628 ?        S    17:03   0:00 /usr/lib/gnome-utils/gnome-dictionary-applet --oaf-activate-iid=OAFIID:GNOME_DictionaryApplet_Factory --oaf-ior-fd=21
1000     20603  0.0  0.5  22808  8608 ?        R    17:03   0:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=24
1000     20611  0.0  0.8  31820 12564 ?        S    17:03   0:00 /usr/lib/indicator-applet/indicator-applet-session --oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=27
1000     20636  0.0  0.1   5764  2260 ?        S    17:03   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.9 /org/gtk/gvfs/exec_spaw/1
1000     20646  0.0  0.1   5676  1940 ?        S    17:03   0:00 /usr/lib/gvfs/gvfsd-metadata
1000     20649  0.0  0.2  12076  3168 ?        S    17:03   0:00 /usr/lib/indicator-session/indicator-status-service
1000     20651  0.0  0.1   6336  2100 ?        S    17:03   0:00 /usr/lib/indicator-session/indicator-users-service
1000     20653  0.0  0.1   6904  2672 ?        S    17:03   0:00 /usr/lib/indicator-session/indicator-session-service
1000     20659  0.0  0.0   1752   488 ?        S    17:03   0:00 /bin/sh /usr/bin/avant-window-navigator
1000     20661  0.1  0.9  38644 14164 ?        Rl   17:03   0:01 gnome-terminal
1000     20662  0.1  0.6  24056 10392 ?        S    17:03   0:01 awn
1000     20663  0.0  0.0   1904   712 ?        S    17:03   0:00 gnome-pty-helper
1000     20664  0.0  0.2   6252  3544 pts/0    Ss   17:03   0:00 bash
1000     20679  0.0  0.5  22396  8044 ?        S    17:03   0:00 Separator -activation -p /usr/share/avant-window-navigator/applets/separator.desktop -u 1263076085 -w 33554482 -o 0 -h 45
1000     20683  0.0  1.3  50468 20836 ?        S    17:03   0:00 python /usr/share/avant-window-navigator/applets/showdesktop/showdesktop.py --uid=1263076080 --window=33554483 --orient=0 --height=45
1000     20690  0.1  2.0  73096 30924 ?        Sl   17:03   0:01 /usr/lib/virtualbox/VirtualBox
1000     20695  0.0  0.2  11764  3300 ?        S    17:03   0:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
1000     20704  0.1  0.5  23008  7896 ?        Sl   17:03   0:01 /usr/lib/virtualbox/VBoxSVC --automate
root     20722  0.0  0.0      0     0 ?        S    17:03   0:00 [pdflush]
1000     20928  0.0  0.0   2644  1012 pts/0    R+   17:17   0:00 ps aux
```



**dmesg | tail -30:** (done after)

```
[ 4704.532494] HighMem per-cpu:
[ 4704.532496] CPU    0: hi:  186, btch:  31 usd:   0
[ 4704.532500] Active_anon:70577 active_file:90139 inactive_anon:70655
[ 4704.532501]  inactive_file:84786 unevictable:455 dirty:75 writeback:0 unstable:0
[ 4704.532502]  free:11227 slab:7559 mapped:54089 pagetables:1631 bounce:0
[ 4704.532506] DMA free:3544kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:2468kB inactive_file:1788kB unevictable:0kB present:15804kB pages_scanned:0 all_unreclaimable? no
[ 4704.532509] lowmem_reserve[]: 0 865 1507 1507
[ 4704.532514] Normal free:39992kB min:3728kB low:4660kB high:5592kB active_anon:120132kB inactive_anon:122028kB active_file:192808kB inactive_file:192884kB unevictable:1820kB present:885944kB pages_scanned:0 all_unreclaimable? no
[ 4704.532517] lowmem_reserve[]: 0 0 5140 5140
[ 4704.532522] HighMem free:1372kB min:512kB low:1204kB high:1896kB active_anon:162176kB inactive_anon:160592kB active_file:165280kB inactive_file:144472kB unevictable:0kB present:657992kB pages_scanned:0 all_unreclaimable? no
[ 4704.532525] lowmem_reserve[]: 0 0 0 0
[ 4704.532528] DMA: 12*4kB 4*8kB 2*16kB 1*32kB 1*64kB 4*128kB 5*256kB 3*512kB 0*1024kB 0*2048kB 0*4096kB = 3536kB
[ 4704.532536] Normal: 7878*4kB 728*8kB 154*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 39992kB
[ 4704.532543] HighMem: 49*4kB 9*8kB 5*16kB 20*32kB 0*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1372kB
[ 4704.532551] 176894 total pagecache pages
[ 4704.532552] 873 pages in swap cache
[ 4704.532554] Swap cache stats: add 17865, delete 16992, find 5223/5520
[ 4704.532556] Free swap  = 2979520kB
[ 4704.532557] Total swap = 2996112kB
[ 4704.539026] 393104 pages RAM
[ 4704.539029] 165794 pages HighMem
[ 4704.539030] 51399 pages reserved
[ 4704.539032] 264156 pages shared
[ 4704.539033] 140220 pages non-shared
[ 4704.590642] [drm] Num pipes: 4
[ 4704.634205] compiz.real[20503]: segfault at 50 ip 08055c3c sp bfb43ce0 error 4 in compiz.real[8048000+34000]
[ 4705.795966] [drm] Setting GART location based on new memory map
[ 4705.797277] [drm] Loading R500 Microcode
[ 4705.797301] [drm] Num pipes: 4
[ 4705.797308] [drm] writeback test succeeded in 1 usecs
```



**dmesg (full):** (done after)

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000005ffa0000 - 000000005ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000005ffae000 - 000000005ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005ffe0000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x5ffa0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FFC0000000 write-back
[    0.000000]   1 base 0040000000 mask FFE0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000005ffa0000 (usable)
[    0.000000]  modified: 000000005ffa0000 - 000000005ffae000 (ACPI data)
[    0.000000]  modified: 000000005ffae000 - 000000005ffe0000 (ACPI NVS)
[    0.000000]  modified: 000000005ffe0000 - 0000000060000000 (reserved)
[    0.000000]  modified: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 37868000 - 37fef483
[    0.000000] Allocated new RAMDISK: 008ad000 - 01034483
[    0.000000] Move RAMDISK from 0000000037868000 - 0000000037fef482 to 008ad000 - 01034482
[    0.000000] ACPI: RSDP 000fad00 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 5ffa0000 00034 (v01 A M I  OEMRSDT  03000629 MSFT 00000097)
[    0.000000] ACPI: FACP 5ffa0200 00084 (v02 A M I  OEMFACP  03000629 MSFT 00000097)
[    0.000000] ACPI: DSDT 5ffa0430 06E7D (v01  A0466 A0466001 00000001 INTL 02002026)
[    0.000000] ACPI: FACS 5ffae000 00040
[    0.000000] ACPI: APIC 5ffa0390 0005C (v01 A M I  OEMAPIC  03000629 MSFT 00000097)
[    0.000000] ACPI: MCFG 5ffa03f0 0003C (v01 A M I  OEMMCFG  03000629 MSFT 00000097)
[    0.000000] ACPI: OEMB 5ffae040 0007B (v01 A M I  AMI_OEM  03000629 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 647MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac258]              BRK ==> [00008a9000 - 00008ac258]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008ad000 - 0001034483]      NEW RAMDISK ==> [00008ad000 - 0001034483]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0005ffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0005ffa0
[    0.000000] On node 0 totalpages: 393007
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c1035200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1296 pages used for memmap
[    0.000000]   HighMem zone: 164498 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 60000000 (gap: 60000000:9f700000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c1c3c000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 389935
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=24420e75-5730-4529-8434-f047727be5cd ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 7862080 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0005ffa0)
[    0.000000] Memory: 1534760k/1572480k available (4566k kernel code, 36492k reserved, 2142k data, 540k init, 663176k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches PMTIMER. 2 loops
[    0.000000] Detected 2405.417 MHz processor.
[    0.000401] spurious 8259A interrupt: IRQ7.
[    0.001613] Console: colour VGA+ 80x25
[    0.001616] console [tty0] enabled
[    0.001669] Calibrating delay loop (skipped), value calculated using timer frequency.. 4810.83 BogoMIPS (lpj=9621668)
[    0.001696] Security Framework initialized
[    0.001718] AppArmor: AppArmor initialized
[    0.001724] Mount-cache hash table entries: 512
[    0.001868] Initializing cgroup subsys ns
[    0.001872] Initializing cgroup subsys cpuacct
[    0.001875] Initializing cgroup subsys memory
[    0.001881] Initializing cgroup subsys freezer
[    0.001883] Initializing cgroup subsys net_cls
[    0.001895] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.001898] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.001901] mce: CPU supports 5 MCE banks
[    0.001919] Performance Counters: AMD PMU driver.
[    0.001925] ... version:                 0
[    0.001927] ... bit width:               48
[    0.001928] ... generic counters:        4
[    0.001930] ... value mask:              0000ffffffffffff
[    0.001932] ... max period:              00007fffffffffff
[    0.001933] ... fixed-purpose counters:  0
[    0.001935] ... counter mask:            000000000000000f
[    0.001939] Checking 'hlt' instruction... OK.
[    0.016597] SMP alternatives: switching to UP code
[    0.020008] ACPI: Core revision 20090521
[    0.030292] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070161] CPU0: AMD Athlon(tm) 64 Processor 4000+ stepping 01
[    0.072001] Brought up 1 CPUs
[    0.072001] Total of 1 processors activated (4810.83 BogoMIPS).
[    0.072001] CPU0 attaching NULL sched-domain.
[    0.072001] Booting paravirtualized kernel on bare hardware
[    0.072001] regulator: core version 0.5
[    0.072001] Time: 15:59:29  Date: 02/23/10
[    0.072001] NET: Registered protocol family 16
[    0.072001] EISA bus registered
[    0.072001] ACPI: bus type pci registered
[    0.072001] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.072001] PCI: Not using MMCONFIG.
[    0.072001] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.072001] PCI: Using configuration type 1 for base access
[    0.072001] bio: create slab <bio-0> at 0
[    0.072001] ACPI: EC: Look up EC in DSDT
[    0.080894] ACPI: Interpreter enabled
[    0.080899] ACPI: (supports S0 S1 S3 S4 S5)
[    0.080917] ACPI: Using IOAPIC for interrupt routing
[    0.081033] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.087979] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.087981] PCI: Using MMCONFIG for extended config space
[    0.096133] ACPI Warning: Incorrect checksum in table [OEMB] - 3D, should be 0F 20090521 tbutils-246
[    0.096219] ACPI: No dock devices found.
[    0.096325] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.096400] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.096403] pci 0000:00:02.0: PME# disabled
[    0.096440] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.096443] pci 0000:00:05.0: PME# disabled
[    0.096476] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.096479] pci 0000:00:06.0: PME# disabled
[    0.096644] pci 0000:00:1c.0: reg 10 32bit mmio: [0xd7ffc000-0xd7ffcfff]
[    0.096693] pci 0000:00:1c.1: reg 10 32bit mmio: [0xd7ffd000-0xd7ffdfff]
[    0.096742] pci 0000:00:1c.2: reg 10 32bit mmio: [0xd7ffe000-0xd7ffefff]
[    0.096813] pci 0000:00:1c.3: reg 10 32bit mmio: [0xd7fff800-0xd7fff8ff]
[    0.096863] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.096867] pci 0000:00:1c.3: PME# disabled
[    0.096920] pci 0000:00:1d.0: reg 10 64bit mmio: [0xd7ff4000-0xd7ff7fff]
[    0.096962] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.096966] pci 0000:00:1d.0: PME# disabled
[    0.097091] pci 0000:00:1e.1: quirk: region 0900-093f claimed by ali7101 ACPI
[    0.097157] pci 0000:00:1f.0: reg 20 io port: [0xff00-0xff0f]
[    0.097225] pci 0000:00:1f.1: reg 10 io port: [0xac00-0xac07]
[    0.097231] pci 0000:00:1f.1: reg 14 io port: [0xa880-0xa883]
[    0.097237] pci 0000:00:1f.1: reg 18 io port: [0xa800-0xa807]
[    0.097244] pci 0000:00:1f.1: reg 1c io port: [0xa480-0xa483]
[    0.097250] pci 0000:00:1f.1: reg 20 io port: [0xa400-0xa40f]
[    0.097257] pci 0000:00:1f.1: reg 24 32bit mmio: [0xd7fffc00-0xd7ffffff]
[    0.097283] pci 0000:00:1f.1: PME# supported from D3hot
[    0.097287] pci 0000:00:1f.1: PME# disabled
[    0.097331] pci 0000:04:00.0: reg 10 64bit mmio: [0xc0000000-0xcfffffff]
[    0.097339] pci 0000:04:00.0: reg 18 64bit mmio: [0xdffe0000-0xdffeffff]
[    0.097345] pci 0000:04:00.0: reg 20 io port: [0xe800-0xe8ff]
[    0.097354] pci 0000:04:00.0: reg 30 32bit mmio: [0xdffc0000-0xdffdffff]
[    0.097372] pci 0000:04:00.0: supports D1 D2
[    0.097404] pci 0000:04:00.1: reg 10 64bit mmio: [0xdfff0000-0xdfffffff]
[    0.097436] pci 0000:04:00.1: supports D1 D2
[    0.097495] pci 0000:00:02.0: bridge io port: [0xe000-0xefff]
[    0.097498] pci 0000:00:02.0: bridge 32bit mmio: [0xdff00000-0xdfffffff]
[    0.097502] pci 0000:00:02.0: bridge 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.097569] pci 0000:03:00.0: reg 10 64bit mmio: [0xdfeffc00-0xdfeffc7f]
[    0.097587] pci 0000:03:00.0: reg 18 64bit mmio: [0xdfef8000-0xdfefbfff]
[    0.097597] pci 0000:03:00.0: reg 20 io port: [0xdc00-0xdc7f]
[    0.097615] pci 0000:03:00.0: reg 30 32bit mmio: [0xdfe00000-0xdfe7ffff]
[    0.097661] pci 0000:03:00.0: supports D1 D2
[    0.097730] pci 0000:00:05.0: bridge io port: [0xd000-0xdfff]
[    0.097733] pci 0000:00:05.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.097789] pci 0000:02:00.0: reg 10 64bit mmio: [0xdfdfc000-0xdfdfffff]
[    0.097797] pci 0000:02:00.0: reg 18 io port: [0xc800-0xc8ff]
[    0.097821] pci 0000:02:00.0: reg 30 32bit mmio: [0xdfdc0000-0xdfddffff]
[    0.097859] pci 0000:02:00.0: supports D1 D2
[    0.097861] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.097866] pci 0000:02:00.0: PME# disabled
[    0.097924] pci 0000:00:06.0: bridge io port: [0xc000-0xcfff]
[    0.097927] pci 0000:00:06.0: bridge 32bit mmio: [0xdfd00000-0xdfdfffff]
[    0.098000] pci 0000:01:11.0: reg 10 io port: [0xbc00-0xbc1f]
[    0.098013] pci 0000:01:11.0: reg 14 64bit mmio: [0xdfa00000-0xdfbfffff]
[    0.098026] pci 0000:01:11.0: reg 1c 64bit mmio: [0xd8000000-0xdbffffff]
[    0.098064] pci 0000:01:11.0: supports D1 D2
[    0.098109] pci 0000:01:13.0: reg 10 32bit mmio: [0xdfcfb800-0xdfcfbfff]
[    0.098117] pci 0000:01:13.0: reg 14 32bit mmio: [0xdfcf4000-0xdfcf7fff]
[    0.098168] pci 0000:01:13.0: supports D1 D2
[    0.098170] pci 0000:01:13.0: PME# supported from D0 D1 D2 D3hot
[    0.098175] pci 0000:01:13.0: PME# disabled
[    0.098223] pci 0000:01:14.0: reg 10 32bit mmio: [0xdfcfc000-0xdfcfffff]
[    0.098231] pci 0000:01:14.0: reg 14 io port: [0xb800-0xb8ff]
[    0.098261] pci 0000:01:14.0: reg 30 32bit mmio: [0xdfcc0000-0xdfcdffff]
[    0.098289] pci 0000:01:14.0: supports D1 D2
[    0.098291] pci 0000:01:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.098295] pci 0000:01:14.0: PME# disabled
[    0.098322] pci 0000:00:1a.0: bridge io port: [0xb000-0xbfff]
[    0.098326] pci 0000:00:1a.0: bridge 32bit mmio: [0xd8000000-0xdfcfffff]
[    0.098341] pci_bus 0000:00: on NUMA node 0
[    0.098345] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.098410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.098464] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]
[    0.098513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.098565] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PE2P._PRT]
[    0.100888] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11 12 14 *15), disabled.
[    0.101036] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.101176] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.101315] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.101455] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.101594] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.101733] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.101869] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15), disabled.
[    0.102009] ACPI: PCI Interrupt Link [LNKP] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.102151] SCSI subsystem initialized
[    0.102185] libata version 3.00 loaded.
[    0.102243] usbcore: registered new interface driver usbfs
[    0.102255] usbcore: registered new interface driver hub
[    0.102274] usbcore: registered new device driver usb
[    0.102365] ACPI: WMI: Mapper loaded
[    0.102366] PCI: Using ACPI for IRQ routing
[    0.102504] Bluetooth: Core ver 2.15
[    0.102524] NET: Registered protocol family 31
[    0.102525] Bluetooth: HCI device and connection manager initialized
[    0.102528] Bluetooth: HCI socket layer initialized
[    0.102530] NetLabel: Initializing
[    0.102531] NetLabel:  domain hash size = 128
[    0.102533] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.102544] NetLabel:  unlabeled traffic allowed by default
[    0.104062] pnp: PnP ACPI init
[    0.104076] ACPI: bus type pnp registered
[    0.108061] pnp 00:09: mem resource (0xc0000000-0xc0000fff) overlaps 0000:00:02.0 BAR 15 (0xc0000000-0xcfffffff), disabling
[    0.108083] pnp 00:09: io resource (0x900-0x91f) overlaps 0000:00:1e.1 BAR 13 (0x900-0x93f), disabling
[    0.108096] pnp 00:09: mem resource (0xc0000000-0xc0000fff) overlaps 0000:04:00.0 BAR 0 (0xc0000000-0xcfffffff), disabling
[    0.109998] pnp: PnP ACPI: found 16 devices
[    0.110000] ACPI: ACPI bus type pnp unregistered
[    0.110003] PnPBIOS: Disabled by ACPI PNP
[    0.110015] system 00:09: ioport range 0x28d-0x28e has been reserved
[    0.110018] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.110021] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.110023] system 00:09: ioport range 0x900-0x9bf could not be reserved
[    0.110026] system 00:09: ioport range 0x9c0-0x9df has been reserved
[    0.110030] system 00:09: iomem range 0xff000000-0xffffffff could not be reserved
[    0.110035] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.110038] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.110042] system 00:0d: ioport range 0xc00-0xc0f has been reserved
[    0.110045] system 00:0d: ioport range 0xd00-0xd0f has been reserved
[    0.110047] system 00:0d: ioport range 0xa20-0xa2f has been reserved
[    0.110050] system 00:0d: ioport range 0xa30-0xa3f has been reserved
[    0.110054] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.110058] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.110061] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[    0.110064] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.110067] system 00:0f: iomem range 0x100000-0x5fffffff could not be reserved
[    0.110069] system 00:0f: iomem range 0xfff80000-0xffffffff has been reserved
[    0.144709] AppArmor: AppArmor Filesystem Enabled
[    0.144740] pci 0000:00:02.0: PCI bridge, secondary bus 0000:04
[    0.144743] pci 0000:00:02.0:   IO window: 0xe000-0xefff
[    0.144746] pci 0000:00:02.0:   MEM window: 0xdff00000-0xdfffffff
[    0.144750] pci 0000:00:02.0:   PREFETCH window: 0x000000c0000000-0x000000cfffffff
[    0.144754] pci 0000:00:05.0: PCI bridge, secondary bus 0000:03
[    0.144757] pci 0000:00:05.0:   IO window: 0xd000-0xdfff
[    0.144760] pci 0000:00:05.0:   MEM window: 0xdfe00000-0xdfefffff
[    0.144763] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.144765] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.144768] pci 0000:00:06.0:   IO window: 0xc000-0xcfff
[    0.144771] pci 0000:00:06.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.144774] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.144777] pci 0000:00:1a.0: PCI bridge, secondary bus 0000:01
[    0.144780] pci 0000:00:1a.0:   IO window: 0xb000-0xbfff
[    0.144785] pci 0000:00:1a.0:   MEM window: 0xd8000000-0xdfcfffff
[    0.144788] pci 0000:00:1a.0:   PREFETCH window: disabled
[    0.144798] pci 0000:00:02.0: setting latency timer to 64
[    0.144803] pci 0000:00:05.0: setting latency timer to 64
[    0.144808] pci 0000:00:06.0: setting latency timer to 64
[    0.144814] pci 0000:00:1a.0: setting latency timer to 64
[    0.144818] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.144820] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.144823] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.144825] pci_bus 0000:04: resource 1 mem: [0xdff00000-0xdfffffff]
[    0.144827] pci_bus 0000:04: resource 2 pref mem [0xc0000000-0xcfffffff]
[    0.144830] pci_bus 0000:03: resource 0 io:  [0xd000-0xdfff]
[    0.144832] pci_bus 0000:03: resource 1 mem: [0xdfe00000-0xdfefffff]
[    0.144835] pci_bus 0000:02: resource 0 io:  [0xc000-0xcfff]
[    0.144837] pci_bus 0000:02: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.144839] pci_bus 0000:01: resource 0 io:  [0xb000-0xbfff]
[    0.144842] pci_bus 0000:01: resource 1 mem: [0xd8000000-0xdfcfffff]
[    0.144873] NET: Registered protocol family 2
[    0.144955] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.145316] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.146295] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.147219] TCP: Hash tables configured (established 131072 bind 65536)
[    0.147222] TCP reno registered
[    0.147321] NET: Registered protocol family 1
[    0.147387] Trying to unpack rootfs image as initramfs...
[    0.148024] Switched to high resolution mode on CPU 0
[    0.333611] Freeing initrd memory: 7709k freed
[    0.341816] cpufreq-nforce2: No nForce2 chipset.
[    0.341840] Scanning for low memory corruption every 60 seconds
[    0.341940] audit: initializing netlink socket (disabled)
[    0.341958] type=2000 audit(1266940768.340:1): initialized
[    0.349602] highmem bounce pool size: 64 pages
[    0.349607] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.350729] VFS: Disk quotas dquot_6.5.2
[    0.350775] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.351215] fuse init (API version 7.12)
[    0.351283] msgmni has been set to 1718
[    0.351433] alg: No test for stdrng (krng)
[    0.351442] io scheduler noop registered
[    0.351444] io scheduler anticipatory registered
[    0.351446] io scheduler deadline registered
[    0.351478] io scheduler cfq registered (default)
[    0.808060] pci 0000:04:00.0: Boot video device
[    0.808150]   alloc irq_desc for 24 on node -1
[    0.808152]   alloc kstat_irqs on node -1
[    0.808160] pcieport-driver 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.808165] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    0.808244]   alloc irq_desc for 25 on node -1
[    0.808246]   alloc kstat_irqs on node -1
[    0.808250] pcieport-driver 0000:00:05.0: irq 25 for MSI/MSI-X
[    0.808255] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    0.808328]   alloc irq_desc for 26 on node -1
[    0.808330]   alloc kstat_irqs on node -1
[    0.808334] pcieport-driver 0000:00:06.0: irq 26 for MSI/MSI-X
[    0.808339] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    0.808413] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
[    0.808418] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
[    0.808422] aer 0000:00:06.0:pcie02: AER service couldn't init device: no _OSC support
[    0.808429] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.808447] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.808548] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.808552] ACPI: Power Button [PWRF]
[    0.808596] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.808598] ACPI: Power Button [PWRB]
[    0.808825] processor LNXCPU:00: registered as cooling_device0
[    0.808828] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.811795] isapnp: Scanning for PnP cards...
[    1.166119] isapnp: No Plug & Play device found
[    1.166934] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.167053] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.167361] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.168172] brd: module loaded
[    1.168534] loop: module loaded
[    1.168589] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.168646] ahci 0000:00:1f.1: version 3.0
[    1.168658]   alloc irq_desc for 19 on node -1
[    1.168659]   alloc kstat_irqs on node -1
[    1.168664] ahci 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.168694]   alloc irq_desc for 27 on node -1
[    1.168696]   alloc kstat_irqs on node -1
[    1.168704] ahci 0000:00:1f.1: irq 27 for MSI/MSI-X
[    1.168798] ahci 0000:00:1f.1: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.168801] ahci 0000:00:1f.1: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    1.169331] scsi0 : ahci
[    1.169420] scsi1 : ahci
[    1.169467] scsi2 : ahci
[    1.169506] scsi3 : ahci
[    1.169599] ata1: SATA max UDMA/133 abar m1024@0xd7fffc00 port 0xd7fffd00 irq 27
[    1.169603] ata2: SATA max UDMA/133 abar m1024@0xd7fffc00 port 0xd7fffd80 irq 27
[    1.169606] ata3: SATA max UDMA/133 abar m1024@0xd7fffc00 port 0xd7fffe00 irq 27
[    1.169609] ata4: SATA max UDMA/133 abar m1024@0xd7fffc00 port 0xd7fffe80 irq 27
[    1.169694] sata_sil24 0000:03:00.0: version 1.1
[    1.169704]   alloc irq_desc for 17 on node -1
[    1.169706]   alloc kstat_irqs on node -1
[    1.169710] sata_sil24 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.169793] sata_sil24 0000:03:00.0: setting latency timer to 64
[    1.170160] scsi4 : sata_sil24
[    1.170231] scsi5 : sata_sil24
[    1.170262] ata5: SATA max UDMA/100 host m128@0xdfeffc00 port 0xdfef8000 irq 17
[    1.170266] ata6: SATA max UDMA/100 host m128@0xdfeffc00 port 0xdfefa000 irq 17
[    1.170353] pata_ali 0000:00:1f.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.170512] scsi6 : pata_ali
[    1.170582] scsi7 : pata_ali
[    1.172775] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.172778] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.173372] Fixed MDIO Bus: probed
[    1.173403] PPP generic driver version 2.4.2
[    1.173506] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.173520]   alloc irq_desc for 23 on node -1
[    1.173522]   alloc kstat_irqs on node -1
[    1.173526] ehci_hcd 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.173536] ehci_hcd 0000:00:1c.3: EHCI Host Controller
[    1.173578] ehci_hcd 0000:00:1c.3: new USB bus registered, assigned bus number 1
[    1.196024] ehci_hcd 0000:00:1c.3: debug port 1
[    1.196048] ehci_hcd 0000:00:1c.3: irq 23, io mem 0xd7fff800
[    1.208017] ehci_hcd 0000:00:1c.3: USB 2.0 started, EHCI 1.00
[    1.208077] usb usb1: configuration #1 chosen from 1 choice
[    1.208101] hub 1-0:1.0: USB hub found
[    1.208111] hub 1-0:1.0: 8 ports detected
[    1.208181] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.208192] ohci_hcd 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.208200] ohci_hcd 0000:00:1c.0: OHCI Host Controller
[    1.208223] ohci_hcd 0000:00:1c.0: new USB bus registered, assigned bus number 2
[    1.208237] ohci_hcd 0000:00:1c.0: irq 17, io mem 0xd7ffc000
[    1.266048] usb usb2: configuration #1 chosen from 1 choice
[    1.266071] hub 2-0:1.0: USB hub found
[    1.266080] hub 2-0:1.0: 3 ports detected
[    1.266115]   alloc irq_desc for 18 on node -1
[    1.266117]   alloc kstat_irqs on node -1
[    1.266120] ohci_hcd 0000:00:1c.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.266127] ohci_hcd 0000:00:1c.1: OHCI Host Controller
[    1.266160] ohci_hcd 0000:00:1c.1: new USB bus registered, assigned bus number 3
[    1.266189] ohci_hcd 0000:00:1c.1: irq 18, io mem 0xd7ffd000
[    1.322048] usb usb3: configuration #1 chosen from 1 choice
[    1.322075] hub 3-0:1.0: USB hub found
[    1.322083] hub 3-0:1.0: 3 ports detected
[    1.322117] ohci_hcd 0000:00:1c.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    1.322124] ohci_hcd 0000:00:1c.2: OHCI Host Controller
[    1.322146] ohci_hcd 0000:00:1c.2: new USB bus registered, assigned bus number 4
[    1.322176] ohci_hcd 0000:00:1c.2: irq 19, io mem 0xd7ffe000
[    1.344497] ata7.00: ATA-7: HDT722525DLAT80, V44OA96A, max UDMA/133
[    1.344499] ata7.00: 488397168 sectors, multi 16: LBA48 
[    1.344734] ata7.01: ATA-6: ST340810A, 3.39, max UDMA/100
[    1.344736] ata7.01: 78165360 sectors, multi 16: LBA 
[    1.360412] ata7.00: configured for UDMA/133
[    1.378052] usb usb4: configuration #1 chosen from 1 choice
[    1.378071] hub 4-0:1.0: USB hub found
[    1.378080] hub 4-0:1.0: 3 ports detected
[    1.378119] uhci_hcd: USB Universal Host Controller Interface driver
[    1.378191] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.378193] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.378483] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.378803] mice: PS/2 mouse device common for all mice
[    1.378878] rtc_cmos 00:02: RTC can wake from S4
[    1.378924] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.378959] rtc0: alarms up to one month, 114 bytes nvram
[    1.379037] device-mapper: uevent: version 1.0.3
[    1.379104] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    1.379145] ata7.01: configured for UDMA/100
[    1.379181] device-mapper: multipath: version 1.1.0 loaded
[    1.379184] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.379284] EISA: Probing bus 0 at eisa.0
[    1.379308] Cannot allocate resource for EISA slot 5
[    1.379323] EISA: Detected 0 cards.
[    1.379366] cpuidle: using governor ladder
[    1.379368] cpuidle: using governor menu
[    1.379772] TCP cubic registered
[    1.379904] NET: Registered protocol family 10
[    1.380279] lo: Disabled Privacy Extensions
[    1.380524] NET: Registered protocol family 17
[    1.380537] Bluetooth: L2CAP ver 2.13
[    1.380538] Bluetooth: L2CAP socket layer initialized
[    1.380541] Bluetooth: SCO (Voice Link) ver 0.6
[    1.380542] Bluetooth: SCO socket layer initialized
[    1.380575] Bluetooth: RFCOMM TTY layer initialized
[    1.380577] Bluetooth: RFCOMM socket layer initialized
[    1.380579] Bluetooth: RFCOMM ver 1.11
[    1.380588] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 4000+ processors (1 cpu cores) (version 2.20.00)
[    1.388726] [Firmware Bug]: powernow-k8: No PSB or ACPI _PSS objects
[    1.388761] Using IPI No-Shortcut mode
[    1.388812] PM: Resume from disk failed.
[    1.388823] registered taskstats version 1
[    1.388936]   Magic number: 14:735:993
[    1.389031] rtc_cmos 00:02: setting system clock to 2010-02-23 15:59:30 UTC (1266940770)
[    1.389034] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.389036] EDD information not available.
[    1.404276] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.488026] ata4: SATA link down (SStatus 0 SControl 300)
[    1.488047] ata3: SATA link down (SStatus 0 SControl 300)
[    1.488066] ata1: SATA link down (SStatus 0 SControl 300)
[    1.488084] ata2: SATA link down (SStatus 0 SControl 300)
[    1.632019] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    1.764880] usb 1-2: configuration #1 chosen from 1 choice
[    2.068017] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    2.289110] usb 2-1: configuration #1 chosen from 1 choice
[    3.252034] ata5: SATA link down (SStatus 0 SControl 0)
[    5.332034] ata6: SATA link down (SStatus 0 SControl 0)
[    5.332138] scsi 6:0:0:0: Direct-Access     ATA      HDT722525DLAT80  V44O PQ: 0 ANSI: 5
[    5.332219] sd 6:0:0:0: Attached scsi generic sg0 type 0
[    5.332270] scsi 6:0:1:0: Direct-Access     ATA      ST340810A        3.39 PQ: 0 ANSI: 5
[    5.332342] sd 6:0:1:0: Attached scsi generic sg1 type 0
[    5.332370] sd 6:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    5.332405] sd 6:0:0:0: [sda] Write Protect is off
[    5.332408] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.332425] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.332518]  sda:
[    5.341154] sd 6:0:1:0: [sdb] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    5.341184] sd 6:0:1:0: [sdb] Write Protect is off
[    5.341187] sd 6:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    5.341203] sd 6:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.341284]  sdb: sda1 sda2 < sdb1
[    5.384117]  sda5 > sda3 sda4
[    5.384316] sd 6:0:0:0: [sda] Attached SCSI disk
[    5.384373] sd 6:0:1:0: [sdb] Attached SCSI disk
[    5.496367] ata8.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.04, max UDMA/66
[    5.496384] ata8.00: WARNING: ATAPI DMA disabled for reliablity issues.  It can be enabled
[    5.496386] ata8.00: WARNING: via pata_ali.atapi_dma modparam or corresponding sysfs node.
[    5.512297] ata8.00: configured for UDMA/66
[    5.514353] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.04 PQ: 0 ANSI: 5
[    5.516046] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.516049] Uniform CD-ROM driver Revision: 3.20
[    5.516107] sr 7:0:0:0: Attached scsi CD-ROM sr0
[    5.516140] sr 7:0:0:0: Attached scsi generic sg2 type 5
[    5.516157] Freeing unused kernel memory: 540k freed
[    5.516567] Write protecting the kernel text: 4568k
[    5.516593] Write protecting the kernel read-only data: 1836k
[    5.623226] Linux agpgart interface v0.103
[    5.658635] Floppy drive(s): fd0 is 1.44M
[    5.661997] sky2 driver version 1.23
[    5.662026] sky2 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.662037] sky2 0000:02:00.0: setting latency timer to 64
[    5.662067] sky2 0000:02:00.0: Yukon-2 EC chip revision 2
[    5.662145]   alloc irq_desc for 28 on node -1
[    5.662148]   alloc kstat_irqs on node -1
[    5.662160] sky2 0000:02:00.0: irq 28 for MSI/MSI-X
[    5.662683] sky2 eth0: addr 00:17:31:95:33:1b
[    5.703640] FDC 0 is a post-1991 82077
[    5.757463] [drm] Initialized drm 1.1.0 20060810
[    5.796570] [drm] radeon default to kernel modesetting DISABLED.
[    5.797429] pci 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.797434] pci 0000:04:00.0: setting latency timer to 64
[    5.797564] [drm] Initialized radeon 1.31.0 20080528 for 0000:04:00.0 on minor 0
[    5.809557]   alloc irq_desc for 20 on node -1
[    5.809560]   alloc kstat_irqs on node -1
[    5.809567] ohci1394 0000:01:13.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    5.815731] usbcore: registered new interface driver hiddev
[    5.820868] Initializing USB Mass Storage driver...
[    5.821016] scsi8 : SCSI emulation for USB Mass Storage devices
[    5.821222] usbcore: registered new interface driver usb-storage
[    5.821225] USB Mass Storage support registered.
[    5.821329] usb-storage: device found at 3
[    5.821330] usb-storage: waiting for device to settle before scanning
[    5.822530] input: Saitek GM3200 Laser mouse as /devices/pci0000:00/0000:00:1c.0/usb2/2-1/2-1:1.0/input/input4
[    5.822597] generic-usb 0003:06A3:0004.0001: input,hidraw0: USB HID v1.10 Mouse [Saitek GM3200 Laser mouse] on usb-0000:00:1c.0-1/input0
[    5.822609] usbcore: registered new interface driver usbhid
[    5.822612] usbhid: v2.6:USB HID core driver
[    5.864070] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[dfcfb800-dfcfbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.864258]   alloc irq_desc for 21 on node -1
[    5.864260]   alloc kstat_irqs on node -1
[    5.864267] skge 0000:01:14.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.864321] skge 1.13 addr 0xdfcfc000 irq 21 chip Yukon-Lite rev 9
[    5.864917] skge eth1: addr 00:17:31:95:2f:97
[    6.725414] xor: automatically using best checksumming function: pIII_sse
[    6.744008]    pIII_sse  :  7253.000 MB/sec
[    6.744011] xor: using function: pIII_sse (7253.000 MB/sec)
[    6.746520] device-mapper: dm-raid45: initialized v0.2594b
[    7.140116] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000a9f7e2]
[    7.156329] PM: Starting manual resume from disk
[    7.156332] PM: Resume from partition 8:5
[    7.156333] PM: Checking hibernation image.
[    7.156469] PM: Resume from disk failed.
[    7.181556] EXT4-fs (sda4): barriers enabled
[    7.191567] kjournald2 starting: pid 405, dev sda4:8, commit interval 5 seconds
[    7.191576] EXT4-fs (sda4): delayed allocation enabled
[    7.191579] EXT4-fs: file extents enabled
[    7.201338] EXT4-fs: mballoc enabled
[    7.201350] EXT4-fs (sda4): mounted filesystem with ordered data mode
[    7.723248] type=1505 audit(1266940776.830:2): operation="profile_load" pid=428 name=/usr/share/gdm/guest-session/Xsession
[    7.735951] type=1505 audit(1266940776.842:3): operation="profile_load" pid=429 name=/sbin/dhclient3
[    7.736207] type=1505 audit(1266940776.846:4): operation="profile_load" pid=429 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.736347] type=1505 audit(1266940776.846:5): operation="profile_load" pid=429 name=/usr/lib/connman/scripts/dhclient-script
[    7.784421] type=1505 audit(1266940776.894:6): operation="profile_load" pid=430 name=/usr/bin/evince
[    7.788712] type=1505 audit(1266940776.898:7): operation="profile_load" pid=430 name=/usr/bin/evince-previewer
[    7.791213] type=1505 audit(1266940776.898:8): operation="profile_load" pid=430 name=/usr/bin/evince-thumbnailer
[    7.808288] type=1505 audit(1266940776.918:9): operation="profile_load" pid=432 name=/usr/lib/cups/backend/cups-pdf
[    7.808595] type=1505 audit(1266940776.918:10): operation="profile_load" pid=432 name=/usr/sbin/cupsd
[    7.810246] type=1505 audit(1266940776.918:11): operation="profile_load" pid=433 name=/usr/sbin/tcpdump
[   10.820565] usb-storage: device scan complete
[   10.821037] scsi 8:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[   10.821373] sd 8:0:0:0: Attached scsi generic sg3 type 0
[   10.822018] sd 8:0:0:0: [sdc] 15695871 512-byte logical blocks: (8.03 GB/7.48 GiB)
[   10.822514] sd 8:0:0:0: [sdc] Write Protect is off
[   10.822517] sd 8:0:0:0: [sdc] Mode Sense: 45 00 00 08
[   10.822519] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[   10.824139] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[   10.824142]  sdc: sdc1
[   10.826139] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[   10.826141] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[   15.896550] udev: starting version 147
[   15.913372] Adding 2996112k swap on /dev/sda5.  Priority:-1 extents:1 across:2996112k 
[   15.980659] lp: driver loaded but no devices found
[   16.086115] parport_pc 00:06: reported by Plug and Play ACPI
[   16.086195] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   16.090474] ali1535_smbus 0000:00:1e.1: ALI1535_smb region uninitialized - upgrade BIOS?
[   16.090478] ali1535_smbus 0000:00:1e.1: ALI1535 not detected, module not inserted.
[   16.090988] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   16.090992] ali15x3_smbus 0000:00:1e.1: ALI15X3 not detected, module not inserted.
[   16.109304] EXT4-fs (sda4): internal journal on sda4:8
[   16.152075] gameport: NS558 PnP Gameport is pnp00:07/gameport0, io 0x201, speed 596kHz
[   16.194392] lp0: using parport0 (interrupt-driven).
[   16.347367]   alloc irq_desc for 22 on node -1
[   16.347371]   alloc kstat_irqs on node -1
[   16.347378] HDA Intel 0000:00:1d.0: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   16.419443] ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.421187] ppdev: user-space parallel port driver
[   16.469435] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.469658] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   16.469661] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   16.469663] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   16.501184] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1d.0/input/input5
[   16.508745] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.561122] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   16.588829] udev: renamed network interface eth1 to eth0
[   16.591648] SB-XFi 0000:01:11.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.890032] udev: renamed network interface eth0_rename to eth1
[   17.208152] kjournald starting.  Commit interval 5 seconds
[   17.208166] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   17.212424] EXT3 FS on sdb1, internal journal
[   17.212429] EXT3-fs: mounted filesystem with writeback data mode.
[   17.297998] sky2 eth1: enabling interface
[   17.298184] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   17.317404] CIFS: Unknown mount option cp850
[   17.337608]  CIFS VFS: Error connecting to socket. Aborting operation
[   17.337615]  CIFS VFS: cifs_mount failed w/return code = -101
[   17.345345] skge eth0: enabling interface
[   17.361930] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.502313] type=1505 audit(1266940786.610:12): operation="profile_replace" pid=1217 name=/usr/share/gdm/guest-session/Xsession
[   17.509324] type=1505 audit(1266940786.618:13): operation="profile_replace" pid=1218 name=/sbin/dhclient3
[   17.509581] type=1505 audit(1266940786.618:14): operation="profile_replace" pid=1218 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.509729] type=1505 audit(1266940786.618:15): operation="profile_replace" pid=1218 name=/usr/lib/connman/scripts/dhclient-script
[   17.528998] type=1505 audit(1266940786.638:16): operation="profile_replace" pid=1219 name=/usr/bin/evince
[   17.541357] type=1505 audit(1266940786.650:17): operation="profile_replace" pid=1219 name=/usr/bin/evince-previewer
[   17.552076] type=1505 audit(1266940786.662:18): operation="profile_replace" pid=1219 name=/usr/bin/evince-thumbnailer
[   17.566044] type=1505 audit(1266940786.674:19): operation="profile_replace" pid=1221 name=/usr/lib/cups/backend/cups-pdf
[   17.566361] type=1505 audit(1266940786.674:20): operation="profile_replace" pid=1221 name=/usr/sbin/cupsd
[   17.570113] type=1505 audit(1266940786.678:21): operation="profile_replace" pid=1222 name=/usr/sbin/tcpdump
[   17.584018] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x00eb2000
[   18.376028] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.376034] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.376039] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.376045] end_request: I/O error, dev sr0, sector 1376896
[   18.381066] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.381070] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.381074] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.381080] end_request: I/O error, dev sr0, sector 1376896
[   18.384157] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.384161] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.384165] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.384171] end_request: I/O error, dev sr0, sector 1377072
[   18.387053] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.387058] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.387061] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.387067] end_request: I/O error, dev sr0, sector 1377072
[   18.392262] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.392267] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.392271] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.392277] end_request: I/O error, dev sr0, sector 1377080
[   18.397077] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.397082] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.397086] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.397092] end_request: I/O error, dev sr0, sector 1377080
[   18.402204] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.402210] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.402213] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.402220] end_request: I/O error, dev sr0, sector 1377080
[   18.411523] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.411529] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.411533] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.411540] end_request: I/O error, dev sr0, sector 1377080
[   18.416328] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.416334] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.416337] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.416343] end_request: I/O error, dev sr0, sector 1377080
[   18.422688] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.422694] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.422698] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.422704] end_request: I/O error, dev sr0, sector 1377080
[   18.427170] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.427175] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.427179] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.427185] end_request: I/O error, dev sr0, sector 1377080
[   18.432603] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.432609] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.432613] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.432620] end_request: I/O error, dev sr0, sector 1377024
[   18.434896] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.434901] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.434905] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.434911] end_request: I/O error, dev sr0, sector 1377072
[   18.438735] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.438740] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.438744] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.438750] end_request: I/O error, dev sr0, sector 1377080
[   18.444489] sr 7:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   18.444494] sr 7:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[   18.444498] sr 7:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[   18.444504] end_request: I/O error, dev sr0, sector 1377080
[   18.957009] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   18.957013] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
[   18.957015] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   18.957016] vboxdrv: the usage of hardware performance counters by
[   18.957017] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   18.957021] vboxdrv: Found 1 processor cores.
[   18.957125] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   18.957127] vboxdrv: Successfully loaded version 3.0.8_OSE (interface 0x000e0000).
[   19.356452] CIFS: Unknown mount option cp850
[   19.356477]  CIFS VFS: Error connecting to socket. Aborting operation
[   19.356481]  CIFS VFS: cifs_mount failed w/return code = -101
[   20.504891] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control rx
[   20.505085] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   21.947655] [drm] Setting GART location based on new memory map
[   21.948578] [drm] Loading R500 Microcode
[   21.948601] [drm] Num pipes: 4
[   21.948608] [drm] writeback test succeeded in 1 usecs
[   31.340015] eth1: no IPv6 routers present
[   33.999616] CIFS: Unknown mount option cp850
[   34.003756]  CIFS VFS: Error connecting to socket. Aborting operation
[   34.003764]  CIFS VFS: cifs_mount failed w/return code = -111
[   34.003858] CIFS: Unknown mount option cp850
[   34.004583]  CIFS VFS: Error connecting to socket. Aborting operation
[   34.004586]  CIFS VFS: cifs_mount failed w/return code = -111
[   34.004635] CIFS: Unknown mount option cp850
[   34.005037]  CIFS VFS: Error connecting to socket. Aborting operation
[   34.005040]  CIFS VFS: cifs_mount failed w/return code = -111
[  369.618202] CIFS: Unknown mount option cp850
[  385.700183] UDF-fs: No VRS found
[  385.700188] UDF-fs: No partition found (1)
[  388.884097] ISO 9660 Extensions: Microsoft Joliet Level 3
[  389.081804] ISOFS: changing to secondary root
[ 3491.483887] padlock: VIA PadLock not detected.
[ 3509.539083] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[ 3553.112061] __ratelimit: 15 callbacks suppressed
[ 3553.112065] Xorg: page allocation failure. order:4, mode:0x40d0
[ 3553.112069] Pid: 2460, comm: Xorg Not tainted 2.6.31-17-generic #54-Ubuntu
[ 3553.112071] Call Trace:
[ 3553.112080]  [<c056e92c>] ? printk+0x18/0x1c
[ 3553.112087]  [<c01b82e0>] __alloc_pages_slowpath+0x340/0x480
[ 3553.112091]  [<c01b852f>] __alloc_pages_nodemask+0x10f/0x120
[ 3553.112094]  [<c01b8587>] __get_free_pages+0x17/0x30
[ 3553.112100]  [<c01e089f>] __kmalloc+0xdf/0x180
[ 3553.112106]  [<c0127bb8>] ? default_spin_lock_flags+0x8/0x10
[ 3553.112170]  [<f8219e38>] radeon_cp_cmdbuf+0xa98/0xbf0 [radeon]
[ 3553.112208]  [<f8116822>] ? drm_lock+0x252/0x350 [drm]
[ 3553.112229]  [<f81136c0>] drm_ioctl+0x180/0x360 [drm]
[ 3553.112251]  [<f82193a0>] ? radeon_cp_cmdbuf+0x0/0xbf0 [radeon]
[ 3553.112255]  [<c015c170>] ? autoremove_wake_function+0x0/0x40
[ 3553.112259]  [<c01603c2>] ? hrtimer_start+0x22/0x30
[ 3553.112265]  [<c02c801f>] ? security_file_permission+0xf/0x20
[ 3553.112274]  [<c01f51f3>] vfs_ioctl+0x73/0x90
[ 3553.112277]  [<c01f54c1>] do_vfs_ioctl+0x71/0x310
[ 3553.112279]  [<c01f57bf>] sys_ioctl+0x5f/0x80
[ 3553.112283]  [<c010336c>] syscall_call+0x7/0xb
[ 3553.112284] Mem-Info:
[ 3553.112286] DMA per-cpu:
[ 3553.112288] CPU    0: hi:    0, btch:   1 usd:   0
[ 3553.112290] Normal per-cpu:
[ 3553.112291] CPU    0: hi:  186, btch:  31 usd:   0
[ 3553.112293] HighMem per-cpu:
[ 3553.112295] CPU    0: hi:  186, btch:  31 usd:   0
[ 3553.112298] Active_anon:87716 active_file:70267 inactive_anon:87783
[ 3553.112300]  inactive_file:72285 unevictable:1606 dirty:11160 writeback:19 unstable:0
[ 3553.112301]  free:7661 slab:8185 mapped:55408 pagetables:1598 bounce:0
[ 3553.112305] DMA free:3540kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:1248kB inactive_file:3008kB unevictable:0kB present:15804kB pages_scanned:0 all_unreclaimable? no
[ 3553.112308] lowmem_reserve[]: 0 865 1507 1507
[ 3553.112313] Normal free:25840kB min:3728kB low:4660kB high:5592kB active_anon:180052kB inactive_anon:180144kB active_file:152792kB inactive_file:158164kB unevictable:4988kB present:885944kB pages_scanned:0 all_unreclaimable? no
[ 3553.112316] lowmem_reserve[]: 0 0 5140 5140
[ 3553.112321] HighMem free:1264kB min:512kB low:1204kB high:1896kB active_anon:170812kB inactive_anon:170988kB active_file:127028kB inactive_file:127968kB unevictable:1436kB present:657992kB pages_scanned:0 all_unreclaimable? no
[ 3553.112325] lowmem_reserve[]: 0 0 0 0
[ 3553.112327] DMA: 11*4kB 7*8kB 3*16kB 2*32kB 2*64kB 3*128kB 5*256kB 3*512kB 0*1024kB 0*2048kB 0*4096kB = 3540kB
[ 3553.112335] Normal: 6394*4kB 9*8kB 0*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 25840kB
[ 3553.112342] HighMem: 60*4kB 24*8kB 2*16kB 5*32kB 6*64kB 2*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1264kB
[ 3553.112350] 144360 total pagecache pages
[ 3553.112351] 486 pages in swap cache
[ 3553.112353] Swap cache stats: add 6189, delete 5703, find 23/33
[ 3553.112355] Free swap  = 2978160kB
[ 3553.112357] Total swap = 2996112kB
[ 3553.118952] 393104 pages RAM
[ 3553.118955] 165794 pages HighMem
[ 3553.118956] 51399 pages reserved
[ 3553.118958] 288120 pages shared
[ 3553.118959] 117132 pages non-shared
[ 3553.192817] [drm] Num pipes: 4
[ 3555.826120] VirtualBox[19097]: segfault at 10 ip 00ebb8f6 sp b6b0f140 error 4 in libXt.so.6.0.0[e94000+4f000]
[ 3559.695529] [drm] Setting GART location based on new memory map
[ 3559.696768] [drm] Loading R500 Microcode
[ 3559.696791] [drm] Num pipes: 4
[ 3559.696799] [drm] writeback test succeeded in 1 usecs
[ 3704.140851] device eth1 entered promiscuous mode
[ 3714.392100] Xorg: page allocation failure. order:4, mode:0x40d0
[ 3714.392106] Pid: 19116, comm: Xorg Not tainted 2.6.31-17-generic #54-Ubuntu
[ 3714.392109] Call Trace:
[ 3714.392120]  [<c056e92c>] ? printk+0x18/0x1c
[ 3714.392127]  [<c01b82e0>] __alloc_pages_slowpath+0x340/0x480
[ 3714.392131]  [<c01b852f>] __alloc_pages_nodemask+0x10f/0x120
[ 3714.392134]  [<c01b8587>] __get_free_pages+0x17/0x30
[ 3714.392140]  [<c01e089f>] __kmalloc+0xdf/0x180
[ 3714.392146]  [<c0127bb8>] ? default_spin_lock_flags+0x8/0x10
[ 3714.392212]  [<f8219e38>] radeon_cp_cmdbuf+0xa98/0xbf0 [radeon]
[ 3714.392248]  [<f8116822>] ? drm_lock+0x252/0x350 [drm]
[ 3714.392270]  [<f81136c0>] drm_ioctl+0x180/0x360 [drm]
[ 3714.392291]  [<f82193a0>] ? radeon_cp_cmdbuf+0x0/0xbf0 [radeon]
[ 3714.392296]  [<c015c170>] ? autoremove_wake_function+0x0/0x40
[ 3714.392300]  [<c01603c2>] ? hrtimer_start+0x22/0x30
[ 3714.392305]  [<c02c801f>] ? security_file_permission+0xf/0x20
[ 3714.392314]  [<c01f51f3>] vfs_ioctl+0x73/0x90
[ 3714.392317]  [<c01f54c1>] do_vfs_ioctl+0x71/0x310
[ 3714.392320]  [<c01f57bf>] sys_ioctl+0x5f/0x80
[ 3714.392323]  [<c010336c>] syscall_call+0x7/0xb
[ 3714.392325] Mem-Info:
[ 3714.392327] DMA per-cpu:
[ 3714.392329] CPU    0: hi:    0, btch:   1 usd:   0
[ 3714.392330] Normal per-cpu:
[ 3714.392332] CPU    0: hi:  186, btch:  31 usd:   0
[ 3714.392334] HighMem per-cpu:
[ 3714.392335] CPU    0: hi:  186, btch:  31 usd:   0
[ 3714.392339] Active_anon:86779 active_file:39493 inactive_anon:86865
[ 3714.392340]  inactive_file:69681 unevictable:5762 dirty:4390 writeback:0 unstable:0
[ 3714.392341]  free:39018 slab:7358 mapped:54092 pagetables:1666 bounce:0
[ 3714.392345] DMA free:3536kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:2468kB inactive_file:1788kB unevictable:0kB present:15804kB pages_scanned:0 all_unreclaimable? no
[ 3714.392348] lowmem_reserve[]: 0 865 1507 1507
[ 3714.392354] Normal free:33416kB min:3728kB low:4660kB high:5592kB active_anon:179864kB inactive_anon:180576kB active_file:115344kB inactive_file:132396kB unevictable:22372kB present:885944kB pages_scanned:0 all_unreclaimable? no
[ 3714.392357] lowmem_reserve[]: 0 0 5140 5140
[ 3714.392362] HighMem free:119120kB min:512kB low:1204kB high:1896kB active_anon:167252kB inactive_anon:166884kB active_file:40160kB inactive_file:144540kB unevictable:676kB present:657992kB pages_scanned:0 all_unreclaimable? no
[ 3714.392365] lowmem_reserve[]: 0 0 0 0
[ 3714.392368] DMA: 12*4kB 8*8kB 4*16kB 1*32kB 2*64kB 3*128kB 5*256kB 3*512kB 0*1024kB 0*2048kB 0*4096kB = 3536kB
[ 3714.392375] Normal: 4284*4kB 2005*8kB 3*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 33416kB
[ 3714.392383] HighMem: 74*4kB 49*8kB 30*16kB 376*32kB 1039*64kB 286*128kB 11*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 119120kB
[ 3714.392391] 112576 total pagecache pages
[ 3714.392392] 2151 pages in swap cache
[ 3714.392394] Swap cache stats: add 15165, delete 13014, find 2082/2320
[ 3714.392396] Free swap  = 2978008kB
[ 3714.392397] Total swap = 2996112kB
[ 3714.398744] 393104 pages RAM
[ 3714.398746] 165794 pages HighMem
[ 3714.398748] 51847 pages reserved
[ 3714.398749] 283347 pages shared
[ 3714.398750] 92315 pages non-shared
[ 3714.611963] [drm] Num pipes: 4
[ 3715.886304] device eth1 left promiscuous mode
[ 3717.144155] [drm] Setting GART location based on new memory map
[ 3717.145405] [drm] Loading R500 Microcode
[ 3717.145429] [drm] Num pipes: 4
[ 3717.145436] [drm] writeback test succeeded in 1 usecs
[ 3792.604041] Xorg: page allocation failure. order:4, mode:0x40d0
[ 3792.604047] Pid: 19719, comm: Xorg Not tainted 2.6.31-17-generic #54-Ubuntu
[ 3792.604049] Call Trace:
[ 3792.604058]  [<c056e92c>] ? printk+0x18/0x1c
[ 3792.604065]  [<c01b82e0>] __alloc_pages_slowpath+0x340/0x480
[ 3792.604068]  [<c01b852f>] __alloc_pages_nodemask+0x10f/0x120
[ 3792.604072]  [<c01b8587>] __get_free_pages+0x17/0x30
[ 3792.604077]  [<c01e089f>] __kmalloc+0xdf/0x180
[ 3792.604081]  [<c0127bb8>] ? default_spin_lock_flags+0x8/0x10
[ 3792.604137]  [<f8219e38>] radeon_cp_cmdbuf+0xa98/0xbf0 [radeon]
[ 3792.604169]  [<f8116822>] ? drm_lock+0x252/0x350 [drm]
[ 3792.604191]  [<f81136c0>] drm_ioctl+0x180/0x360 [drm]
[ 3792.604213]  [<f82193a0>] ? radeon_cp_cmdbuf+0x0/0xbf0 [radeon]
[ 3792.604218]  [<c015c170>] ? autoremove_wake_function+0x0/0x40
[ 3792.604222]  [<c01603c2>] ? hrtimer_start+0x22/0x30
[ 3792.604228]  [<c02c801f>] ? security_file_permission+0xf/0x20
[ 3792.604236]  [<c01f51f3>] vfs_ioctl+0x73/0x90
[ 3792.604239]  [<c01f54c1>] do_vfs_ioctl+0x71/0x310
[ 3792.604242]  [<c01f57bf>] sys_ioctl+0x5f/0x80
[ 3792.604245]  [<c010336c>] syscall_call+0x7/0xb
[ 3792.604247] Mem-Info:
[ 3792.604249] DMA per-cpu:
[ 3792.604251] CPU    0: hi:    0, btch:   1 usd:   0
[ 3792.604253] Normal per-cpu:
[ 3792.604254] CPU    0: hi:  186, btch:  31 usd:   0
[ 3792.604256] HighMem per-cpu:
[ 3792.604258] CPU    0: hi:  186, btch:  31 usd:   0
[ 3792.604261] Active_anon:79826 active_file:80637 inactive_anon:80189
[ 3792.604263]  inactive_file:78402 unevictable:1144 dirty:7536 writeback:2796 unstable:0
[ 3792.604264]  free:7846 slab:7340 mapped:53532 pagetables:1646 bounce:0
[ 3792.604268] DMA free:3528kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:2468kB inactive_file:1788kB unevictable:0kB present:15804kB pages_scanned:0 all_unreclaimable? no
[ 3792.604271] lowmem_reserve[]: 0 865 1507 1507
[ 3792.604276] Normal free:26692kB min:3728kB low:4660kB high:5592kB active_anon:165520kB inactive_anon:166648kB active_file:159996kB inactive_file:160240kB unevictable:4316kB present:885944kB pages_scanned:0 all_unreclaimable? no
[ 3792.604279] lowmem_reserve[]: 0 0 5140 5140
[ 3792.604284] HighMem free:1164kB min:512kB low:1204kB high:1896kB active_anon:153784kB inactive_anon:154108kB active_file:160084kB inactive_file:151580kB unevictable:260kB present:657992kB pages_scanned:0 all_unreclaimable? no
[ 3792.604287] lowmem_reserve[]: 0 0 0 0
[ 3792.604290] DMA: 12*4kB 7*8kB 4*16kB 1*32kB 2*64kB 3*128kB 5*256kB 3*512kB 0*1024kB 0*2048kB 0*4096kB = 3528kB
[ 3792.604298] Normal: 6309*4kB 100*8kB 17*16kB 6*32kB 1*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 26692kB
[ 3792.604305] HighMem: 105*4kB 19*8kB 5*16kB 2*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1164kB
[ 3792.604313] 161509 total pagecache pages
[ 3792.604314] 1358 pages in swap cache
[ 3792.604316] Swap cache stats: add 17206, delete 15848, find 3545/3807
[ 3792.604318] Free swap  = 2978552kB
[ 3792.604319] Total swap = 2996112kB
[ 3792.611065] 393104 pages RAM
[ 3792.611069] 165794 pages HighMem
[ 3792.611070] 51399 pages reserved
[ 3792.611071] 280910 pages shared
[ 3792.611073] 125847 pages non-shared
[ 3792.677823] [drm] Num pipes: 4
[ 3796.147848] [drm] Setting GART location based on new memory map
[ 3796.149263] [drm] Loading R500 Microcode
[ 3796.149286] [drm] Num pipes: 4
[ 3796.149294] [drm] writeback test succeeded in 1 usecs
[ 4704.532261] Xorg: page allocation failure. order:4, mode:0x40d0
[ 4704.532267] Pid: 20244, comm: Xorg Not tainted 2.6.31-17-generic #54-Ubuntu
[ 4704.532270] Call Trace:
[ 4704.532280]  [<c056e92c>] ? printk+0x18/0x1c
[ 4704.532287]  [<c01b82e0>] __alloc_pages_slowpath+0x340/0x480
[ 4704.532291]  [<c01b852f>] __alloc_pages_nodemask+0x10f/0x120
[ 4704.532294]  [<c01b8587>] __get_free_pages+0x17/0x30
[ 4704.532299]  [<c01e089f>] __kmalloc+0xdf/0x180
[ 4704.532305]  [<c0127bb8>] ? default_spin_lock_flags+0x8/0x10
[ 4704.532371]  [<f8219e38>] radeon_cp_cmdbuf+0xa98/0xbf0 [radeon]
[ 4704.532408]  [<f8116822>] ? drm_lock+0x252/0x350 [drm]
[ 4704.532429]  [<f81136c0>] drm_ioctl+0x180/0x360 [drm]
[ 4704.532451]  [<f82193a0>] ? radeon_cp_cmdbuf+0x0/0xbf0 [radeon]
[ 4704.532456]  [<c015c170>] ? autoremove_wake_function+0x0/0x40
[ 4704.532460]  [<c01603c2>] ? hrtimer_start+0x22/0x30
[ 4704.532466]  [<c02c801f>] ? security_file_permission+0xf/0x20
[ 4704.532474]  [<c01f51f3>] vfs_ioctl+0x73/0x90
[ 4704.532477]  [<c01f54c1>] do_vfs_ioctl+0x71/0x310
[ 4704.532480]  [<c01f57bf>] sys_ioctl+0x5f/0x80
[ 4704.532484]  [<c010336c>] syscall_call+0x7/0xb
[ 4704.532486] Mem-Info:
[ 4704.532487] DMA per-cpu:
[ 4704.532489] CPU    0: hi:    0, btch:   1 usd:   0
[ 4704.532491] Normal per-cpu:
[ 4704.532493] CPU    0: hi:  186, btch:  31 usd:   0
[ 4704.532494] HighMem per-cpu:
[ 4704.532496] CPU    0: hi:  186, btch:  31 usd:   0
[ 4704.532500] Active_anon:70577 active_file:90139 inactive_anon:70655
[ 4704.532501]  inactive_file:84786 unevictable:455 dirty:75 writeback:0 unstable:0
[ 4704.532502]  free:11227 slab:7559 mapped:54089 pagetables:1631 bounce:0
[ 4704.532506] DMA free:3544kB min:64kB low:80kB high:96kB active_anon:0kB inactive_anon:0kB active_file:2468kB inactive_file:1788kB unevictable:0kB present:15804kB pages_scanned:0 all_unreclaimable? no
[ 4704.532509] lowmem_reserve[]: 0 865 1507 1507
[ 4704.532514] Normal free:39992kB min:3728kB low:4660kB high:5592kB active_anon:120132kB inactive_anon:122028kB active_file:192808kB inactive_file:192884kB unevictable:1820kB present:885944kB pages_scanned:0 all_unreclaimable? no
[ 4704.532517] lowmem_reserve[]: 0 0 5140 5140
[ 4704.532522] HighMem free:1372kB min:512kB low:1204kB high:1896kB active_anon:162176kB inactive_anon:160592kB active_file:165280kB inactive_file:144472kB unevictable:0kB present:657992kB pages_scanned:0 all_unreclaimable? no
[ 4704.532525] lowmem_reserve[]: 0 0 0 0
[ 4704.532528] DMA: 12*4kB 4*8kB 2*16kB 1*32kB 1*64kB 4*128kB 5*256kB 3*512kB 0*1024kB 0*2048kB 0*4096kB = 3536kB
[ 4704.532536] Normal: 7878*4kB 728*8kB 154*16kB 0*32kB 1*64kB 1*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 39992kB
[ 4704.532543] HighMem: 49*4kB 9*8kB 5*16kB 20*32kB 0*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 1372kB
[ 4704.532551] 176894 total pagecache pages
[ 4704.532552] 873 pages in swap cache
[ 4704.532554] Swap cache stats: add 17865, delete 16992, find 5223/5520
[ 4704.532556] Free swap  = 2979520kB
[ 4704.532557] Total swap = 2996112kB
[ 4704.539026] 393104 pages RAM
[ 4704.539029] 165794 pages HighMem
[ 4704.539030] 51399 pages reserved
[ 4704.539032] 264156 pages shared
[ 4704.539033] 140220 pages non-shared
[ 4704.590642] [drm] Num pipes: 4
[ 4704.634205] compiz.real[20503]: segfault at 50 ip 08055c3c sp bfb43ce0 error 4 in compiz.real[8048000+34000]
[ 4705.795966] [drm] Setting GART location based on new memory map
[ 4705.797277] [drm] Loading R500 Microcode
[ 4705.797301] [drm] Num pipes: 4
[ 4705.797308] [drm] writeback test succeeded in 1 usecs
```





**Xorg.0.log:** (after crash)

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux SPOONS 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=24420e75-5730-4529-8434-f047727be5cd ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb 23 17:17:53 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:4:0:0) 1002:7249:1002:0b12 ATI Technologies Inc R580 [Radeon X1900 XT] (Primary) rev 0, Mem @ 0xc0000000/268435456, 0xdffe0000/65536, I/O @ 0x0000e800/256, BIOS @ 0x????????/131072
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
	Section "Device"
		Identifier	"Builtin Default ati Device 0"
		Driver	"ati"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default ati Screen 0"
		Device	"Builtin Default ati Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default vesa Device 0"
		Driver	"vesa"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default vesa Screen 0"
		Device	"Builtin Default vesa Device 0"
	EndSection
	Section "Device"
		Identifier	"Builtin Default fbdev Device 0"
		Driver	"fbdev"
	EndSection
	Section "Screen"
		Identifier	"Builtin Default fbdev Screen 0"
		Device	"Builtin Default fbdev Device 0"
	EndSection
	Section "ServerLayout"
		Identifier	"Builtin Default Layout"
		Screen	"Builtin Default ati Screen 0"
		Screen	"Builtin Default vesa Screen 0"
		Screen	"Builtin Default fbdev Screen 0"
	EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default ati Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default ati Device 0"
(==) No monitor specified for screen "Builtin Default ati Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
	Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 6.12.99
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 2.2.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Radeon 4800 Series, ATI Radeon 4800 Series, ATI FirePro M7750,
	ATI M98, ATI M98, ATI M98, ATI Mobility Radeon HD 4650,
	ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
	ATI FirePro M5750, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI FirePro RG220, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3000 Graphics,
	ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI RS880
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 04@00:00:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) [KMS] drm report modesetting isn't supported.
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.0.2
	ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): Built from git commit 7968e1fb89f6b59d1654df48249bf4b81990c008
(II) RADEON(0): TOTO SAYS 00000000dffe0000
(II) RADEON(0): MMIO registers at 0x00000000dffe0000: size 64KB
(II) RADEON(0): PCI bus 4 card 0 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Builtin Default ati Screen 0" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(--) RADEON(0): Chipset: "ATI Radeon X1900" (ChipID = 0x7249)
(--) RADEON(0): Linear framebuffer at 0x00000000c0000000
(II) RADEON(0): PCIE card detected
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): ATOM BIOS detected
(II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1002 SubsystemID: 0x0b12
	IOBaseAddress: 0xe800
	Filename:             
	BIOS Bootup Message: 

A52021 X1900XTX BIOS                                                        


(II) RADEON(0): Framebuffer space used by Firmware (kb): 20
(II) RADEON(0): Start of VRAM area used by Firmware: 0x7ffb000
(II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
(II) RADEON(0): AtomBIOS VRAM scratch base: 0x7ffb000
(II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
(II) RADEON(0): Default Engine Clock: 500000
(II) RADEON(0): Default Memory Clock: 600000
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1100000
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
(II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
(II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
(II) RADEON(0): Maximum Pixel Clock: 400000
(II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.31.0
(==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (256 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 110000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 500.000000, mclk: 600.000000
(II) RADEON(0): PLL parameters: rf=2700 rd=13 min=64800 max=110000; xclk=40000
(II) RADEON(0): Skipping TV-Out
(II) RADEON(0): Skipping Component Video
(II) RADEON(0): Output DVI-1 has no monitor section
(II) RADEON(0): I2C bus "DVI-1" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI-0" initialized.
(II) RADEON(0): Port0:
  XRANDR name: DVI-1
  Connector: DVI-I
  CRT2: INTERNAL_KLDSCP_DAC2
  DFP1: INTERNAL_KLDSCP_TMDS1
  DDC reg: 0x7e50
(II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_KLDSCP_DAC1
  DFP3: INTERNAL_LVTM1
  DDC reg: 0x7e40
(II) RADEON(0): I2C device "DVI-1:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
finished output detect: 0
(II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
(II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
finished output detect: 1
finished all detect
before xf86InitialConfiguration
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
(II) RADEON(0): Panel infos found from DDC detailed: 1920x1080
(II) RADEON(0): EDID vendor "VSC", prod id 64545
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Output DVI-1 disconnected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Using exact sizes for initial modes
(II) RADEON(0): Output DVI-0 using initial mode 1920x1080
(==) RADEON(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) RADEON(0): Using EXA acceleration architecture
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(II) UnloadModule: "vesa"
(II) Unloading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[25] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[26] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) RADEON(0): RADEONScreenInit c0000000 0 0
Output DFP3 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): Dynamic Power Management Disabled
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x20000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): Allocating from a screen of 262112 kb
(II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00e10000
(II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00e14000
(II) RADEON(0): Will use 14400 kb for front buffer at offset 0x00000000
(II) RADEON(0): Will use 32 kb for PCI GART at offset 0x0fff8000
(II) RADEON(0): Will use 14400 kb for back buffer at offset 0x00e18000
(II) RADEON(0): Will use 14400 kb for depth buffer at offset 0x01c28000
(II) RADEON(0): Will use 108544 kb for textures at offset 0x02a38000
(II) RADEON(0): Will use 110336 kb for X Server offscreen at offset 0x09438000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xc0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 32768 kB allocated with handle 0xf903a000
(II) RADEON(0): [pci] ring handle = 0xf903a000
(II) RADEON(0): [pci] Ring mapped at 0xb7627000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf913b000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb772e000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf913c000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xa73b6000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf933c000
(II) RADEON(0): [pci] GART Texture map mapped at 0xa5736000
(II) RADEON(0): [drm] register handle = 0x2bffc000
(II) RADEON(0): [dri] Visual configs initialized
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffc000 0xdfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 18
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xdfffc000 is: 0xdfffc000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0xffffffc0
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffc000 0xdfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled for R300/R400/R500 type cards.
(II) RADEON(0): Setting EXA maxPitchBytes
(II) RADEON(0): num quad-pipes is 4
(II) EXA(0): Offscreen pixmap area of 112984064 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Set up textured video
Output DFP3 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Output DFP3 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1920x1080 - 2200 1125 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffc000 0xdfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
freq: 148500000
best_freq: 148500000
best_feedback_div: 55
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 5
(II) RADEON(0): crtc(0) Clock: mode 148500, PLL 148500
(II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x37(55), fracfbdiv 0, pdiv 5
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
(II) RADEON(0): Coherent Mode enabled
Output digital setup success
Output DFP3 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
Blank CRTC 1 success
Disable CRTC 1 success
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Output DFP3 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Mode 1920x1080 - 2200 1125 5
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xdfffc000 0xdfffc000
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
freq: 148500000
best_freq: 148500000
best_feedback_div: 55
best_frac_feedback_div: 0
best_ref_div: 2
best_post_div: 5
(II) RADEON(0): crtc(0) Clock: mode 148500, PLL 148500
(II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x37(55), fracfbdiv 0, pdiv 5
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
(II) RADEON(0): Coherent Mode enabled
Output digital setup success
Output DFP3 enable success
Enable CRTC 0 success
Unblank CRTC 0 success
(--) RandR disabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:04:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:04:00.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_make_current_read
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 477 x 268
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Saitek GM3200 Laser mouse
(**) Saitek GM3200 Laser mouse: always reports core events
(**) Saitek GM3200 Laser mouse: Device: "/dev/input/event4"
(II) Saitek GM3200 Laser mouse: Found 9 mouse buttons
(II) Saitek GM3200 Laser mouse: Found x and y relative axes
(II) Saitek GM3200 Laser mouse: Found scroll wheel(s)
(II) Saitek GM3200 Laser mouse: Configuring as mouse
(**) Saitek GM3200 Laser mouse: YAxisMapping: buttons 4 and 5
(**) Saitek GM3200 Laser mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Saitek GM3200 Laser mouse" (type: MOUSE)
(**) Saitek GM3200 Laser mouse: (accel) keeping acceleration scheme 1
(**) Saitek GM3200 Laser mouse: (accel) filter chain progression: 2.00
(**) Saitek GM3200 Laser mouse: (accel) filter stage 0: 20.00 ms
(**) Saitek GM3200 Laser mouse: (accel) set acceleration profile 0
(II) Saitek GM3200 Laser mouse: initialized for relative axes.
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
(II) RADEON(0): EDID vendor "VSC", prod id 64545
(II) RADEON(0): Using EDID range info for horizontal sync
(II) RADEON(0): Using EDID range info for vertical refresh
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
(II) RADEON(0): EDID vendor "VSC", prod id 64545
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
(II) RADEON(0): EDID vendor "VSC", prod id 64545
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
(II) RADEON(0): EDID vendor "VSC", prod id 64545
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Dac detection success
(II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
Unhandled monitor type 0
(II) RADEON(0): EDID for output DVI-1
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
(II) RADEON(0): EDID vendor "VSC", prod id 64545
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1400x1050"x0.0  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Output: DVI-0, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
(II) RADEON(0): Manufacturer: VSC  Model: fc21  Serial#: 16843009
(II) RADEON(0): Year: 2009  Week: 45
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: Off
(II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
(II) RADEON(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported established timings:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): 1152x870@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported standard timings:
(II) RADEON(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) RADEON(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) RADEON(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) RADEON(0): #3: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
(II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) RADEON(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): Supported detailed timing:
(II) RADEON(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) RADEON(0): Serial No: R2S094520926
(II) RADEON(0): Ranges: V min: 50 V max: 75 Hz, H min: 24 H max: 82 kHz, PixClock max 180 MHz
(II) RADEON(0): Monitor name: VX2260WM
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff005a6321fc01010101
(II) RADEON(0): 	2d13010380301b782e3585a656489a24
(II) RADEON(0): 	125054bfef80b300a940950090408180
(II) RADEON(0): 	8140714f0101023a801871382d40582c
(II) RADEON(0): 	4500dd0c1100001e000000ff00523253
(II) RADEON(0): 	3039343532303932360a000000fd0032
(II) RADEON(0): 	4b185212000a202020202020000000fc
(II) RADEON(0): 	00565832323630574d0a20202020006c
(II) RADEON(0): EDID vendor "VSC", prod id 64545
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1400x1050"x59.9  101.00  1400 1448 1480 1560  1050 1053 1057 1080 +hsync -vsync (64.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x59.9   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
```




Thanks again mate. :)

---

### Post by Satoru-san on 2010-02-23
It is not gnome that is crashing, you are not even using gnome as your window manager, you are using compiz, you will have to disable it, do this by opening up your desktop settings and turning off effects. This will solve the problem, however you will not have pretty stuff anymore. :P

---

### Post by NiGhtMarEs0nWax on 2010-02-23
i thought gnome was the equivalent of windows explorer? and Compiz was just for desktop effects, essentially a 'plugin.'



anyway, is there another way round it? I mean, what is causing it to crash, there must be a conflict? is there a way to tell if it's a specific plugin?

Thanks.

---

### Post by Satoru-san on 2010-02-23
> **NiGhtMarEs0nWax said:**
> i thought gnome was the equivalent of windows explorer? and Compiz was just for desktop effects, essentially a 'plugin.'



anyway, is there another way round it? I mean, what is causing it to crash, there must be a conflict? is there a way to tell if it's a specific plugin?

Thanks.
No, it is not a "plugin" compiz is a compositing window manager that replaces gnome's window manager. I cannot tell what is causing the conflict, I am not that intimate with compiz. I will try to find out for you and ask some other people to look at this for you.

The equivalent of windows explorer I am thinking is nautilus, it is responsible for your menus background and file browser. 

Best of luck.

---

### Post by Chris_82 on 2010-12-23
> **Satoru-san said:**
> can you please paste these:
Also you could please paste the /var/log/Xorg.0.log after X crashes and you get terminal. To do these though you will have to put them on a flash drive.
```
dmesg > /mnt/usb/dmesg.txt
cp /var/log/Xorg.0.log /mnt/usb
```

You don't need a flash drive to copy the logfiles from your machine..you can copy them wherever you want e.g.:
```

dmesg > ~/dmesg.txt
cp /var/log/Xorg.0.log ~/Xorg.0.log

```
would copy the two files to your home folder which is /home/your_user_name/ by default.

> **NiGhtMarEs0nWax said:**
> i thought gnome was the equivalent of windows explorer? and Compiz was just for desktop effects, essentially a 'plugin.'

Gnome is not an explorer..it's a Desktop that sits on top op GNU/Linux or Unix. Gnomes comes along with all those applications like for example Nautilus which is the default file explorer for Gnome..

Now having a quick look at the log files I saw this:
```
[ 4704.634205] compiz.real[20503]: segfault at 50 ip 08055c3c sp bfb43ce0 error 4 in compiz.real[8048000+34000]
```

..which doesn't sound good.
A workaround would be to disable compiz if you don't care about the glitter too much.

Is your machine working fine now? It has been some time since the last post.. ;-)

cheers.

---

