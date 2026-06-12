---
title: "synaptic package manager"
date: 2005-12-08
forum: General Help
---

### Post by summit on 2005-12-08
Hi all, being new to ubuntu I seem to be having problems with installing software that doesn't show up in the package manager. I was wondering if someone out there could simply explain to me how I would go about that..........thanks

---

### Post by Knomefan on 2005-12-08
[QUOTE=summit]Hi all, being new to ubuntu I seem to be having problems with installing software that doesn't show up in the package manager. I was wondering if someone out there could simply explain to me how I would go about that..........thanks[/QUOTE]

Hi, installing applications that are not in the repositories can be a bit tricky.
What exactly are you trying to install and did you enable the universe and multiverse repositories in synaptic to make sure that the app you are looking really isn't in the repositories?

---

### Post by aysiu on 2005-12-08
[QUOTE=summit]I was wondering if someone out there could simply explain to me how I would go about that[/QUOTE] [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by chakra_dude on 2005-12-08
Do I have to connect to the web to to apt-get update?
I pop in the cd, then do an apt-get update, but still errors pop out.

---

### Post by aysiu on 2005-12-08
[QUOTE=chakra_dude]Do I have to connect to the web to to apt-get update?[/quote] Yes.

> 
I pop in the cd, then do an apt-get update, but still errors pop out. The CD doesn't have much software on it (apart from what's already installed).

Ubuntu is a bad idea if you fit into both of these categories:
1. Likes to install a lot of software
2. Has no internet connection

---

### Post by Qrk on 2005-12-08
Yes, if you don't have an internet connection, a more "complete" linux distro might be better. SuSE and Fedora both have a ton more stuff included in their iso's than Ubuntu. (As they should, because they are both multi-cd distros.)

---

### Post by summit on 2005-12-08
[QUOTE=Knomefan]Hi, installing applications that are not in the repositories can be a bit tricky.
What exactly are you trying to install and did you enable the universe and multiverse repositories in synaptic to make sure that the app you are looking really isn't in the repositories?[/QUOTE]

Ok where do I enable the universe and multiverse repositories? Also what I am trying to install are ending in tar.gz's and diff.gz and any other one that doesn't show up in synaptic.

Quite a bit of a change from mac and windows os's.

---

### Post by RAOF on 2005-12-08
In general, the install process is very different on linux (& Ubuntu in particular) to Windows.  In Ubuntu, the package manager (synaptic) does **everything** - it downloads, unpacks, installs, and sets-up the programs for you.  Unlike Windows & Mac, the first step is **not** to download an installer program.  The first (and only) step is to open up Synaptic.

In order to add the "Universe" & "Multiverse" repositories, you can go to Synaptic -> Settings -> Repositories -> Add, and select all the boxes (main, restricted, universe, non-free (multiverse)).

---

### Post by Bachstelze on 2005-12-08
run

```
sudo gedit /etc/apt/sources.list
```

delete everything in the file and copy/paste this instead

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

```

save your file, lose gedit, open Synaptic and click on the Reload button.

---

### Post by summit on 2005-12-09
Thanks everbody.................summit

---

