---
title: "apt issues"
date: 2005-05-31
forum: Desktop Environments
---

### Post by somuchfortheafter on 2005-05-31
Im having a bit of trouble with my backport repositories in my sources.list file
the file reads as folows *only the backports part for space*
```

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

```
error occurs after i run an sudo apt-get update
the error is
```

Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/universe PackagesIgn http://ubuntu-backports.mirrormax.net hoary-extras-staging/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
  404 Not Found
Hit http://security.ubuntu.com hoary-security/main Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports-staging/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports-staging/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports-staging/multiverse Packages
  404 Not Found
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit ftp://ftp.nerim.net testing Release
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports-staging/restricted Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-extras-staging/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-extras-staging/universe Packages  404 Not Found
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Err http://ubuntu-backports.mirrormax.net hoary-extras-staging/multiverse Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-extras-staging/restricted Packages
  404 Not Found
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit ftp://ftp.nerim.net testing/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Fetched 4B in 2s (1B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports-staging/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras-staging/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras-staging/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras-staging/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras-staging/restricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports-staging/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports-staging_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports-staging/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports-staging_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports-staging/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports-staging_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports-staging/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports-staging_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras-staging/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras-staging_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras-staging/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras-staging_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras-staging/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras-staging_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras-staging/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras-staging_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
so does anyone have any ideas of what i can do, im doing a fresh install of ubuntu and the new version of the guide requires the use of backports, and if backports dont work then i am sort of sol lol.

---

### Post by SGC on 2005-05-31
Pick another mirror for backport from here:
[http://backports.ubuntuforums.org/url.php](http://backports.ubuntuforums.org/url.php)

---

### Post by paddygman on 2005-10-26
right sorry to bother all but i am having some issues with my apt-get update
below is a copy of the output of apt-get update


***************************************************************

Ign cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary Release.gpg
Ign cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary Release
Ign cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary/main Packages
Ign cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary/restricted Packages
Err cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release [30.9kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [4045B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [14B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [1613B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [2254B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages [91.6kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [641B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release [30.9kB]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources [46.9kB]
Get:16 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging Release.gpg
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release [30.9kB]
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging Release.gpg
Get:18 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras Release.gpg
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages [585kB]
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras Release.gpg
Get:20 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging Release
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging Release
Get:21 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras Release
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras Release
Get:22 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/main Packages
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/main Packages
Get:23 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/universe Packages
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/universe Packages
Get:24 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/multiverse Packages
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/multiverse Packages
Get:25 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/restricted Packages
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/restricted Packages
Get:26 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/main Packages
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages [5061B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources [232kB]
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/main Packages
Get:29 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/universe Packages
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/universe Packages
Get:30 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/multiverse Packages
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources [1454B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages [2304kB]
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/multiverse Packages
Get:33 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/restricted Packages
Ign [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/restricted Packages
Get:34 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/main Packages [33B]
Get:35 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/universe Packages [33B]
Get:36 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/multiverse Packages [33B]
Get:37 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-backports-staging/restricted Packages [33B]
Get:38 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/main Packages [33B]
Get:39 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/universe Packages [33B]
Get:40 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/multiverse Packages [33B]
Get:41 [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) breezy-extras/restricted Packages [33B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources [915kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages [15.4kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources [3872B]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Fetched 4322kB in 14s (302kB/s)
Failed to fetch cdrom:[Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407)]/dists/hoary/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407)]/dists/hoary/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _Breezy Badger_ - Release i386 (20050407) hoary/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20050407)_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

***********************************************************

Any ideas as to the problem let me kno actually scratch that i mainly want the solution as i have enough problems! Cheers, 

PS
Managed to get my backports working from this thread cheers

---

### Post by paddygman on 2005-10-26
edited my sources.list to comment out the cdrom reference so that i no longer get any errors but what is the purpose of this line??

"##deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050407)]/ breezy main restricted"

cheers
paddy

---

