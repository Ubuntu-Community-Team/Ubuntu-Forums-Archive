---
title: "Has anyone installed 0.9.21~winehq~ubuntu~6.06-1 yet?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by bswilson on 2006-09-15
This morning, Dapper notified me of an update to wine -- the newest version that I'd read about on *Slashdot*.  When attempting to do this install, I was warned that the package's validity could not be confirmed.

[LIST=1]
[*]Has anyone else experienced this?  I've not seen this before.
[*]Has anyone installed this new version, and have their been any problems?
[/LIST]

My sources.list is included.

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.getautomatix.com/apt dapper main
deb http://wine.budgetdedicated.com/apt dapper main
```

---

### Post by jackkerouac on 2006-09-15
I installed it and everything was fine.

---

