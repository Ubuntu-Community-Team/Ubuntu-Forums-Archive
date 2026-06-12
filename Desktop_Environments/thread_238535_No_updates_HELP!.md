---
title: "No updates HELP!"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-17
hello

Has there been any updates in the past 2 weeks because for 2 weeks I have not seen any updates.  What is the deal here?  

Is anyone else having this problem besides me?

Thanks

---

### Post by arkham on 2006-08-17
Try doing a manual update with this command:

sudo apt-get update

Do you get any errors?

---

### Post by taurus on 2006-08-17
There are a few upgrades the last few days or so.  Did you check it by hand, from a terminal, or do you reply on the update icon on the panel?

```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by Magiczero on 2006-08-17
Here is what I got 

tanner@ubuntu:~$
tanner@ubuntu:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Fetched 4B in 18s (0B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tanner@ubuntu:~$

---

### Post by taurus on 2006-08-17
You have another apt thing running in the background so you need to kill it.  This command will show you all the processes running on your system.  Paste it here and I will show you how to kill it!!!

```

ps -A

```

---

### Post by arkham on 2006-08-17
That error may be because of aptitude (package manager) running - at the same time.  Or it could be a stale lock.....

Try rebooting and then see if the same issue re-occurs.  If it does, then try this:

```
sudo rm /var/lib/dpkg/lock
```

Then re-run the apt-get commands in the previous posts.

---

### Post by Magiczero on 2006-08-17
tanner@ubuntu:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:04 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
   64 ?        00:00:00 pdflush
   65 ?        00:00:00 pdflush
   67 ?        00:00:00 aio/0
   66 ?        00:00:01 kswapd0
  655 ?        00:00:00 kseriod
 1748 ?        00:00:00 khubd
 1830 ?        00:00:00 kjournald
 2056 ?        00:00:01 udevd
 2826 ?        00:00:00 shpchpd_event
 2871 ?        00:00:00 kgameportd
 3207 ?        00:00:00 dhclient3
 3358 ?        00:00:00 kjournald
 3620 ?        00:00:00 syslogd
 3646 ?        00:00:00 dd
 3648 ?        00:00:00 klogd
 3667 ?        00:00:00 dbus-daemon
 3682 ?        00:00:05 hald
 3683 ?        00:00:00 hald-runner
 3735 ?        00:00:00 hald-addon-keyb
 3746 ?        00:00:00 hald-addon-stor
 3747 ?        00:00:01 hald-addon-stor
 3997 ?        00:00:00 gdm
 4004 ?        00:00:00 gdm
 4014 tty7     00:05:40 Xorg
 4043 ?        00:00:01 cupsd
 4061 ?        00:00:00 hpiod
 4070 ?        00:00:00 python
 4103 ?        00:00:00 kapmd
 4114 ?        00:00:00 apmd
 4195 ?        00:00:00 gdomap
 4247 ?        00:00:01 hulamanager
 4362 ?        00:00:00 nmbd
 4373 ?        00:00:00 smbd
 4395 ?        00:00:00 smbd
 4425 ?        00:00:00 hcid
 4431 ?        00:00:00 sdpd
 4440 ?        00:00:00 krfcommd
 4453 ?        00:00:00 mdadm
 4488 ?        00:00:00 atd
 4501 ?        00:00:00 cron
 4578 tty1     00:00:00 getty
 4579 tty2     00:00:00 getty
 4580 tty3     00:00:00 getty
 4581 tty4     00:00:00 getty
 4582 tty5     00:00:00 getty
 4583 tty6     00:00:00 getty
 4594 ?        00:00:03 x-session-manag
 4640 ?        00:00:00 ssh-agent
 4643 ?        00:00:00 dbus-launch
 4644 ?        00:00:00 dbus-daemon
 4646 ?        00:00:03 gconfd-2
 4649 ?        00:00:00 gnome-keyring-d
 4651 ?        00:00:00 bonobo-activati
 4653 ?        00:00:04 gnome-settings-
 4657 ?        00:00:00 esd
 4664 ?        00:00:25 metacity
 4667 ?        00:00:07 nautilus
 4672 ?        00:00:44 gnome-panel
 4674 ?        00:00:00 gnome-volume-ma
 4676 ?        00:00:04 update-notifier
 4680 ?        00:00:00 gnome-vfs-daemo
 4682 ?        00:00:03 gnome-cups-icon
 4696 ?        00:00:03 clock-applet
 4703 ?        00:00:01 gnome-power-man
 4707 ?        00:00:05 mixer_applet2
 4709 ?        00:00:00 mapping-daemon
 4718 ?        00:00:08 gnome-netstatus
 4724 ?        00:00:03 gnome-screensav
 4730 ?        00:00:00 firefox
 4741 ?        00:00:00 run-mozilla.sh
 4746 ?        00:09:48 firefox-bin
 4750 ?        00:01:18 gaim
 4964 ?        00:00:03 gksu
 4965 ?        00:02:23 synaptic
 5106 ?        00:00:11 gnome-terminal
 5110 ?        00:00:00 gnome-pty-helpe
 5113 pts/0    00:00:00 bash
 5159 ?        00:00:03 notification-da
 5407 pts/1    00:00:00 bash
 5576 pts/1    00:00:00 ps

---

### Post by taurus on 2006-08-17
You have synaptic running in the background so you need to kill it if you want to run "apt-get/aptitude..."  At a prompt, do

```

sudo kill -9 4965
sudo aptitude update
sudo aptitude upgrade

```

---

