---
title: "I can't install mplayer"
date: 2006-01-28
forum: Desktop Environments
---

### Post by El Kabong on 2006-01-28
Hey everyone, I am trying to install mplayer, because Totem blows. However, everytime I go to the Add Applications menu, it's greyed out. When I highlight it, it says the following:

This program is not currently installable. It should be available in the "multiverse" section of the repository. Enable that section in the Repositories dialog in the Settings menu to install it.

I have no idea how to update the repositories things, can someone please explain how to do it and why I'm doing it? Thanks ahead of time for any help!

---

### Post by e-blade on 2006-01-28
I suggest you go to [http://ubuntuguide.org](http://ubuntuguide.org), scroll down a bit to the section called: How to add ekstra repositories. Follow the example (involves editing the sources.list in /etc/apt/ ). back-up your original sources.list, copy what the example gives you, and run: sudo apt-get update. Ubuntu will now add extra repositories for you, which means your search using synaptic will broaden.

Try it and i'll bet your mplayer installation will work like a charm.

---

### Post by Gcool on 2006-01-28
You indeed need to edit your repositories. 

* Open console
* sudo nano /etc/apt/sources.list
* These are the main ones (which should also include mplayer):

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

---

### Post by kaamos on 2006-01-28
Generate your sources.list file from [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic). Ubuntuguide is for ubuntu 5.04 (so they are the wrong repos!) and the above post contains the closed mirrormax backports.

---

### Post by bikeman on 2006-01-28
Or, you could just do it the easy way, with [Automatix]("http://www.ubuntuforums.org/showthread.php?t=80295&highlight=automatix").  This script is amazing and has worked perfectly for everything that I have used it for.  Just make sure that your username has sudoer permissions.

---

