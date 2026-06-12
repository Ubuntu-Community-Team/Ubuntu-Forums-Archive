---
title: "problem with sources.list plz help"
date: 2009-02-27
forum: General Help
---

### Post by meinvateristnein on 2009-02-27
when i try to do anyting involving adding/removing programs and sources this happens
ubuntu 8.10


Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by avtolle on 2009-02-27
Can you post your /etc/apt/sources.list for us to review?

---

### Post by meinvateristnein on 2009-02-27
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid main restricted
deb-src 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-updates main restricted
deb-src 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid universe
deb-src 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid universe
deb 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-updates universe
deb-src 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid multiverse
deb-src 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid multiverse
deb 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-updates multiverse
deb-src 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-backports main restricted universe multiverse
# deb-src 
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse




PS. it says line 5 is wrong but i found nothing wrong with it

---

### Post by thtrgremlin on 2009-02-27
I could be wrong, but there should not be newlines between "deb" and the address. This starts at line 5, but how the file got that way is beyond me, so either your paste didn't format correctly, or that is a different way to do the config.

The only lines that look correct to me are these:
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

Make all your lines look like that. 

At very least:
> # deb
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-backports main restricted universe multiverse
# deb-src
[ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-backports main restricted universe multiverse

would cause total failure because lines that begin with '#' are ignored, so it only sees the address and doesn't know what to do with it. Those lines should be 

> # deb [ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-backports main restricted universe multiverse
# deb-src [ftp://ftp.cs.mun.ca/](ftp://ftp.cs.mun.ca/) intrepid-backports main restricted universe multiverse

Then the entire line is properly commented out.

After that you just need to do an 'sudo apt-get update', and everything should be ok

---

