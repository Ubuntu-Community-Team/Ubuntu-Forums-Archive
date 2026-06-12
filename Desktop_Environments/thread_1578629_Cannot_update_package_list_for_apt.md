---
title: "Cannot update package list for apt"
date: 2010-09-20
forum: Desktop Environments
---

### Post by cgdz on 2010-09-20
Hello all,

I'm new to GNU/Linux and recently installed Edubuntu 10.10 beta on a workplace computer. I'm currently a technology intern at a public school and want to install Edubuntu on some older computers here. I am working behind a network proxy provided by the department of education.

I tried to install flashplugin-nonfree and noticed I didn't have a full package list. After running sudo apt-get update I get the error "unable to connect to us.archive.ubuntu.com:http:"

I'm thinking this might have to do with the network proxy, but for some reason I'm able to browse [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) just fine in Firefox.

How do I update the package list?

Thank you

Edit: I installed Ubuntu 10.04 on another machine at work and it has the same issue, i.e. I can't update the package list.

Edit 2: I am using a .pac file for the proxy.

---

### Post by LinuxPhreak on 2010-09-22
> **cgdz said:**
> Hello all,

I'm new to GNU/Linux and recently installed Edubuntu 10.10 beta on a workplace computer. I'm currently a technology intern at a public school and want to install Edubuntu on some older computers here. I am working behind a network proxy provided by the department of education.

I tried to install flashplugin-nonfree and noticed I didn't have a full package list. After running sudo apt-get update I get the error "unable to connect to us.archive.ubuntu.com:http:"

I'm thinking this might have to do with the network proxy, but for some reason I'm able to browse [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) just fine in Firefox.

How do I update the package list?

Thank you

Edit: I installed Ubuntu 10.04 on another machine at work and it has the same issue, i.e. I can't update the package list.

I'm not to familair with proxies in this manner. But I will just throw this suggestion out which may or may not help you. As root navigate to /etc/apt/sources.list and uncomment all of the repos. 

```
gksu gedit /etc/apt/sources.list
```

Below is an example of my sources list. 

```

deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe

deb http://download.virtualbox.org/virtualbox/debian lucid non-free

```

Save changes then type sudo apt-get update in the terminal.

---

### Post by DemonBob on 2010-09-22
Try this. 

[http://www.unixmen.com/linux-tutorials/939-configure-apt-get-to-work-behind-a-proxy-in-ubuntu-lucid-](http://www.unixmen.com/linux-tutorials/939-configure-apt-get-to-work-behind-a-proxy-in-ubuntu-lucid-)

---

### Post by cgdz on 2010-09-24
Yes! Thank you Demonbob! This seems to work so far.

I did what that link said and also did what the first comment said:

> 
this is the way it worked for me:
 add to /etc/apt/apt.conf (create new if not existing) 
 ```
Acquire::http::Proxy    "http://proxy.example.com:8080/";
```
Then it worked!

Thank you so much! :P

Edit: I tried adding the quoted code to apt.conf only on another system and it worked too! So it seems I don't need to edit /etc/bash.bashrc

---

