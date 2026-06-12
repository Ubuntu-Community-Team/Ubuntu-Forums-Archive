---
title: "installing mono/monodevelop"
date: 2005-10-15
forum: Desktop Environments
---

### Post by tr333 on 2005-10-15
what packages are required to install the mono framework and monodevelop?

---

### Post by nehalem on 2005-10-17
Just go into synaptic package management and lookup monodevelop.  It will install the things you need.  Hopefully you have more luck than me, monodevelop is broke and buggy so far.

---

### Post by tr333 on 2005-10-17
thanks.
seems to work for me.
```
sudo apt-get install mono gtk-sharp gtk-sharp2 monodevelop mono-classlib-2.0
```

---

### Post by zdavidlnx on 2005-10-28
[QUOTE=tr333]thanks.
seems to work for me.
```
sudo apt-get install mono gtk-sharp gtk-sharp2 monodevelop mono-classlib-2.0
```[/QUOTE]

Which repositories are you using? I try to make a apt-get install... but gives me an error: Can't find package.

I am using Ubuntu 5.10 breeze.

Thanks

---

### Post by tr333 on 2005-10-28
i have the standard repos plus the universe repositories available in synaptic.

---

### Post by zdavidlnx on 2005-10-29
[QUOTE=tr333]i have the standard repos plus the universe repositories available in synaptic.[/QUOTE]


May post hereyour /etc/apt/sources.list file here, i think i also have standard repos but cant find thode packages.

Thanks.

---

### Post by tr333 on 2005-10-30
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release powerpc (20051012)]/ breezy main restricted


deb-src http://au.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://au.archive.ubuntu.com/ubuntu breezy universe main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```


you might also want to look at this article on [The Fridge](http://fridge.ubuntu.com/node/51).

EDIT:  it is much easier to add/remove repositories using synaptic.

---

