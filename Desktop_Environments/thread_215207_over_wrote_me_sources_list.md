---
title: "over wrote me sources list"
date: 2006-07-13
forum: Desktop Environments
---

### Post by shazbot on 2006-07-13
playing with Automatix and I overwrote my sources list and now the Synaptics list is quite differnet

Can anyone give me the correct list to correct the file, mine shows 

[http://paste.ubuntu-nl.org/17953](http://paste.ubuntu-nl.org/17953) 

Thanks

---

### Post by John.Michael.Kane on 2006-07-13
Heres a clean sources.list
**sudo gedit /etc/apt/sources.list**
```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main

```
**sudo aptitude update **

---

### Post by shazbot on 2006-07-14
done that thanks, for info how is the sourecelist.save filled ?? and what is the sources list backup ?? which does not have any info in it

---

