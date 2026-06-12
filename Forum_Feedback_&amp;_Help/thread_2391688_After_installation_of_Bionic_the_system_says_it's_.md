---
title: "After installation of Bionic the system says it's Linux Mint 18.3?"
date: 2018-05-12
forum: Forum Feedback &amp; Help
---

### Post by cogitans on 2018-05-12
I’ve been using Linux Mint for several years now. But now I decided to go to Ubuntu as the terms of Ubuntu changed.

 
So I downloaded “ubuntu-18.04-desktop-amd64.iso” and installed it. I installed a few programs that I’m fond of.

 
But now i began optimizing the system itself. And now things slowly   began to confuse me. Several places the system told me that my system is   Linux Mint 18.3. That’s pretty strange to say the least. I did a  format  of my partition when I did the install so leftover files from  Linux  Mint can’t be the issue.

 
I compared the 2 files from Ubuntu and Linux Mint. They aren’t of the   same name and my used iso-file is of the same name that Ubuntu   presents.

 
I did several systemcalls:

 
“cat /etc/lsb-release”
->
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=18.3
DISTRIB_CODENAME=sylvia
DISTRIB_DESCRIPTION=“Linux Mint 18.3 Sylvia”


 “head -11 /usr/share/mintsources/rebecca/mintsources.conf”
->
[general]
description=Linux Mint 17.1 "Rebecca"
codename=rebecca
base_codename=trusty
use_ppas=true

 [mirrors]
default=http://packages.linuxmint.com
base_default=http://archive.ubuntu.com/ubuntu
mirrors=/usr/share/python-apt/templates/LinuxMint.mirrors
base_mirrors=/usr/share/python-apt/templates/Ubuntu.mirrors


 I was almost sure that somehow I got the iso of Linux Mint downloaded   and installed and I was just about to do a redownload and install   everything from scratch…again.

 
Then I wanted to make sure that the visuals agreed on my discoveries. And on
[https://www.ubuntu.com/desktop](https://www.ubuntu.com/desktop)
then desktop of Ubuntu looks just the same as my desktop although my system states that I’m using Linux Mint 18.3.

 
What’s going on here?
Has the mirrors of Ubuntus downloads been tampered with so some are pointing to Linux Mints servers?
How come the visuals are the same concerning the desktop?
I did all of these discoveries as I somehow noticed that there was a   folder named “linuxmint” in   “/usr/lib/linuxmint/mintSources/mintSources.py” during my updates.   That’s pretty strange, too, if I’m on Ubuntu Bionic.

 What’s going on here???

 
PS:
I’ve got my Home-directory on a partition separate from the main system.   It shouldn’t have any influenze on the systemfiles on my   systempartition. But I though it was worth mentioning that my   Home-folder is the only thing I’ve got from my old Linux Mint (with some   configuration-files on it).

 
PPS:
Oh, by the way: as the iso of Ubuntu 18.04 destroyed my GRUB during   installation (several attempts) and as “boot-repair” wasn’t able to fix   it I installed the system from an iso of Ubuntu 16.04 and did a   distribution-upgrade.

PPPS:
The command "cat /etc/apt/sources.list" states this confusing output:

# deb cdrom:[Ubuntu 16.04.4 LTS _Xenial Xerus_ - Release amd64 (20180228)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic main restricted
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic universe
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic-updates universe
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic-updates multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#-->>deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

---

### Post by jeremy31 on 2018-05-12
Duplicate of [https://ubuntuforums.org/showthread.php?t=2391687](https://ubuntuforums.org/showthread.php?t=2391687)
Closed

---

