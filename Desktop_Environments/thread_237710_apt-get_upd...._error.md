---
title: "apt-get upd.... error"
date: 2006-08-16
forum: Desktop Environments
---

### Post by matko on 2006-08-16
hello.

havin this message long time 
```
Zlyhalo stiahnutie http://debian.space-based.de/debs/dists/experimental/Release  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)

```

i thought it is temporary. but getting this message quite long time.
do you know what this message mean because I cant install InitNG?
thanx

---

### Post by PriceChild on 2006-08-16
Well it looks like a malformed line in your sources list...

Post the output of your sources file:
```
gksudo gedit /etc/apt/sources.list
```
So we can repair the line :)

---

### Post by matko on 2006-08-17
here is my sources list
hope it helps. cause i cant see there any mistakes
> matko@dapper:~$ cat /etc/apt/sources.list
deb [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
deb-src [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
deb [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://sk.archive.ubuntu.com/ubuntu/](http://sk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
matko@dapper:~$


---

### Post by jak on 2006-08-17
those space-based.de repositories don't seem to be for Dapper. try removing the first two lines, then re-running apt-get.

---

### Post by matko on 2006-08-17
no they are good.
used to work for me long time ago.
it is source for InitNG from this howto

```
[https://help.ubuntu.com/community/InitNG]("https://help.ubuntu.com/community/InitNG")
```

---

### Post by jak on 2006-08-18
Well it's that repository which is causing the problem. You could just ignore it if you wanted, it's just one of the problems of using unofficial repositories - they aren't always working or even there sometimes.

---

