---
title: "Couldn't stat source package list?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by Almighty on 2006-01-31
When I go through Synaptic or try to update through terminal etc, I get a Warning  box that says>  :The following problems were found on your system:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


I have tried to update and I have also tried to re-enable my repositories, and no good so far. No functionality of the operating system is apparent. No weird glitches or anything. I just prefer not to have any mystery boxes poping up.

Any help would be awesome...Thanks

---

### Post by carlosqueso on 2006-01-31
Open up your sources.list by typing ```
sudo gedit /etc/apt/sources.list
``` and put a # and a space in front of the line with cdrom.   It should work then.

---

### Post by Almighty on 2006-01-31
'CDROM' doesnt appear anyplace in the source list. After messing around with it for a while, this is what it looks like.

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

deb http://wine.sourceforge.net/apt/ binary/

## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free
## deb http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
## deb-src http://seveas.ubuntulinux.nl/ breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
## created by arnieplanetremoved


```

---

### Post by Almighty on 2006-02-03
Well I have finally figured out how to fix my problem. It seems as though there was a new release of Automatix, from 5.0 to 5.2. So all I did was install the newest version of the software. If you are having the same problem use type this into terminal...

```
wget http://beerorkid.com/automatix/automatix_5.2-1_i386.deb
sudo dpkg -i automatix_5.2-1_i386.deb
```

---

