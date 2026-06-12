---
title: "I can't use ubuntu anymore..."
date: 2006-08-29
forum: Desktop Environments
---

### Post by gizmoog on 2006-08-29
Hello,
I'm new in linux and I install dapper a week ago. Everything was working fine until today. When I connect, the Desktop screen appears but not complete and the CPU begin to be over used (I can hear my ventilator running faster and faster). Everything seems to be frozen but when i drop my mouse on the garbage bin it tells me that more and more files are on the way to it (10000 and more). I don't know why and I don't know how to stop it.
Just before that, I had to reboot with the power button because the screen was frozen on the openoffice boot window.

can somebody help me ??

sorry for my english.

gizmoog

---

### Post by Tomosaur on 2006-08-29
Uhhh. Sounds like you told the computer to delete everything on startup or something like that. Do you remember following any 'unofficial advice' from a forum or something, and if so, can you point us to it?

---

### Post by gizmoog on 2006-08-29
Thanks for your answer...
no, I don't think I did anything like that.
what I've done previously was install the alien pakage to transform a .rpm in .deb and then install from a rpm the lx-viewer pakage. Anything else I guess.
What else... I use on my pc winXP and ubuntu and pass from one to the other after hibernate and not total reboot. Was that wrong ?
Is there any virus on linux :confused:

---

### Post by Tomosaur on 2006-08-29
There are a few viruses on linux, but I stress 'A FEW'. The likelihood of you getting one is virtually negligible unless you do something stupid like install it yourself. They just really aren't much of an issue at all.

Where did you download the .rpm package from?

---

