---
title: "Breezy: libgtk2.0-dev unmet dependencies"
date: 2005-10-18
forum: Desktop Environments
---

### Post by jfelectron on 2005-10-18
I just did a fresh install of Ubuntu 5.10 Breezy. When I try to apt-get libgtk2.0-dev it appears that the package has unmet dependencies. I have universe and multiverse enabled. See below for the full transcript. 


jonathan@electron:~$ sudo apt-get install libgtk2.0-dev Reading package lists... Done Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.7.5-0ubuntu2) but 2.8.6-0ubuntu2 is to be installed
                 Depends: libglib2.0-dev (>= 2.7.1) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.9.1) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
                 Depends: libcairo1-dev (>= 0.6) but it is not going to be installed
                 Depends: libx11-dev but it is not going to be installed or
                          xlibs-dev but it is not going to be installed
                 Depends: libxext-dev but it is not going to be installed or
                          xlibs-dev but it is not going to be installed
E: Broken packages

---

### Post by rasbach on 2005-10-18
I had this same problem, I changed my sources list a bit and it seemed to correct the problem for me.  What I did was change the US part of the URLs to CA.  See below:

# deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted

---

### Post by jfelectron on 2005-10-18
Great!!! That worked. I was beating my head against the wall. Thanks.:)

---

