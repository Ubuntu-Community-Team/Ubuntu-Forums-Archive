---
title: "Duplicate entry in sources.list"
date: 2009-05-20
forum: General Help
---

### Post by Tribulation on 2009-05-20
Apparently, I have a duplicate entry in my sources.list file. Every time I run apt-get update I get the message

```
W: Duplicate sources.list entry http://ppa.launchpad.net jaunty/main Packages (/var/lib/apt/lists/ppa.launchpad.net_bogdanb_ppa_ubuntu_dists_jaunty_main_binary-amd64_Packages)
```

I can't see to find the duplicate entry though.. Here's the contents of sources.list in case..

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.osuosl.org/ubuntu/ jaunty main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.osuosl.org/ubuntu/ jaunty-updates main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ubuntu.osuosl.org/ubuntu/ jaunty universe
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty universe
deb http://ubuntu.osuosl.org/ubuntu/ jaunty-updates universe
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.osuosl.org/ubuntu/ jaunty multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty multiverse
deb http://ubuntu.osuosl.org/ubuntu/ jaunty-updates multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://ubuntu.osuosl.org/ubuntu/ jaunty-security main restricted
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty-security main restricted
deb http://ubuntu.osuosl.org/ubuntu/ jaunty-security universe
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty-security universe
deb http://ubuntu.osuosl.org/ubuntu/ jaunty-security multiverse
deb-src http://ubuntu.osuosl.org/ubuntu/ jaunty-security multiverse
deb http://packages.medibuntu.org/ gutsy free non-free
deb http://archive.ubuntu.com/ubuntu jaunty universe multiverse
deb-src http://archive.ubuntu.com/ubuntu jaunty universe multiverse

## amarok 1.4 
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```

It's probably something simple, but I seem to be stuck anyhow.

---

### Post by _Purple_ on 2009-05-20
Why do you have a gusty repo?
```
deb http://packages.medibuntu.org/ gutsy free non-free

```

Which version of Ubuntu are you using?

---

### Post by Tribulation on 2009-05-20
You know, I'm really not sure why I have a Gutsy repo... I don't recall adding it. I probably added it by mistake at some point. I'm using Jaunty.

---

### Post by Soul-Sing on 2009-05-20
medibuntu doesn,t come default with ubuntu, so you made a very little mistake with gutsy.

---

### Post by Yellow Pasque on 2009-05-20
apt seems to think this is the duplicate line:
```
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```

I don't see two listings for it (I may be missing it). Note that you might have other source files in /etc/apt/sources.list.d

---

### Post by _Purple_ on 2009-05-20
Change gutsy to jaunty and remove this line
```
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```
Then run
```
sudo apt-get update
```
Post back if you get any error again.

---

### Post by Yellow Pasque on 2009-05-20
_Purple_, I doubt that will prevent the "duplicate line" warning (although it definitely needs done if the user wishes to use medibuntu packages).

---

### Post by Tribulation on 2009-05-20
Thanks _Purple_, that did the trick. I'm curious though, how was that identified as the duplicate? The closest I saw to that was 

```
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```

---

### Post by _Purple_ on 2009-05-20
Tribulation, sorry. I thought that line was repeated. Can you still access that repository even after removing that line? Try to to run this 
```
sudo apt-get install amarok14
```

Is there any error message?

---

### Post by Tribulation on 2009-05-20
Yeah, I can access it just fine.

---

