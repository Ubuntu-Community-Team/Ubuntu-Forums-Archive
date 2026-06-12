---
title: "Disabling unnecessary services"
date: 2005-01-18
forum: Desktop Environments
---

### Post by Viro on 2005-01-18
There are a lot of services that start with Ubuntu by default. Just glancing at the boot screen, I see a MTA (Mail Transfer Agent), RAID monitoring software and other stuff that I won't need since I run a laptop (Powerbook G4).

Where can I find a list of services that I can safely disable? This is the biggest thing that's bugging me right now as I don't want to disable something important. If anyone can help tell me what services I can disable.

```
root@komek:/etc/init.d # ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:03 events/0
    4 ?        00:00:00 khelper
   24 ?        00:00:00 kblockd/0
   36 ?        00:00:00 pdflush
   37 ?        00:00:00 pdflush
   38 ?        00:00:00 kswapd0
   39 ?        00:00:00 aio/0
  191 ?        00:00:02 kjournald
  251 ?        00:00:00 udevd
  707 ?        00:00:00 thermostat
  780 ?        00:00:00 khpsbpkt
 1576 ?        00:00:00 khubd
 2695 ?        00:00:00 knodemgrd_0
 2980 ?        00:00:00 dhclient3
 3243 ?        00:00:00 syslogd
 3254 ?        00:00:00 klogd
 3327 ?        00:00:00 inetd
 3451 ?        00:00:00 mdadm
 3462 ?        00:00:00 atd
 3473 ?        00:00:00 cron
 3511 tty2     00:00:00 getty
 3512 tty3     00:00:00 getty
11915 ?        00:00:00 portmap
12235 ?        00:00:00 apmd
13214 ?        00:00:00 famd
13363 ?        00:00:00 dbus-daemon-1
13367 ?        00:00:04 hald
13749 ?        00:00:03 pbbuttonsd
17055 ?        00:00:02 cupsd
19325 ?        00:00:00 gdm
19326 ?        00:00:00 gdm
19339 tty4     00:00:00 getty
19342 tty5     00:00:00 getty
19343 tty6     00:00:00 getty
19407 ?        00:06:08 XFree86
19473 tty1     00:00:00 getty
19481 ?        00:00:01 x-session-manag
19527 ?        00:00:00 ssh-agent
19530 ?        00:00:00 dbus-launch
19531 ?        00:00:00 dbus-daemon-1
19533 ?        00:00:03 gconfd-2
19536 ?        00:00:00 gnome-keyring-d
19538 ?        00:00:01 esd
19540 ?        00:00:00 bonobo-activati
19542 ?        00:00:01 gnome-smproxy
19544 ?        00:00:01 gnome-settings-
19553 ?        00:00:00 xscreensaver
19578 ?        00:00:19 metacity
19596 ?        00:00:12 gnome-panel
19598 ?        00:00:16 nautilus
19600 ?        00:00:00 gnome-volume-ma
19606 ?        00:00:01 gnome-cups-icon
19607 ?        00:00:00 nautilus
19608 ?        00:00:00 nautilus
19609 ?        00:00:00 gnome-cups-icon
19613 ?        00:00:00 gnome-vfs-daemo
19614 ?        00:00:00 gnome-vfs-daemo
19615 ?        00:00:00 gnome-vfs-daemo
19619 ?        00:00:00 mapping-daemon
19620 ?        00:00:00 nautilus
19621 ?        00:00:00 nautilus
19622 ?        00:00:00 nautilus
19623 ?        00:00:00 nautilus
19624 ?        00:00:00 nautilus
19625 ?        00:00:00 nautilus
19627 ?        00:00:13 wnck-applet
19629 ?        00:00:01 trashapplet
19630 ?        00:00:00 trashapplet
19631 ?        00:00:00 trashapplet
19632 ?        00:00:00 trashapplet
19634 ?        00:00:01 clock-applet
19636 ?        00:00:02 mixer_applet2
19638 ?        00:00:11 battstat-applet
19642 ?        00:00:01 notification-ar
19697 ?        00:00:00 gconfd-2
19725 ?        00:00:00 gksudo
19726 ?        00:03:15 synaptic
20009 ?        00:00:32 http
20199 ?        00:00:03 gnome-keyboard-
20363 ?        00:00:12 gnome-cpufreq-a
20544 ?        00:00:05 gweather-applet
20545 ?        00:00:00 gweather-applet
20546 ?        00:00:00 gweather-applet
20547 ?        00:00:00 gweather-applet
20948 ?        00:00:00 xfslogd/0
20949 ?        00:00:00 xfsdatad/0
20950 ?        00:00:00 xfsbufd
20953 ?        00:00:00 jfsIO
20954 ?        00:00:00 jfsCommit
20955 ?        00:00:00 jfsSync
21625 ?        00:00:00 scsi_eh_4
23587 ?        00:00:02 gaim
23590 ?        00:00:00 gaim
23591 ?        00:00:00 gaim
23593 ?        00:00:00 evolution-data-
23594 ?        00:00:00 evolution-data-
23595 ?        00:00:00 evolution-data-
23596 ?        00:00:00 gaim
23922 ?        00:01:30 firefox-bin
23950 ?        00:00:00 firefox-bin
23951 ?        00:00:00 firefox-bin
23954 ?        00:00:00 firefox-bin
23992 ?        00:00:00 gksudo
23993 ?        00:00:02 gnome-terminal
23995 ?        00:00:00 bonobo-activati
23996 ?        00:00:00 gnome-pty-helpe
23997 pts/0    00:00:00 bash
23998 ?        00:00:00 gnome-terminal
24000 ?        00:00:00 gnome-terminal
24114 ?        00:00:00 powernowd
24291 ?        00:00:00 gnome-cups-icon
24292 pts/0    00:00:00 ps
``` 

