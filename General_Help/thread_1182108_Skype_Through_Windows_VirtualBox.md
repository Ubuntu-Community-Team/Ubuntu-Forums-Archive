---
title: "Skype Through Windows VirtualBox"
date: 2009-06-08
forum: General Help
---

### Post by nmaster on 2009-06-08
There clearly [problems]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/362203") with Jaunty and skype related to CPU usage and audio.  Has anyone tried using skype through a windows virtualbox?  I was wondering if this would solve the problems with pulse.  I'll try later and (hopefully) post my success story.

If anyone has already tried, any info would be appreciated.

---

### Post by nikgare on 2009-06-08
"Looks like it can be fixed with skype-static
[http://www.lockergnome.com/linux/2009/06/01/the-final-skype-on-ubuntu-904-solution/](http://www.lockergnome.com/linux/2009/06/01/the-final-skype-on-ubuntu-904-solution/) "

This worked for me - maybe it'll work for you?

---

### Post by nmaster on 2009-06-08
skype-static depends on skype-common version 2.0.0.72-0medibuntu4, but I can only find version2.0.0.72-0mediubuntu1.1

I'm not sure what to do.  I've looked at a lot of ways to fix skype on jaunty, I'd love to find a way that works.

---

### Post by nikgare on 2009-06-09
This is my sources.list, the version of skype-common will be somewhere in there!

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.telfort.nl/ubuntu/ jaunty main restricted
deb-src http://ftp.telfort.nl/ubuntu/ jaunty main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.telfort.nl/ubuntu/ jaunty-updates main restricted
deb-src http://ftp.telfort.nl/ubuntu/ jaunty-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.telfort.nl/ubuntu/ jaunty universe
deb-src http://ftp.telfort.nl/ubuntu/ jaunty universe
deb http://ftp.telfort.nl/ubuntu/ jaunty-updates universe
deb-src http://ftp.telfort.nl/ubuntu/ jaunty-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.telfort.nl/ubuntu/ jaunty multiverse
deb-src http://ftp.telfort.nl/ubuntu/ jaunty multiverse
deb http://ftp.telfort.nl/ubuntu/ jaunty-updates multiverse
deb-src http://ftp.telfort.nl/ubuntu/ jaunty-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner
deb http://ftp.telfort.nl/ubuntu/ jaunty-security main restricted
deb-src http://ftp.telfort.nl/ubuntu/ jaunty-security main restricted
deb http://ftp.telfort.nl/ubuntu/ jaunty-security universe
deb-src http://ftp.telfort.nl/ubuntu/ jaunty-security universe
deb http://ftp.telfort.nl/ubuntu/ jaunty-security multiverse
deb http://ftp.telfort.nl/ubuntu/ jaunty-backports restricted main multiverse universe
deb-src http://ftp.telfort.nl/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main #Amarok 1.4 PPA
deb http://ppa.launchpad.net/awn-testing/ppa/ubuntu jaunty main #avant-window-navigator
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main #chromium-browser
deb http://deb.opera.com/opera/ lenny non-free #opera
deb http://download.skype.com/linux/repos/debian stable non-free #skype
deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu jaunty main #midori
deb http://ppa.launchpad.net/do-core/ubuntu jaunty main #gnome-do
deb http://dl.google.com/linux/deb/ stable non-free #google
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main #ubuntu-tweak
deb http://ppa.launchpad.net/transmissionbt/ubuntu jaunty main #transmission-gtk
deb http://ppa.launchpad.net/shutter/ppa/ubuntu jaunty main #shutter

deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu jaunty main #XBMC

deb http://apt.boxee.tv jaunty main
deb http://ppa.launchpad.net/team-xbmc-svn/ppa/ubuntu jaunty main
deb http://download.virtualbox.org/virtualbox/debian jaunty non-free #Virtualbox
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/specto/ppa/ubuntu jaunty main #specto
deb http://ppa.launchpad.net/exaile-devel/ubuntu jaunty main #exaile
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main

```

---

### Post by nmaster on 2009-06-09
Thanks for the post.  I'll try that when I get a chance (probably in the next few days).  

I'm still curious about using Windows XP through VirtualBox as a solution though; I'll need XP to run other programs anyway.  I kind of just want to see what anyone else's experiences have been with it.  I know that some people use VirtualBox for gaming and I don't game but I thought it would be okay for Skype.

I say XP and not Vista because I would like the virtual machine to not be bloated.  I was hoping to use nLite to slim XP down even more.

Anyone with experience with VirtualBox or nLite, please let me know if you had success or what other resources to look at or anything.

---

