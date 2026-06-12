---
title: "Xubuntu and Firefox is so slow"
date: 2007-08-12
forum: Desktop Environments
---

### Post by lenniboy on 2007-08-12
I am experiencing a slowdown of my laptop which is running Xbuntu Feisty. (Turion 64, 1.6 GHz, 256 MB Ram). I know that's not exactly high end hardware but should be okay for XFCE.

Firefox seems to be the culprit because it slows down terribly whenever I open more than one tab. 

The whole machine used to be much quicker and has only started to slow down recently. 

The only big change I have done is to shrink the root partition but there's still 3 GB empty space so that shouldn't affect it shouldn't it?

Here the output of ps aux:
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.6   2908  1472 ?        Ss   12:02   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    12:02   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   12:02   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    12:02   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   12:02   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   12:02   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   12:02   0:00 [kthread]
root        30  0.0  0.0      0     0 ?        S<   12:02   0:00 [kblockd/0]
root        31  0.0  0.0      0     0 ?        S<   12:02   0:00 [kacpid]
root        32  0.0  0.0      0     0 ?        S<   12:02   0:00 [kacpi_notify]
root       121  0.0  0.0      0     0 ?        S<   12:02   0:00 [kseriod]
root       146  0.0  0.0      0     0 ?        S    12:02   0:00 [pdflush]
root       147  0.0  0.0      0     0 ?        S    12:02   0:00 [pdflush]
root       148  0.0  0.0      0     0 ?        D<   12:02   0:02 [kswapd0]
root       149  0.0  0.0      0     0 ?        S<   12:02   0:00 [aio/0]
root      1882  0.0  0.0      0     0 ?        S<   12:02   0:00 [ksuspend_usbd]
root      1883  0.0  0.0      0     0 ?        S<   12:02   0:00 [khubd]
root      1900  0.0  0.0      0     0 ?        S<   12:02   0:00 [ata/0]
root      1901  0.0  0.0      0     0 ?        S<   12:02   0:00 [ata_aux]
root      1925  0.0  0.0      0     0 ?        S<   12:02   0:00 [khpsbpkt]
root      2135  0.0  0.0      0     0 ?        S<   12:02   0:00 [knodemgrd_0]
root      2274  0.0  0.0      0     0 ?        S<   12:02   0:00 [kjournald]
root      2473  0.0  0.1   2424   424 ?        S<s  12:02   0:00 /sbin/udevd --daemon
root      3334  0.0  0.0      0     0 ?        S<   12:02   0:00 [kmmcd]
root      3352  0.0  0.0      0     0 ?        S<   12:02   0:00 [pccardd]
root      3356  0.0  0.0      0     0 ?        S<   12:02   0:00 [tifm/0]
root      3374  0.0  0.0      0     0 ?        S<   12:02   0:00 [kpsmoused]
root      3613  0.0  0.0      0     0 ?        S    12:02   0:02 [wrap_wq]
root      3614  0.0  0.0      0     0 ?        S    12:02   0:01 [ntos_wq]
root      3615  0.0  0.0      0     0 ?        S    12:02   0:00 [ndis_wq]
root      3974  0.0  0.1   1652   224 tty4     Ss+  12:02   0:00 /sbin/getty 38400 tty4
root      3975  0.0  0.1   1652   224 tty5     Ss+  12:02   0:00 /sbin/getty 38400 tty5
root      3980  0.0  0.0   1648   220 tty2     Ss+  12:02   0:00 /sbin/getty 38400 tty2
root      3981  0.0  0.0   1648   216 tty3     Ss+  12:02   0:00 /sbin/getty 38400 tty3
root      3982  0.0  0.1   1652   224 tty1     Ss+  12:02   0:00 /sbin/getty 38400 tty1
root      3983  0.0  0.1   1652   224 tty6     Ss+  12:02   0:00 /sbin/getty 38400 tty6
root      4251  0.0  0.3   2260   812 ?        Ss   12:02   0:01 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4344  0.0  0.1   1700   336 ?        Ss   12:02   0:00 /sbin/syslogd
root      4396  0.0  0.0   1796   216 ?        Ss   12:02   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4398  0.0  0.5   2432  1160 ?        Ss   12:02   0:00 /sbin/klogd -P /var/run/klogd/kmsg
104       4419  0.0  0.3   2720   676 ?        Ss   12:02   0:08 /usr/bin/dbus-daemon --system
107       4437  0.0  3.3   9952  7348 ?        Ss   12:02   0:05 /usr/sbin/hald
root      4438  0.0  0.2   2876   452 ?        S    12:02   0:00 hald-runner
107       4444  0.0  0.2   2108   528 ?        S    12:02   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      4445  0.0  0.1   2932   376 ?        S    12:02   0:00 /usr/lib/hal/hald-addon-cpufreq
107       4452  0.0  0.1   2104   328 ?        S    12:02   0:00 hald-addon-keyboard: listening on /dev/input/event1
107       4465  0.0  0.1   2108   316 ?        S    12:02   0:00 hald-addon-keyboard: listening on /dev/input/event5
107       4468  0.0  0.1   2104   312 ?        S    12:02   0:00 hald-addon-keyboard: listening on /dev/input/event6
107       4471  0.0  0.1   2108   312 ?        S    12:02   0:00 hald-addon-keyboard: listening on /dev/input/event7
107       4486  0.0  0.1   2104   332 ?        S    12:02   0:03 hald-addon-storage: polling /dev/hdc
avahi     4505  0.0  0.3   2664   684 ?        Ss   12:02   0:00 avahi-daemon: running [picard.local]
avahi     4506  0.0  0.1   2664   272 ?        Ss   12:02   0:00 avahi-daemon: chroot helper
root      4520  0.0  0.1   2868   388 ?        Ss   12:02   0:00 /usr/bin/system-tools-backends
root      4521  0.0  0.1   2720   352 ?        S    12:02   0:00 dbus-daemon --session --print-address --nofork
root      4553  0.0  0.3  12260   816 ?        Ss   12:02   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      4554  0.0  0.4  12752  1100 ?        S    12:02   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      4559  5.0 15.8  54724 35260 tty7     SLs+ 12:02   8:30 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tc
root      4612  0.0  0.0      0     0 ?        S<   12:02   0:00 [kondemand/0]
root      4641  0.3  1.7  15316  3788 ?        S    12:02   0:36 /usr/bin/python /opt/wicd/daemon.py
root      4662  0.0  0.1   2284   364 ?        Ss   12:02   0:00 /usr/sbin/cron
root      4764  0.0  0.1   3780   444 ?        Ss   12:02   0:00 wpa_supplicant -B -i wlan0 -c encryption/configurations/00184d53be8
lenni     4820  0.0  0.0   1716   216 ?        Ss   12:03   0:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
lenni     4854  0.0  0.1   4256   344 ?        Ss   12:03   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session startxf
lenni     4857  0.0  0.1   2664   332 ?        S    12:03   0:00 /usr/bin/dbus-launch --exit-with-session startxfce4
lenni     4858  0.0  0.2   2716   592 ?        Ss   12:03   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --sessi
lenni     4863  0.0  0.4   5432  1040 ?        S    12:03   0:00 xscreensaver -no-splash
lenni     4866  0.0  1.1  28676  2608 ?        S    12:03   0:01 /usr/bin/xfce4-session
lenni     4872  0.0  3.2  39476  7164 ?        Ss   12:03   0:04 xfce-mcs-manager
lenni     4873  0.0  2.3  18968  5284 ?        S    12:03   0:03 xfwm4 --sm-client-id 117f000101000118242920800000049390000 --displa
lenni     4874  0.0  2.0  74656  4560 ?        Sl   12:03   0:00 Thunar --sm-client-id 117f000101000118242920900000049390002 --daemo
lenni     4876  0.0  0.2   2544   552 ?        S    12:03   0:01 /usr/lib/gamin/gam_server
lenni     4888  0.0  3.1  34088  6908 ?        S    12:03   0:06 xfce4-panel --sm-client-id 117f000101000118242920800000049390001 --
lenni     4902  0.1  3.4  23624  7672 ?        Ss   12:03   0:10 /usr/bin/python /opt/wicd/tray-edgy.py
lenni     4914  0.0  3.4  33648  7756 ?        S    12:03   0:00 /usr/lib/xfdesktop4/xfce4/panel-plugins/xfce4-menu-plugin socket_id
lenni     4918  0.0  2.1  33124  4708 ?        S    12:03   0:04 /usr/lib/xfce4-mixer/xfce4/panel-plugins/xfce4-mixer-plugin socket_
lenni     9326  0.1  3.9  48320  8864 ?        S    14:14   0:02 xfce4-terminal
lenni     9407  0.0  0.1   2460   292 ?        S    14:14   0:00 gnome-pty-helper
lenni     9408  0.0  0.9   5656  2152 pts/0    Ss   14:14   0:00 bash
lenni    18683 15.1 25.5 225900 56840 ?        Ssl  14:47   0:22 /usr/lib/firefox/firefox-bin
lenni    18714  0.1  0.9   5424  2128 ?        S    14:47   0:00 /usr/lib/libgconf2-4/gconfd-2 12
lenni    18799  0.0  0.0      0     0 ?        Z    14:47   0:00 [netstat] <defunct>
root     19399  0.5  0.0      0     0 ?        Z    14:49   0:00 [sh] <defunct>
lenni    19409  4.0  0.4   2564   996 pts/0    R+   14:49   0:00 ps -aux
```

Can anyone help?

---

### Post by Happy_Man on 2007-08-12
Hmmm, yes that may be it. When I shrunk down my WIndows partition to make room for Ubuntu, it definitely made my Windows install very slow, probably due to the trashed NTFS filesystem. So I recommend running fsck from a liveCD. It may fix your problem. Another option would be to reinstall, so that the cylinders and other HDD stuff are back in check. 

Of course, that entire paragraph may be BS, and if it is, please, anyone, don't hesitate to yell at me and then suggest an alternate solution.

---

### Post by ffi on 2007-08-12
suddenl ysince  last week gam_server started making my box very slow, to disable it:

[http://ubuntuforums.org/showthread.php?t=210329&highlight=gam_server](http://ubuntuforums.org/showthread.php?t=210329&highlight=gam_server)

---

### Post by K.Mandla on 2007-08-12
You might try booting a live CD, and seeing if Firefox behaves badly there too. If it doesn't then it might be an issue with your installation. If it does, then it's something going on with Xubuntu.

---

