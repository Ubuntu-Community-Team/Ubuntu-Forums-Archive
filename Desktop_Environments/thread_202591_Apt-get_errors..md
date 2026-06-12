---
title: "Apt-get errors."
date: 2006-06-23
forum: Desktop Environments
---

### Post by divali on 2006-06-23
I wonder whether someone could help me resolve these problems that are shown whenever I use Apt-get?

divali@ubuntu:~$ sudo apt-get update
Password:
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release.gpg
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:4 [http://kubuntu.org](http://kubuntu.org) breezy Release.gpg [189B]
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy Release
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy Release
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Err [http://theli.free.fr](http://theli.free.fr) ./ Packages
  404 Not Found
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Packages
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://kubuntu.org](http://kubuntu.org) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages [39.7kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [19.2kB]
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages
  404 Not Found
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages [12.9kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages [708B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.8kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [37.1kB]
Err [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Sources
  404 Not Found
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [71.5kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages [14.0kB]
84% [23 Packages 5842/14.0kB 41%] [19 Packages 21615/71.5kB 30%] [Waiting for h
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
  Sub-process bzip2 returned an error code (2)
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages [26.1kB]
81% [21 Packages bzip2 0] [24 Packages 1399/26.1kB 5%] [19 Packages 21615/71.5k
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
  Sub-process bzip2 returned an error code (2)
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages [1353B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages [14B]
Get:27 [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages [741B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4458B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [3830B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Fetched 376kB in 4s (81.1kB/s)
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Sorry if it's too much readout. I'm not sure which bits are most relevant.
Thank you in advance.
divali.

---

