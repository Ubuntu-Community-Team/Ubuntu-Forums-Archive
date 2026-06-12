---
title: "Java help"
date: 2005-10-14
forum: Desktop Environments
---

### Post by nix4me on 2005-10-14
The java that is installed is not working with my java aplets.

How do I install Sun Java?  the j2re package is gone from synaptic.

nix

---

### Post by ChrisTheGeek on 2005-10-14
Hi, you can install Sun Java by following the instructions here:

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

---

### Post by ichiban on 2005-10-14
Read this: :D 

[http://ubuntuforums.org/showthread.php?t=70428&highlight=java+fakeroot](http://ubuntuforums.org/showthread.php?t=70428&highlight=java+fakeroot)

---

### Post by nix4me on 2005-10-14
doesn't work.

nix4me@underworld:~$ sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package

---

### Post by ichiban on 2005-10-14
You need to add the proper repositories first.

Here is a howto: 
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Just uncomment all repositories.

---

### Post by nix4me on 2005-10-14
those repositories are for hoary.  Im using brezzy final.

---

### Post by ichiban on 2005-10-14
The howto needs to be updated. 
Just uncomment the brezzy repositories.

---

### Post by nix4me on 2005-10-14
The backports repositories are not working at all.  That seems to be my problem.

---

### Post by ichiban on 2005-10-14
Hmmm 

Here is what mine looks like:

also maybe this is a better way to do it: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://dk.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```

So you don't need the backports.

---

### Post by nix4me on 2005-10-14
That did it!

I had to do this too:
sudo update-alternatives --config java

and select j2re as the default.


Thanks alot!
nix

---

### Post by KrazyPenguin on 2005-10-14
Another way to install java.

Add Applications

Apply

Installs 1.4 and everything seems to work , including pogo games.

;-)

---

