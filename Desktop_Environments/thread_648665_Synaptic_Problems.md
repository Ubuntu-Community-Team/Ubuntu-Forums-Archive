---
title: "Synaptic Problems"
date: 2007-12-23
forum: Desktop Environments
---

### Post by blueberry17 on 2007-12-23
Hi! i am using Ubuntu 7.10 Gutsy. Even though all of my repositories are enabled in Synaptic, I get this message:

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release/dists/gutsy/partner/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy/Release/dists/gutsy/partner/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release/dists/gutsy/partner/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release/dists/gutsy/partner/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80][/B]


What will fix it? I've also noticed that some packages I want to download don't show up (again, ALL of the repositories are enabled!)

---

### Post by richardjennings on 2007-12-23
do you get the same error with:

sudo apt-get update

---

### Post by blueberry17 on 2007-12-23
yes, i do.

---

### Post by reckless2k2 on 2007-12-23
try backing up your sources list and then use this one:

```
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

deb http://packages.medibuntu.org/ gutsy free non-free

```

---

### Post by blueberry17 on 2007-12-23
it won't let me edit the file. How do I log in as root?

---

### Post by reckless2k2 on 2007-12-23
yeah that's scary. ok...here's the hand holding:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.BAK

```
then edit sources list:

```
gksudo gedit /etc/apt/sources.list
```

replace your current code with mine. the first line backed up your file so your good.

the run 

```
sudo apt-get update
```

---

### Post by blueberry17 on 2007-12-23
still, it won't let me save it. Now I've accessed it both through the terminal and through Nautilus, but it still won't let me change the file! Now what?!

---

### Post by reckless2k2 on 2007-12-23
if you are getting errors saying it won't save, make sure you have synaptic closed and have admin rights using sudo. if not, i assume you are not an admin and do not have access to an admin account or root. you should be able to edit and save using sudo. make sure the package manager is closed.

---

### Post by blueberry17 on 2007-12-23
THANK YOU!!! THANK YOU!!! THANK YOU!!! It worked! I just wonder how it became messed up in the first place though...

---

### Post by reckless2k2 on 2007-12-23
mark solved baby.....your welcome...your welcome.....i'm here all night. hahaha

---

