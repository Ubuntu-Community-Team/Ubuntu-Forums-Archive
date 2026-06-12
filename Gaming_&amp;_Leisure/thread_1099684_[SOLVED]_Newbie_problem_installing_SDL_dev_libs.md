---
title: "[SOLVED] Newbie problem installing SDL dev libs"
date: 2009-03-18
forum: Gaming &amp; Leisure
---

### Post by Disch on 2009-03-18
I'm not entirely sure if this belongs here -- it's somewhat gaming related.

Anyway I recently installed Xubuntu 8.10 after being on WinNT for most of my life.  I'm trying to get myself set up, but all of this is very different from what I'm used to, and it's all very new to me.

I've been working on various projects using SDL, and so I'm trying to get the dev libs for SDL installed on this computer.  I found "libsdl1.2-dev" in Synaptic and tried to install it, but I get errors saying some of its dependencies aren't going to be installed.

Here's the exact output:

> libsdl1.2-dev:
 Depends: libglu1-xorg-dev but it is not going to be installed or
	libglu-dev
 Depends: libx11-dev but it is not going to be installed
 Recommends: libaa1-dev but it is not going to be installed
 Recommends: libartsc0-dev but it is not going to be installed
 Recommends: libcaca-dev but it is not going to be installed
 Recommends: libdirectfb-dev but it is not going to be installed
 Recommends: libxext-dev but it is not going to be installed
 Recommends: libxt-dev but it is not going to be installed

It says I should make sure all of the required repositories are added and enabled.  I went in Settings|Repositories and I have the following included (all three of them enabled):

> 
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner (Source Code)
cdrom:[Xubuntu 8.10_Intrepid Ibex_ - Release i386 (20081030.3)]/ intrepid main multiverse restricted


Am I missing something I should have?  I'm hoping this is just a simple matter of adding the right repository and not a more serious issue.  I tried looking around SDL's site, and it linked me to [{this page}](http://packages.debian.org/stable/libs/) which has the SDL package listed... but am I supposed to add that page as a repository?  Do I download the package and try to open it (and if so what do I open it with)?

Again this is all new stuff for me, so a walkthrough in simple steps/terms would be fantastic.

Any help greatly appreciated.  Thanks in advance!

---

### Post by Perfect Storm on 2009-03-18
Please post the output of this command;

```
cat /etc/apt/sources.list
```

---

### Post by Disch on 2009-03-18
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb cdrom:[Xubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030.3)]/ intrepid main multiverse restricted

```

I take it I'm to uncomment those two commented lines?

I'll try that and report back

edit:

Ack, apparently I can't edit the file with mousepad (not letting me save).  I'm assuming I'd need to input the admin password (or whatever it's called) to change it, but I'm never being prompted.

---------------------------------------
UPDATE:

Turns out the problem was a version confliction with libx11-6.  I realized this by trying to install the dependencies one at a time until I tried to install libx11-dev, when I got this error:

Depends: libx11-6 (=2:1.1.5-2ubuntu1) but 2:1.1.5-2ubuntu1.1 is to be installed

After a while of bouncing around, I just downloaded the 2:1.1.5-2ubuntu1 package and force installed it with dpkg.  the SDL lib installed fine after that.

Dunno how that happened.  But alas, it appears to be solved now.

---