I see stuff like jfsIO,jfsSync, jfsCommit, xfsbufd, xfslogd, that I don't think I need since I don't use JFS or XFS. Unless I'm mistaken and these processes don't have anything to do with those file systems.

If anyone is able to tell me what services are safe to turn off, I will turn them off.

---

### Post by bin on 2005-01-19
Get hold of rcconf via synaptic or apt-get

In a terminal sudo rcconf. 

Scroll down the list and use the space bar to uncheck the services postfix, fetchmail, mdadm. If you don't need ppp then that can go too!

---

### Post by mrosenlof on 2005-01-19
try and get hold of an O'Reilly book (that's the publisher) called something like "101 Linux Server Hacks".  It might not have the '101' in the title.  Sorry, I don't remember the author.

This book has a whole section devoted to unnecessary server processes.

Whatever you do, keep notes, or backup the rcN.d directory that you modify to turn services off, do something to make it easy to restore.

---

### Post by cafeina on 2005-01-20
I tried sudo rcconf from a terminal, but it does not seem to work. All I get is the following:  sudo: rcconf: command not found.

---

### Post by nocturn on 2005-01-20
[QUOTE=cafeina]I tried sudo rcconf from a terminal, but it does not seem to work. All I get is the following:  sudo: rcconf: command not found.[/QUOTE]

sudo aptitude update
sudo aptitude install rcconf

The error you get is because it is not installed.

---

### Post by shmonkey on 2005-01-21
You can also do :

update-rc.d -f <name-of-service> remove

This is part of the base system.

---

### Post by pgoya on 2005-01-23
Yeah... it's all beautifull, but the main question here still in the air. 
WHAT IS each of these services?? 

Postfix  :confused: 
mdadm  :confused: 
fetchmail  :confused: 

Is there a explanation somewere?
Thanks!

---

### Post by Viro on 2005-01-24
Postfix and fetchmail are MTAs, Mail transfer agents, stuff that shouldn't be running on a desktop/laptop. mdadm seems to be a daemon for managing RAID devices, also not meant ot be on a desktop/laptop. If you want to know what the services are, you could just go to /etc/init.d/ and read the scripts. Some of them have good comments and explain what the script does. Others.... well, let's not go into that :)

---

### Post by Juergen on 2005-01-24
> Postfix and fetchmail are MTAs, Mail transfer agents, stuff that shouldn't be running on a desktop/laptop.Can I still receive messages from cron-jobs or other daemons if I turn them off?
I usually keep them running because I want these messages.

---

### Post by nocturn on 2005-01-24
[QUOTE=Juergen]Can I still receive messages from cron-jobs or other daemons if I turn them off?
I usually keep them running because I want these messages.[/QUOTE]

If you kill postfix you will not get any messages from cron or from apt.

---

### Post by lykoszine on 2005-01-24
Is there a way to change the mails from Cron and Apt to MH format rather than Mbox? If they are delivered by postfix do I just change the settings there? Ta

---

### Post by nocturn on 2005-01-24
[QUOTE=lykoszine]Is there a way to change the mails from Cron and Apt to MH format rather than Mbox? If they are delivered by postfix do I just change the settings there? Ta[/QUOTE]

Postfix should be able to cope with that.  Check out the delivery system. 
I user Cyrus Imap for that, which uses MH as backing store.

---

### Post by mendicant on 2005-01-24
[QUOTE=Juergen]Can I still receive messages from cron-jobs or other daemons if I turn them off?
I usually keep them running because I want these messages.[/QUOTE]

You can just set up your mailer to only do local deliveries and accept only local connections.
If you do a dpkg-reconfigure postfix, you should be able to get the option to do that.

---

