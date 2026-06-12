---
title: "Cant Install GParted"
date: 2006-07-22
forum: Desktop Environments
---

### Post by pt123 on 2006-07-22
sudo apt-get install gparted
Reading package lists... Done
Building dependency tree... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate


In synaptic the gparted is just 1KB

---

### Post by taurus on 2006-07-22
The easiest thing is to use synaptic and search for it.  It will tell you what else it needs to install besides gparted...

---

### Post by pt123 on 2006-07-22
I said in synaptic its listed as just 1 kb  -

Trying to install it gives the same error:

gparted:

Package gparted has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by Billquinn1 on 2006-07-22
I just installed that myself this afternoon through synaptic. Maybe your sources.list is messed up?

---

### Post by taurus on 2006-07-22
Or the repo's site is down, like us.archive.ubuntu.com!!!

---

### Post by ardchoille on 2006-07-22
Can you post your /etc/apt/sources.list so we can see if there are any errors in it?

---

### Post by pt123 on 2006-07-22
> **taurus said:**
> Or the repo's site is down, like us.archive.ubuntu.com!!!

Yes I am getting the same problem for this.

---

### Post by pt123 on 2006-07-23
Well I changed the us. to au for Australia. The sourcelist updated fine. But I am still getting the same problems when trying to install GParted.

This is my source lisr ```


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


##deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted
##deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## 'universe'repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
##deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
##deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## Backports
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) dapper-backports main universe multiverse restricted
##deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) dapper-extras main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
# deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main


```]

---

### Post by aysiu on 2006-07-23
You seem to have a mix of Breezy and Dapper repositories. Comment out the first two lines. "Comment out" means put a # sign in front of the line.

---

### Post by ardchoille on 2006-07-23
gparted: partition editor for GNOME is in repository main. I see that you have main comented out, so you aren't seeing the packages in the dapper main repo.

Uncomment this line:

##deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted

then do sudo apt-get update, then apt-cache search gparted.

---

### Post by pt123 on 2006-07-27
Ok it worked got my source list screwed when trying to upgrade from 5.10 to 6.06.

Thanks

---

### Post by weird_c00kie on 2006-10-15
> **ardchoille said:**
> gparted: partition editor for GNOME is in repository main. I see that you have main comented out, so you aren't seeing the packages in the dapper main repo.

Uncomment this line:

##deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted

then do sudo apt-get update, then apt-cache search gparted.

i was missing that repository. i added it and it's downloading now. thanks :D

---

