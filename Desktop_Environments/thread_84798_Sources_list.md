---
title: "Sources list"
date: 2005-10-31
forum: Desktop Environments
---

### Post by umdzig on 2005-10-31
I have upgraded to breezy and now when i want to install something via synaptic, like  faad it is not there. Most programs are there, im having a problem finding a few. Is it because they are in the backports? I have posted my sources list to see if any of you guys can tell me what im missing if anything. 

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
  #deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
  #deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu breezy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe
```

---

### Post by Manny C on 2005-11-01
Ok...This is how Ubuntu/Kubuntu is structured. There are the following divisions in the repositories:[LIST=1]
[*] breezy
[*]breezy-updates
[*] breezy-security
[*](breezy-backports -> not open yet.)[/LIST]In each of these three divisions, there are four main distributions:[LIST=1]
[*]Main
[*]Restricted
[*] Universe
[*] Multiverse[/LIST]Furthermore for each package there is the binary (in the lines starting with deb) and there is a package source (in the lines starting with deb-src). 

Unless you are going to hack programs, you don't really need the ones starting with deb-src - I don't. In order to be able to install non-free stuff you probably need Multiverse. 

So to have all repositories open (sans the ones with source packages) your sources.list file should look like this:
```

deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

``` 

This is the entire content of my sources.list file. If you don't live in the US, say you live in Australia, then the first two letters after http:// should be au.

---

### Post by aysiu on 2005-11-01
You could also follow these directions:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

