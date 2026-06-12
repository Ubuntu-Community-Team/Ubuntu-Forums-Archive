---
title: "Collection of 5.10 tricks"
date: 2005-11-11
forum: Desktop Environments
---

### Post by the_bob on 2005-11-11
Starting a little collection of tips and tricks untill the 5.10 unoffical guide is done.
I don't have a lot of time tonight but I'll be adding to it as I tweak my new install.
If anyone wants to add feel free. Thanks

**Extra repositories**
open terminal and type
*sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup*
*sudo gedit /etc/apt/sources.list*
then replace whats there with
[I]## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse [/I]

**install libdvdcss**
Just type _sudo apt-get install libdvdcss2_ into the terminal after installing extra repos.

---

### Post by bionnaki on 2005-11-11
[http://doc.gwos.org/index.php/BreezyCust](http://doc.gwos.org/index.php/BreezyCust)

---

### Post by openmind on 2005-11-11
The 5.10 unofficial guide lives in your help file. Go check it out.

---

