---
title: "Broken dependencies"
date: 2005-07-12
forum: Desktop Environments
---

### Post by Umbra on 2005-07-12
Im getting the same error for most packages i have tried to install. I updated my sources list like the one in the ubuntuguide.org, i also did the apt-get check, -f, --fix-broken and still the same.

> The following packages have unmet dependencies:
  amsn: Depends: imlib1 but it is not going to be installed
        Depends: sox but it is not going to be installed
        Depends: libpng10-0 but it is not going to be installed
        Depends: docker but it is not going to be installed
        Depends: tcltls but it is not going to be installed
  kdepim: Depends: karm (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
          Depends: korganizer (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
          Depends: kpilot (>= 4:3.4.0-0ubuntu10) but it is not going to be installed 

That's and example with AMSN, but i got the same for many other apps.

---

### Post by rosslaird on 2005-07-12
Why don't you post your sources.list.

Also, make sure to try this (I'm sure you have, but the syntax is important):

sudo apt-get -f install

Also, you might try doing:

sudo apt-get update
sudo apt-get dist-upgrade

Then try again.

---

### Post by Xian on 2005-07-12
Since I am not getting those same error messages on my Hoary box, let's just work with the idea that this might be a repo source issue. There really is no reason why apt should behave differently on your system that mine if we are both running x86 archs.

Listed below is my apt-session and my sources.list.
Back up your /etc/apt/source.list and try mine in their place.
Run an 'sudo apt-get update' command after the change.

```
# apt-get install amsn
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  docker imlib-base imlib1 libpng10-0 tcltls
Suggested packages:
  mozilla galeon konqueror imagemagick imlib-progs
The following NEW packages will be installed:
  amsn docker imlib-base imlib1 libpng10-0 tcltls
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 2376kB of archives.
After unpacking 8356kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb http://mirrors.xmission.com/ubuntu hoary-updates main restricted universe multiverse
#deb-src http://mirrors.xmission.com/ubuntu hoary-updates main restricted universe multiverse

##Security Mirrors
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backup Security Mirrors
#deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb http://kubuntu.org/hoary-kde341 hoary-updates main

##Backports
#deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
#deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by Umbra on 2005-07-12
That sources lists look very different to mine. :oops:

Gonna try that one and see what happening.
Thanks.

---

### Post by Xian on 2005-07-12
[QUOTE=Umbra]That sources lists look very different to mine. :oops:[/QUOTE]
Heh. It's been xian-tweaked®

---

### Post by Umbra on 2005-07-13
I did it with that source list. Im still getting the same f****ng sh*t:

> The following packages have unmet dependencies:
 amsn: Depends: imlib1 but it is not going to be installed
 Depends: sox but it is not going to be installed
 Depends: libpng10-0 but it is not going to be installed
 Depends: docker but it is not going to be installed
 Depends: tcltls but it is not going to be installed
 kdepim: Depends: karm (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
 Depends: korganizer (>= 4:3.4.0-0ubuntu10) but it is not going to be installed
 Depends: kpilot (>= 4:3.4.0-0ubuntu10) but it is not going to be installed 

The amsn package it's an example, 'cause this ocurrs to every single package i have tried to install.

Some details maybe i need to mention. I have tried the amd64 distribution with similar problem, so i thought it was more difficult to get 64bit packages so i install the 32bit distribution, and got the same thing. When i installed ubuntu/kubuntu amd64/i386 in the installation process i receive I/O Erros in that part of the installation process when it unpacks and configures many packages after the base system was installed. I repeat, this happened to me with both cds, i386 and the amd64. 
Could be these I/O erros the packages missing mentioned in the apt problem? and if so... why doesnt it fix them?

Note, i have updated the sources lists with the same than you (no errors at this point), i also have made an 'apt-get dist-upgrade' this last one sent me the same error above.. grrr

---

### Post by Xian on 2005-07-13
[QUOTE=Umbra]Could be these I/O erros the packages missing mentioned in the apt problem? and if so... why doesnt it fix them?[/QUOTE]
Yes, that is possible. There is definitely something wrong here since two machines using the same arch and installation media (I am running x86) should not have such dramatically different results from the identical source list.

Perhaps the way to go here would be to see why these individual packages are being held back. If you direct apt to install them specifically it will give you more detailed error outputs. Let's try a few, starting with docker. Issue the command below and post the output.
```
$ sudo apt-get -f install
$ sudo apt-get install docker 
```

---

### Post by Umbra on 2005-07-13
Oh Thx a lot!!

After million tries, seems to magically fixed, it fixed the problem and got it working fine.

Ouuuuh, this apt command is wonderful, install fast, easy.

---

