---
title: "Can't Upgrade to Breezy"
date: 2005-10-19
forum: Desktop Environments
---

### Post by domstyledesign on 2005-10-19
i'm trying to upgrade to breezy.  i've changed my sources.list, but when i run apt-get update, this is what i get:
```
$ sudo apt-get update
Ign http://archive.ubuntu.com Breezy Release.gpg
Ign http://security.ubuntu.com Breezy-security Release.gpg
Ign http://archive.ubuntu.com Breezy Release
Ign http://security.ubuntu.com Breezy-security Release
Ign http://archive.ubuntu.com Breezy/multiverse Packages
Ign http://security.ubuntu.com Breezy-security/main Packages
Ign http://archive.ubuntu.com Breezy/multiverse Sources
Ign http://security.ubuntu.com Breezy-security/restricted Packages
Ign http://security.ubuntu.com Breezy-security/main Sources
Ign http://security.ubuntu.com Breezy-security/restricted Sources
Err http://archive.ubuntu.com Breezy/multiverse Packages
  404 Not Found [IP: 82.211.81.151 80]
Ign http://security.ubuntu.com Breezy-security/universe Packages
Ign http://security.ubuntu.com Breezy-security/universe Sources
Err http://security.ubuntu.com Breezy-security/main Packages
  404 Not Found
Err http://archive.ubuntu.com Breezy/multiverse Sources
  404 Not Found [IP: 82.211.81.151 80]
Err http://security.ubuntu.com Breezy-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com Breezy-security/main Sources
  404 Not Found
Err http://security.ubuntu.com Breezy-security/restricted Sources
  404 Not Found
Err http://security.ubuntu.com Breezy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com Breezy-security/universe Sources
  404 Not Found
Ign http://us.archive.ubuntu.com Breezy Release.gpg
Ign http://us.archive.ubuntu.com Breezy-updates Release.gpg
Ign http://us.archive.ubuntu.com Breezy Release
Ign http://us.archive.ubuntu.com Breezy-updates Release
Ign http://us.archive.ubuntu.com Breezy/main Packages
Ign http://us.archive.ubuntu.com Breezy/restricted Packages
Ign http://us.archive.ubuntu.com Breezy/main Sources
Ign http://us.archive.ubuntu.com Breezy/restricted Sources
Ign http://us.archive.ubuntu.com Breezy/universe Packages
Ign http://us.archive.ubuntu.com Breezy/universe Sources
Ign http://us.archive.ubuntu.com Breezy-updates/main Packages
Ign http://us.archive.ubuntu.com Breezy-updates/restricted Packages
Ign http://us.archive.ubuntu.com Breezy-updates/main Sources
Ign http://us.archive.ubuntu.com Breezy-updates/restricted Sources
Err http://us.archive.ubuntu.com Breezy/main Packages
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy/restricted Packages
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy/main Sources
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy/restricted Sources
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy/universe Packages
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy/universe Sources
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy-updates/main Packages
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy-updates/restricted Packages
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy-updates/main Sources
  404 Not Found [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com Breezy-updates/restricted Sources
  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Breezy/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.151 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Breezy-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/Breezy/multiverse/source/Sources.gz  404 Not Found [IP: 82.211.81.151 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Breezy-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Breezy-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Breezy-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Breezy-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/Breezy-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy/main/binary-i386/Packages.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy/restricted/binary-i386/Packages.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy/main/source/Sources.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy/restricted/source/Sources.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy/universe/binary-i386/Packages.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy/universe/source/Sources.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy-updates/main/binary-i386/Packages.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy-updates/restricted/binary-i386/Packages.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy-updates/main/source/Sources.gz  404 Not Found [IP: 130.239.18.165 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/Breezy-updates/restricted/source/Sources.gz  404 Not Found [IP: 130.239.18.165 80]
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com Breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com Breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com Breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com Breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com Breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_Breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com Breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com Breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com Breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_Breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com Breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

here's my sources.list
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu Breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu Breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu Breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu Breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu Breezy universe
deb-src http://us.archive.ubuntu.com/ubuntu Breezy universe

deb http://security.ubuntu.com/ubuntu Breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu Breezy-security main restricted

deb http://security.ubuntu.com/ubuntu Breezy-security universe
deb-src http://security.ubuntu.com/ubuntu Breezy-security universe

deb http://archive.ubuntu.com/ubuntu Breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu Breezy multiverse

## Backports
#deb http://ubuntu-backports.mirrormax.net/ Breezy-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ Breezy-extras main universe multiverse restricted

```

is this just from server overload?  or did i do something wrong?

---

### Post by migueljacq on 2005-10-19
i've heard that removing the 'us' from the urls helps. view this thread:

[http://ubuntuforums.org/showthread.php?t=78010](http://ubuntuforums.org/showthread.php?t=78010)

in particular, dbott67's sources.list is probably what you need

---

