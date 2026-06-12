---
title: "Package system is broken."
date: 2012-07-18
forum: Desktop Environments
---

### Post by Lovecore on 2012-07-18
So i've been trying to resolve this issue for about 30 minutes and I'm now short on time. Here is my error details:


```
The following packages have unmet dependencies:

libdbusmenu-qt2:i386: Depends: libc6 (>= 2.1.3) but 2.15-0ubuntu10 is installed
                      Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
                      Depends: libqt4-dbus (>= 4:4.6.2) but 4:4.8.1-0ubuntu4.1 is installed
                      Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.1 is installed
                      Depends: libqtgui4 (>= 4:4.7.0~beta2) but 4:4.8.1-0ubuntu4.1 is installed
                      Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is installed
libqt4-dbus:i386: Depends: libqt4-xml (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                  Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
libqt4-declarative:i386: Depends: libqt4-network (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                         Depends: libqt4-script (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                         Depends: libqt4-sql (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                         Depends: libqt4-xmlpatterns (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                         Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                         Depends: libqtgui4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
libqt4-network:i386: Depends: libqt4-dbus (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                     Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
libqt4-script:i386: Depends: libqt4-dbus (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                    Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
libqt4-sql-mysql:i386: Depends: libqt4-sql (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                       Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
libqt4-sql:i386: Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
libqt4-xml:i386: Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
libqt4-xmlpatterns:i386: Depends: libqt4-network (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                         Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
libqtgui4:i386: Depends: libqt4-declarative (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
                Depends: libqtcore4 (= 4:4.8.1-0ubuntu4.1) but 4:4.8.1-0ubuntu4.1 is installed
skype-bin:i386: Depends: libc6 (>= 2.4) but 2.15-0ubuntu10 is installed
                Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
                Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.1 is installed
                Depends: libqt4-network (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.1 is installed
                Depends: libqtcore4 (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.1 is installed
                Depends: libqtgui4 (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.1 is installed
                Depends: libstdc++6 (>= 4.2.1) but 4.6.3-1ubuntu5 is installed
sni-qt:i386: Depends: libc6 (>= 2.2) but 2.15-0ubuntu10 is installed
             Depends: libdbusmenu-qt2 (>= 0.3.5) but 0.9.2-0ubuntu1 is installed
             Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
             Depends: libqt4-dbus (>= 4:4.6.1) but 4:4.8.1-0ubuntu4.1 is installed
             Depends: libqtcore4 (>= 4:4.7.3-1ubuntu3~) but 4:4.8.1-0ubuntu4.1 is installed
             Depends: libqtgui4 (>= 4:4.7.3) but 4:4.8.1-0ubuntu4.1 is installed
             Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is installed

```

things i've done:
apt-get install -f
dpkg --audit
dpkg --configure -a
rm /var/cache/apt/archives -- nothing there
I've tried to manually install aptitude and dependencies but that didn't work either.
commented out unnecessary repositories in /etc/apt/sources.list
Attempted to manually download the proper libqtcore4 deb file and add it, failed as well.
Also done some other things that i can't seem to think off as im in a rush. 

Any help is appreciated!

Other info:

dpkg --audit result
```
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 skype                VOIP and instant messaging client
 libqtgui4:i386       Qt 4 GUI module
 libqt4-sql:i386      Qt 4 SQL module
 libqt4-declarative:i386 Qt 4 Declarative module
 libqt4-network:i386  Qt 4 network module
 libqt4-sql-mysql:i386 Qt 4 MySQL database driver
 libqt4-script:i386   Qt 4 script module
 libqt4-dbus:i386     Qt 4 D-Bus module
 sni-qt:i386          indicator support for Qt
 libqt4-xml:i386      Qt 4 XML module
 skype-bin:i386       VOIP and instant messaging client - binary files
 libqt4-xmlpatterns:i386 Qt 4 XML patterns module
 libdbusmenu-qt2:i386 Qt implementation of the DBusMenu protocol

```

