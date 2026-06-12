---
title: "Konsole Slow to open and switch to."
date: 2008-12-11
forum: Desktop Environments
---

### Post by va1ha11a on 2008-12-11
I have a strange issue with my server (running a KDE desktop)

I have a hard disk failure (mounted at /usr) I then rebuilt the system by making a list of installed packages then I reinstalled keeping home and copies of etc.

After I reinstalled i reloaded etc and all the packages. Most stuff is working fine but there is one issue that has me stumped.

If I open a konsole window the window appears relatively quickly however the window is blank for over 1 min before the shell shows up and again if i open a new tab the same issue also if i switch to another window I have to wait again.

Any Ideas?
N.B. it was working fine before the reinstall.

---

### Post by va1ha11a on 2008-12-12
Hmm, I just noticed that it seems to start 2 processes when I open a konsole window...

hmm again...looks like it keeps spawning more konsle processes.... i'm stumped what is causing this.

one more time, looks like the same thing on kdesu also :(

---

### Post by va1ha11a on 2008-12-15
Hmm not getting much atcion here, but I thought I would post all the running processes anyway, many seem to be duplicated to me.

```

  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:02 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:02 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:04 migration/2
   10 ?        00:00:00 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:07 migration/3
   13 ?        00:00:00 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:01 events/0
   16 ?        00:00:01 events/1
   17 ?        00:00:01 events/2
   18 ?        00:00:01 events/3
   19 ?        00:00:00 khelper
   56 ?        00:00:06 kblockd/0
   57 ?        00:00:02 kblockd/1
   58 ?        00:00:00 kblockd/2
   59 ?        00:00:00 kblockd/3
   62 ?        00:00:00 kacpid
   63 ?        00:00:00 kacpi_notify
  151 ?        00:00:00 kseriod
  187 ?        00:00:00 pdflush
  188 ?        00:00:02 pdflush
  189 ?        00:00:08 kswapd0
  231 ?        00:00:00 aio/0
  232 ?        00:00:00 aio/1
  233 ?        00:00:00 aio/2
  234 ?        00:00:00 aio/3
 1364 ?        00:00:00 ksnapd
 1683 ?        00:00:00 ksuspend_usbd
 1686 ?        00:00:00 khubd
 1812 ?        00:00:06 ata/0
 1813 ?        00:00:02 ata/1
 1814 ?        00:00:00 ata/2
 1815 ?        00:00:00 ata/3
 1816 ?        00:00:00 ata_aux
 1840 ?        00:00:00 khpsbpkt
 2091 ?        00:00:00 scsi_eh_0
 2092 ?        00:00:21 scsi_eh_1
 2135 ?        00:00:00 knodemgrd_0
 2671 ?        00:00:00 scsi_eh_2
 3125 ?        00:00:00 scsi_eh_3
 3288 ?        00:00:24 firefox
 3569 ?        00:00:00 scsi_eh_4
 3570 ?        00:00:00 scsi_eh_5
 3571 ?        00:00:00 scsi_eh_6
 3572 ?        00:00:00 scsi_eh_7
 3574 ?        00:00:00 scsi_eh_8
 3575 ?        00:00:00 scsi_eh_9
 3576 ?        00:00:00 scsi_eh_10
 3577 ?        00:00:00 scsi_eh_11
 3981 ?        00:00:08 kjournald
 4185 ?        00:00:00 udevd
 4628 ?        00:00:00 edac-poller
 4692 ?        00:00:00 kpsmoused
 4788 ?        00:00:00 kgameportd
 6024 ?        00:00:00 kjournald
 6025 ?        00:00:00 kjournald
 6026 ?        00:00:00 kjournald
 6027 ?        00:00:00 kjournald
 6029 ?        00:00:00 kjournald
 6358 tty4     00:00:00 getty
 6359 tty5     00:00:00 getty
 6361 tty2     00:00:00 getty
 6363 tty3     00:00:00 getty
 6366 tty6     00:00:00 getty
 6572 ?        00:00:00 acpid
 6621 ?        00:00:00 kondemand/0
 6622 ?        00:00:00 kondemand/1
 6623 ?        00:00:00 kondemand/2
 6624 ?        00:00:00 kondemand/3
 6723 ?        00:00:00 syslogd
 6785 ?        00:00:00 dd
 6787 ?        00:00:00 klogd
 6811 ?        00:00:00 dbus-daemon
 6839 ?        00:00:00 kdm
 6845 tty7     00:07:56 Xorg
 6854 ?        00:00:00 kdm
 6878 ?        00:00:14 named
 6916 ?        00:00:00 sshd
 6951 ?        00:00:00 avahi-daemon
 6952 ?        00:00:00 avahi-daemon
 6999 ?        00:00:00 cupsd
 7037 ?        00:00:00 mysqld_safe
 7079 ?        00:00:52 mysqld
 7080 ?        00:00:00 logger
 7185 ?        00:04:14 atieventsd
 7383 ?        00:00:00 freshclam
 7431 ?        00:00:03 ddclient
 7581 ?        00:00:01 master
 7602 ?        00:00:00 qmgr
 7650 ?        00:00:01 nmbd
 7652 ?        00:00:00 smbd
 7671 ?        00:00:00 smbd
 7716 ?        00:00:00 winbindd
 7722 ?        00:00:00 winbindd
 7762 ?        00:00:00 xinetd
 7831 ?        00:00:03 dovecot
 7838 ?        00:00:02 dovecot-auth
 7873 ?        00:00:02 ntpd
 7904 ?        00:00:02 hald
 7907 ?        00:00:00 console-kit-dae
 7908 ?        00:00:00 hald-runner
 7989 ?        00:00:04 imap-login
 7990 ?        00:00:03 imap-login
 7991 ?        00:00:03 imap-login
 8010 ?        00:00:00 hald-addon-acpi
 8024 ?        00:00:00 hald-addon-inpu
 8052 ?        00:00:03 hald-addon-stor
 8069 ?        00:00:19 hald-addon-stor
 8097 ?        00:00:00 mdadm
 8134 ?        00:00:00 dhcpd3
 8248 ?        00:00:00 atd
 8264 ?        00:00:00 cron
 8343 ?        00:00:03 apache2
 8434 ?        00:00:00 apache2
 8435 ?        00:00:00 apache2
 8436 ?        00:00:00 apache2
 8437 ?        00:00:00 apache2
 8438 ?        00:00:00 apache2
 9325 ?        00:00:00 kio_file
 9546 ?        00:00:00 kio_uiserver
 9908 ?        00:00:00 kio_uiserver
10213 tty1     00:00:00 getty
10269 ?        00:00:00 kio_uiserver
10612 ?        00:00:00 kio_uiserver
10974 ?        00:00:00 kio_uiserver
11335 ?        00:00:00 kio_uiserver
11523 ?        00:00:00 startkde
11666 ?        00:00:00 ssh-agent
11667 ?        00:00:00 ssh-agent
11681 ?        00:00:00 kio_uiserver
11718 ?        00:00:00 start_kdeinit
11719 ?        00:00:00 kdeinit
11722 ?        00:00:00 dcopserver
11725 ?        00:00:01 klauncher
11745 ?        00:00:09 kded
11786 ?        00:00:00 kwrapper
11788 ?        00:00:00 ksmserver
11789 ?        00:00:03 kwin
11800 ?        00:00:04 kdesktop
11811 ?        00:00:10 kicker
11833 ?        00:00:00 kio_uiserver
11876 ?        00:00:45 artsd
11880 ?        00:00:00 kaccess
11899 ?        00:00:00 katapult
11903 ?        00:00:00 krandrtray
11905 ?        00:00:00 kmix
11928 ?        00:00:05 knotify
11933 ?        00:00:20 klipper
11956 ?        00:00:09 adept_notifier
12063 ?        00:00:00 kio_uiserver
12133 ?        00:00:00 pickup
12713 ?        00:00:00 xterm
12714 pts/1    00:00:00 bash
13577 ?        00:00:00 apache2
14172 pts/1    00:00:00 ps
16457 ?        00:03:57 snort
20397 ?        00:00:00 konqueror
23016 ?        00:00:00 kdesktop
23377 ?        00:00:00 kdesktop
23677 ?        00:00:00 sshd
23697 ?        00:05:03 sshd
23698 ?        00:01:00 sftp-server
23750 ?        00:00:00 kdesktop
24093 ?        00:01:55 kdesktop
24385 ?        00:00:00 dbus-launch
24386 ?        00:00:00 dbus-daemon
25137 ?        00:00:00 kio_uiserver
25480 ?        00:00:00 kio_uiserver
25843 ?        00:00:00 kio_uiserver
26029 ?        00:00:00 winbindd
26030 ?        00:00:00 winbindd
26213 ?        00:00:00 kio_uiserver
27363 ?        00:00:00 gconfd-2

```

---

