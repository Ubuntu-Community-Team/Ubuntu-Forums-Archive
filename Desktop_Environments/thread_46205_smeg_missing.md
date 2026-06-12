---
title: "smeg missing?"
date: 2005-07-03
forum: Desktop Environments
---

### Post by WMCoolmon on 2005-07-03
I can't seem to apt-get smeg, although I have all the new repos listed in the guide. (I double-checked)

Just in case something's wrong that I missed, here's my sources.list - I'm on Hoary64, if that changes anything:
```


deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
#More backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

#Marillat repos
#For use only as last-ditch, as they are technically
#Debian, and not Ubuntu.
# deb ftp://ftp.nerim.net/debian-marillat/ unstable main
# deb ftp://ftp.nerim.net/debian-marillat/ testing main
# deb ftp://ftp.nerim.net/debian-marillat/ stable main

#WINE Repos
# deb http://wine.sourceforge.net/apt/ stable main
# deb-src http://wine.sourceforge.ent/apt/ stable main
```

---

### Post by mrcbrown on 2005-07-03
[QUOTE=WMCoolmon]I can't seem to apt-get smeg, although I have all the new repos listed in the guide. (I double-checked)

Just in case something's wrong that I missed, here's my sources.list - I'm on Hoary64, if that changes anything:
```


deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
#More backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted

#Marillat repos
#For use only as last-ditch, as they are technically
#Debian, and not Ubuntu.
# deb ftp://ftp.nerim.net/debian-marillat/ unstable main
# deb ftp://ftp.nerim.net/debian-marillat/ testing main
# deb ftp://ftp.nerim.net/debian-marillat/ stable main

#WINE Repos
# deb http://wine.sourceforge.net/apt/ stable main
# deb-src http://wine.sourceforge.ent/apt/ stable main
```[/QUOTE]
 Does it give a error message as to why it didn't install? I know it didn't show up in the menus for me, but I can easily type smeg at a terminal, and it'll run.

---

