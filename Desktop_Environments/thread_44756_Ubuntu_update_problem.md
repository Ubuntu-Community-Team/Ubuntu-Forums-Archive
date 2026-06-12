---
title: "Ubuntu update problem"
date: 2005-06-27
forum: Desktop Environments
---

### Post by vishnukv on 2005-06-27
When I **apt-get update** I have problems with a site.
This is what I get. Please tell me a fix for this.

Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricteddeb/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricteddeb/binary-i386/Packages.gz)  404 Not Found [IP: 70.84.217.98 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/cdrom:](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/cdrom:)[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]//binary-i386/Packages.gz  404 Not Found [IP: 70.84.217.98 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/hoary/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/hoary/binary-i386/Packages.gz)  404 Not Found [IP: 70.84.217.98 80]
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages - open (2 No such file or directory)
Reading package lists... Done
W: Duplicate sources.list entry [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Thanx

---

### Post by rockmusic88 on 2005-06-27
Make sure your** /etc/apt/sources.list** looks like this:

```

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

and if some packages still dont download they could be broken packages in the repositorie.

---

