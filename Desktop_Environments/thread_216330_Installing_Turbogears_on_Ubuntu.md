---
title: "Installing Turbogears on Ubuntu"
date: 2006-07-15
forum: Desktop Environments
---

### Post by blowfish on 2006-07-15
Im trying to install the python framework TurboGears([www.turbogears.org](www.turbogears.org)) on my dapper box, but have run into a problem with the following error,

*error: /usr/include/python2.4/pyconfig.h: No such file or directory*

Im told that i need to install the package python2.4-dev. However,

*sudo apt-get install python2.4-dev* returns the following,

[I]Reading package lists... Done
Building dependency tree... Done
Package python2.4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python2.4
E: Package python2.4-dev has no installation candidate[/I]

What has happend to the package python2.4-dev and is there a replacement or a workaround that i can use.



Thanks for your help.

---

### Post by Ramses de Norre on 2006-07-15
```
However the following packages replace it:
python2.4
```
Seems like that's a replacement, do you have that installed yet?

---

### Post by blowfish on 2006-07-15
sudo apt-get install python2.4
Reading package lists... Done
Building dependency tree... Done
python2.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


yes.

---

### Post by Ramses de Norre on 2006-07-15
Have you got all repos enabled? Because I checked here and I've got python2.4-dev in my repos.

EDIT: [link]("http://packages.ubuntulinux.org/dapper/python/python2.4-dev")

---

### Post by blowfish on 2006-07-15
# Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

## Cipherfunk multimedia packages (GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

## Breezy PLF
## only uncomment it if you need it
## since the Dapper PLF repository isn't available yet
## deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
## deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free

## Dapper PLF repository. 
## NOT YET AVAILABLE
## deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
## deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

## Bleeding edge (official) wine repository for Dapper
## only uncomment it if you need it
## deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
## deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

## skype 
## only uncomment it if you need it
## deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by Ramses de Norre on 2006-07-15
You don't have the main and restricted dapper repos, so add
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted
```

---

### Post by blowfish on 2006-07-15
ok, that worked. thanks for your help.

---

