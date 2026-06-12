---
title: "CVS problems :("
date: 2006-07-19
forum: Desktop Environments
---

### Post by darkchron on 2006-07-19
Hello everyone.. 

I am new to ubuntu and i am trying to figure out how to get CVS going..

i have followed many "HOW TO's" so please don't direct me to them.
```
Install CVS files:
sudo apt-get install cvs

Install the CVS server:
sudo apt-get install cvsd
```
DOESN'T WORK!

All i get is this
```
darkchron@darkchron:~$ sudo apt-get install cvs
Reading package lists... Done
Building dependency tree... Done
Package cvs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cvs has no installation candidate
```

How do i install Cvs please? :(

---

### Post by Perfect Storm on 2006-07-19
How's your sourcelist looks like?

---

### Post by darkchron on 2006-07-19
Hi

Source list looks like this.

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


# deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
# deb-src http://no.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://no.archive.ubuntu.com/ubuntu dapper-updates main restricted
# deb-src http://no.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://no.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://no.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://wine.budgetdedicated.com/apt dapper main
deb http://www.beerorkid.com/automatix/apt dapper main
```

---

### Post by RAOF on 2006-07-19
You have to uncomment some of those repositories!  As it is, you have **none** of the official Ubuntu repositories enabled :)

You should at least have this:
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
```
in there.

In case it's not obvious, the '#' at the beginning of the line indicates a comment - they're ignored.

---

### Post by Perfect Storm on 2006-07-19
You need to uncomment some of your sources, so it looks like:

> 
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
#deb [http://www.beerorkid.com/automatix/apt](http://www.beerorkid.com/automatix/apt) dapper main


To do so you need to **sudo gedit /etc/apt/sources.list**
After change the sourcelist do **sudo apt-get update**
Then try again :)

---

### Post by darkchron on 2006-07-19
Thank you, got it installed ;)

---

