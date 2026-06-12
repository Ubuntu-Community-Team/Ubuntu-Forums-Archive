---
title: "Constant Hard Drive activity"
date: 2009-04-30
forum: General Help
---

### Post by mtbdrew on 2009-04-30
Hello,

I have a Mythbuntu system now running 9.04 that shows a constant flashing hard drive light. I've searched the forums and have tried the settings listed:

[http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

As well as killing the mythbackend, I've also re-configured the Mysql settings but none of these things have helped. 

The thing is I noticed this started about two weeks ago on 8.10 after installing updates and is one of the reasons I went ahead and did a clean install of 9.04. Any ideas on what's causing this or what I need to check. The forums as well as web search seems to show this a pretty common situation that has started recently but no one seems to have come up with an answer.

Thanks in advance
Andrew

---

### Post by cmnorton on 2009-04-30
Start by finding out what's running ps -ef > ps.out

---

### Post by mtbdrew on 2009-04-30
> **cmnorton said:**
> Start by finding out what's running ps -ef > ps.out

Hello and thanks for the reply. When I run this in a terminal I don't see any output. Am I supposed to see results in the terminal window or is there a file somewhere?

BR
Andrew

---

### Post by cmnorton on 2009-04-30
You're directing the output to a file named ps.out. I suggested you do that to have a record of what's there. You can also pipe it out to less

ps -ef | less

so, stuff will page and you can look at your leisure.

---

### Post by mtbdrew on 2009-05-04
> **cmnorton said:**
> You're directing the output to a file named ps.out. I suggested you do that to have a record of what's there. You can also pipe it out to less

ps -ef | less

so, stuff will page and you can look at your leisure.

Here's the results:

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 22:24 ?        00:00:01 /sbin/init
root         2     0  0 22:24 ?        00:00:00 [kthreadd]
root         3     2  0 22:24 ?        00:00:00 [migration/0]
root         4     2  0 22:24 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 22:24 ?        00:00:00 [watchdog/0]
root         6     2  0 22:24 ?        00:00:00 [migration/1]
root         7     2  0 22:24 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 22:24 ?        00:00:00 [watchdog/1]
root         9     2  0 22:24 ?        00:00:00 [events/0]
root        10     2  0 22:24 ?        00:00:00 [events/1]
root        11     2  0 22:24 ?        00:00:00 [khelper]
root        12     2  0 22:24 ?        00:00:00 [kstop/0]
root        13     2  0 22:24 ?        00:00:00 [kstop/1]
root        14     2  0 22:24 ?        00:00:00 [kintegrityd/0]
root        15     2  0 22:24 ?        00:00:00 [kintegrityd/1]
root        16     2  0 22:24 ?        00:00:00 [kblockd/0]
root        17     2  0 22:24 ?        00:00:00 [kblockd/1]
root        18     2  0 22:24 ?        00:00:00 [kacpid]
root        19     2  0 22:24 ?        00:00:00 [kacpi_notify]
root        20     2  0 22:24 ?        00:00:00 [cqueue]
root        21     2  0 22:24 ?        00:00:00 [ata/0]
root        22     2  0 22:24 ?        00:00:00 [ata/1]
root        23     2  0 22:24 ?        00:00:00 [ata_aux]
root        24     2  0 22:24 ?        00:00:00 [ksuspend_usbd]
root        25     2  0 22:24 ?        00:00:00 [khubd]
root        26     2  0 22:24 ?        00:00:00 [kseriod]
root        27     2  0 22:24 ?        00:00:00 [kmmcd]
root        28     2  0 22:24 ?        00:00:00 [btaddconn]
root        29     2  0 22:24 ?        00:00:00 [btdelconn]
root        30     2  0 22:24 ?        00:00:00 [pdflush]
root        31     2  0 22:24 ?        00:00:00 [pdflush]
root        32     2  0 22:24 ?        00:00:00 [kswapd0]

---

### Post by mtbdrew on 2009-05-06
bump

---

### Post by mtbdrew on 2009-05-07
Any ideas?

---

### Post by ookmarc on 2009-05-07
> **mtbdrew said:**
> Any ideas?
The list you posted looks like the first page. Nothing helpful there; post the whole output file (written when the disk activity occurs). Is the disk access permanent? Or does it happen only occasionally?
There are a lot of cron processes that may access the drive at hourly,daily or weekly intervals.

---

### Post by mtbdrew on 2009-05-08
> **ookmarc said:**
> The list you posted looks like the first page. Nothing helpful there; post the whole output file (written when the disk activity occurs). Is the disk access permanent? Or does it happen only occasionally?
There are a lot of cron processes that may access the drive at hourly,daily or weekly intervals.

Okay I'll get the whole thing when I get home. The activity is 24/7 every 2 seconds.

---

### Post by mtbdrew on 2009-05-09
> **ookmarc said:**
> The list you posted looks like the first page. Nothing helpful there; post the whole output file (written when the disk activity occurs). Is the disk access permanent? Or does it happen only occasionally?
There are a lot of cron processes that may access the drive at hourly,daily or weekly intervals.

Here the complete list:

UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 20:39 ?        00:00:01 /sbin/init
root         2     0  0 20:39 ?        00:00:00 [kthreadd]
root         3     2  0 20:39 ?        00:00:00 [migration/0]
root         4     2  0 20:39 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 20:39 ?        00:00:00 [watchdog/0]
root         6     2  0 20:39 ?        00:00:00 [migration/1]
root         7     2  0 20:39 ?        00:00:00 [ksoftirqd/1]
root         8     2  0 20:39 ?        00:00:00 [watchdog/1]
root         9     2  0 20:39 ?        00:00:00 [events/0]
root        10     2  0 20:39 ?        00:00:00 [events/1]
root        11     2  0 20:39 ?        00:00:00 [khelper]
root        12     2  0 20:39 ?        00:00:00 [kstop/0]
root        13     2  0 20:39 ?        00:00:00 [kstop/1]
root        14     2  0 20:39 ?        00:00:00 [kintegrityd/0]
root        15     2  0 20:39 ?        00:00:00 [kintegrityd/1]
root        16     2  0 20:39 ?        00:00:00 [kblockd/0]
root        17     2  0 20:39 ?        00:00:00 [kblockd/1]
root        18     2  0 20:39 ?        00:00:00 [kacpid]
root        19     2  0 20:39 ?        00:00:00 [kacpi_notify]
root        20     2  0 20:39 ?        00:00:00 [cqueue]
root        21     2  0 20:39 ?        00:00:00 [ata/0]
root        22     2  0 20:39 ?        00:00:00 [ata/1]
root        23     2  0 20:39 ?        00:00:00 [ata_aux]
root        24     2  0 20:39 ?        00:00:00 [ksuspend_usbd]
root        25     2  0 20:39 ?        00:00:00 [khubd]
root        26     2  0 20:39 ?        00:00:00 [kseriod]
root        27     2  0 20:39 ?        00:00:00 [kmmcd]
root        28     2  0 20:39 ?        00:00:00 [btaddconn]
root        29     2  0 20:39 ?        00:00:00 [btdelconn]
root        30     2  0 20:39 ?        00:00:00 [pdflush]
root        31     2  0 20:39 ?        00:00:00 [pdflush]
root        32     2  0 20:39 ?        00:00:00 [kswapd0]
root        33     2  0 20:39 ?        00:00:00 [aio/0]
root        34     2  0 20:39 ?        00:00:00 [aio/1]
root        35     2  0 20:39 ?        00:00:00 [ecryptfs-kthrea]
root        38     2  0 20:39 ?        00:00:00 [scsi_eh_0]
root        39     2  0 20:39 ?        00:00:00 [scsi_eh_1]
root        40     2  0 20:39 ?        00:00:00 [scsi_eh_2]
root        41     2  0 20:39 ?        00:00:00 [scsi_eh_3]
root        42     2  0 20:39 ?        00:00:00 [kstriped]
root        43     2  0 20:39 ?        00:00:00 [kmpathd/0]
root        44     2  0 20:39 ?        00:00:00 [kmpathd/1]
root        45     2  0 20:39 ?        00:00:00 [kmpath_handlerd]
root        46     2  0 20:39 ?        00:00:00 [ksnapd]
root        47     2  0 20:39 ?        00:00:00 [kondemand/0]
root        48     2  0 20:39 ?        00:00:00 [kondemand/1]
root        49     2  0 20:39 ?        00:00:00 [krfcommd]
root       719     2  0 20:39 ?        00:00:00 [kjournald]
root       853     1  0 20:40 ?        00:00:00 /sbin/udevd --daemon
root      1501     2  0 20:40 ?        00:00:00 [kpsmoused]
root      1531     1  0 20:40 ?        00:00:00 /usr/sbin/lircd -d /dev/lirc1 --output=/dev/lircd1 --listen
root      1533     1  0 20:40 ?        00:00:00 /usr/sbin/lircd -d /dev/lirc0 --output=/dev/lircd --connect=localhost 8765 --pidfile=/var/run/lircd2.pid
root      1551     2  0 20:40 ?        00:00:00 [saa7133[0]]
root      1994     2  0 20:40 ?        00:00:00 [xfs_mru_cache]
root      1997     2  0 20:40 ?        00:00:00 [xfslogd/0]
root      2003     2  0 20:40 ?        00:00:00 [xfslogd/1]
root      2004     2  0 20:40 ?        00:00:00 [xfsdatad/0]
root      2005     2  0 20:40 ?        00:00:00 [xfsdatad/1]
root      2006     2  0 20:40 ?        00:00:00 [xfsbufd]
root      2007     2  0 20:40 ?        00:00:00 [xfsaild]
root      2012     2  0 20:40 ?        00:00:00 [xfssyncd]
root      2276     1  0 20:40 tty4     00:00:00 /sbin/getty 38400 tty4
root      2277     1  0 20:40 tty5     00:00:00 /sbin/getty 38400 tty5
root      2287     1  0 20:40 tty2     00:00:00 /sbin/getty 38400 tty2
root      2288     1  0 20:40 tty3     00:00:00 /sbin/getty 38400 tty3
root      2291     1  0 20:40 tty6     00:00:00 /sbin/getty 38400 tty6
root      2356     1  0 20:40 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
syslog    2401     1  0 20:40 ?        00:00:00 /sbin/syslogd -u syslog
109       2424     1  0 20:40 ?        00:00:00 /bin/dbus-daemon --system
root      2492     1  0 20:40 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
nobody    2593     1  0 20:40 ?        00:00:02 /usr/local/sbin/LCDd
112       2791     1  0 20:40 ?        00:00:00 /usr/sbin/hald
root      2796     1  0 20:40 ?        00:00:00 /usr/sbin/console-kit-daemon
root      2865  2791  0 20:40 ?        00:00:00 hald-runner
root      2926  2865  0 20:40 ?        00:00:00 hald-addon-input: Listening on /dev/input/event1 /dev/input/event0 /dev/input/event3 /dev/input/event4
root      3004  2865  0 20:40 ?        00:00:00 /usr/lib/hal/hald-addon-cpufreq
112       3006  2865  0 20:40 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
root      3009  2865  0 20:40 ?        00:00:00 hald-addon-storage: polling /dev/sr0 (every 2 sec)
mythtv    3043     1  1 20:40 ?        00:00:30 /usr/bin/mythbackend --daemon --logfile /var/log/mythtv/mythbackend.log --pidfile /var/run/mythtv/mythbackend.pid
root      3067     2  0 20:40 ?        00:00:01 [kdvb-ad-0-fe-16]
root      3068     1  0 20:40 ?        00:00:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      3069  3068  0 20:40 ?        00:00:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      3075  3069  2 20:40 tty7     00:00:41 /usr/bin/X :0 -br -audit 0 -dpi 100 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
root      3080     2  0 20:40 ?        00:00:02 [kdvb-ad-1-fe-0]
root      3106     1  0 20:40 ?        00:00:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
avahi     3147     1  0 20:40 ?        00:00:00 avahi-daemon: running [mythbox.local]
avahi     3148  3147  0 20:40 ?        00:00:00 avahi-daemon: chroot helper
root      3150     1  0 20:40 ?        00:00:00 /sbin/wpa_supplicant -u -f /var/log/wpa_supplicant.log
root      3152     1  0 20:40 ?        00:00:00 /usr/sbin/nm-system-settings --config /etc/NetworkManager/nm-system-settings.conf
root      3176     1  0 20:40 ?        00:00:00 /usr/bin/system-tools-backends
root      3240  3106  0 20:40 ?        00:00:00 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-eth0.pid -lf /var/lib/dhcp3/dhclient-eth0.lease -cf /var/run/nm-dhclient-eth0.conf eth0
daemon    3270     1  0 20:40 ?        00:00:00 /usr/sbin/atd
root      3298     1  0 20:40 ?        00:00:00 /usr/sbin/cron
root      3321     1  0 20:40 ?        00:00:00 /usr/sbin/apache2 -k start
root      3398     1  0 20:40 tty1     00:00:00 /sbin/getty 38400 tty1
www-data  3403  3321  0 20:40 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3404  3321  0 20:40 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3405  3321  0 20:40 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3406  3321  0 20:40 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  3407  3321  0 20:40 ?        00:00:00 /usr/sbin/apache2 -k start
mysql     3427  2492  0 20:40 ?        00:00:01 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      3428  2492  0 20:40 ?        00:00:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
mythbox   3543  3069  0 20:40 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
mythbox   3725  3543  0 20:40 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
mythbox   3728     1  0 20:40 ?        00:00:00 /usr/bin/dbus-launch --exit-with-session /usr/share/mythbuntu/session.sh
mythbox   3729     1  0 20:40 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 9 --session
ntp       3758     1  0 20:40 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 105:108 -g
mythbox   3762     1  0 20:40 ?        00:00:00 /usr/bin/mtd -d
mythbox   3779  3543  0 20:40 ?        00:00:00 /usr/bin/xfce4-session
mythbox   3781     1  0 20:40 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2
mythbox   3783     1  0 20:40 ?        00:00:00 /usr/lib/xfconfd
mythbox   3791  3779  0 20:40 ?        00:00:02 xfwm4 --sm-client-id 23b0051e1-5e8e-4a0b-9340-103704e490e6 --display :0.0
mythbox   3792     1  0 20:40 ?        00:00:00 xfsettingsd
mythbox   3793  3779  0 20:40 ?        00:00:01 xfdesktop --sm-client-id 2e861bedb-ac76-4396-a369-cb2bc8f7fed0 --display :0.0
mythbox   3794  3779  0 20:40 ?        00:00:04 xfce4-panel -r --sm-client-id 23bda3279-6daa-4787-aff9-df4710754ab8
mythbox   3797     1  0 20:40 ?        00:00:00 xfce4-settings-helper --display :0.0 --sm-client-id 26e5b935d-5e55-46df-80e9-88b4e09968c4
mythbox   3800     1  0 20:40 ?        00:00:00 /usr/lib/gamin/gam_server
mythbox   3801  3779  0 20:40 ?        00:00:00 update-notifier --sm-config-prefix /update-notifier-F3aBGo/ --sm-client-id 2f372ac74-7627-46ba-ad3f-4f812ea54390 --screen 0
mythbox   3804  3794  0 20:40 ?        00:00:06 /usr/lib/xfce4/panel-plugins/xfce4-menu-plugin socket_id 16777278 name xfce4-menu id 1 display_name Xfce Menu size 24 screen_position 1
mythbox   3806  3794  0 20:40 ?        00:00:00 /usr/lib/xfce4/panel-plugins/xfce4-mixer-plugin socket_id 16777330 name xfce4-mixer-plugin id 12407888440 display_name Mixer size 24 screen_position 1
mythbox   3810     1  0 20:40 ?        00:00:00 gnome-power-manager --sm-config-prefix /gnome-power-manager-DU5B0l/ --sm-client-id 2a1b38c5f-b465-437e-bdef-646e16b639fb --screen 0
mythbox   3814     1  0 20:40 ?        00:00:00 /usr/lib/gvfs/gvfsd
mythbox   3841     1  0 20:40 ?        00:00:00 python /usr/share/system-config-printer/applet.py
mythbox   3849     1  0 20:40 ?        00:00:00 nm-applet --sm-disable
mythbox   3864     1  0 20:40 ?        00:00:00 /usr/lib/notification-daemon/notification-daemon
mythbox   3883     1  0 20:40 ?        00:00:00 /usr/bin/mythlcdserver -v none
root      3889     1  0 20:40 ?        00:00:00 /usr/bin/python /usr/lib/system-service/system-service-d
root      3940     1  0 20:43 ?        00:00:00 dbus-launch --autolaunch 97440520da4bd5c7f7c43b1349f30141 --binary-syntax --close-stderr
root      3941     1  0 20:43 ?        00:00:00 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
root      3958     2  0 20:43 ?        00:00:00 [scsi_eh_4]
root      3960     2  0 20:43 ?        00:00:00 [usb-storage]
root      4007     1  0 20:43 ?        00:00:00 /sbin/mount.ntfs-3g /dev/sdb1 /media/EX_VIDEO -o rw,nosuid,nodev,uhelper=hal
root      4028     1  0 20:46 ?        00:00:01 /usr/bin/python /usr/share/jockey/jockey-backend --debug -l /var/log/jockey.log
mythbox   4723  3804  3 20:50 ?        00:00:32 /usr/lib/firefox-3.0.10/firefox
root      4745     1  0 20:51 ?        00:00:00 /usr/bin/perl /usr/share/system-tools-backends-2.0/scripts/SystemToolsBackends.pl -m Platform
mythbox   4757     1  0 20:51 ?        00:00:00 /usr/lib/gvfs/gvfs-hal-volume-monitor
mythbox   4761     1  0 20:51 ?        00:00:00 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
root      5355     2  0 21:01 ?        00:00:01 [saa7133[0] dvb]
root      5413     2  0 21:02 ?        00:00:00 [cx23885[0] dvb]
mythbox   5414  3804  0 21:02 ?        00:00:00 xfce4-terminal
mythbox   5415  5414  0 21:02 ?        00:00:00 gnome-pty-helper
mythbox   5416  5414  0 21:02 pts/0    00:00:00 bash
mythbox   5436  5416  0 21:05 pts/0    00:00:00 ps -ef

---

### Post by chellrose on 2009-05-09
> **mtbdrew said:**
> Hello,

I have a Mythbuntu system now running 9.04 that shows a constant flashing hard drive light. I've searched the forums and have tried the settings listed:

[http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

As well as killing the mythbackend, I've also re-configured the Mysql settings but none of these things have helped. 

The thing is I noticed this started about two weeks ago on 8.10 after installing updates and is one of the reasons I went ahead and did a clean install of 9.04. Any ideas on what's causing this or what I need to check. The forums as well as web search seems to show this a pretty common situation that has started recently but no one seems to have come up with an answer.

Thanks in advance
Andrew

How much RAM does your system have?

---

### Post by mtbdrew on 2009-05-10
> **Sissy13 said:**
> How much RAM does your system have?

Right now 1 Gig but it was doing it with 2 Gig too.

---

### Post by chellrose on 2009-05-10
Sounds like you have plenty of RAM.  I don't know what the problem is.  Sorry I don't have something more helpful. :(

---

### Post by mtbdrew on 2009-05-11
Bump, anyone else have any ideas?

---

### Post by mtbdrew on 2009-05-12
Bump

---

### Post by mtbdrew on 2009-05-13
Should the mythbackend log be running all the time? When I look at htop, there are four instances for the mythbackend log that remain at the top of the list.

---

### Post by mtbdrew on 2009-05-13
Confirmed with iotop that the mythbackend log is running between 7.5 - 11 K/s read of the disk constantly. How do I stop this or change the settings?

---

### Post by mtbdrew on 2009-05-13
Okay here is the last few lines from mythbackend.log. Seems to be getting some errors with the Mysql server going away:

2009-05-13 20:31:42.743 DB Error (HouseKeeper Cleaning TVChain Table):
Query was:
SELECT DISTINCT chainid FROM tvchain WHERE endtime > '2009-05-13T16:31:42' ;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-13 20:31:42.745 DB Error (Housekeeper Creating Temporary Table):
Query was:
CREATE TEMPORARY TABLE IF NOT EXISTS temprecordedcleanup ( chanid int(10) unsigned NOT NULL default '0', starttime datetime NOT NULL default '0000-00-00 00:00:00' );
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-13 20:31:42.751 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-13 20:31:42.941 DB Error (Error in JobQueue::GetJobs(), Unable to query list of Jobs in Queue.):
Query was:
SELECT j.id, j.chanid, j.starttime, j.inserttime, j.type, j.cmds, j.flags, j.status, j.statustime, j.hostname, j.args, j.comment, r.endtime, j.schedruntime FROM jobqueue j, recorded r WHERE j.chanid = r.chanid AND j.starttime = r.starttime ORDER BY j.schedruntime, j.id;
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:
MySQL server has gone away

2009-05-13 20:31:51.158 MainServer::HandleAnnounce Monitor
2009-05-13 20:31:51.258 adding: mythbox as a client (events: 0)
2009-05-13 20:31:51.260 MainServer::HandleAnnounce Monitor
2009-05-13 20:31:51.325 adding: mythbox as a client (events: 1)
2009-05-13 20:32:52.856 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-13 20:34:34.707 MainServer::HandleAnnounce Monitor
2009-05-13 20:34:34.739 adding: mythbox as a client (events: 0)
2009-05-13 20:34:34.742 MainServer::HandleAnnounce Monitor
2009-05-13 20:34:34.743 adding: mythbox as a client (events: 1)
2009-05-13 20:43:23.544 DVBSM(0), Warning: Can not measure Signal Strength
			eno: Invalid argument (22)
2009-05-13 20:47:52.907 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by mtbdrew on 2009-05-14
Any idea how to clear the MySql errors?

---

### Post by mtbdrew on 2009-05-14
anyone?

---

### Post by tsh on 2009-05-17
(sorry, k'ed keyboard)
try searhig the myth wiki for periodic maintenance. there are progs with the release that will ??? fix the prob. with your Database, worth a try for a start at least.

---

### Post by mtbdrew on 2009-07-08
I've rolled back to 8.10 because of stability issues and still have this issue. Have changed MB and done clean load yet the hard drive is still showing constant activity or at least the HDD LED does.

---

### Post by mtbdrew on 2009-07-22
Bump

---

### Post by gwagchunks on 2009-07-22
I'm no expert, is your system recording any programmes? For some reason on my case the HDD light stays on all the time. If I listen very carefully (as the drive is quiet), when recording the drive will blip regulary, though when not recording, it does seem quite inactive.

---

### Post by dk06 on 2009-07-22
> **mtbdrew said:**
> Hello,

I have a Mythbuntu system now running 9.04 that shows a constant flashing hard drive light. I've searched the forums and have tried the settings listed:

[http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998)

As well as killing the mythbackend, I've also re-configured the Mysql settings but none of these things have helped. 

The thing is I noticed this started about two weeks ago on 8.10 after installing updates and is one of the reasons I went ahead and did a clean install of 9.04. Any ideas on what's causing this or what I need to check. The forums as well as web search seems to show this a pretty common situation that has started recently but no one seems to have come up with an answer.

Thanks in advance
Andrew


What happens when you turn off your wireless or disconnect your network?


If your machine is working really hard and its not showing up in your processes & you can't determine the cause, you may have been hacked.

Try :
> kill -9 _______ & replace ________ w/PID from ps -ax or whatever you're using to list processes

Mythbuntu adds a lot of risky service & opens ports, both of which can be used to gain access to your machine.

Check into a fresh install
&
OSSEC
& 
Disable extra services 
&
Maybe install some Hardening Apps...
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)
[http://ubuntu-unleashed.com/tag/harden-ubuntu-kernel](http://ubuntu-unleashed.com/tag/harden-ubuntu-kernel)

edit:
Just noticed the "common situation that has started recently but no one seems to have come up with an answer." part



[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)
> 
**Performance regressions on Intel graphics cards**

  Users of Intel video chipsets have reported performance regressions in Ubuntu 8.10 compared with previous releases ([252094]("https://bugs.launchpad.net/bugs/252094")).  Many of the issues have been resolved in Ubuntu 9.04, but some remain. 
 
[LIST]
[*] Some users have found improved performance by using the "greedy" migration heuristic. This can be done by running "sudo gedit /etc/X11/xorg.conf", and adding Option "MigrationHeuristic" "greedy" to the Device section of your xorg.conf.  
[*] Alternatively, a new experimental acceleration architecture option, "DRI2/UXA", is available for Intel graphics users which our [testing]("https://wiki.ubuntu.com/X/UxaTesting") has found provides significant performance improvements in some cases, but has also shown risk of severe stability problems. You can opt-in to enable this by running "sudo gedit /etc/X11/xorg.conf", and adding Option "AccelMethod" "UXA" to the Device section of your xorg.conf.  Users wishing to maximize stability should stay with the standard default acceleration method, "EXA". 
 [IMG]https://wiki.ubuntu.com/htdocs/ubuntu/img/alert.png[/IMG] In some cases this will lead to the graphical environment not starting at all or becoming entirely unusable. In that case, start into rescue mode or press Ctrl+Alt+F2 and log into the text console, and use sudo nano /etc/X11/xorg.conf to revert the UXA option. 
[*] If none of the above helps, some users reported success with [using an older driver version]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4"). 
[/LIST]
 **Display freezes with Intel graphics cards**

  Users of various Intel video chipsets reported freezes under various conditions (e. g. a few minutes after suspend on the i945, see [339091]("https://bugs.launchpad.net/bugs/339091")). In many cases, switching off desktop effects in System &#8594; Preferences &#8594; Appearance was reported to help.   
 If it still happens without desktop effects, you can add Option "DRI" "off" to the Device section of /etc/X11/xorg.conf, as described above. This will disable 3D acceleration and desktop effects, but makes suspend work reliably again and also avoid many types of crashes. 
 These freezes happen particularly often on the i965 chips ([359392]("https://bugs.launchpad.net/bugs/359392")). For that reason, desktop effects were disabled by default on this chipset in the final release. They will be re-enabled in a 9.04 Update once the problem has been fixed. 

Don't know the answer

---

### Post by mtbdrew on 2009-07-23
Not recording does not affect the activity light.

Thought I could be hacked too so did a clean install already and even rolled back to 8.10 from 9.04 and the situation is still the same.

Seems to be a lot of people having the same issue and one suggestion is the Mythbackend and MySql not being correctly setup but don't know how to make sure this is done correctly. Have run the reconfig for MySql/Myth and still see the same issue.

---

### Post by dk06 on 2009-07-24
> **mtbdrew said:**
> 
Seems to be a lot of people having the same issue and one suggestion is the Mythbackend and MySql not being correctly setup but don't know how to make sure this is done correctly. Have run the reconfig for MySql/Myth and still see the same issue.

Maybe these guys can help you more:
**   **

**Mythbuntu **

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

**Support**

                                          We are glad to offer community based full support on the project. We have a wide range of support from our wiki to the Mythbuntu Forums. The forum and wiki are community supported and will provide a wealth of knowledge and expertise from and for users. 
 **Do it yourself support**

 See the following support channels for help:
 
[LIST]
[*][The Mythbuntu Installation Manual (PDF Format)]("http://www.mythbuntu.org/installation_manual")
[*]The Mythbuntu Wiki, [http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)
[*]The Upstream MythTV wiki, [http://wiki.mythtv.org]("http://wiki.mythtv.org/")
[/LIST]
 **Community Support**

 See the following support channels for help:
 
[LIST]
[*][Official Mythbuntu Forum]("http://ubuntuforums.org/forumdisplay.php?f=301")
[*]The MythTV Users mailing list, [http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)
[/LIST]

 **Live Support (IRC)**

 Live support is available in the form of Internet Relay Chat (IRC). Please ask your question and wait, we will check the channel periodically and will see your question.
 ** IRC Clients **

 If you have an IRC Client installed, then visit us at #ubuntu-mythtv on irc.freenode.net.
If you don't have one installed currently, you can try some of these below:
 [X-Chat (Ubuntu) ]("apt://xchat")
[Pidgin (Ubuntu) ]("apt://pidgin")
[X-Chat (Windows) ]("http://www.silverex.org/news/")
[Pidgin (Windows) ]("http://www.pidgin.im/")
 ** Web IRC Client**

 If you do not have an IRC client installed, then you may visit us via our [java based IRC client here]("http://www.mythbuntu.org/chat"). Please keep in mind that IRC often does not provide instant answers. Proper etiquette is to ask your question and wait. Users will periodically check in from time to time and may know the answer to your question. IRC is not instant response, it is more like under 4 hour response. 
 **Weekly Build Support**

 [Support for weekly builds can be found here ]("http://www.mythbuntu.org/auto-builds-faq")

---

