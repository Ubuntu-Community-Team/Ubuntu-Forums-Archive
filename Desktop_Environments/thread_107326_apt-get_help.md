---
title: "apt-get help"
date: 2005-12-22
forum: Desktop Environments
---

### Post by 65 mustang on 2005-12-22
Hi,
  This is my first post.  I need to learn how to use apt-get better to fix my problem.

I had added some sources into my /etc/apt/sources.list file that were aparently no longer valid and apt-get update was timing out when trying to reach the sources.  I removed those sources from my sources.list file and did another apt-get update.  I assumed since i removed them from the sources.list file that it would no longer try to reach them but it does.

How do i get rid of these old sources?  I am posting the results from a "apt-get update" and the contents of my sources.list file.

Thanks for the help everyone.

```

tsmith@tsmith:~$ sudo -s -H
Password:
root@tsmith:/home/tsmith# apt-get update
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release
Ign http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Ign http://wine.sourceforge.net binary/ Release.gpg
Hit http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Hit http://wine.sourceforge.net binary/ Release
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:5 http://security.ubuntu.com breezy-security Release [19.6kB]
Ign http://wine.sourceforge.net binary/ Packages
Get:6 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Hit http://wine.sourceforge.net binary/ Packages
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Get:8 http://security.ubuntu.com breezy-security/main Packages [25.7kB]
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://security.ubuntu.com breezy-security/restricted Packages
Get:9 http://security.ubuntu.com breezy-security/main Sources [8416B]
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Get:10 http://archive.ubuntu.com breezy-backports/universe Packages [24.4kB]
Get:11 http://security.ubuntu.com breezy-security/universe Packages [19.6kB]
Get:12 http://security.ubuntu.com breezy-security/universe Sources [2962B]
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://archive.ubuntu.com breezy-backports/main Sources
Hit http://archive.ubuntu.com breezy-backports/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/universe Sources
Hit http://archive.ubuntu.com breezy-backports/multiverse Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Get:13 http://archive.ubuntu.com breezy-backports/universe Packages [24.4kB]
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Ign http://public.planetmirror.com breezy Release.gpg
Ign http://public.planetmirror.com breezy Release
Ign http://public.planetmirror.com breezy/free Packages
Ign http://public.planetmirror.com breezy/non-free Packages
Err http://public.planetmirror.com breezy/free Packages
  404 Not Found [IP: 203.16.234.20 80]
Err http://public.planetmirror.com breezy/non-free Packages
  404 Not Found [IP: 203.16.234.20 80]
Fetched 165kB in 5s (28.3kB/s)
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz  404 Not Found [IP: 203.16.234.20 80]
Failed to fetch http://public.planetmirror.com/pub/plf/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz  404 Not Found [IP: 203.16.234.20 80]
Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-amd64_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@tsmith:/home/tsmith#

```


```
root@tsmith:/home/tsmith# cat /etc/apt/sources.list
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
## created by arniebackports

deb http://wine.sourceforge.net/apt/ binary/
root@tsmith:/home/tsmith#

```

---

### Post by 65 mustang on 2005-12-22
I fixed it.  I had duplicate sources.  Now i am trying to install wine which isnt working.  :mad: 

```
root@tsmith:/home/tsmith# cat /etc/apt/sources.list
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
## created by arniebackports

deb http://wine.sourceforge.net/apt/ binary/
root@tsmith:/home/tsmith#

```

```
root@tsmith:/home/tsmith# apt-get update
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net breezy-extras Release
Ign http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/restricted Packages
Ign http://wine.sourceforge.net binary/ Release.gpg
Hit http://ubuntu-backports.mirrormax.net breezy-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net breezy-extras/multiverse Packages
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://archive.ubuntu.com breezy Release
Hit http://wine.sourceforge.net binary/ Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy-updates Release
Ign http://wine.sourceforge.net binary/ Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://wine.sourceforge.net binary/ Packages
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://archive.ubuntu.com breezy-backports/main Sources
Hit http://archive.ubuntu.com breezy-backports/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/universe Sources
Hit http://archive.ubuntu.com breezy-backports/multiverse Sources
Fetched 4B in 1s (4B/s)
Reading package lists... Done
root@tsmith:/home/tsmith#

```

```
root@tsmith:/home/tsmith# apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
root@tsmith:/home/tsmith#

```

---

### Post by darth_vector on 2005-12-22
you are best off installing wine from the deb package provided at [www.winehq.com](www.winehq.com) since it is a newer version than the one in the repositories.

---

### Post by hoodwink on 2005-12-22
[QUOTE=darth_vector]you are best off installing wine from the deb package provided at [www.winehq.com](www.winehq.com) since it is a newer version than the one in the repositories.[/QUOTE]
Does that create any problems later on when a Ubuntu package is released that should replace the package?

---

