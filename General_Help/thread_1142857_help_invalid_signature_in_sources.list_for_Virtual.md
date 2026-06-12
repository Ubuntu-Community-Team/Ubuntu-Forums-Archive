---
title: "help: invalid signature in sources.list for VirtualBox"
date: 2009-04-29
forum: General Help
---

### Post by agnes on 2009-04-29
Hello everyone,

every time I do sudo apt-get update I get this error at the end:

```
Fetched 199B in 0s (265B/s)
Reading package lists... Done
W: GPG error: http://download.virtualbox.org intrepid Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>
W: You may want to run apt-get update to correct these problems

```

I went to the website of VirtualBox and they said to get the key, do this:
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -

```
Then is see "OK"  in my terminal but I still get that error message.

Also when I do
sudo apt-key add sun_vbox.asc
I get 
gpg: can't open `sun_vbox.asc': No such file or directory

I have VirtualBox version 2.2.2 (the latest).

This is the content of my /etc/apt/sources.list file:
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ intrepid-proposed restricted main multiverse universe
deb http://ppa.launchpad.net/project-neon/ppa/ubuntu intrepid main
deb http://ppa.launchpad.net/kubuntu-members-kde4/ppa/ubuntu intrepid main
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
```

I already tried some other method whith running a script for automatically searching keys (or something like that) which helped me with the errors for KDE libraries, but not with this error.

---

### Post by TimBosse on 2009-05-02
Sadly, it appears that the download site is busted.  No real information yet.  Nothing posted on the virtualbox site.

---

### Post by agnes on 2009-05-03
Ok. 

Well I'll just remove the line from the sources.list then, for me there's no necessity for upgrades/patches for VirtualBox anyway (I just wanted to know what was wrong).

---

### Post by AlexanderDGreat on 2009-08-07
Hi, I'm also experiencing the same problem, others as well: [http://forums.virtualbox.org/viewtopic.php?f=7&t=12384](http://forums.virtualbox.org/viewtopic.php?f=7&t=12384)

So I just downloaded the .deb for Virtualbox 3.04 and installed from there.

---

