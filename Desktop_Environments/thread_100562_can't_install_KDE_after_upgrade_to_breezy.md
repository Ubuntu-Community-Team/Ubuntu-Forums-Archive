---
title: "can't install KDE after upgrade to breezy"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Rory on 2005-12-07
I upgraded to Breezy without issue but a tonne of packages were held back.  I then added the new kde 3.5 deb to my source list and imported the key.  

When I upgraded, it uninstalled kde and now I boot in to Gnome.  I can't reinstall kde, whether the 3.5 repo is active or not.  

I've apt-get update, upgrade and dist-upgrade.  

In terminal, these are my results:
```

rory@ubuntu:~$ sudo apt-get install kubuntu-desktop Reading package lists... Done Building dependency tree... Done
Package kubuntu-desktop is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kubuntu-desktop has no installation candidate

```


sudo apt-get install kde ... gives me:
```

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not installable
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not installable
       Depends: kdeadmin but it is not going to be installed
       Depends: kdeartwork but it is not installable
       Depends: kdegraphics but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdenetwork but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdeutils but it is not going to be installed
       Depends: kdewebdev but it is not installable
       Depends: kdesdk but it is not going to be installed
       Depends: kdeaccessibility but it is not going to be installed
       Depends: kdevelop3 but it is not going to be installed

```

I even tried:
```

rory@ubuntu:~$ sudo apt-get install kde kde-core kde-amusements kdeaddons kdeadmin kdeartwork kdegraphics kdemultimedia kdenetwork kdepim kdeutils kdewebdev kdesdk kdeaccessibility kdevelop3
Reading package lists... Done
Building dependency tree... Done
Package kde-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kde-core has no installation candidate

```


This is my sources list.  Is anything missing?  
```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## Official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

## PLF - http://wiki.ubuntu-fr.org/doc/plf
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
  

#deb ftp://ftp.nerim.net/debian-marillat/ sarge main
#deb ftp://ftp.nerim.net/debian-marillat/ etch main

#deb ftp://ftp.nerim.net/debian-marillat/ sid main
#deb ftp://ftp.nerim.net/debian-marillat/ sid main
#deb http://kubuntu.org/packages/kde35 breezy main
#deb http://kubuntu.org/packages/amarok-1.3.7 breezy main

```


I've tried the above with the kde35 active and commented out (which is what it now is).  Neither worked.  

Anyone have any ideas???

Thanks,
Rory

---

### Post by aysiu on 2005-12-07
Can you try following the instructions in the first link of my sig?
It won't get you KDE 3.5, but it will get you kubuntu-desktop.
It also backs up your current sources.list.

---

