---
title: "Can't find gset-compiz"
date: 2006-08-11
forum: Desktop Environments
---

### Post by mikeytag on 2006-08-11
Hi everyone, I have been using XGL/Compiz for quite a while. I had a series of issues with a corrupted nvidia-glx but was able to fix it. By the time it was fixed I had installed/reinstalled a ton of packages, as I though compiz was the culprit, and have since lost my gset-compiz program. I can't find it anymore in synaptic no less. Here is my /etc/apt/sources.list

```


deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.beerorkid.com/compiz dapper main
deb http://ubuntu.compiz.net dapper main
deb http://www.beerorkid.com/automatix/apt dapper main

```

Does anyone know where I can find this package as it was immensely helpful in configuring compiz?

---

### Post by distroman on 2006-08-11
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
I can find it with these,,

gset-compiz seems to be a bit outdated. I don't think it handles the new plugins to well. 
You might what to have a look at compiz-settings, you can find it at the compiz forum.
Other then that I guess it's up to gconf-editor &

[http://xgl.compiz.info/](http://xgl.compiz.info/)
edit,,,
sleepy, off to bed

---

### Post by mcg on 2006-08-13
I can't find it in the repositories as well, and since compiz-quinn is dependant on it, cannot be installed.  Any ideas?

---

### Post by gruvsyco on 2006-08-13
I think (according to compiz.net) the people that host her DNS were under some kind of attack earlier today.  Keep trying it should come back.  And, yes gset-compiz is dated.  Compiz-settings is a little more up to date and appears to be somewhat dynamic too.

---

### Post by Flipper on 2006-08-13
Dont use gset-compiz, its not used anymore, use gconf-editor instead :)

btw:if you need help with XGL go to #Xgl @ Freenode in IRC

---

### Post by mcg on 2006-08-13
The quinn packages need to remove the deps on it then if it's deprecated.

---

### Post by mariner09 on 2006-08-14
The vanilla packages require the same thing.  I want to move forward, but kinda stuck at this point...

---

### Post by mcg on 2006-08-14
Something might be borked with the archive since I was able to download/install manually.  You can grab gset-compiz here
[http://www.beerorkid.com/compiz/pool/main/g/gset-compiz/]("http://www.beerorkid.com/compiz/pool/main/g/gset-compiz/")

---

### Post by holmes on 2006-08-16
Here's a Repository mirror I found for gset-compiz [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)


deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

---

