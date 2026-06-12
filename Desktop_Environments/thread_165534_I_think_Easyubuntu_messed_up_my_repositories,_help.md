---
title: "I think Easyubuntu messed up my repositories, help!"
date: 2006-04-24
forum: Desktop Environments
---

### Post by Poirot on 2006-04-24
Hi, I have been playing with easyubuntu and have since had some problems with Synaptic.

I am pretty sure I did something bad, the easyubuntu (3.0-beta) process did not go well, I got loads of errors. So I tried an older version (2.4-beta4) and it seemed to work better.

Anyway, I then got the following error in Synaptic along with similar ones in update manager.

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)

I'm not very confident with getting my hands dirty but I am keen to learn if need be. 

Please help, I want to upgrade to Dapper without any hitches. :(

---

### Post by robotgeek on 2006-04-25
please paste your /etc/apt/sources.list

Also, what do you mean by easyubuntu beta did not go well

---

### Post by Poirot on 2006-04-25
OK, I've been causing trouble. Here is a run down of what I did.

I should have mentioned that the attempted installation of easyubuntu 3.0beta caused error messages about changing my repository sources list. For some reason it failed to make the changes it needed (I think). Perhaps I had Synaptic open at the time, I can't remember. 

Since it didn't work, I found a version 2.4beta4 and ran that. It seemed to work fine and I noticed it changed my repository source list. When I then came to use Synaptic I got an error. I thought I would be clever and so I removed the new repositories from my list thinking this would solve the problem. It didn't solve the problem but it now looks like it changed the error message.

At that point I posted the original message.

Since then I have rerun easyubuntu 2.4beta4 and my repository list is back to where it was.

I have an AMD64 machine running breezy.

I currently have problems when I run Synaptic or Update manager. They both produce this error.

================================
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)

================================

but Update Manager produces this one first

================================
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz:) 404 Not Found
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-amd64/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-amd64/Packages.gz:) 404 Not Found
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-amd64/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-amd64/Packages.gz:) 404 Not Found
================================

This is my sources.list

================================
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
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
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
================================

What have I done to my beautiful Ubuntu?

---

### Post by robotgeek on 2006-04-25
Weird, you don't seem to have "http://antesis.freecontrib.org" repository which is causing all the problem in your sources.list.

A "sudo apt-get update" and "sudo apt-get -f install" should fix your system

---

### Post by Poirot on 2006-04-25
this is what I got on running "sudo apt-get update"

