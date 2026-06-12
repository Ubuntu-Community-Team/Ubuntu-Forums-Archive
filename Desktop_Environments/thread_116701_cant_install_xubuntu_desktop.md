---
title: "cant install xubuntu desktop"
date: 2006-01-13
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-13
hmmm. I try to install xubuntu-desktop trough synaptic but it tellsm me I 
need sylpheed but that its not going to be installed.
I cant seem to install it at all.

any ideas?

---

### Post by gs10 on 2006-01-13
try using command line 

sudo apt-get -d xubuntu-desktop

[QUOTE=syklitengutt]hmmm. I try to install xubuntu-desktop trough synaptic but it tellsm me I 
need sylpheed but that its not going to be installed.
I cant seem to install it at all.

any ideas?[/QUOTE]

---

### Post by syklitengutt on 2006-01-13
chris@chris:~$ sudo apt-get -d xubuntu-desktop
E: Invalid operation xubuntu-desktop

---

### Post by aysiu on 2006-01-13
[QUOTE=syklitengutt]hmmm. I try to install xubuntu-desktop trough synaptic but it tellsm me I 
need sylpheed but that its not going to be installed.
I cant seem to install it at all.

any ideas?[/QUOTE] What repositories do you have enabled? Can you post your /etc/apt/sources.list file?

---

### Post by syklitengutt on 2006-01-13
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

## created by arniebackports

deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental all
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental all

deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-backports main multiverse restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-backports main multiverse restricted universe

deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) stable main

---

### Post by Ampersand on 2006-01-13
You should be able to get some more details of what's causing the problem if you select Sylpheed for installation in Synaptic.

---

### Post by syklitengutt on 2006-01-13
When trying to install sylphid:
> sylpheed:
  Depends: libcairo2 (>=1.0.2-2) but 1.0.2-0ubuntu1 is to be installed
  Depends: libglib2.0-0 (>=2.8.5) but 2.8.3-0ubuntu1 is to be installed
  Depends: libgpg-error0 (>=1.1) but 1.0-1 is to be installed
  Depends: libpango1.0-0 (>=1.10.2) but 1.10.1-0ubuntu1 is to be installed
  Depends: libreadline5 (>=5.1) but 5.0-10 is to be installed
 Depends: libssl0.9.8 (>=0.9.8a-1) but it is not installable
  Depends: libxrender1 (>=1:0.9.0.2) but 1:0.9.0-1 is to be installed
 Depends: sylpheed-i18n but it is not going to be installed
  

And when trying to install sylpheed-i18n this is what I get:
> sylpheed-i18n:
 Depends: sylpheed but it is not going to be installed

Lol---- dont get it----

---

### Post by aysiu on 2006-01-13
[QUOTE=syklitengutt]```
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse


deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free
deb [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi
deb-src [http://seveas.ubuntulinux.nl/](http://seveas.ubuntulinux.nl/) breezy-seveas breezy-backports breezy-custom breezy-extras freenx madwifi

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

## created by arniebackports

deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental all
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental all

deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-backports main multiverse restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) breezy-backports main multiverse restricted universe

deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) stable main
```[/QUOTE] Your repositories are kind of a mess. Try using the appropriate one from the first link of my signature. I suspect some of your repositories may be causing conflicts with others.

---

### Post by syklitengutt on 2006-01-13
tnx... that did it...
installed now...
Reestart soon...

---

### Post by aysiu on 2006-01-13
[QUOTE=syklitengutt]tnx... that did it...
installed now...
Reestart soon...[/QUOTE] Tip for the future--if you use non-Ubuntu repositories, add them, apt-get install the program you need, then delete them.

---

### Post by syklitengutt on 2006-01-13
I think I will stick to that from now....

---

