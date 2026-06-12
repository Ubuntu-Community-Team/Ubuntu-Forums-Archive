---
title: "some 404s not found when trying to update"
date: 2006-06-01
forum: Desktop Environments
---

### Post by hazillow on 2006-06-01
joseph@carpenter:~$ sudo apt-get update
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Err [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
  404 Not Found
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release.gpg
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release
Ign [http://kubuntu.org](http://kubuntu.org) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Ign [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Err [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Err [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Fetched 4B in 5s (1B/s)
Failed to fetch [http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz](http://deb.opera.com/opera/dists/etch/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/breezy/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://kubuntu.org/packages/kde351/dists/breezy/main/binary-i386/Packages.gz](http://kubuntu.org/packages/kde351/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://wine.lowvoice.nl/apt/dists/breezy/main/source/Sources.gz](http://wine.lowvoice.nl/apt/dists/breezy/main/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_etch_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.



any idea why these are not found? this is my sources.list:

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main
deb-src [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) breezy main

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

## created by arnieamuleremoved



any help would be greatly appreciated

---

### Post by hazillow on 2006-06-01
oi, sorry, i posted this in the wrong forum...i meant for it to go into the kubuntu forum... still, if anyone has any ideas, it would help a lot :)

---

