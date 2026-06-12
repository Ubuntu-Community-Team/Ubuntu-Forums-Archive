---
title: "Confused about libcupsys2 packages.."
date: 2006-08-19
forum: Desktop Environments
---

### Post by seanf on 2006-08-19
I'm trying to build HPLIP from source, which requires the libcupsys2-dev package.

Synaptic shows me that "libcupsys2-dev 1.2.0-0ubuntu5 (dapper)" is available, but I can't install it because the libcupsys2 libs package is at v1.2.2

Launchpad shows libcupsys2-dev at the version I need...

[https://launchpad.net/distros/ubuntu/dapper/i386/libcupsys2-dev/1.2.2-0ubuntu0.6.06](https://launchpad.net/distros/ubuntu/dapper/i386/libcupsys2-dev/1.2.2-0ubuntu0.6.06)

...and I have downloaded and installed the deb from there with no problems.

My question is: why doesn't this newer version appear in Synaptic?

thanks, apt sources follow..

========================================================
sources.list:

```
sean@sean-laptop:/usr/src$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

# VIM7
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas backports
deb-src [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas backports

# eye candy
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

#easycam
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
```

---