========================================
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [27.0kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [30.9kB]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages [49.0kB]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Get:7 htts.freecontrib.org breezy/free Packages
  404 Not Found
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  404 Not Found
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4130B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [15.1kB]
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  404 Not Found
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [33.3kB]
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  404 Not Found
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [2993B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources [1025B]
Fetched 227kB in 4s (46.7kB/s)
Failed to fetch p://archive.ubuntu.com breezy-updates/main Packages [38.6kB]
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  404 Not Found
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  404 Not Found
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages [4130B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources [15.1kB]
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  404 Not Found
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages [14B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources [18.6kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources [960B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages [33.3kB]
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  404 Not Found
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources [14B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources [5007B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages [2993B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources [1025B]
Fetched 227kB in 4s (46.7kB/s)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
========================================

and then on "sudo apt-get -f install" I was presented with this response

========================================
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
========================================

These messages look very familiar, it seems Synaptic and Update Manager are getting the errors from apt-get and passing them to me.

I tried running "sudo apt-get update" again and got this response

========================================
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  404 Not Found
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  404 Not Found
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
  404 Not Found
Err [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
  404 Not Found
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Fetched 3B in 1s (2B/s)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-amd64/Packages.gz](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-amd64/Packages.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
========================================

I'm still none the wiser as to how to solve this. I don't really understand what's going on.

---

### Post by robotgeek on 2006-04-25
are you sure you posted your complete sources.list?

Maybe you might wanto to generate a new sources.list from here: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

---

### Post by Poirot on 2006-04-28
I'm afraid that is my full sources.list, I don't think replacing it with a fresh one can help. I have tried adding a gb. prefix to all the archive locations. The error messages persists.

I am really greatful for the help so far, it has given me the confidence to investigate for myself.

I have been looking into this a bit deeper and I think it may either be a problem with the location or a problem with the files I have elsewhere.

I tried to follow the error message to find some clues.

=========================================
This was the first error message (of four similar ones)
=========================================
W: Couldn't stat source package list [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
=========================================

The error message implies there's a problem with this repository:
[http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages

It goes on to reference the following location as being part of the problem.
/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages

Sure enough, though many similar files exist, this file is not in my /var/lib/apt/lists/ directory.

In /var/lib/apt/lists/ I have a whole collection of files. I'm not sure what they are but they seem to describe the repositories.

=============================================
this is an example of one of the files in  /var/lib/apt/lists/
the file is named antesis.freecontrib.org_mirrors_ubuntu_freecontrib_dists_breezy_free_source_Sources
=============================================
Format: 1.0
Package: amsncvs
Version: 20051023-1ubuntu1
Binary: amsncvs
Maintainer: Kévin <dunglas@gmail.com>
Architecture: any
Standards-Version: 3.6.1
Build-Depends: debhelper (>= 4.0.0), autotools-dev, tcl8.4-dev, tk8.4-dev, imlib1-dev
Directory: pool/free/amsncvs
Files:
 5b35990d28ab9582791288681b09a790 629 amsncvs_20051023-1ubuntu1.dsc
 40ebea2e588df84c1f9c971c8611c167 5315984 amsncvs_20051023.orig.tar.gz
 69d2640a608c3bc2dc8023c3c2691917 25374 amsncvs_20051023-1ubuntu1.diff.gz
=============================================
end of example
=============================================

So I think that either the error is  due to the fact that the named file is not in my /var/lib/apt/lists/ folder or because the actual location does not exist, I have checked this too and found the following:

the error mentions this location

antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_binary-amd64_Packages

this maps directly to this
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/binary-amd64/)

Which does exist, however there is no file or folder named 'Packages' at that location.

Perhaps this is the problem.

I have never delved this deep into the workings of this stuff, any further help on the subject would be greatly appreciated.

I'm quite excited really but I need to find (and understand) the solution otherwise it's just more confusion that I don't need.

Please help, my brain hurts.

---

### Post by Ramses de Norre on 2006-04-28
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak && sudo touch /etc/apt/sources.list && sudo apt-get update
sudo mv /etc/apt/sources.list.bak /etc/apt/sources.list && sudo apt-get update
```

---

### Post by robotgeek on 2006-04-28
```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://gb.archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

```

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
gksudo gedit /etc/apt/sources.list

```

Paste the sources.list entries in there, and 
```

sudo apt-get clean
sudo apt-get update

```

---

### Post by Poirot on 2006-04-29
Sorry, I thought I replied to this last night but it was quite late and I must have closed without posting my long and involved reply. This time I have kept it short.

A summary of what I have done is as follows.

First I ran the code suggested by Ramses de Norre. Thanks Ramses, I'm not sure whether this helped but it felt good.

Then I commented out the offending repositories (effectively converting my sources.list to the one you suggested).

I now get no errors, great! That's my main concern dealt with.

However, am I not supposed to have these repositories in my sources.list?
If not then why did easyubuntu put them there without cleaning up after itself?
If so then I still have a problem because they are commented out.

Also, I would love to know what those files in /var/lib/apt/lists/ are. Should they be there now I have adjusted my sources.list? I like to run a tidy ship here and if they are superfluous I would like to be without them.

I offer one thousand thankyou's to robotgeek and Ramses de Norre. Without your help I would have remained an ignorant fool with nasty error messages.

---

### Post by robotgeek on 2006-04-29
easyubuntu (python) versions don't touch your sources.list at all. I cannot help with bash version, sorry

---

### Post by John andrew on 2006-08-25
I am a newbie and have this problem.  After I downloaded and installed Easy 
Ubuntu componets, i keepgettin the following error, espcially when trying to install more of the Easy Ubuntu programs. I get the following error messages](*,) :rolleyes: 

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)

I do not know how to uncomment lines or commands.  I used the list file command in Terminaland got

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

How can I get rid of this bug, and install the programs I need from Easy Ubuntu?  Remember that I do not know how to write or use the linux command language.  I am very eager to learn, but everywhere I turn for answers the reply was too anvanced for my skills.
:rolleyes:

---

### Post by John andrew on 2006-08-25
I clicked on this in error

---

### Post by Poirot on 2006-09-04
The '#' character makes a line a comment.

A comment is just there for you to see it is not passed through as code.

TO uncomment a line, remove the '#'s. To remove a line, just add a '#' at the beginning.

Usually anything after the '#' character is ignored or 'commented out', anything before it is read as part of the programme.

As for your particular problem... I remain an ignorant fool. I have left my system in the state my previous posts describe.

Try the easyubuntu forum [http://www.ubuntuforums.org/forumdisplay.php?f=86](http://www.ubuntuforums.org/forumdisplay.php?f=86)

---

