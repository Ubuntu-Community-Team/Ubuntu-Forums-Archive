---
title: "Updates Not installing"
date: 2007-01-04
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2007-01-04
Hi All,

When I start my system I am seeing the updates available icon and when I click that it ask for enter password and when I give the password, Software Updates window appears and it will not install. See the screen shot. 

I am getting an error and Updates don't installs. 

Please help me if you have any ideas.

[IMG]/home/swaroop/ScreenShot.png[/IMG]

Regards,

Swaroop Kunduru.

---

### Post by taurus on 2007-01-04
The screenshot is no good but why don't you shut down that program or automate update and try to see if you can update it fro ma terminal!

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by SwaroopKunduru on 2007-01-04
sudo aptitude update


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [50.9kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [84.7kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  404 Not Found
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [6460B]
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  404 Not Found
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [16.4kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [968B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [84.7kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [6460B]
99% [15 Packages 6091/6460B 94%]bzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Sub-process bzip2 returned an error code (2)
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [16.4kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [968B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [43.9kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [5419B]
Fetched 233kB in 3s (64.3kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache


This was the result.

Regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2007-01-04
sudo aptitude upgrade


E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This is the result.

Regards,

Swaroop Kunduru.

---

### Post by taurus on 2007-01-04
Looks like you still have the GUI update running so you need to terminate that.  What's the output of this command from a terminal?

```
ps -A
```

---

### Post by SwaroopKunduru on 2007-01-04
PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  135 ?        00:00:00 pdflush
  136 ?        00:00:00 pdflush
  138 ?        00:00:00 aio/0
  137 ?        00:00:00 kswapd0
  725 ?        00:00:00 kseriod
 1819 ?        00:00:00 khubd
 1836 ?        00:00:00 khpsbpkt
 1860 ?        00:00:00 knodemgrd_0
 1929 ?        00:00:00 kjournald
 2158 ?        00:00:00 udevd
 2987 ?        00:00:00 shpchpd_event
 3112 ?        00:00:00 pccardd
 3137 ?        00:00:00 Ieee80211/0
 3858 ?        00:00:00 acpid
 3976 ?        00:00:00 dd
 3978 ?        00:00:00 klogd
 4297 ?        00:00:00 gdm
 4309 ?        00:00:00 gdm
 4331 tty7     00:00:30 Xorg
 4340 ?        00:00:00 hpiod
 4355 ?        00:00:00 python
 4438 ?        00:00:00 dbus-daemon
 4453 ?        00:00:01 hald
 4454 ?        00:00:00 hald-runner
 4469 ?        00:00:00 dhclient3
 4476 ?        00:00:00 hald-addon-acpi
 4536 ?        00:00:00 hald-addon-keyb
 4556 ?        00:00:00 hald-addon-stor
 4557 ?        00:00:00 hald-addon-stor
 4603 ?        00:00:00 mysqld_safe
 4667 ?        00:00:00 mysqld
 4668 ?        00:00:00 logger
 4827 ?        00:00:00 hcid
 4831 ?        00:00:00 sdpd
 4846 ?        00:00:00 krfcommd
 4859 ?        00:00:00 mdadm
 4894 ?        00:00:00 atd
 4907 ?        00:00:00 cron
 4934 ?        00:00:00 apache2
 4995 ?        00:00:00 apache2
 4996 ?        00:00:00 apache2
 4997 ?        00:00:00 apache2
 4998 ?        00:00:00 apache2
 5002 ?        00:00:00 apache2
 5010 tty1     00:00:00 getty
 5011 tty2     00:00:00 getty
 5012 tty3     00:00:00 getty
 5013 tty4     00:00:00 getty
 5014 tty5     00:00:00 getty
 5015 tty6     00:00:00 getty
 5035 ?        00:00:00 x-session-manag
 5078 ?        00:00:00 ssh-agent
 5081 ?        00:00:00 dbus-launch
 5082 ?        00:00:00 dbus-daemon
 5084 ?        00:00:00 gconfd-2
 5087 ?        00:00:00 gnome-keyring-d
 5089 ?        00:00:00 bonobo-activati
 5091 ?        00:00:00 gnome-settings-
 5096 ?        00:00:00 esd
 5101 ?        00:00:00 esd
 5104 ?        00:00:04 metacity
 5111 ?        00:00:03 gnome-panel
 5113 ?        00:00:02 nautilus
 5116 ?        00:00:00 gnome-volume-ma
 5122 ?        00:00:00 update-notifier
 5126 ?        00:00:00 gnome-cups-icon
 5131 ?        00:00:00 gnome-vfs-daemo
 5144 ?        00:00:00 gnome-power-man
 5151 ?        00:00:00 dhclient3
 5159 ?        00:00:00 mapping-daemon
 5170 ?        00:00:00 trashapplet
 5174 ?        00:00:00 gnome-keyboard-
 5176 ?        00:00:00 clock-applet
 5180 ?        00:00:00 gnome-netstatus
 5182 ?        00:00:00 mixer_applet2
 5191 ?        00:00:00 gnome-screensav
 5195 ?        00:00:00 firefox
 5206 ?        00:00:00 run-mozilla.sh
 5211 ?        00:00:48 firefox-bin
 5220 ?        00:00:00 netstat <defunct>
 5421 ?        00:00:00 cupsd
 5538 ?        00:00:00 syslogd
 5546 ?        00:00:04 acroread
 5604 ?        00:00:01 festival-synthe
 5606 ?        00:00:00 festival
 5607 ?        00:00:00 festival
 5608 ?        00:00:00 audsp
 5619 ?        00:00:00 notification-da
 5624 ?        00:00:00 gksu
 5625 ?        00:00:07 update-manager
 5633 ?        00:00:00 gconfd-2
 6361 ?        00:00:02 gnome-terminal
 6362 ?        00:00:00 gnome-pty-helpe
 6363 pts/0    00:00:00 bash
 6537 pts/0    00:00:00 ps

---

### Post by taurus on 2007-01-04
I think this is the guy...

```
5625 ? 00:00:07 update-manager
```
So from a terminal, kill it and then see if you can update it with

```
sudo kill -9 5625
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by SwaroopKunduru on 2007-01-04
sudo aptitude update

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [84.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
99% [8 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting fobzip2: (stdin) is not a bzip2 file.
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [84.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
99% [9 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectingbzip2: (stdin) is not a bzip2 file.
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  404 Not Found
Get:10 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Fetched 10B in 6s (2B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

---

### Post by SwaroopKunduru on 2007-01-04
sudo aptitude upgrade

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  bluez-pcmcia-support foomatic-db-gutenprint g++-4.0 gok
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast
  gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist
  gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth
  gtk2-engines-thinice ijsgutenprint kmplayer-doc libcompfaceg1 libgnutls12
  libnetcdf3 libstdc++6-4.0-dev libtasn1-2 libxine-main1 pcmcia-cs
  python-gadfly python-htmltmpl python-kjbuckets python-netcdf
  python-parted python-pgsql python-soappy python-stats python-syck wine
  x-window-system-core
0 packages upgraded, 0 newly installed, 0 to remove and 34 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by taurus on 2007-01-04
This is bad...  You are apparently running Dapper but somehow you have a few lines in /etc/apt/sources.list that contain edgy!!!  You can't mix them in /etc/apt/sources.list or bad things can happen to your machine and will happen.  Therefore, edit /etc/apt/sources.list and place a # in front of the lines that have edgy in them or replace edgy with dapper...

```
gksudo gedit /etc/apt/sources.list
```
Save it and see if you can update it now.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by SwaroopKunduru on 2007-01-04
is there any errors in the **source.list** I have pasted the contents as under.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
#deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

#deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
#deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free

---

### Post by taurus on 2007-01-04
Okay, it looks good now.  Now, run those two commands and see if it lets you update your Dapper!

```
sudo aptitude update
sudo aptitude upgrade
```

---

