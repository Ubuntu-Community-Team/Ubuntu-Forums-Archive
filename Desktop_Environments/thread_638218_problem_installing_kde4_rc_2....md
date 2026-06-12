---
title: "problem installing kde4 rc 2..."
date: 2007-12-11
forum: Desktop Environments
---

### Post by searayman on 2007-12-11
mike@mike-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libqimageblitz4 kdebase-workspace systemsettings-kde4 libbluetooth-dev
  kdebase-data-kde4 libsmbclient-dev libkeyutils-dev x11proto-xf86misc-dev
  libnm-util-dev libsoprano-dev libboost-dev libstreams-dev libcaptury-dev
  kdebase-kio-plugins-kde4 libsqlite0-dev libxxf86misc-dev
  libstrigiqtdbusclient-dev libqt4-dev knetattach-kde4 libusb-dev
  kdebase-workspace-bin klipper-kde4 libraw1394-dev libungif4-dev libplasma1
  kdebase-workspace-data libpq-dev libqimageblitz-dev ksysguard-kde4
  network-manager-dev libstreamanalyzer-dev libsensors-dev kdepimlibs-data
  libenchant-dev libcapseo-dev libxkbfile-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdebase-runtime-bin-kde4
The following NEW packages will be installed:
  kdebase-runtime-bin-kde4
0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
13 not fully installed or removed.
Need to get 0B/60.1kB of archives.
After unpacking 283kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  kdebase-runtime-bin-kde4
Install these packages without verification [y/N]? y
(Reading database ... 195014 files and directories currently installed.)
Unpacking kdebase-runtime-bin-kde4 (from .../kdebase-runtime-bin-kde4_4%3a3.97.0-1ubuntu3~gutsy1~ppa2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a3.97.0-1ubuntu3~gutsy1~ppa2_all.deb (--unpack):
 trying to overwrite `/usr/bin/kwriteconfig', which is also in package kdebase-bin
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-runtime-bin-kde4_4%3a3.97.0-1ubuntu3~gutsy1~ppa2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mike@mike-desktop:~$

---

### Post by inportb on 2007-12-11
Hm... try

sudo apt-get -f dist-upgrade

apparently, some of the updated packages need other packages that have not yet been installed. hence, dist-upgrade.

(I just installed that stuff too, and it's a bit confusing.)

---

### Post by rmtatum on 2007-12-12
"If you're having trouble installing KDE4, in a !Terminal run: « sudo apt-get --purge remove $(dpkg -l | grep "4:3.97.0" |awk '{print $2}') » then run « sudo apt-get update && sudo apt-get dist-upgrade » - After that install KDE4 as normal" -- ubotu bot on freenode IRC chat channel #kubuntu

---

### Post by shimatta on 2007-12-12
I got it installed fine, but when I try to login into KDE4 from KDM, it just restarts X, any idea?

- Jaska

---

### Post by undine on 2007-12-12
> **shimatta said:**
> I got it installed fine, but when I try to login into KDE4 from KDM, it just restarts X, any idea?

- Jaska

The only way I could get around this problem was to add the line:

```
export KDEHOME=~/.kde4

```

To:

```
/usr/lib/kde4/bin/startkde
```

---

### Post by shimatta on 2007-12-12
> **undine said:**
> The only way I could get around this problem was to add the line:

```
export KDEHOME=~/.kde4

```

To:

```
/usr/lib/kde4/bin/startkde
```

Thank you. Works fine now.

---

