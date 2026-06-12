---
title: "[SOLVED] Beryl Installation Phailure!!!!1"
date: 2008-01-01
forum: Desktop Effects &amp; Customization
---

### Post by r41nz0r on 2008-01-01
I'm stuck trying to install beryl, I started with djRobbieF's XGL&Beryl Tutorial [http://ubuntuforums.org/showthread.php?t=268036&highlight=xgl+beryl+djrobbief]("http://ubuntuforums.org/showthread.php?t=268036&highlight=xgl+beryl+djrobbief")

Anyhow I Seem to be having great difficulty even typing the first command into terminal. ```
sudo apt-get update
```

After entering that I get the following error reply from terminal:
```
E: Type 'sudo' is not known on line 65 in source list /etc/apt/sources.list
```

So I browse to /etc/apt/sources.list and look at whats being displayed. .



```
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main #Added by software-properties

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Wine, Ubuntu Gutsy (7.10):
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main



deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe #Added by software-properties

deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx

sudo apt-get update
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
sudo gedit /etc/gdm/gdm.conf-custom

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

Can someone tell me where I went wrong? It'd be greatly appreciated,

Also here are some images. .

---

### Post by overdrank on 2008-01-01
> **r41nz0r said:**
> I'm stuck trying to install beryl, I started with djRobbieF's XGL&Beryl Tutorial [http://ubuntuforums.org/showthread.php?t=268036&highlight=xgl+beryl+djrobbief]("http://ubuntuforums.org/showthread.php?t=268036&highlight=xgl+beryl+djrobbief")

Anyhow I Seem to be having great difficulty even typing the first command into terminal. ```
sudo apt-get update
```

After entering that I get the following error reply from terminal:
```
E: Type 'sudo' is not known on line 65 in source list /etc/apt/sources.list
```

So I browse to /etc/apt/sources.list and look at whats being displayed. .



```
# 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted main #Added by software-properties

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Wine, Ubuntu Gutsy (7.10):
deb http://wine.budgetdedicated.com/apt gutsy main
deb-src http://wine.budgetdedicated.com/apt gutsy main



deb http://ca.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe #Added by software-properties

[COLOR="Red"]deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx

sudo apt-get update
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald emerald-themes
sudo gedit /etc/gdm/gdm.conf-custom

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true[/COLOR]

```

Can someone tell me where I went wrong? It'd be greatly appreciated,

Also here are some images. .
Hi and yes that "how to" is out dated it is for dapper and your using gutsy. Beryl support has ended for dapper. Edit your apt sources list and remove what I have highlighted in red. Then save and update and please give us some specs on your system and we can help.

---

### Post by r41nz0r on 2008-01-01
If It Were Only That Easy. I've tried making a new file and replacing, tried opening it w/other applications. tried and failed. Can anyone here suggest some alternatives please. Thanks :(

---

### Post by FuturePilot on 2008-01-01
You need to open the file with root privileges
```
gksudo gedit /etc/apt/sources.list
``` 
Remove the lines that overdrank highlighted then run
```
sudo apt-get update
```

---

### Post by r41nz0r on 2008-01-01
Thanks, Future Pilot and Overdrank! Problem has been resolved \\:D/

---

### Post by LazKapitaL on 2008-01-07
Please someone tell me a brief guide for installing Bery . I use Ubuntu 7.10 Gutsy Graphic Car Nvidia Geforce 5200. i implement processes in [http://ubuntusoftware.info/beryl.html](http://ubuntusoftware.info/beryl.html). But i couldnt run svn co svn://svn.beryl-project.org/beryl/trunk/ beryl becouse this web adress doesnot exsists. So what should i do? Please help me about find out safe guide.

Regards

---

### Post by FuturePilot on 2008-01-07
Beryl is no longer being developed. Ubuntu Gutsy has Compiz Fusion by default. Just make sure to install the drivers for your Nvidia card. System>Administration>Restricted Driver Manager.

---

