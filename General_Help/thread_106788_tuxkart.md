---
title: "tuxkart?"
date: 2005-12-21
forum: General Help
---

### Post by tmasboa on 2005-12-21
Hi, i am a former Hoary user, and i used to play Tuxkart. 

In Breezy, i made the repostories to universal and everything, but tuxkart doesn't show up.

So, I downloaded it. I downloaded plib-1.8.0. When i did a ./configure, it gave me:

> checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable cc found in $PATH



So, i did
> 
sudo apt-get install gcc


Then, i tried it again:
> 

checking for gcc... gcc
checking for C compiler default output... configure: error: C compiler cannot cr eate executables



Please help! Thanks

-Daniel

---

### Post by aysiu on 2005-12-21
[QUOTE=tmasboa]Hi, i am a former Hoary user, and i used to play Tuxkart. 

In Breezy, i made the repostories to universal and everything, but tuxkart doesn't show up.[/quote] According to [the Ubuntu packages site](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=tux&searchon=names&subword=1&version=breezy&release=all) it's in the Universe repositories. Can you post you /etc/apt/sources.list?

---

### Post by tmasboa on 2005-12-21
Thanks, here is my /etc/apt/sources.list:
> 
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


---

### Post by tmasboa on 2005-12-21
OK, i figured it out. Some of them weren't uncommented (obviously). Thanks.

---

### Post by tmasboa on 2005-12-21
oh and btw, i like breezy better. It seems faster on my old computer than it was on my newer one.

---

