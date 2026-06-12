---
title: "problem installing compiz-gnome"
date: 2006-07-09
forum: Desktop Environments
---

### Post by zekopeko on 2006-07-09
hi,
trying to run xgl on this machine

amd barton xp 2600+
1 GB
ATI Radeon 9600Pro 128 MB
ubuntu 6.06 LTS updated

zekopeko@leviathan:~$ compiz --version
zekopeko@leviathan:~$ compiz 0.0.13-quinn11

followed this howto [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

i think that my ati card is properly installed

zekopeko@leviathan:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5879 (8.26.122

getting 2600+ fps in glxgears


the problem is installing compiz-gnome
i get the following error when installing with synaptic packet manager:

compiz-gnome:
  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed

what can i do to fix this? i'm pretty new to linux/ubuntu so have mercy 126

thank you for any info/help in advance

---

### Post by Dr. Nick on 2006-07-09
Just your standard version mismatch it appears, What howto, if any are you trying here?

Look [here]("http://ubuntuforums.org/showthread.php?t=148351&highlight=compiz+howto") and their is a link on how to get xgl running on radeon cards. Dont post a question on the thread I linked as it is "not a support thread" but if you click the how to on radeon link you may get the help ypu need

---

### Post by Anduu on 2006-07-09
I highly recomend this how to [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

---

### Post by zekopeko on 2006-07-10
this still doesn't help me.
 on compiz forum they said that i need dapper updates enabled. the thing is i don't know if i got everything ok in my sources.list
---------------------
is this ok?

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

---

### Post by titsmahoney on 2006-07-12
I get the same error...   

compiz-gnome:
Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed


anyone?

---

### Post by RAOF on 2006-07-12
> **zekopeko said:**
> ...
```

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
[color=red]deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse[/color]
## Uncomment the following two lines to add software from the 'universe'
## repository.
...

```
You need to add the (new) red line - you had the source packages for the dapper-updates, just not the actual (installable) binary packages :)

---