dpkg --configure -a results:
```

pkg: dependency problems prevent configuration of libqtgui4:i386:
 libqtgui4:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
dpkg: error processing libqtgui4:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql:i386:
 libqt4-sql:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
dpkg: error processing libqt4-sql:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-declarative:i386:
 libqt4-declarative:i386 depends on libqt4-sql (= 4:4.8.1-0ubuntu4.1); however:
  Package libqt4-sql:i386 is not configured yet.
 libqt4-declarative:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
 libqt4-declarative:i386 depends on libqtgui4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libqt4-declarative:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-network:i386:
 libqt4-network:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
dpkg: error processing libqt4-network:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-sql-mysql:i386:
 libqt4-sql-mysql:i386 depends on libqt4-sql (= 4:4.8.1-0ubuntu4.1); however:
  Package libqt4-sql:i386 is not configured yet.
 libqt4-sql-mysql:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
dpkg: error processing libqt4-sql-mysql:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-script:i386:
 libqt4-script:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
dpkg: error processing libqt4-script:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-dbus:i386:
 libqt4-dbus:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
dpkg: error processing libqt4-dbus:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sni-qt:i386:
 sni-qt:i386 depends on libqt4-dbus (>= 4:4.6.1); however:
  Package libqt4-dbus:i386 is not configured yet.
 sni-qt:i386 depends on libqtcore4 (>= 4:4.7.3-1ubuntu3~); however:
  Package libqtcore4:i386 is not installed.
 sni-qt:i386 depends on libqtgui4 (>= 4:4.7.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing sni-qt:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xml:i386:
 libqt4-xml:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
dpkg: error processing libqt4-xml:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of skype-bin:i386:
 skype-bin:i386 depends on libqt4-dbus (>= 4:4.5.3); however:
  Package libqt4-dbus:i386 is not configured yet.
 skype-bin:i386 depends on libqt4-network (>= 4:4.5.3); however:
  Package libqt4-network:i386 is not configured yet.
 skype-bin:i386 depends on libqtcore4 (>= 4:4.5.3); however:
  Package libqtcore4:i386 is not installed.
 skype-bin:i386 depends on libqtgui4 (>= 4:4.5.3); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing skype-bin:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libqt4-xmlpatterns:i386:
 libqt4-xmlpatterns:i386 depends on libqt4-network (= 4:4.8.1-0ubuntu4.1); however:
  Package libqt4-network:i386 is not configured yet.
 libqt4-xmlpatterns:i386 depends on libqtcore4 (= 4:4.8.1-0ubuntu4.1); however:
  Package libqtcore4:i386 is not installed.
dpkg: error processing libqt4-xmlpatterns:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdbusmenu-qt2:i386:
 libdbusmenu-qt2:i386 depends on libqt4-dbus (>= 4:4.6.2); however:
  Package libqt4-dbus:i386 is not configured yet.
 libdbusmenu-qt2:i386 depends on libqtcore4 (>= 4:4.7.0~beta1); however:
  Package libqtcore4:i386 is not installed.
 libdbusmenu-qt2:i386 depends on libqtgui4 (>= 4:4.7.0~beta2); however:
  Package libqtgui4:i386 is not configured yet.
dpkg: error processing libdbusmenu-qt2:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of skype:
 skype depends on skype-bin; however:
  Package skype-bin is not installed.
  Package skype-bin:i386 is not configured yet.
dpkg: error processing skype (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libqtgui4:i386
 libqt4-sql:i386
 libqt4-declarative:i386
 libqt4-network:i386
 libqt4-sql-mysql:i386
 libqt4-script:i386
 libqt4-dbus:i386
 sni-qt:i386
 libqt4-xml:i386
 skype-bin:i386
 libqt4-xmlpatterns:i386
 libdbusmenu-qt2:i386
 skype

```

---

### Post by Cheesehead on 2012-07-18
There are some pretty big version changes there.

> Depends: libc6 (>= 2.1.3) but 2.15-0ubuntu10 is installed
For example, 2.1.3 is so old that no supported version uses it anymore, yet 2.15 is the latest version in 12.04.

What version of Ubuntu are you running?

Please paste your /etc/apt/sources.list here.

---

### Post by Lovecore on 2012-07-19
EDIT:: I created a back up source.list and then re-created one from here: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) This seems to fixed the issue, I'm currently mid-update with no issues. 
EDIT 2:: That resolved the issue. Thanks for all the help :)

I'm on Ubuntu 12.04 LTS

here's the contents of sources.list

```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/
# deb http://packages.linuxmint.com/ precise main upstream import # disabled on upgrade to precise
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ precise partner
# deb http://packages.medibuntu.org/ precise free non-free # disabled on upgrade to precise

# deb http://archive.getdeb.net/ubuntu oneiric-getdeb apps
# deb http://archive.getdeb.net/ubuntu oneiric-getdeb games


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

## deb http://security.ubuntu.com/ubuntu precise-security main restricted
## deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
## deb http://security.ubuntu.com/ubuntu precise-security universe
## deb-src http://security.ubuntu.com/ubuntu precise-security universe
## deb http://security.ubuntu.com/ubuntu precise-security multiverse
## deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
# deb http://ppa.launchpad.net/cheako/packages4diabloiii/ubuntu precise main
# deb-src http://ppa.launchpad.net/cheako/packages4diabloiii/ubuntu precise main
```

Thanks for the help so far!

---

