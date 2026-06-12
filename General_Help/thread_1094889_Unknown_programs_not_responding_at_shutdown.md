---
title: "Unknown programs not responding at shutdown"
date: 2009-03-13
forum: General Help
---

### Post by euthymos on 2009-03-13
Hi,

I've got always some program not responding at shutdown, so that I have to click "Terminate session" to kill them.
They're reported as "UNKNOWN" and their state is "NOT RESPONDING".

What can I do?



I post ps -e output:
```

  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 events/0
    7 ?        00:00:00 khelper
   46 ?        00:00:00 kintegrityd/0
   48 ?        00:00:00 kblockd/0
   50 ?        00:00:00 kacpid
   51 ?        00:00:00 kacpi_notify
  148 ?        00:00:00 cqueue
  152 ?        00:00:00 kseriod
  192 ?        00:00:00 pdflush
  193 ?        00:00:00 pdflush
  194 ?        00:00:00 kswapd0
  238 ?        00:00:00 aio/0
 1306 ?        00:00:00 ksuspend_usbd
 1311 ?        00:00:00 khubd
 1327 ?        00:00:00 khpsbpkt
 1340 ?        00:00:00 ata/0
 1342 ?        00:00:00 ata_aux
 1988 ?        00:00:00 knodemgrd_0
 1992 ?        00:00:00 scsi_eh_0
 1993 ?        00:00:00 scsi_eh_1
 2171 ?        00:00:00 scsi_eh_2
 2174 ?        00:00:00 usb-storage
 2233 ?        00:00:00 kjournald
 2391 ?        00:00:00 udevd
 4372 tty4     00:00:00 getty
 4373 tty5     00:00:00 getty
 4379 tty2     00:00:00 getty
 4380 tty3     00:00:00 getty
 4382 tty6     00:00:00 getty
 4557 ?        00:00:00 acpid
 4594 ?        00:00:00 kondemand/0
 4674 ?        00:00:00 syslogd
 4726 ?        00:00:00 dd
 4728 ?        00:00:00 klogd
 4751 ?        00:00:00 dbus-daemon
 4773 ?        00:00:00 avahi-daemon
 4774 ?        00:00:00 avahi-daemon
 4817 ?        00:00:00 cupsd
 5134 ?        00:00:00 hald
 5137 ?        00:00:00 console-kit-dae
 5200 ?        00:00:00 hald-runner
 5223 ?        00:00:00 hald-addon-inpu
 5229 ?        00:00:00 hald-addon-stor
 5232 ?        00:00:00 hald-addon-acpi
 5234 ?        00:00:00 hald-addon-stor
 5237 ?        00:00:00 hald-addon-stor
 5240 ?        00:00:00 hald-addon-stor
 5255 ?        00:00:00 hald-addon-stor
 5291 ?        00:00:00 NetworkManager
 5296 ?        00:00:00 wpa_supplicant
 5299 ?        00:00:00 nm-system-setti
 5329 ?        00:00:00 gdm
 5332 ?        00:00:00 gdm
 5336 tty7     00:00:11 Xorg
 5356 ?        00:00:00 system-tools-ba
 5406 ?        00:00:00 atd
 5434 ?        00:00:00 cron
 5500 tty1     00:00:00 getty
 5531 ?        00:00:00 x-session-manag
 5667 ?        00:00:00 ssh-agent
 5670 ?        00:00:00 dbus-launch
 5671 ?        00:00:00 dbus-daemon
 5679 ?        00:00:00 pulseaudio
 5681 ?        00:00:00 gconf-helper
 5683 ?        00:00:00 gconfd-2
 5689 ?        00:00:00 seahorse-agent
 5693 ?        00:00:00 gvfsd
 5696 ?        00:00:00 gnome-keyring-d
 5700 ?        00:00:00 gnome-keyring-d
 5701 ?        00:00:00 gnome-settings-
 5703 ?        00:00:00 metacity
 5708 ?        00:00:00 gvfs-fuse-daemo
 5719 ?        00:00:01 gnome-panel
 5721 ?        00:00:00 nautilus
 5724 ?        00:00:00 bonobo-activati
 5729 ?        00:00:01 vino-server
 5734 ?        00:00:00 update-notifier
 5735 ?        00:00:00 gnome-power-man
 5749 ?        00:00:00 gvfs-hal-volume
 5750 ?        00:00:00 gnome-screensav
 5752 ?        00:00:00 gvfs-gphoto2-vo
 5755 ?        00:00:00 gvfsd-burn
 5758 ?        00:00:00 gvfsd-trash
 5762 ?        00:00:00 trashapplet
 5766 ?        00:00:00 fast-user-switc
 5770 ?        00:00:00 mixer_applet2
 5779 ?        00:00:00 evolution-data-
 5788 ?        00:00:22 firefox
 5840 ?        00:00:00 gnome-terminal
 5842 ?        00:00:00 gnome-pty-helpe
 5843 pts/0    00:00:00 bash
 5868 pts/0    00:00:00 ps

```

---

### Post by euthymos on 2009-03-13
Please help me. :( I think I'll soon format my hard drive because I consider the possibility that this weirdness can be caused by malware.
This situation is unacceptable. I'm not saying that it's your fault (I didn't ever think about it) but it's simply absurd that such things can happen. Why can't I know what the hell is preventing system from shutting down? Are we joking?

Actually, I've seen things like that only under Windows. ;)

Thank you in advance

---

### Post by euthymos on 2009-03-16
Help

---

### Post by pcjunkie on 2009-03-17
Start with

sudo apt-get update
sudo apt-get install build-essential


have you checked your log files?

# cd /var/logs

Or browse there....

look for dmesg

    * /var/log/message: General message and system related stuff
    * /var/log/auth.log: Authenication logs
    * /var/log/kern.log: Kernel logs
    * /var/log/cron.log: Crond logs (cron job)
    * /var/log/maillog: Mail server logs
    * /var/log/qmail/ : Qmail log directory (more files inside this directory)
    * /var/log/httpd/: Apache access and error logs directory
    * /var/log/lighttpd: Lighttpd access and error logs directory
    * /var/log/boot.log : System boot log
    * /var/log/mysqld.log: MySQL database server log file
    * /var/log/secure: Authentication log
    * /var/log/utmp or /var/log/wtmp : Login records file
    * /var/log/yum.log: Yum log files

Ref#[http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/)

---

### Post by richardh9936 on 2009-03-17
I have the same issue, but it doesn't seem to cause any problems.  However, am I hosting some rogue?  I don't understand the log contents - they just look normal to me....  What would I see if I had a rogue process running?

---

### Post by richardh9936 on 2009-03-17
Don't panic.  These people think it's a remnant from Firefox.  See 
 [http://ubuntuforums.org/showpost.php?p=6629969&postcount=9]("http://ubuntuforums.org/showpost.php?p=6629969&postcount=9")

---

### Post by euthymos on 2009-03-20
Very mysterious. I don't like it.

---

