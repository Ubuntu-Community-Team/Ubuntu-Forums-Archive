---
title: "Updating of some libraries ???"
date: 2006-07-19
forum: Desktop Environments
---

### Post by SreckoMicic on 2006-07-19
When tryed to install new version of Yafray it prompt me the dependecies problem: 
```

dpkg: dependency problems prevent configuration of yafray:
 yafray depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 yafray depends on libgcc1 (>= 1:4.1.0); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 yafray depends on libstdc++6 (>= 4.1.0); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing yafray (--install):
 dependency problems - leaving unconfigured

```

When can I expect that this libraries will be updated?
Thanks for any answer.

---

### Post by Ramses de Norre on 2006-07-19
You must be missing some repos because I have the right version of all those libraries here, if you post your sources.list I'll take a look at it.

---

### Post by SreckoMicic on 2006-07-19
Here it is,

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://cs.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cs.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://cs.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://cs.archive.ubuntu.com/ubuntu dapper universe main restricted multiverse
deb-src http://cs.archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://cs.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://cs.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu dapper-backports main universe multiverse restricted
##JASHAKA
deb http://repo.jahshaka.org/ubuntu/dapper/ binary-i386/

```

Tnx for fast reply.:D

---

### Post by Ramses de Norre on 2006-07-19
I don't really see the missing repo, at least one of your libs (libc6) should be in main.. maybe the cs servers aren't up to date..
This are my sources and I think they are very complete:
```
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## Penguin Liberation Front (PLF)
##deb http://theli.free.fr/packages/dapper/ ./

## Dapper PLF repository
deb http://packages.freecontrib.org/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## Skype
##deb http://seveas.theplayboymansion.net/seveas breezy-seveas extras
##deb http://download.skype.com/linux/repos/debian/ stable non-free

## wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main

## opera web browser
##deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
##deb http://people.ubuntu.com/~doko/OOo2 ./

## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/kde-latest dapper main

## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/koffice-latest dapper main

## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/amarok-14 dapper main

## Cipherfunk multimedia (GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

## Seveas repo
##deb http://seveas.ubuntulinux.nl dapper-seveas all
##deb-src http://seveas.ubuntulinux.nl dapper-seveas all

## Canonical commercial repo
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

---

### Post by SreckoMicic on 2006-07-19
Please just can you tell me, do you have 2.3.6-6 version of libc installed?
I used your list but still there is earlier version.

---

### Post by Ramses de Norre on 2006-07-19
Ok, I might have misread your first post, are you trying to install a non-repo version of yafray? In that case you'll probably have to wait untill edgy for the new version of libc6.
You can try to find the new version in debian repos but it could break a lot..
Sorry for the confusion.

---

### Post by SreckoMicic on 2006-07-19
Yes I'm trying to install new version of Yafray 0.9. It was released couple days ago. Hmmm then waiting again .... ](*,)

---

