---
title: "High memory usage in 8.10"
date: 2009-04-08
forum: General Help
---

### Post by vancouverite on 2009-04-08
Hi all,
I am wondering why my ubuntu computer has such excessive memory usage. The command free returns

```

             total       used       free     shared    buffers     cached
Mem:       2056836    1929064     127772          0      35408     493736
-/+ buffers/cache:    1399920     656916
Swap:      4883140       2144    4880996

```

I see that ~500 MB is cache, but that still means that 1.4 GB is being used and I'm not actually doing anything.

The print out from Top is

```

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   4100   900 ?        Ss   21:00   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   21:00   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   21:00   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   21:00   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   21:00   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   21:00   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S<   21:00   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   21:00   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   21:00   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   21:00   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   21:00   0:00 [khelper]
root        49  0.0  0.0      0     0 ?        S<   21:00   0:00 [kintegrityd/0]
root        50  0.0  0.0      0     0 ?        S<   21:00   0:00 [kintegrityd/1]
root        52  0.0  0.0      0     0 ?        S<   21:00   0:00 [kblockd/0]
root        53  0.0  0.0      0     0 ?        S<   21:00   0:00 [kblockd/1]
root        55  0.0  0.0      0     0 ?        S<   21:00   0:00 [kacpid]
root        56  0.0  0.0      0     0 ?        S<   21:00   0:00 [kacpi_notify]
root       143  0.0  0.0      0     0 ?        S<   21:00   0:00 [cqueue]
root       147  0.0  0.0      0     0 ?        S<   21:00   0:00 [kseriod]
root       196  0.0  0.0      0     0 ?        S    21:00   0:00 [pdflush]
root       197  0.0  0.0      0     0 ?        S    21:00   0:00 [pdflush]
root       198  0.0  0.0      0     0 ?        S<   21:00   0:02 [kswapd0]
root       244  0.0  0.0      0     0 ?        S<   21:00   0:00 [aio/0]
root       245  0.0  0.0      0     0 ?        S<   21:00   0:00 [aio/1]
root      1194  0.0  0.0      0     0 ?        S<   21:00   0:00 [ksuspend_usbd]
root      1197  0.0  0.0      0     0 ?        S<   21:00   0:00 [khubd]
root      1297  0.0  0.0      0     0 ?        S<   21:00   0:00 [ata/0]
root      1298  0.0  0.0      0     0 ?        S<   21:00   0:00 [ata/1]
root      1299  0.0  0.0      0     0 ?        S<   21:00   0:00 [ata_aux]
root      1339  0.0  0.0      0     0 ?        S<   21:00   0:00 [khpsbpkt]
root      2060  0.0  0.0      0     0 ?        S<   21:00   0:00 [scsi_eh_0]
root      2062  0.0  0.0      0     0 ?        S<   21:00   0:00 [scsi_eh_1]
root      2129  0.0  0.0      0     0 ?        S<   21:00   0:00 [scsi_eh_2]
root      2130  0.0  0.0      0     0 ?        S<   21:00   0:00 [scsi_eh_3]
root      2131  0.0  0.0      0     0 ?        S<   21:00   0:00 [scsi_eh_4]
root      2134  0.0  0.0      0     0 ?        S<   21:00   0:00 [scsi_eh_5]
root      2171  0.0  0.0      0     0 ?        S<   21:00   0:00 [scsi_eh_6]
root      2172  0.0  0.0      0     0 ?        S<   21:00   0:00 [usb-storage]
root      2205  0.0  0.0      0     0 ?        S<   21:00   0:00 [knodemgrd_0]
root      2345  0.0  0.0      0     0 ?        S<   21:00   0:00 [kjournald]
root      2525  0.0  0.0  17272  1320 ?        S<s  21:00   0:00 /sbin/udevd --daemon
root      2974  0.0  0.0      0     0 ?        S<   21:00   0:00 [kpsmoused]
root      4285  0.0  0.0      0     0 ?        S<   21:00   0:00 [kstriped]
root      4449  0.0  0.0      0     0 ?        S<   21:00   0:00 [kjournald]
root      4473  0.0  0.0  16320  1208 ?        Ss   21:00   0:00 /sbin/mount.ntfs /dev/sda1 /media/win_xp -o rw,umask=007,gid=46
root      4759  0.0  0.0   3940   596 tty4     Ss+  21:00   0:00 /sbin/getty 38400 tty4
root      4760  0.0  0.0   3940   596 tty5     Ss+  21:00   0:00 /sbin/getty 38400 tty5
root      4767  0.0  0.0   3940   596 tty2     Ss+  21:00   0:00 /sbin/getty 38400 tty2
root      4768  0.0  0.0   3940   596 tty3     Ss+  21:00   0:00 /sbin/getty 38400 tty3
root      4769  0.0  0.0   3940   600 tty6     Ss+  21:00   0:00 /sbin/getty 38400 tty6
root      4956  0.0  0.0   4864  1644 ?        Ss   21:00   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4997  0.0  0.0      0     0 ?        S<   21:00   0:00 [kondemand/0]
root      4998  0.0  0.0      0     0 ?        S<   21:00   0:00 [kondemand/1]
syslog    5079  0.0  0.0  12364   740 ?        Ss   21:00   0:00 /sbin/syslogd -u syslog
root      5135  0.0  0.0   8204   612 ?        S    21:00   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5137  0.0  0.2   7820  4432 ?        Ss   21:00   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       5160  0.0  0.0  21848  1612 ?        Ss   21:00   0:00 /bin/dbus-daemon --system
avahi     5182  0.0  0.0  29808  1616 ?        Ss   21:00   0:00 avahi-daemon: running [seth-desktop.local]
avahi     5183  0.0  0.0  29680   520 ?        Ss   21:00   0:00 avahi-daemon: chroot helper
root      5213  0.0  0.0  48912  1176 ?        Ss   21:00   0:00 /usr/sbin/sshd
root      5248  0.0  0.1  72932  2716 ?        Ss   21:00   0:00 /usr/sbin/cupsd
root      5414  0.0  0.3  86036  7960 ?        S    21:00   0:01 python -O /usr/lib/wicd/wicd-daemon.py
109       5438  0.0  0.2  36384  4968 ?        Ss   21:00   0:00 /usr/sbin/hald
root      5441  0.0  0.1 109052  2732 ?        Ssl  21:00   0:00 /usr/sbin/console-kit-daemon
root      5504  0.0  0.0  17932  1272 ?        S    21:00   0:00 hald-runner
root      5527  0.0  0.0  20048  1176 ?        S    21:00   0:00 hald-addon-input: Listening on /dev/input/event6 /dev/input/event5 /dev/input/event2 /dev/input/event
109       5545  0.0  0.0  16752   996 ?        S    21:00   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      5557  0.0  0.0  20052  1180 ?        S    21:00   0:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5560  0.0  0.0  20052  1176 ?        S    21:00   0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
root      5563  0.0  0.0  20052  1176 ?        S    21:00   0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
root      5566  0.0  0.0  20052  1180 ?        S    21:00   0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
root      5569  0.0  0.0  20052  1176 ?        S    21:00   0:00 hald-addon-storage: polling /dev/sde (every 2 sec)
root      5572  0.0  0.0  20052  1180 ?        S    21:00   0:00 hald-addon-storage: polling /dev/sdf (every 2 sec)
root      5613  0.0  0.0  30364  1664 ?        Ss   21:00   0:00 /usr/sbin/bluetoothd
root      5620  0.0  0.0      0     0 ?        S<   21:00   0:00 [btaddconn]
root      5621  0.0  0.0      0     0 ?        S<   21:00   0:00 [btdelconn]
root      5653  0.0  0.0      0     0 ?        S<   21:00   0:00 [krfcommd]
root      5720  0.0  0.0 118228  2032 ?        Ss   21:00   0:00 /usr/sbin/gdm
root      5723  0.0  0.1 139332  3656 ?        S    21:00   0:00 /usr/sbin/gdm
root      5731  0.0  0.3  76464  7808 ?        S    21:00   0:00 python /usr/lib/wicd/monitor.py
root      5745  0.0  0.0  35384  1236 ?        Ss   21:00   0:00 /usr/bin/system-tools-backends
daemon    5779  0.0  0.0  16512   448 ?        Ss   21:00   0:00 /usr/sbin/atd
root      5808  0.0  0.0  19920  1128 ?        Ss   21:01   0:00 /usr/sbin/cron
root      5897  0.0  0.0   3940   596 tty1     Ss+  21:01   0:00 /sbin/getty 38400 tty1
root      7651  0.4  1.0 152180 22208 ?        S    21:47   0:00 /usr/bin/python /usr/share/jockey/jockey-backend
root      7824  2.7  2.4 129104 50124 tty7     SLs+ 21:47   0:05 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
****      7859  0.0  0.1  62400  2332 ?        S    21:48   0:00 /usr/bin/gnome-keyring-daemon -d --login
****      7869  0.0  0.3 147684  6692 ?        Ssl  21:48   0:00 x-session-manager
****      8007  0.0  0.0  25868   708 ?        S    21:48   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/pulse-session /usr/bin/seahorse-agent --execute x-s
****      8008  0.0  0.0  21640  1240 ?        Ss   21:48   0:00 //bin/dbus-daemon --fork --print-pid 6 --print-address 9 --session
****      8011  0.0  0.2 154808  4496 ?        Ssl  21:48   0:00 /usr/bin/pulseaudio -D --log-target=syslog
****      8014  0.0  0.1  61640  2996 ?        S    21:48   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
****      8016  0.1  0.3  46688  6632 ?        S    21:48   0:00 /usr/lib/libgconf2-4/gconfd-2
****      8022  0.0  0.3 142980  7256 ?        Ss   21:48   0:00 /usr/bin/seahorse-agent --execute x-session-manager
****      8025  0.0  0.1  44920  2344 ?        S    21:48   0:00 /usr/lib/gvfs/gvfsd
****      8031  0.0  0.1  62428  2284 ?        Ssl  21:48   0:00 /usr/lib/gvfs//gvfs-fuse-daemon /home/seth/.gvfs
****      8037  0.0  0.2 115884  4192 ?        S    21:48   0:00 /usr/lib/gnome-session/helpers/gnome-keyring-daemon-wrapper
****      8040  0.2  1.1 278892 23420 ?        Ssl  21:48   0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
****      8041  0.0  0.0   4020   636 ?        S    21:48   0:00 /bin/sh /usr/bin/compiz
****      8106  1.7  1.6 267468 33696 ?        SL   21:48   0:03 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding core ccp
****      8113  0.0  0.1 195720  3556 ?        Ss   21:48   0:00 gnome-screensaver
****      8114  0.0  0.0   4020   572 ?        Ss   21:48   0:00 /bin/sh -c /usr/bin/compiz-decorator
****      8115  0.0  0.0   4020   596 ?        S    21:48   0:00 /bin/sh /usr/bin/compiz-decorator
****      8117  0.0  0.6 144844 13748 ?        S    21:48   0:00 /usr/bin/gtk-window-decorator
****      8121  0.3  1.5 372368 31936 ?        S    21:48   0:00 gnome-panel
****      8122  0.1  1.5 421960 31360 ?        S    21:48   0:00 nautilus --no-desktop --browser
****      8125  0.0  0.1 152400  4084 ?        Ssl  21:48   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
****      8133  0.2  0.1  47556  3344 ?        S    21:48   0:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
****      8136  0.1  0.4 191776  9888 ?        S    21:48   0:00 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --o
****      8139  0.0  0.5 194036 12064 ?        S    21:48   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-io
****      8142  0.0  0.1  55288  2916 ?        S    21:48   0:00 /usr/lib/gvfs/gvfsd-trash --spawner :1.5 /org/gtk/gvfs/exec_spaw/0
****      8149  0.0  0.1  36916  2604 ?        S    21:48   0:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
****      8154  0.0  0.7 206484 16452 ?        S    21:48   0:00 /usr/lib/fast-user-switch-applet/fast-user-switch-applet --oaf-activate-iid=OAFIID:GNOME_FastUserSwit
****      8157  0.0  0.9 245996 19032 ?        Sl   21:48   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd
****      8161  0.0  0.1  44916  2400 ?        S    21:48   0:00 /usr/lib/gvfs/gvfsd-burn --spawner :1.5 /org/gtk/gvfs/exec_spaw/1
****      8173  0.0  1.0 198580 22548 ?        S    21:48   0:00 python -O /usr/lib/wicd/wicd-client.py
****      8174  0.0  0.4  72844  8812 ?        SNl  21:48   0:00 trackerd
****      8176  0.0  0.3 123960  6404 ?        S    21:48   0:00 tracker-applet
****      8178  0.0  0.8 212124 16876 ?        S    21:48   0:00 update-notifier
****      8179  0.0  0.8 209360 17628 ?        S    21:48   0:00 python /usr/share/system-config-printer/applet.py
****      8182  0.0  0.5 213832 10388 ?        Ss   21:48   0:00 gnome-power-manager
****      8197  3.8  4.3 496808 89944 ?        Sl   21:48   0:07 /usr/lib/firefox-3.0.8/firefox
****      8269  0.3  1.4 284096 29600 ?        Rl   21:49   0:00 gnome-terminal
****      8273  0.0  0.0  19452   880 ?        S    21:49   0:00 gnome-pty-helper
****      8274  0.0  0.1  20816  3684 pts/0    Ss   21:49   0:00 bash
****      8319  0.0  0.0  15164  1128 pts/0    R+   21:51   0:00 ps aux

```

If I add up all the memory usage, it isn't anywhere near the 66% indicated by free (used - [buffers + cache]).

What is using the other memory?  Any ideas would be greatly appreciated!

Cheers!

---

### Post by Xiangxianni on 2009-04-08
Try to input "F" then "N" in your top window to find the total physical memory used by processes.For other memory ,I think they are been cached,just my opinions!

---

### Post by hyper_ch on 2009-04-08
I see that 1.4 GB are cache

---

### Post by blueb73 on 2009-04-13
I am having this same problem.

Not as good with the command line, but when I use system monitor, it will show me using large amounts of memory, but if I look at the processes running, it doesnt add up to anywhere close what is being claimed.

Any ideas what might be causing this?

thanks!

---

### Post by hyper_ch on 2009-04-14
unused ram = wasted ram

---

