---
title: "Software index is broken"
date: 2009-05-27
forum: General Help
---

### Post by umarblur on 2009-05-27
i try to install unrar package on ubuntu debian, but "software index broken" message appear.

[IMG]http://i216.photobucket.com/albums/cc165/umarblur/Screenshot-2.png

i've tried to solve it using terminal command like this but it wont fix the problem... 

this the terminal line happened after i insert the"  sudo apt-get install -f" command

[IMG]http://i216.photobucket.com/albums/cc165/umarblur/Screenshot-3.png[/IMG]


Someone help me please??? :(

---

### Post by salvachn on 2009-05-27
Might it be that your internet connection was not proper at that time? Try apt-get update. If it doesn't work you can edit /etc/apt/sources.list manually.

---

### Post by x33a on 2009-05-27
post the output of 
```
cat /etc/apt/sources.list
```

---

### Post by muhittin on 2009-05-29
Hi all,

I have a same problem. I run in terminal sudo apt-get update and sudo apt-get install -f but didn't solved. 

output of **cat /etc/apt/sources.list**;

```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://tr.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://tr.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://tr.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://tr.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://tr.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://tr.archive.ubuntu.com/ubuntu/ hardy universe
deb http://tr.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://tr.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://tr.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://tr.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://tr.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://tr.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://tr.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://tr.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb http://ppa.launchpad.net/teknoraver/ubuntu hardy main
deb-src http://ppa.launchpad.net/teknoraver/ubuntu hardy main

```

What can I do?

---

### Post by oldos2er on 2009-05-29
> **umarblur said:**
> i try to install unrar package on ubuntu debian, but "software index broken" message appear.

[IMG]http://i216.photobucket.com/albums/cc165/umarblur/Screenshot-2.png

i've tried to solve it using terminal command like this but it wont fix the problem... 

this the terminal line happened after i insert the"  sudo apt-get install -f" command

[IMG]http://i216.photobucket.com/albums/cc165/umarblur/Screenshot-3.png[/IMG]


Someone help me please??? :(

 Run
```
gksu gedit /etc/apt/sources.list
```
in a terminal. Hit Ctrl-I, type in 54, and add a comment mark # at the beginning of line 54. Save and exit the file, then run
```
sudo apt-get update
```

---

