---
title: "Problem with last.fm scrobbler not reporting."
date: 2007-08-09
forum: Desktop Environments
---

### Post by Burbruee on 2007-08-09
Hi, I hope I put this in the correct forum, so many categories. 

Yesterday, I started using Amarok instead of XMMS which is what I normally use, and I really liked it, it reported my songs fine to last.fm after I had put in my username and password in the settings.

But suddenly, Amarok crashed as I was builing up my playlist by dragging and dropping.
After that, I can no longer get it to report songs for last.fm. :confused:
So I tried XMMS with scrobbler plugin, and it's the same problem.. It doesn't report back to last.fm server.

Anyway, I decided I better stick with XMMS again, Amarok seemed to use up quite a bit of resources. I think it kept scanning for media forever, causing online games to lag so much it was unplayable. I had to switch back to XMMS.

So, I tried to go into my .xmms folder and remove the scrobblerqueue.txt and touch it again. But it keeps filling it up with about 30 songs now. 
If I delete it and recreate it, it puts all songs back in the file. :(

Any ideas what could be the problem? It worked fine until yesterday when Amarok crashed. :confused:
Username and Password is correct in the audioscrobbler plugin for XMMS, and is activated.

---

### Post by tgalati4 on 2007-08-09
There is probably an audioscrobbler daemon that is hung in your process table.  

>ps -ef

to get a list of processes.  Kill the one that looks like a scrobbler.  I don't know what it is called off hand.  Restart xmms and see if starts scrobbling again.  There is a delay before tracks show up in last.fm.  The delay depends on how busy the site is.

---

### Post by Burbruee on 2007-08-09
Thanks.
I also tried to restart my system, but XMMS still does not seem to report correctly to last.fm.
And Amarok gives me the message that it failed to submit 8 tracks to last.fm

I can't seem to find any related process, I'll post the output here:

```

  PID TTY      STAT   TIME COMMAND
    1 ?        Ss     0:01 /sbin/init
    2 ?        S      0:00 [migration/0]
    3 ?        SN     0:00 [ksoftirqd/0]
    4 ?        S      0:00 [watchdog/0]
    5 ?        S<     0:00 [events/0]
    6 ?        S<     0:00 [khelper]
    7 ?        S<     0:00 [kthread]
   30 ?        S<     0:00 [kblockd/0]
   31 ?        S<     0:00 [kacpid]
   32 ?        S<     0:00 [kacpi_notify]
  151 ?        S<     0:00 [kseriod]
  176 ?        S      0:00 [pdflush]
  177 ?        S      0:00 [pdflush]
  178 ?        S<     0:00 [kswapd0]
  179 ?        S<     0:00 [aio/0]
 1996 ?        S<     0:00 [ksuspend_usbd]
 1997 ?        S<     0:00 [khubd]
 2025 ?        S<     0:00 [ata/0]
 2026 ?        S<     0:00 [ata_aux]
 2034 ?        S<     0:00 [khpsbpkt]
 2225 ?        S<     0:00 [scsi_eh_0]
 2226 ?        S<     0:00 [usb-storage]
 2268 ?        S<     0:00 [knodemgrd_0]
 2471 ?        S<     0:00 [kjournald]
 2671 ?        S<s    0:00 /sbin/udevd --daemon
 3612 ?        S<     0:00 [kpsmoused]
 3698 ?        S<     0:00 [kgameportd]
 4185 ?        Ss     0:00 /sbin/mount.ntfs-3g /dev/disk/by-uuid/B604FA1004F9D2FB /media/C -o rw,locale=sv_SE.UTF-8
 4189 ?        Ss     0:00 /sbin/mount.ntfs-3g /dev/disk/by-uuid/F2445017444FDCCB /media/D -o rw,locale=sv_SE.UTF-8
 4193 ?        Ss     0:00 /sbin/mount.ntfs-3g /dev/disk/by-uuid/F03C7D6C3C7D2F2A /media/E -o rw,locale=sv_SE.UTF-8
 4197 ?        Ss     0:00 /sbin/mount.ntfs-3g /dev/disk/by-uuid/1CB80292B8026B1A /media/F -o rw,locale=sv_SE.UTF-8
 4477 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 4478 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 4481 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 4483 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 4484 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 4485 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 4723 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 4825 ?        Ss     0:00 /sbin/syslogd
 4883 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 4885 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 4906 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 4922 ?        Ss     0:00 /usr/sbin/hald
 4923 ?        S      0:00 hald-runner
 4929 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event1
 4930 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event4
 4931 ?        S      0:00 hald-addon-keyboard: listening on /dev/input/event5
 4934 ?        S      0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
 4943 ?        S      0:00 hald-addon-storage: polling /dev/hdb (every 2 sec)
 4951 ?        S      0:00 hald-addon-storage: polling /dev/sda (every 2 sec)
 4954 ?        S      0:00 hald-addon-storage: polling /dev/sdb (every 2 sec)
 4956 ?        S      0:00 hald-addon-storage: polling /dev/sdc (every 2 sec)
 4958 ?        S      0:00 hald-addon-storage: polling /dev/sdd (every 2 sec)
 4971 ?        Ss     0:00 /usr/sbin/dhcdbd --system
 4986 ?        Ssl    0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
 5018 ?        Ss     0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
 5033 ?        Ss     0:00 /usr/bin/system-tools-backends
 5034 ?        S      0:00 dbus-daemon --session --print-address --nofork
 5087 ?        Ss     0:00 /usr/sbin/cupsd
 5132 ?        Ss     0:00 /usr/sbin/hpiod
 5135 ?        S      0:00 python /usr/sbin/hpssd
 5252 ?        Ss     0:00 /usr/sbin/hcid -x -s
 5269 ?        S<     0:00 [krfcommd]
 5279 ?        S      0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
 5299 ?        Ss     0:00 proftpd: (accepting connections)
 5332 ?        Ss     0:00 /usr/sbin/atd
 5346 ?        Ss     0:00 /usr/sbin/cron
 5419 ?        Ss     0:00 /usr/bin/kdm
 5438 tty7     Ss+    0:18 /usr/bin/X -br -nolisten tcp :0 vt7 -auth /var/run/xauth/A:0-UYf49J
 5458 ?        S      0:00 -:0
 5552 ?        S<s    0:00 avahi-autoipd: [eth1] bound 169.254.3.190
 5553 ?        S<s    0:00 avahi-autoipd: [eth1] callout dispatcher
 5557 ?        S<s    0:00 dhclient3 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases eth1
 5575 ?        Ss     0:00 /bin/sh /usr/bin/startkde
 5623 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
 5626 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/startkde
 5627 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
 5662 ?        S      0:00 start_kdeinit --new-startup +kcminit_startup
 5663 ?        Ss     0:00 kdeinit Running...
 5666 ?        S      0:00 dcopserver [kdeinit] --nosid
 5669 ?        S      0:00 klauncher [kdeinit] --new-startup
 5671 ?        S      0:01 kded [kdeinit] --new-startup
 5676 ?        S      0:00 kwrapper ksmserver
 5678 ?        S      0:00 ksmserver [kdeinit]
 5679 ?        S      0:01 kwin [kdeinit] -session 1016c1c21ab1aa000118663433900000072170028_1186669658_329624
 5681 ?        S      0:02 kdesktop [kdeinit]
 5683 ?        S      0:02 kicker [kdeinit]
 5685 ?        S      0:00 kio_file [kdeinit] file /tmp/ksocket-burbruee/klauncherCjdaNa.slave-socket /tmp/ksocket-burbruee/kdesktopVDgMlb.slav
 5691 ?        S      0:00 kio_uiserver [kdeinit]
 5706 ?        S      0:01 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f
 5709 ?        S      0:00 kaccess [kdeinit]
 5712 ?        S      0:00 kmix [kdeinit] -session 10d8cecf96000111065458100000063760027_1186669658_275066
 5713 ?        S      0:00 katapult -session 10d9d39668000112680660600000081280032_1186669658_266475
 5714 ?        S      0:00 konqueror [kdeinit] -session 1016c1c21ab1aa000118660112800000214450055_1186669658_266676
 5720 ?        S      0:00 aspell -a -S -C -Tutf8 --encoding=utf-8
 5724 ?        S      0:01 kopete -session 1016c1c21ab1aa000118660686200000214450060_1186669658_266863
 5725 ?        Sl     0:03 skype -session 1016c1c21ab1aa000118660174800000214450058_1186669658_267125
 5733 ?        S      0:02 konqueror [kdeinit] --preload
 5748 ?        S      0:00 knotify [kdeinit]
 5753 ?        S      0:00 klipper [kdeinit]
 5772 ?        S      0:00 knetworkmanager [kdeinit]
 5775 ?        S      0:00 /usr/bin/yakuake
 5777 ?        S      0:00 /usr/bin/passkey-agent --default /usr/lib/kdebluetooth/kbluepin
 5779 ?        S      0:00 kbluetoothd --dontforceshow
 5780 ?        S      0:02 adept_notifier
 5802 pts/1    Ss     0:00 /bin/bash
 5826 ?        S      0:00 kwalletmanager --kwalletd
 5875 ?        S      0:07 konqueror [kdeinit] --preload
 5927 ?        S      0:00 kio_http [kdeinit] http /tmp/ksocket-burbruee/klauncherCjdaNa.slave-socket /tmp/ksocket-burbruee/konquerorZPNIBa.sla
 5931 ?        S      0:00 kio_http [kdeinit] http /tmp/ksocket-burbruee/klauncherCjdaNa.slave-socket /tmp/ksocket-burbruee/konquerorz3j2gc.sla
 5932 ?        S      0:00 kio_http [kdeinit] http /tmp/ksocket-burbruee/klauncherCjdaNa.slave-socket /tmp/ksocket-burbruee/konquerorJM70hb.sla
 5933 ?        S      0:00 kio_http [kdeinit] http /tmp/ksocket-burbruee/klauncherCjdaNa.slave-socket /tmp/ksocket-burbruee/konquerorNNhTTb.sla
 5934 ?        S      0:00 kio_http [kdeinit] http /tmp/ksocket-burbruee/klauncherCjdaNa.slave-socket /tmp/ksocket-burbruee/konquerorbBLpvc.sla
 5938 ?        S      0:00 kio_http [kdeinit] http /tmp/ksocket-burbruee/klauncherCjdaNa.slave-socket /tmp/ksocket-burbruee/konqueroreHO6sa.sla
 5969 ?        S      0:00 aspell -a -S -C -Tutf8 --encoding=utf-8
 6006 pts/1    R+     0:00 ps -ax


```

---

### Post by Burbruee on 2007-08-10
Help?

---

