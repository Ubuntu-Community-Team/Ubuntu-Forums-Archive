---
title: "could not dowload all repository indexes"
date: 2009-03-02
forum: General Help
---

### Post by alvarojabril on 2009-03-02
Hi, I'm completely new to linux. I now have it hooked up to the internet but I'm having trouble updating, when I try to reload the list of available programs I get a dialog box that says "could not download all repository indexes" and then this

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]

I've found other people with this problem but the solutions seem to be different for everyone/difficult for me to follow. I put in gedit /etc/apt/sources.list and got this:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse

Anyone have ideas? Thanks very much.

---

### Post by Titan8990 on 2009-03-02
You say that you are new to linux, but you are using a version that is two years old. Its end of life was in October 2008. Any reason you chose this older version?

---

### Post by alvarojabril on 2009-03-02
I didn't mean to install an old version, I thought it was up to date. I will try to update now. Thanks.

ed: unfortunately when i try to update via the update manager the same "could not download all repository indexes" message comes up.

---

### Post by punx45 on 2009-03-02
if you just installed, you should just get the latest install disc and start over, but if you really want to do a network upgrade:

see here,
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)
 especially the section "Fully Updating 7.04" where it tells you to add new repo sites 

```

deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

i suggest starting from scratch, since the network upgrade will only get you to 7.10 which will also be seeing end of life soon.   8.04 Hardy is the current LTS, so i would reccommend this as the oldest version to use.

---

### Post by geoffree on 2009-04-27
I am having same problem, though I'm running Hardy Heron.  A triangle icon with an exclamation mark appeared on tool bar with following message.  What can I do to fix this problem.

Thank You



**Could not download all repository indexes**

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.92.46 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz)  404 Not Found

---

