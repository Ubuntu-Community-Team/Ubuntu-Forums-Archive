---
title: "Repository Conflicts"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Luggy on 2006-08-24
I seem to be getting a lot of repository confilcts as of late.
Example:
```
libglib2.0-dev:
  Depends: libglib2.0-0 (=2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed
```

I think I might have broken my repositories, any chance someone could lend me their /etc/apt/sources.list or some over advice on how to fix this problem?

---

### Post by carontis on 2006-08-24
Try use synaptic to fix all

---

### Post by Ramses de Norre on 2006-08-24
This is mine:
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
#deb http://xgl.compiz.info/ dapper main
#deb-src http://xgl.compiz.info/ dapper main
#deb http://ubuntu.compiz.net/ dapper main

```
Be carefull with the third party repo (I've had for example trouble with the XGL/Compiz ones, their commented out now).

When you've set this as sources.list do ```
sudo aptitude update && sudo aptitude upgrade
``` and report all errors if you get some.

---

### Post by boes on 2006-08-29
I couldn't install mplayer thru Synaptic Package Manager(SPM) and gave me error. also I used command Fix broken Package in SPM but nothing change.

by using the code "sudo aptitude update && sudo aptitude upgrade"
you gave then I repeat to do following steps:

"How to install Multimedia Player (MPlayer) with Plug-in for Mozilla Firefox

    * Read #General Notes
    * Read #How to add extra repositories
    * Read #How to install Multimedia Codecs
    * Read #How to install DVD playback capability 

sudo apt-get install mplayer-386
sudo apt-get install mplayer-fonts
sudo apt-get install mozilla-mplayer
sudo cp /etc/mplayer/mplayer.conf /etc/mplayer/mplayer.conf_backup
sudo gedit /etc/mplayer/mplayer.conf"

the result is 100% work!

now I could hear the radio which its station using mplayer with plug-in.

thanks.

---

