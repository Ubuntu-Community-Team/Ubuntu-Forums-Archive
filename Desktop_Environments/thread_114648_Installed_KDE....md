---
title: "Installed KDE..."
date: 2006-01-09
forum: Desktop Environments
---

### Post by Mercurybird on 2006-01-09
I'm running Ubuntu 5.10 Breezy. I followed the instructions for installing KDE found here: [http://www.madpenguin.org/cms/?m=show&id=5668](http://www.madpenguin.org/cms/?m=show&id=5668) and everything went perfectly according to the results on the screen at each step.

But upon reboot there is no sign of KDE anywhere on the disk that I can find. Does anyone know what happened?

Thanks so much.

---

### Post by Sef on 2006-01-09
> But upon reboot there is no sign of KDE anywhere on the disk that I can find. Does anyone know what happened?

KDE should be listed under the session menu right where you enter your name and password.

>  I followed the instructions for installing KDE found here: [http://www.madpenguin.org/cms/?m=show&id=5668](http://www.madpenguin.org/cms/?m=show&id=5668) and everything went perfectly according to the results on the screen at each step.

Next time to get KDE, type this in the terminal:  

sudo apt-get install kubuntu-desktop

---

### Post by Mercurybird on 2006-01-09
It's not present in the Session Menu.

Typing sudo apt-get install kubuntu-desktop gives me this result...

Reading package lists... Done
Building dependancy tree... Done
E: Couldn't find package kubuntu-desktop

E: drive? Is that the problem?

---

### Post by gingermark on 2006-01-09
No, E: means something else (probably "error" or something). You don't get drives with letters assigned in Linux, rather you get a single tree with other drives mounted at certain points within it.

Anyways, you might want to post the contents of your sources.list file (located in /etc/apt) because kubuntu-desktop should be in the main repository.

Are you certain your internet connection was active? And are you certain you spelt "kubuntu-desktop" correctly?

---

### Post by Mercurybird on 2006-01-09
[QUOTE=gingermark]No, E: means something else (probably "error" or something). You don't get drives with letters assigned in Linux, rather you get a single tree with other drives mounted at certain points within it.

Anyways, you might want to post the contents of your sources.list file (located in /etc/apt) because kubuntu-desktop should be in the main repository.

Are you certain your internet connection was active? And are you certain you spelt "kubuntu-desktop" correctly?[/QUOTE]

I've made certain of the syntax and spelling so that's not it. Here is the contents of my sources.list file.

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# Ubuntu 5.10 KDE Repository
deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

---

### Post by gingermark on 2006-01-09
For some reason many of your repositories are commented out. You can enable each one by removing the '#' before each "deb" line. Unless they are commented out for a specific reason, I'd do that and try sudo apt-get install kubuntu-desktop again.

EDIT: Also check out the "[Source-o-matic](http://www.ubuntulinux.nl/source-o-matic)". You'll probably want to keep the line regarding your CD, but the sources.list it provides you with will give you access to many more packages (although be aware of legal issues in the states, and be careful using unofficial repositories).

---

### Post by Azriphale on 2006-01-09
once you uncomment (by removing the #) the deb lines, before you try "sudo apt-get install kubuntu-desktop", you need to "sudo apt-get update"

---

### Post by gingermark on 2006-01-09
[QUOTE=Azriphale]once you uncomment (by removing the #) the deb lines, before you try "sudo apt-get install kubuntu-desktop", you need to "sudo apt-get update"[/QUOTE]

Tis true. Sorry, forgot to mention that... :???:

---

### Post by Mercurybird on 2006-01-09
Thank you folks! Everything was very successful. Did as you directed, and the stuff that came rolling in here was like a tidal wave. :) 

The new look and feel are eye candy! :p 

Thank you so much.

---

