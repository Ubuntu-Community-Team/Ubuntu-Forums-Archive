---
title: "Open Office"
date: 2009-01-28
forum: General Help
---

### Post by sports fan Matt on 2009-01-28
Is the current version 2.4.1? or was 3.0 released ? Im running Intrepid (upgraded online from Hardy) and here is my cat /etc/apt/sources.list, does it look ok? : office@office-desktop:~$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid main restricted
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-updates main restricted
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid universe
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid multiverse
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-security main restricted
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-security universe
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-security multiverse
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-proposed restricted main multiverse universe
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-proposed restricted main multiverse universe #Added by software-properties
deb [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-backports restricted main multiverse universe
deb-src [http://ubuntu.osuosl.org/ubuntu/](http://ubuntu.osuosl.org/ubuntu/) intrepid-backports restricted main multiverse universe #Added by software-properties

---

### Post by ajcham on 2009-01-28
3.0.1 is the latest version of OpenOffice, however version 3 was not ready in time for Intrepid - hence why only 2.4.1 appears in the official repositories.

The PPA repo has version 3.0 available (v3.0.1 is a very recent release and hasn't found it's way to the repo yet).  Add the following to sources.list if you want it:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main

```

---

