---
title: "List of Repositories"
date: 2006-09-10
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-10
I'm sure there is a thread abut this, but I wasn't able to find it. Sorry if I'm double posting

I just switched to Xubuntu after my Ubuntu crashed and I'm having troubles trying to find aMule, and unrar (among others) using Synaptic (or apt-get through the command line), so I guess I'm missing some important repositories.

Now, where do I find a list of such? Just the basic stuff, but I can't find it..

Gabriel

---

### Post by aysiu on 2006-09-10
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Ramses de Norre on 2006-09-10
Note that there are a couple of third party repos and xgl repos and stuff in my sources.list, modify it and use it at your own risk ;)
```
ramses@icarus:~$ cat /etc/apt/sources.list
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

## kubuntu.org packages for the latest KDE version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/kde-latest dapper main

## kubuntu.org packages for the latest Koffice version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/koffice-latest dapper main

## kubuntu.org packages for the latest amaroK version (GPG key: DD4D5088)
##deb http://kubuntu.org/packages/amarok-14 dapper main

## Cipherfunk multimedia (GPG key: 33BAC1B3)
#deb ftp://cipher"funk.org/pub/packages/ubuntu/ dapper main
#deb-src ftp://cipher"funk.org/pub/packages/ubuntu dapper main

## Seveas repo
##deb http://seveas.ubuntulinux.nl dapper-seveas all
##deb-src http://seveas.ubuntulinux.nl dapper-seveas all

## Canonical commercial repo
deb http://archive.canonical.com/ubuntu dapper-commercial main

##XGL/Compiz repos
#deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
deb http://ubuntu.compiz.net/ dapper main

```

---

### Post by GabrielWolff on 2006-09-10
Thanks, lads.

Works fine

G

---

