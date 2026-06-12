---
title: "Codec and Installation errors"
date: 2007-05-18
forum: Desktop Environments
---

### Post by MrMadison on 2007-05-18
Every time I try to install a codec or any program for that matter, i always get
```
Error: Cannot find Installation Candidate
```and packages not found.

And when I try to use automatix, I keep getting Fatal Errors and packages not found.



Am I doing something wrong? (obviously...lol)
Can anyone help? 

Thanks in advance

-Madison

---

### Post by taurus on 2007-05-18
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by MrMadison on 2007-05-18
All this popped up when I put it into terminal...Hope this is right.


```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

```

---

### Post by dannyboy79 on 2007-05-18
probably just need to do a 

sudo aptitude update

to solve this one. also, if you used automatix, than you should've already chose all the codec's and what not and you should just be able to watch avi's and dvd's and such.

---

### Post by MrMadison on 2007-05-18
But when I use automatix to try and install something, it doesn't work, i keep getting Fatal Errors...




I opened the sources.list and the only links I found were for Automatix fiesty and the Fiesty-commercial main

---

### Post by taurus on 2007-05-18
If you install Automatix and are having problems with your machine, I suggest you seek help at [http://www.getautomatix.com](http://www.getautomatix.com).

And just so you know, you don't need Automatix to install codecs for Feisty.  It's already available.

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

