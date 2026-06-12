---
title: "Sooo many!!.automatix doesnt start!!1 nm-applet 20 threads????"
date: 2006-03-10
forum: Desktop Environments
---

### Post by sherlock-holmes on 2006-03-10
Hello,

here is the output of ps -e on my box.

 [PHP]PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
    5 ?        00:00:00 kthread
    7 ?        00:00:00 kacpid
  102 ?        00:00:00 kblockd/0
  126 ?        00:00:00 pdflush
  127 ?        00:00:00 pdflush
  129 ?        00:00:00 aio/0
  128 ?        00:00:00 kswapd0
  714 ?        00:00:00 kseriod
 1898 ?        00:00:00 khubd
 3044 ?        00:00:00 kjournald
 3096 ?        00:00:00 udevd
 4384 ?        00:00:00 pccardd
 4439 ?        00:00:00 pccardd
 4573 ?        00:00:00 cardmgr
 5063 ?        00:00:00 shpchpd_event
 5756 ?        00:00:00 ipw2200/0
 6009 ?        00:00:00 kIrDAd
 6814 ?        00:00:00 acpid
 6829 ?        00:00:00 syslogd
 6846 ?        00:00:00 dd
 6848 ?        00:00:00 klogd
 6861 ?        00:01:15 dbus-daemon
 6874 ?        00:00:01 hald
 6879 ?        00:00:00 hald-addon-acpi
 6891 ?        00:00:07 hald-addon-stor
 6907 ?        00:00:06 NetworkManager
 6919 ?        00:00:00 NetworkManagerD
 7323 ?        00:00:00 gdm
 7328 ?        00:00:00 gdm
 7373 ?        00:09:32 Xorg
 7404 ?        00:00:13 cupsd
 7427 ?        00:00:00 hpiod
 7471 ?        00:00:01 python
 7629 ?        00:00:00 powernowd
 7642 ?        00:00:00 cron
 7815 ?        00:00:00 su
 7816 ?        00:00:00 bash
 7817 ?        00:00:00 lm_TMW.ld
 7818 ?        00:00:00 sh
 7820 ?        00:00:00 lm_TMW.vd1
 7845 tty1     00:00:00 getty
 7846 tty2     00:00:00 getty
 7847 tty3     00:00:00 getty
 7848 tty4     00:00:00 getty
 7849 tty5     00:00:00 getty
 7850 tty6     00:00:00 getty
 7875 ?        00:00:01 x-session-manag
 7915 ?        00:00:00 ssh-agent
 7918 ?        00:00:00 dbus-launch
 7919 ?        00:00:00 dbus-daemon
 7921 ?        00:00:02 gconfd-2
 7957 ?        00:00:00 gnome-keyring-d
 7959 ?        00:00:01 esd
 7963 ?        00:00:00 bonobo-activati
 7965 ?        00:00:02 gnome-settings-
 7971 ?        00:00:00 gam_server
 7983 ?        00:00:01 xscreensaver
 8010 ?        00:00:25 metacity
 8012 ?        00:00:00 gnome-volume-ma
 8014 ?        00:00:17 gnome-panel
 8016 ?        00:00:02 nautilus
 8050 ?        00:00:13 wnck-applet
 8053 ?        00:00:01 trashapplet
 8055 ?        00:00:00 gnome-vfs-daemo
 8057 ?        00:00:06 nm-applet
 8059 ?        00:00:06 nm-applet
 8064 ?        00:00:00 update-notifier
 8069 ?        00:00:18 gnome-cups-icon
 8071 ?        00:00:05 nm-applet
 8077 ?        00:00:05 nm-applet
 8088 ?        00:00:02 notification-da
 8108 ?        00:00:00 dhcdbd
 8112 ?        00:00:00 mapping-daemon
 8135 ?        00:00:01 notification-ar
 8137 ?        00:00:01 gnome-netstatus
 8139 ?        00:00:01 battstat-applet
 8141 ?        00:00:00 mixer_applet2
 8143 ?        00:00:24 clock-applet
11572 ?        00:00:00 dhclient
18711 ?        00:00:01 gnome-terminal
18712 ?        00:00:00 gnome-pty-helpe
18713 pts/0    00:00:00 bash
18745 pts/1    00:00:00 bash
18760 ?        00:00:00 nm-applet
18766 ?        00:00:00 nm-applet
18771 ?        00:00:00 nm-applet
18778 ?        00:00:00 nm-applet
18783 ?        00:00:00 nm-applet
18790 ?        00:00:00 nm-applet
18798 ?        00:00:00 nm-applet
18805 ?        00:00:00 nm-applet
18811 ?        00:00:00 nm-applet
18815 ?        00:00:00 nm-applet
18822 ?        00:00:00 nm-applet
18826 ?        00:00:00 nm-applet
18831 ?        00:00:00 nm-applet
18835 ?        00:00:00 nm-applet
18842 ?        00:00:00 nm-applet
18846 ?        00:00:00 nm-applet
18850 pts/0    00:00:00 ps[/PHP]

and I cannot start automatix  too. problem working with FF1.5 etc....why is nm-applet running these many threads? any clue? please advise!!!

---

### Post by sherlock-holmes on 2006-03-11
bump ...[-(

---

