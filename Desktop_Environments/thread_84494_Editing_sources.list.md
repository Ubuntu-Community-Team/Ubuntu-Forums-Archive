---
title: "Editing sources.list"
date: 2005-10-31
forum: Desktop Environments
---

### Post by linbetwin on 2005-10-31
> aurelian@home02282:~$ sudo apt-get update
Get:1 [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy Release.gpg [189B]
Get:2 [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy-updates Release.gpg [189B]
Get:3 [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security Release.gpg [189B]
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security Release
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy-updates Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/main Packages
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy/main Packages
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy/restricted Packages
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/restricted Sources
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy/restricted Sources
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy/universe Packages
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy/universe Sources
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy/universe Packages
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy-updates/main Packages
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy-updates/restricted Packages
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy-updates/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com") breezy-security/universe Sources
Hit [http://ro.archive.ubuntu.com]("http://ro.archive.ubuntu.com") breezy-updates/restricted Sources
Fetched 3B in 0s (6B/s)
Reading package lists... Done
aurelian@home02282:~$
 
Is there something wrong with my sources list?> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://ro.archive.ubuntu.com/ubuntu]("http://ro.archive.ubuntu.com/ubuntu") breezy main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu]("http://ro.archive.ubuntu.com/ubuntu") breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ro.archive.ubuntu.com/ubuntu]("http://ro.archive.ubuntu.com/ubuntu") breezy-updates main restricted
deb-src [http://ro.archive.ubuntu.com/ubuntu]("http://ro.archive.ubuntu.com/ubuntu") breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ro.archive.ubuntu.com/ubuntu]("http://ro.archive.ubuntu.com/ubuntu") breezy universe
deb-src [http://ro.archive.ubuntu.com/ubuntu]("http://ro.archive.ubuntu.com/ubuntu") breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ro.archive.ubuntu.com/ubuntu]("http://ro.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu]("http://ro.archive.ubuntu.com/ubuntu") breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") breezy-security universe

deb [http://ro.archive.ubuntu.com/ubuntu/]("http://ro.archive.ubuntu.com/ubuntu/") breezy universe


What does "Hit" mean? Do I really have access to all these repos or does "hit" actually mean "miss"? Please, help me edit my sources.list to get access to universe and multiverse.

---

### Post by Xian on 2005-10-31
[QUOTE=linbetwin]Please, help me edit my sources.list to get access to universe and multiverse.[/QUOTE]
Read the wiki entry: [Adding Universe and Multiverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse).

---

### Post by linbetwin on 2005-10-31
Is it true you can't use the backports repo with Breezy yet?

---

### Post by linbetwin on 2005-10-31
I  followed the instructions in the wiki to add backports repo and this is what I get in Synaptic:
> [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.182 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.182 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.182 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.182 80]
and:
> W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)


---

### Post by Pablo_Escobar on 2005-10-31
Backports are still offline. Comment them out.

---

### Post by linbetwin on 2005-10-31
Thanks! I only uncommented them because the wiki said they were open.

---

