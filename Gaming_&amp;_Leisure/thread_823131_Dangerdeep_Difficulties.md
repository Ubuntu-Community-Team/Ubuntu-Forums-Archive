---
title: "Dangerdeep Difficulties"
date: 2008-06-08
forum: Gaming &amp; Leisure
---

### Post by jukingeo on 2008-06-08
Hello all,

I been having a tough time getting Dangerdeep to play on Ubuntu.  I just managed to get the game installed from a .bin file (and believe it or not that was a fiasco).  It went through the installation.  During installation on the directory change screen it said in bold letters -DO NOT CHANGE-, So of course I didn't.

Anyway, I have now an icon on my desktop with a lock on it that says "Danger From The Deep".

Double click on it and I get this error message:

There was an error launching the program:

Failed to change directory (no such file or directory).

I am curious if anyone else had/has this problem and if there is a fix.

Thanx,

Geo

---

### Post by Robin T Cox on 2008-06-09
I'm using Gutsy, and simply installed dangerdeep from the repository without any problems.

---

### Post by Vadi on 2008-06-09
I can't find it on 8.04, and packages.ubuntu.com didn't list it for 7.10 either... what is the name of the package?

Because their .bin installer does suck.

---

### Post by Robin T Cox on 2008-06-09
The package is called dangerdeep. I'm not sure exactly which repository it's in, but I have the following /etc/apt/sources.list:

> # 
# deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.2)]/ gutsy main restricted

# deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.2)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


## Medibuntu.  
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free 



---

### Post by Vadi on 2008-06-09
Edit: nvm, they provide a 32bit .deb. I'm on 64bit and can't use it - but I'll ask getdeb.net to make one.

---

### Post by jukingeo on 2008-06-09
So, any ideas on my error message and how to solve the problem?

---

### Post by Vadi on 2008-06-09
No idea, sorry. The installer most likely can't find it's own files. I'd wait for a .deb from getdeb.net or ask them for help.

---

