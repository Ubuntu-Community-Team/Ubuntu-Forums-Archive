---
title: "General Issues and General Malaise"
date: 2008-05-11
forum: Desktop Environments
---

### Post by damonjablons on 2008-05-11
Hey Forumers,

I've been running Ubuntu since I did a Windows update on my Vista laptop, and it broke the OS, now I don't even dual-boot anymore, I just run Ubuntu straight up -- thank you to all developers.

I upgraded to Hardy and since then I've been having a few issues with my system.

First of all, my sources file looks weird, and has been having a few issues, here it is:

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ hardy universe main multiverse restricted
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-backports universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## Gnome Do sources
deb http://ppa.launchpad.net/rharding/ubuntu hardy main
deb-src http://ppa.launchpad.net/rharding/ubuntu hardy main
deb-src http://ppa.launchpad.net/rharding/ubuntu hardy main

## AWN Sources
#deb http://download.tuxfamily.org/syzygy42 hardy avant-window-navigator
#deb-src http://download.tuxfamily.org/syzygy42 hardy avant-window-navigator

#AUTOMATIX REPOS START

#deb http://www.getautomatix.com/apt hardy main
#AUTOMATIX REPOS END
deb http://dl.google.com/linux/deb/ stable non-free

#Ubuntu Tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main

#IE
# deb http://us.archive.ubuntu.com/ubuntu edgy universe

#MoBlock Repos
# deb http://moblock-deb.sourceforge.net/debian gutsy main
# deb-src http://moblock-deb.sourceforge.net/debian gutsy main

## Wine, Ubuntu Gutsy (7.10):
deb http://wine.budgetdedicated.com/apt hardy main
deb-src http://wine.budgetdedicated.com/apt hardy main

```

In addition to that, when I close my laptop it's supposed to go on standby.  Maybe one out of five times it actually does.  When it does, I have a fifty-fifty chance of getting the password prompt to log back into the system.  The other half of the time, I just get a beige screen with a cursor, and I'm forced to manually restart my machine.

My machine is an Inspiron 1520 if that helps, and it didn't have any issues running Gutsy.

I appreciate all of the help.

Regards,
Damon

---

### Post by macaholic on 2008-05-11
You can safely remove any additions in your sources file related to gutsy, or you can remove them in System > Administration > Software Sources. 
As far as the standby, I've never been able to get suspend hibernate or anything of the like working on my machine, but maybe someone else can help you with that.
P.S. Why is one of the tags for tjhis post "butts"? :p

---

