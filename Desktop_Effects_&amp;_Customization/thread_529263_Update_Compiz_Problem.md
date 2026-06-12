---
title: "Update Compiz Problem"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by adolfofoliaco on 2007-08-19
Hello..

I first install compiz fallowing this Instruction:

```
sudo apt-get remove compiz-core desktop-effects
```
```
sudo gedit /etc/apt/sources.list
```
I add this.
```
# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```
 then I did That 
```
gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -
```

```
sudo apt-get update
sudo apt-get upgrade
```

an them 

```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf
```

and them did this update.

[http://ubuntuforums.org/showthread.php?t=481314&highlight=install+compiz](http://ubuntuforums.org/showthread.php?t=481314&highlight=install+compiz)

and now I don't have all the effect that soupose be and I have the Update Manger Software say that is a update but it does not install.

plase help I dont want to format the Pc againg.

thanks

---

### Post by hyperair on 2007-08-19
Please post your /etc/apt/sources.list file here.

---

### Post by adolfofoliaco on 2007-08-19
thanks for the rply.

```
deb http://ubuntu.cafuego.net edgy-cafuego bcm43xx

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse

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
```

---

### Post by hyperair on 2007-08-19
And compiz-core is having problems right? Try this: 
```

sudo apt-get clean
sudo apt-get update
sudo apt-get install compiz-core

```

---

### Post by adolfofoliaco on 2007-08-19
Thank but nothing.  this is the problem I missing some plug ins and effects of compiz, and the update manager tell me that I have a update when I say apply it apply but the update still there, here are the images:

[IMG]http://ubuntuforums.org/g/images/349698/1_Screenshot.png[/IMG]

and then I Install the Update and this is the screen 

[IMG]http://ubuntuforums.org/g/images/349698/1_Screenshot-1.png[/IMG]

after that I said apply and the screen is this one

[IMG]http://ubuntuforums.org/g/images/349698/1_Screenshot-2.png[/IMG] 

and the goes back to this screen 

[IMG]http://ubuntuforums.org/g/images/349698/1_Screenshot.png[/IMG]

and the update still there.???   :confused::confused::confused:

Adolph Foliaco

---

### Post by MeathooK427 on 2007-08-19
It's a problem with the repos. Just take the items you added into your sources.list file out, and it'll fix your problem. You'll have to add them back in whenever you update in the future though. Good luck.

---

