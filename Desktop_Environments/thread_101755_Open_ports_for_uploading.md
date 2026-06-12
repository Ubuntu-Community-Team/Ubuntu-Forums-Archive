---
title: "Open ports for uploading?"
date: 2005-12-10
forum: Desktop Environments
---

### Post by vtechstu on 2005-12-10
Ok, so I live on campus at my school, and am always connected to the network.  I have been on ubuntu all week, as usuall, I do not turn my computer off.  I got an email this morning for excessive uploads( more then 650 mb ).  Now I certainly havn't uploaded anything that I know of, especially that much.  I'm curious to find out what could be causing this upload excess, something running on my computer, or what.  Anyway to find out that you suggest I would greatly appreciate, thanks.


vtechstu

---

### Post by taurus on 2005-12-10
I never turn off my computers either but first, too what processes are running on your machine by

ps -A

Then, install some type of firewall like firestarter to monitor your network.

---

### Post by vtechstu on 2005-12-10
Here is the output of the command:

```
 PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
    5 ?        00:00:00 kthread
    7 ?        00:00:00 kacpid
  117 ?        00:00:00 kblockd/0
  146 ?        00:00:00 pdflush
  147 ?        00:00:00 pdflush
  149 ?        00:00:00 aio/0
  148 ?        00:00:00 kswapd0
  736 ?        00:00:00 kseriod
 1941 ?        00:00:00 ata/0
 1944 ?        00:00:00 scsi_eh_0
 1945 ?        00:00:00 scsi_eh_1
 1956 ?        00:00:00 khubd
 3450 ?        00:00:00 kjournald
 3584 ?        00:00:00 udevd
 5549 ?        00:00:00 shpchpd_event
 6630 ?        00:00:00 kgameportd
 7000 ?        00:00:00 dhclient3
 7342 ?        00:00:00 acpid
 7357 ?        00:00:00 syslogd
 7374 ?        00:00:00 dd
 7376 ?        00:00:00 klogd
 7389 ?        00:00:00 dbus-daemon
 7402 ?        00:00:00 hald
 7407 ?        00:00:00 hald-addon-acpi
 7418 ?        00:00:00 hald-addon-stor
 7801 ?        00:00:00 gdm
 7805 ?        00:00:00 gdm
 7849 ?        00:01:10 Xorg
 7887 ?        00:00:00 cupsd
 7911 ?        00:00:00 hpiod
 7944 ?        00:00:00 python
 8013 ?        00:00:00 cron
 8072 ?        00:00:00 vmnet-bridge
 8086 ?        00:00:00 vmnet-natd
 8127 ?        00:00:00 timidity
 8131 tty1     00:00:00 getty
 8132 tty2     00:00:00 getty
 8133 tty3     00:00:00 getty
 8134 tty4     00:00:00 getty
 8135 tty5     00:00:00 getty
 8138 tty6     00:00:00 getty
 8161 ?        00:00:00 vmnet-netifup
 8168 ?        00:00:00 vmnet-netifup
 8225 ?        00:00:00 vmnet-dhcpd
 8226 ?        00:00:00 vmnet-dhcpd
 8227 ?        00:00:00 gnome-session
 8271 ?        00:00:00 ssh-agent
 8274 ?        00:00:00 dbus-launch
 8275 ?        00:00:00 dbus-daemon
 8277 ?        00:00:00 gconfd-2
 8280 ?        00:00:00 gnome-keyring-d
 8282 ?        00:00:00 esd
 8286 ?        00:00:00 bonobo-activati
 8288 ?        00:00:00 gnome-settings-
 8294 ?        00:00:00 gam_server
 8306 ?        00:00:00 xscreensaver
 8330 ?        00:00:07 metacity
 8335 ?        00:00:01 gnome-panel
 8337 ?        00:00:08 nautilus
 8339 ?        00:00:00 gnome-volume-ma
 8347 ?        00:00:00 gnome-cups-icon
 8352 ?        00:00:00 gnome-vfs-daemo
 8358 ?        00:00:00 mapping-daemon
 8360 ?        00:00:00 trashapplet
 8371 ?        00:00:01 wnck-applet
 8373 ?        00:00:00 notification-ar
 8375 ?        00:00:00 mixer_applet2
 8377 ?        00:00:00 clock-applet
 9335 ?        00:00:03 gaim
 9563 ?        00:00:02 kompose
 9565 ?        00:00:00 kdeinit
 9569 ?        00:00:00 dcopserver
 9571 ?        00:00:00 klauncher
 9573 ?        00:00:00 kded
 9626 ?        00:00:00 eclipse
 9627 ?        00:00:17 java
 9684 ?        00:00:00 firefox
 9695 ?        00:00:00 run-mozilla.sh
 9700 ?        00:00:24 firefox-bin
10542 ?        00:00:00 gnome-terminal
10543 ?        00:00:00 gnome-pty-helpe
10544 pts/1    00:00:00 bash
10558 pts/1    00:00:00 ps

```

---

### Post by cwaldbieser on 2005-12-10
[QUOTE=vtechstu]Ok, so I live on campus at my school, and am always connected to the network.  I have been on ubuntu all week, as usuall, I do not turn my computer off.  I got an email this morning for excessive uploads( more then 650 mb ).  Now I certainly havn't uploaded anything that I know of, especially that much.  I'm curious to find out what could be causing this upload excess, something running on my computer, or what.  Anyway to find out that you suggest I would greatly appreciate, thanks.


vtechstu[/QUOTE]
1) Do you have roomates who use the computer?  Maybe one of them has some idea?

2) Are you running any kind of servers (Samba/Windows filesharing, email server, ftp server, ssh server, vnc server, etc.).  Maybe someone is using that?

3) If you are connected via a router, lots of times the router will keep logs of sites visited, etc.  It's a good way to see if someone else has been using your network connection (especially if it is wireless and they haven't actually been using your computer).

4) You should ask you admins for any details they can provide you about the uploads.

5) It is possible to set up something called IP Accounting on your system.  This can basically keep track of how much data is flowing in/out of your various network cards.  That way, you can keep track of what is going on yourself and find out if you really have a problem or someone just made an accounting error.

---

