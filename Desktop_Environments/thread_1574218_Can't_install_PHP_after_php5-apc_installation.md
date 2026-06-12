---
title: "Can't install PHP after php5-apc installation"
date: 2010-09-13
forum: Desktop Environments
---

### Post by jonyD on 2010-09-13
Hi,

My first post and I must say that I'm a jackass. Explanation bellow.

I wanted to add another extension to my PHP5.3.2-1ubuntu4.2 -> php5-apc, and despite inf. that other extensions will be removed I have continued. PHP is no longer installed  other extensions like php-gd, -mcrypt, -mysql, phpmyadmin too... Sweet Jesus how can I fix this? Im getting:
```

sudo apt-get install php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5: Depends: libapache2-mod-php5 (>= 5.3.3-0.dotdeb.0) but it is not going to be installed or
                 libapache2-mod-php5filter (>= 5.3.3-0.dotdeb.0) but it is not going to be installed or
                 php5-cgi (>= 5.3.3-0.dotdeb.0) but it is not going to be installed or
                 php5-fpm (>= 5.3.3-0.dotdeb.0) but it is not going to be installed
E: Broken packages

```

sources.list
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb http://ie.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ie.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ie.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ie.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ie.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

deb http://archive.canonical.com/ lucid partner
deb http://deb.opera.com/opera etch non-free
deb http://php53.dotdeb.org stable all
deb http://php53.dotdeb.org stable all
```

Ubuntu 10.04 Lucid Lynx. 
](*,)

---

### Post by jonyD on 2010-09-14
anyone?

---

### Post by cutekazuya on 2010-09-14
```
sudo dpkg --purge php5
```

then 

```
sudo apt-get install php5
```

give "Xampp" a try, easier to install and configure.

---

