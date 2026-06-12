---
title: "Koha 3.0: Zebra installation and downgrading Perl"
date: 2009-02-11
forum: General Help
---

### Post by Jac3510 on 2009-02-11
Thread originally posted in Installation forum, moved here:

-----------------------------------------------------------
Two questions with my Koha 3.0 installation:

1. I'm running 8.10 (well, I installed 10, but I think it upgraded to 11?) and things appear to have gone wonderfully smooth. However, there is a complaint, which I found unanswered in [this thread](http://ubuntuforums.org/showthread.php?t=1013854&highlight=koha), that Perl 5.10 is buggy and should be replaced with 5.8. How should I go about that?

2. I have to install Zebra to get this version of Koha to work. I followed the following instructions taken from Zebra's [Ubuntu installation page](http://www.indexdata.dk/zebra/doc/installation-debian.tkl):

> These Zebra packages are specifically compiled for GNU/Debian Linux systems. Installation on other GNU/Debian systems is possible by re-compilation the Debian way: you need to add only the deb-src sources lines to the /etc/apt/sources.list configuration file, that is either the Sarge sources

```
deb-src http://ftp.indexdata.dk/debian sarge main
```
or the Etch sources 

```
deb-src http://ftp.indexdata.dk/debian etch main
```
After refreshing the package cache with the command 

```
apt-get update
apt-get build-dep idzebra-2.0
```
as root, the Zebra indexer is recompiled and installed issuing 

```
fakeroot apt-get source --compile idzebra-2.0
```
as normal user. The compiled GNU/Debian packages can then be installed as root issuing 

```
dpkg -i install idzebra-2.0*.deb libidzebra-2.0*.deb
```
I get as far as apt-get build-dep idzebra-2.0 and I get this error message:

```
root@chris-desktop:~# apt-get build-dep idzebra-2.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/ftp.indexdata.dk_debian_dists_indexdata_sarge_released_source_Sources - open (2 No such file or directory)
root@chris-desktop:~#
```
How do I solve this non-existent file problem?

Thanks everyone

---

### Post by Jac3510 on 2009-02-11
Regarding Zebra, I think I have a more general question that will be easier to answer that I can use to solve my problem:

The index to Zebra's source code is here:

[http://ftp.indexdata.dk/pub/](http://ftp.indexdata.dk/pub/)

What would the process be for getting the code and compiling/installing it myself, and which ones should I get?

Thanks again.

---

