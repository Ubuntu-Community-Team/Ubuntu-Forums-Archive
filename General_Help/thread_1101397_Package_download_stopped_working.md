---
title: "Package download stopped working"
date: 2009-03-20
forum: General Help
---

### Post by simonbrain on 2009-03-20
I am trying to install gettext package, I tried with synaptic package manager but that will not work. I have now tried apt-get install gettext and all i get is waiting for headers. I do not have apt proxy installed. When I first installed Ubuntu a few days ago i used the synatic package manager successfully to install a number of packages. What could have changed?

Thanks in advance for any help.

Simon

---

### Post by taurus on 2009-03-20
Post the whole output when you ran that command from a terminal.

---

### Post by simonbrain on 2009-03-20
root@simon-linux:/home/simon/Documents/gettext-0.17# apt-get install gettext
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  cvs gettext-doc
The following NEW packages will be installed
  gettext
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1984kB of archives.
After this operation, 7852kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  gettext
Install these packages without verification [y/N]? y
0% [Waiting for headers]^C
root@simon-linux:/home/simon/Documents/gettext-0.17#

---

### Post by taurus on 2009-03-20
What is the output of this command?

```
sudo apt-get update
```

---

### Post by simonbrain on 2009-03-20
root@simon-linux:/home/simon/Documents/gettext-0.17# apt-get update
0% [Waiting for headers] [Waiting for headers]^C

when I ran it there was a response that went away after a few seconds saying something about SIP. This is interesting as I am trying to install SIPE protocol for Pidgin IM. I have setup a an account which uses SIP. Could this be something to do with the problem as the package manager did work before I started setting this up?

---

### Post by taurus on 2009-03-20
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

p.s.  Any reason you log in as root?  Should stick with user account, simon, and if you need root privilege, use sudo or gksudo.

---

### Post by simonbrain on 2009-03-20
root@simon-linux:/home/simon# cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
root@simon-linux:/home/simon# 

I am just learning Linux, thanks for the tip on login I will read up a bit more.

---

### Post by simonbrain on 2009-03-23
I found the problem with this problem. I had set a proxy setting within Pidgin which was stopping this working.

Thanks for help.

Simon

---

