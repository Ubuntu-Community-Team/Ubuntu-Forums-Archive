---
title: "Really slow gnome booting since gutsy"
date: 2007-10-28
forum: Desktop Environments
---

### Post by Adnarim on 2007-10-28
Hi,
my system-booting is as usual (as it was with edgy and feisty..) but after GDM, after I logged in it became terribly slow. It takes between 30-60 sec after I logged in until I'm on my desktop and I can work. With feisty this lasted about 5 sec! 

I'm just using gnome, no compiz. But I'm wondering when does gutsy do this check if my graphic-card can handle compiz? I'm thinking this check is what is causing my problem.

Is there a way to remove compiz from gutsy or at least to switch it totally off?

greets

---

### Post by Hairy_Palms on 2007-10-28
i dont think its a compiz issue, this happened to me for a while, try adding the gutsy-proposed sources.list line, an update from there seems to have fixed it, the problem i think was that gnome-settings-daemon took a very long time to launch.

---

### Post by Adnarim on 2007-10-28
Here's my sourcs.list:
```

cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties
deb http://archive.canonical.com/ubuntu gutsy partner

```

Seems all gutsy-repos are here or?

---