### Post by gizmoog on 2006-08-30
I download it on sourceforge, so I guess it should be ok. By the way, maybe it's important, as the software doesn't fit my needs, I desinstall it by the synaptic packages tool and I precised "desinstall all". Could it be the reason ?
I succeed in opening an xterm window while my bin was getting bigger and bigger and I type "ps - aux" as I remember from my older uses of unix it could be interesting. you'll find the result at the end of the post. Could you see someting in it (nautilus trash is it someting I can kill for example?) ? Could I try to type someting more efficient ?
Another thing : that problem is only related to my account. I created two other accounts (lucky guy i am...) and everything is ok for them both.
thanks for your help
gizmo

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.0   1564   532 ?        Ss   19:30   0:01 init [2]         
root         2  0.0  0.0      0     0 ?        SN   19:30   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    19:30   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   19:30   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   19:30   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   19:30   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   19:30   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   19:30   0:00 [kacpid]
root       123  0.0  0.0      0     0 ?        S<   19:30   0:00 [kseriod]
root       156  0.0  0.0      0     0 ?        S    19:30   0:00 [pdflush]
root       157  0.0  0.0      0     0 ?        S    19:30   0:00 [pdflush]
root       158  0.0  0.0      0     0 ?        S    19:30   0:00 [kswapd0]
root       159  0.0  0.0      0     0 ?        S<   19:30   0:00 [aio/0]
root      1755  0.0  0.0      0     0 ?        S<   19:30   0:00 [khubd]
root      1774  0.0  0.0      0     0 ?        S    19:30   0:00 [khpsbpkt]
root      1802  0.0  0.0      0     0 ?        S    19:30   0:00 [knodemgrd_0]
root      1898  0.0  0.0      0     0 ?        S<   19:30   0:00 [kjournald]
root      2098  0.0  0.0   2432   920 ?        S<s  19:30   0:00 /sbin/udevd --daemon
root      2892  0.0  0.0      0     0 ?        S<   19:30   0:00 [shpchpd]
root      3057  0.0  0.0      0     0 ?        S<   19:30   0:00 [kpsmoused]
root      3073  0.0  0.0      0     0 ?        S    19:30   0:00 [pccardd]
root      3079  0.0  0.0      0     0 ?        S<   19:30   0:00 [ipw2200/0]
root      3548  0.0  0.0   2332   756 ?        S<s  19:31   0:00 dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
root      3558  0.0  0.0   2336   756 ?        S<s  19:31   0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.leases eth0
root      3580  0.0  0.0      0     0 ?        S<   19:32   0:00 [kjournald]
root      4012  0.0  0.1   2152  1192 ?        Ss   19:32   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    4100  0.0  0.0   1768   688 ?        Ss   19:32   0:00 /sbin/syslogd -u syslog
root      4126  0.0  0.0   1680   496 ?        Ss   19:32   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4128  0.0  0.1   2368  1296 ?        Ss   19:32   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      4151  0.0  0.1  10940  1816 ?        Ss   19:32   0:00 /usr/sbin/gdm
root      4164  0.0  0.2  11508  2748 ?        S    19:32   0:00 /usr/sbin/gdm
root      4175  3.3  2.1  26504 22492 tty7     Rs+  19:32   0:18 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
hplip     4182  0.0  0.0   4672   860 ?        Ss   19:32   0:00 /usr/sbin/hpiod
cupsys    4246  0.0  0.1   4336  2004 ?        Ss   19:32   0:00 /usr/sbin/cupsd
104       4272  4.0  0.0   2192   872 ?        Ss   19:32   0:22 /usr/bin/dbus-daemon --system
108       4287  3.6  0.5   6820  5428 ?        Ss   19:32   0:19 /usr/sbin/hald
root      4288  0.0  0.0   2716   976 ?        S    19:32   0:00 hald-runner
108       4293  0.0  0.0   2004   792 ?        S    19:32   0:00 /usr/lib/hal/hald-addon-acpi
108       4299  0.0  0.0   2004   792 ?        S    19:32   0:00 /usr/lib/hal/hald-addon-keyboard
108       4313  0.0  0.0   2012   820 ?        S    19:32   0:00 /usr/lib/hal/hald-addon-storage
108       4314  0.0  0.0   2012   820 ?        S    19:32   0:00 /usr/lib/hal/hald-addon-storage
root      4365  0.0  0.0   1556   260 ?        SNs  19:32   0:00 /usr/sbin/powernowd -q
root      4407  0.0  0.0   1972   708 ?        Ss   19:32   0:00 hcid: processing events
root      4411  0.0  0.0   1620   460 ?        Ss   19:32   0:00 /usr/sbin/sdpd
root      4426  0.0  0.0      0     0 ?        S<   19:32   0:00 [krfcommd]
root      4439  0.0  0.0   1624   296 ?        Ss   19:32   0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
daemon    4474  0.0  0.0   1804   400 ?        Ss   19:32   0:00 /usr/sbin/atd
root      4487  0.0  0.0   2120   840 ?        Ss   19:32   0:00 /usr/sbin/cron
root      4564  0.0  0.0   1564   492 tty1     Ss+  19:32   0:00 /sbin/getty 38400 tty1
root      4565  0.0  0.0   1564   496 tty2     Ss+  19:32   0:00 /sbin/getty 38400 tty2
root      4566  0.0  0.0   1560   492 tty3     Ss+  19:32   0:00 /sbin/getty 38400 tty3
root      4567  0.0  0.0   1560   492 tty4     Ss+  19:32   0:00 /sbin/getty 38400 tty4
root      4568  0.0  0.0   1560   492 tty5     Ss+  19:32   0:00 /sbin/getty 38400 tty5
root      4569  0.0  0.0   1564   496 tty6     Ss+  19:32   0:00 /sbin/getty 38400 tty6
gizmo     5123  0.2  0.9  19784 10116 ?        Ss   19:37   0:00 x-session-manager
gizmo     5165  0.0  0.0   4332   692 ?        Ss   19:37   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
gizmo     5168  0.0  0.0   2716   652 ?        S    19:37   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
gizmo     5169  0.0  0.0   2196   912 ?        Ss   19:37   0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
gizmo     5171  1.1  0.4   6808  4284 ?        S    19:37   0:03 /usr/lib/libgconf2-4/gconfd-2 5
gizmo     5174  0.0  0.0   2344   728 ?        S    19:37   0:00 /usr/bin/gnome-keyring-daemon
gizmo     5176  2.0  0.3   6700  3340 ?        Ss   19:37   0:05 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
gizmo     5178  0.1  0.8  27572  9208 ?        Sl   19:37   0:00 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd=25
gizmo     5180  0.0  0.4   5800  4320 ?        Ss   19:37   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
gizmo     5186  2.2  0.8  14724  8564 ?        Ss   19:37   0:06 /usr/bin/metacity --sm-client-id=default0
gizmo     5193  9.5  4.3  64300 44644 ?        Ssl  19:37   0:27 gnome-panel --sm-client-id default1
gizmo     5199  0.0  0.5  17816  5808 ?        Ss   19:37   0:00 gnome-volume-manager --sm-client-id default4
gizmo     5211  0.0  1.0  19760 10812 ?        Ss   19:37   0:00 update-notifier
gizmo     5215  0.1  0.8  54768  8484 ?        Ss   19:37   0:00 gnome-cups-icon --sm-client-id default3
gizmo     5221  0.2  0.5  18400  6100 ?        Ss   19:37   0:00 gnome-power-manager
gizmo     5223  2.9  1.7  78936 17732 ?        Sl   19:37   0:08 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=34
gizmo     5258  0.0  1.0  38708 10764 ?        S    19:37   0:00 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activate-iid=OAFIID:GNOME_GWeatherApplet_Factory --oaf-ior-fd=36
gizmo     5275  0.0  0.0   2284   800 ?        S    19:37   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
gizmo     6962  0.0  0.8  21384  8976 ?        Sl   19:37   0:00 nautilus trash:
gizmo     7179  0.0  0.2  14816  2776 ?        Ss   19:37   0:00 gnome-screensaver
gizmo     8595  7.3  2.4  94124 25312 ?        Ssl  19:38   0:16 nautilus --sm-client-id 117f000001000115687302700000051230002 --screen 0
gizmo    16723  0.1  0.5  11228  5972 ?        S    19:39   0:00 xterm
gizmo    16748  0.0  0.3   5736  3348 pts/0    Ss   19:39   0:00 bash
root     20243  0.1  0.2   5220  3104 pts/0    S    19:40   0:00 /bin/bash
root     24406  1.8  1.9  40832 19828 pts/0    S    19:41   0:00 gedit
root     24425  0.8  0.3   6436  3888 pts/0    S    19:41   0:00 /usr/lib/libgconf2-4/gconfd-2 12
root     24501  0.0  0.1   3084  1456 ?        Ss   19:41   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 17
gizmo    26213  0.0  0.4  20472  4620 ?        Sl   19:41   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=39
root     26219  0.0  0.0   2432  1028 pts/0    R+   19:41   0:00 ps -aux

---

### Post by gizmoog on 2006-09-11
Now everything seems to be ok (I'm writing from my own session).
I just rename ~/.gnome/gnome-vfs/.trash_entry_cache and a new file has been created at the beginning of the session and now it works.
I just don't know what occured...

---

