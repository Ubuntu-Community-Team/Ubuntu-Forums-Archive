---
title: "sources list/breezy backports not working"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Brando569 on 2005-10-17
hey it seems my breezy backports arent working, it keeps on saying directory not found or something liek that heres the errors:

```

Ign http://us.archive.ubuntu.com breezy-backports/main Packages
Ign http://us.archive.ubuntu.com breezy-backports/restricted Packages
Ign http://us.archive.ubuntu.com breezy-backports/universe Packages
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://us.archive.ubuntu.com breezy-backports/main Sources
Ign http://us.archive.ubuntu.com breezy-backports/restricted Sources
Ign http://us.archive.ubuntu.com breezy-backports/universe Sources
Ign http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Err http://us.archive.ubuntu.com breezy-backports/main Packages
  404 Not Found [IP: 82.211.81.182 80]
Err http://us.archive.ubuntu.com breezy-backports/restricted Packages
  404 Not Found [IP: 82.211.81.182 80]
Err http://us.archive.ubuntu.com breezy-backports/universe Packages
  404 Not Found [IP: 82.211.81.182 80]
Err http://us.archive.ubuntu.com breezy-backports/multiverse Packages
  404 Not Found [IP: 82.211.81.182 80]
Err http://us.archive.ubuntu.com breezy-backports/main Sources
  404 Not Found [IP: 82.211.81.182 80]
Err http://us.archive.ubuntu.com breezy-backports/restricted Sources
  404 Not Found [IP: 82.211.81.182 80]
Err http://us.archive.ubuntu.com breezy-backports/universe Sources
  404 Not Found [IP: 82.211.81.182 80]
Err http://us.archive.ubuntu.com breezy-backports/multiverse Sources
  404 Not Found [IP: 82.211.81.182 80]
Fetched 191B in 1s (139B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 82.211.81.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz  404 Not Found [IP: 82.211.81.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz  404 Not Found [IP: 82.211.81.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz  404 Not Found [IP: 82.211.81.182 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz  404 Not Found [IP: 82.211.81.182 80]
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

i didnt add anything to my sources.lst, i have the default one with the repos in ther uncommented.

---

### Post by Pablo_Escobar on 2005-10-17
Breezy backports have not been started yet. They're in the sources list, but for a reason commented out.
Leave them commented out for a time being, and when the Breezy backports will launch uncomment them.

---

### Post by Brando569 on 2005-10-17
oh ok thanks

---

### Post by Terracotta on 2005-10-17
Hye, I've got quite the same problem, but with my complete sources.list file, I can't install anything, I can't update anything... Here's my sources.list:

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Can anyone help, cause I need some other programs.

---

### Post by Pablo_Escobar on 2005-10-17
Maybe try to use :
> 
##deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 

Changed bit - "us" for "be" (I'm from Poland but I use us) and added multiverse

---

