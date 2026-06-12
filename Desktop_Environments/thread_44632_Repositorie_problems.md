---
title: "Repositorie problems"
date: 2005-06-27
forum: Desktop Environments
---

### Post by Synthetic on 2005-06-27
First my repositorie list:

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports-mirrormax.net/](http://ubuntu-backports-mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports-mirrormax.net/](http://ubuntu-backports-mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

## Kubuntu
deb [http://kubuntu.org/hoary-kde341](http://kubuntu.org/hoary-kde341) hoary-updates main
deb [http://download.kde.org/stable/3.4.1/kubuntu](http://download.kde.org/stable/3.4.1/kubuntu) hoary-updates main
deb [http://kubuntu.org/hoary-koffice14](http://kubuntu.org/hoary-koffice14) hoary-updates main
deb [http://download.kde.org/pub/kde/stable/koffice-1.4/kubuntu](http://download.kde.org/pub/kde/stable/koffice-1.4/kubuntu) hoary-updates main

I thought it looked ok but I guess there must be a problem somewhere cause when I use Kynaptic to scan for updates at the end I get:

Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)

And it does that for just about all the repositories, when i try apt-get update here is what I get:

Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging Release
Ign [http://kubuntu.org](http://kubuntu.org) hoary-updates Release.gpg
Ign [http://kubuntu.org](http://kubuntu.org) hoary-updates Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://kubuntu.org](http://kubuntu.org) hoary-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release
Ign [http://kubuntu.org](http://kubuntu.org) hoary-updates Release
Ign [http://download.kde.org](http://download.kde.org) hoary-updates Release.gpg
Ign [http://download.kde.org](http://download.kde.org) hoary-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports-staging/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Ign [http://kubuntu.org](http://kubuntu.org) hoary-updates/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras-staging/restricted Packages
Ign [http://download.kde.org](http://download.kde.org) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Ign [http://kubuntu.org](http://kubuntu.org) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://download.kde.org](http://download.kde.org) hoary-updates Release
Hit [http://kubuntu.org](http://kubuntu.org) hoary-updates/main Packages
Ign [http://download.kde.org](http://download.kde.org) hoary-updates/main Packages
Hit [http://kubuntu.org](http://kubuntu.org) hoary-updates/main Packages
Ign [http://download.kde.org](http://download.kde.org) hoary-updates/main Packages
Err [http://download.kde.org](http://download.kde.org) hoary-updates/main Packages
  302 Found
Err [http://download.kde.org](http://download.kde.org) hoary-updates/main Packages
  302 Found
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports Release.gpg
  Could not resolve 'ubuntu-backports-mirrormax.net'
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras Release.gpg
  Could not resolve 'ubuntu-backports-mirrormax.net'
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports Release
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/restricted Packages
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/main Packages
  Could not resolve 'ubuntu-backports-mirrormax.net'
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/universe Packages
  Could not resolve 'ubuntu-backports-mirrormax.net'
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/multiverse Packages
  Could not resolve 'ubuntu-backports-mirrormax.net'
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/restricted Packages
  Could not resolve 'ubuntu-backports-mirrormax.net'
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/main Packages
  Could not resolve 'ubuntu-backports-mirrormax.net'
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/universe Packages
  Could not resolve 'ubuntu-backports-mirrormax.net'
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/multiverse Packages
  Could not resolve 'ubuntu-backports-mirrormax.net'
Err [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/restricted Packages
  Could not resolve 'ubuntu-backports-mirrormax.net'
Fetched 3B in 16s (0B/s)
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-backports/Release.gpg](http://ubuntu-backports-mirrormax.net/dists/hoary-backports/Release.gpg)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-extras/Release.gpg](http://ubuntu-backports-mirrormax.net/dists/hoary-extras/Release.gpg)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://download.kde.org/stable/3.4.1/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://download.kde.org/stable/3.4.1/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://download.kde.org/pub/kde/stable/koffice-1.4/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://download.kde.org/pub/kde/stable/koffice-1.4/kubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)  302 Found
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports-mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-backports-mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://ubuntu-backports-mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://ubuntu-backports-mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz](http://ubuntu-backports-mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz](http://ubuntu-backports-mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://ubuntu-backports-mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  Could not resolve 'ubuntu-backports-mirrormax.net'
Failed to fetch [http://ubuntu-backports-mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://ubuntu-backports-mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz)  Could not resolve 'ubuntu-backports-mirrormax.net'
Reading package lists... Done
W: Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports-mirrormax.net](http://ubuntu-backports-mirrormax.net) hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports-mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://download.kde.org](http://download.kde.org) hoary-updates/main Packages (/var/lib/apt/lists/download.kde.org_stable_3.4.1_kubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://download.kde.org](http://download.kde.org) hoary-updates/main Packages (/var/lib/apt/lists/download.kde.org_pub_kde_stable_koffice-1.4_kubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

It looks like for the most part the sites are to blame but I'm not sure so any help in clearing this up would be great. :)

---

### Post by fdoving on 2005-06-27
change:
deb [http://ubuntu-backports-mirrormax.net/](http://ubuntu-backports-mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports-mirrormax.net/](http://ubuntu-backports-mirrormax.net/) hoary-extras main universe multiverse restricted

to:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


And you can safely remove the download.kde.org mirrors. kubuntu.org have everything you need.

---

### Post by Synthetic on 2005-06-27
Thanks! That help out a lot, but I still can't seem to get the kubuntu.org repositories to work. This is what I have them as:

deb [http://kubuntu.org/](http://kubuntu.org/)hoary-kde341 hoary-updates main
deb [http://kubuntu.org/](http://kubuntu.org/)hoary-koffice14 hoary-updates main

Any ideas?

---

### Post by Fintan on 2005-06-27
[QUOTE=fdoving]change:
deb [http://ubuntu-backports-mirrormax.net/](http://ubuntu-backports-mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports-mirrormax.net/](http://ubuntu-backports-mirrormax.net/) hoary-extras main universe multiverse restricted

to:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


And you can safely remove the download.kde.org mirrors. kubuntu.org have everything you need.[/QUOTE]

Pray tell, where is the difference. the paths are exactly the same. 
May be i am blind but they dont want to work.At least not today
Cheers Fintan

---

### Post by Synthetic on 2005-06-28
[QUOTE=Fintan]Pray tell, where is the difference. the paths are exactly the same. 
May be i am blind but they dont want to work.At least not today
Cheers Fintan[/QUOTE]Look in between backports and mirrormax....

---

### Post by Fintan on 2005-06-28
[QUOTE=Synthetic]Look in between backports and mirrormax....[/QUOTE]
 Yup im blind i quess i'll go to sleep now, long night:))))) and thanks
cheers
Fintan

---

### Post by fdoving on 2005-06-28
[QUOTE=Synthetic]Thanks! That help out a lot, but I still can't seem to get the kubuntu.org repositories to work. This is what I have them as:

deb [http://kubuntu.org/](http://kubuntu.org/)hoary-kde341 hoary-updates main
deb [http://kubuntu.org/](http://kubuntu.org/)hoary-koffice14 hoary-updates main

Any ideas?[/QUOTE]
 do you get a error message?

---

### Post by Synthetic on 2005-06-28
[QUOTE=fdoving]do you get a error message?[/QUOTE]Well I did but now I'm not any more so I guess all is good. Thanks for the help.

---

