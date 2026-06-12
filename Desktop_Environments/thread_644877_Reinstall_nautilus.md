---
title: "Reinstall nautilus?"
date: 2007-12-19
forum: Desktop Environments
---

### Post by Bultot on 2007-12-19
Nautilus wasn't working properly.. so I deleted nautilus with apt. Then I tried to install nautilus but it seems it isn't in the repositories? 
How can I reinstall nautilus?

Thanks in advance

---

### Post by rsambuca on 2007-12-19
It is definitely there.  Make sure you have your repositories enabled.  Go to "System - Administration - Software Sources".  Make sure the repositories you want are enabled by checking the boxes.  Then update them and you will be able to get back Nautilus.

---

### Post by SOULRiDER on 2007-12-19
You can just do
```
sudo aptitude install ubuntu-desktop
``` That will install all applications that were there by default.

---

### Post by rsambuca on 2007-12-19
> **SOULRiDER said:**
> You can just do
```
sudo aptitude install ubuntu-desktop
``` That will install all applications that were there by default.

That won't work if the repositories aren't enabled first!

---

### Post by Bultot on 2007-12-20
Below is my sources.list. When I try to install ubuntu-desktop it gives the following error:
```
No candidate version found for ubuntu-desktop
```

```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

# last fm
deb http://apt.last.fm/ debian testing

# avant-window-navigator
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

# Gnome Do
deb http://ppa.launchpad.net/rharding/ubuntu gutsy main
deb-src http://ppa.launchpad.net/rharding/ubuntu gutsy main

```

---

### Post by rich.bradshaw on 2007-12-20
Have you done sudo apt-get update?

Anyway, it won't make any difference once it's reinstalled - you need to delete user settings in ~/.nautilus

---

### Post by rsambuca on 2007-12-20
You are missing the four of the most important repos!  You need to add the following line to your sources:

```
deb http://nl.archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted
```

---

### Post by Bultot on 2007-12-20
Thank you! That did the trick..

---

### Post by phillipbeynon on 2008-04-01
Be carefull not to use the commands:
 
sudo apt-get -y --purge remove nautilus 
sudo apt-get -y install nautilus

Or you'll end up with:
.
phillipbeynon@ThinkCenter8185-D3U:~$ sudo apt-get install rythmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rythmbox

Thankfully the command previously mentioned worked.

sudo aptitude -y install ubuntu-desktop

This resolves the issue, yes.  But this still leaves me perplexed about the question about dependancies aptitude asked me that I answered yes to as I haven';t seen it before and don't understand what aptitude was asking me, but that was too far back to scroll the terminal widow. If someone can tell me how to find a log with the output or would like to recreate and post maybe I would be able to learn something here, but aptitude didn't give the same output when I attempted to recreate the issue. Strange. and I'm still left with my original issue and reason for proding at it in the first place.

Still Unresolved Issue

Nautilus somehow became fullscreen and I cannot figure out how to change it!  Any thoughts?

---

### Post by hollowhead on 2008-04-10
I had nautilus corrupted the only reason for this I could see was Rhythmbox crashing when we plugged in an ipod shuffle it was setup to load when an ipod was connected.  Try as I might reinstalling it did not work and I had to reinstall gutsy.  Please let us know if reinstalling  nautilus works.....

---

