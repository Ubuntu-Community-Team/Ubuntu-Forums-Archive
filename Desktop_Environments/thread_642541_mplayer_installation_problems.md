---
title: "mplayer installation problems"
date: 2007-12-16
forum: Desktop Environments
---

### Post by stansaraczewski on 2007-12-16
I seem to be going in circles in trying to install devede - it is complaining that it cannot find mplayer, but in doing a sudo apt-get install mplayer I get this :

The following packages have unmet dependencies:
  mplayer: Depends: libfaac0 (>= 1.24clean) but it is not going to be installed
           Depends: libmp4v2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp) but it is not going to be installed
E: Broken packages

I've tried installing both of the Depends but they are already found.

How can I get this cleaned up ?

Thank You -

---

### Post by fosix on 2007-12-18
this might be helpful
[http://ubuntuforums.org/showthread.php?t=634174](http://ubuntuforums.org/showthread.php?t=634174)

---

### Post by stansaraczewski on 2007-12-18
I still have the same problem with the dependencies. It's probably not a mplayer-install problem at this point, but syncronization of some sort...

---

### Post by FuturePilot on 2007-12-19
It might be an issue with your sources.list
Could you post it?
```
cat /etc/apt/sources.list
```

---

### Post by stansaraczewski on 2007-12-19
Thank you for the assistance -

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted univer se multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe m ultiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe mu ltiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
#AUTOMATIX REPOS END
deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib

---

