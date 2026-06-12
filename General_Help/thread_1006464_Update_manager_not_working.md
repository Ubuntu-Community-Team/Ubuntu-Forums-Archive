---
title: "Update manager not working"
date: 2008-12-09
forum: General Help
---

### Post by anirudh_sml on 2008-12-09
Hi i was using ubuntu 8.01 with apache2, modperl and mason .Everything was fine and working quite good today i was configuring catalyst and os crashed might i had done some thing wrong .I install ubuntu again through CD it is ubuntu7.10 now when i try to update through update manager it is not working properly and not updating anything and if i run  
sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Reading package lists... Done
happens and again no updates actually iwant to install apache2 and mod perl and mason  so plssssssssssss anyone help pls

thanks

---

### Post by adult swim on 2008-12-09
go to a terminal and type in ```
cat /etc/apt/sources.list
``` and then paste the results here

---

### Post by anirudh_sml on 2008-12-09
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by adult swim on 2008-12-09
you arent getting any updates because the only place that is marked for updates is the ubuntu cd.  go to system>administration>synaptic package manager and then click on settings in the top and select repositories.  make sure that the first four boxes are checked and then close that window.  now try to update.

---

### Post by anirudh_sml on 2008-12-09
I had done but when i reload after checking all the four check it gives an error message  Can not download all the repo0sitary indexes,and say me to check 
[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]

---

### Post by anirudh_sml on 2008-12-09
Actually everything was working fine the problem started when today when os got crashed and i again reinstall the ubuntu shall i format the system and then install it .

---

### Post by adult swim on 2008-12-09
you already reinstalled once didnt you?  
EDIT:  try switching the download from server, which is in the same settings box as last time.

---

### Post by anirudh_sml on 2008-12-09
Now i dont have apache2 and not modperl nothing i dont know , i thing i shall install it manualy

---

### Post by adult swim on 2008-12-09
can you update now?

---

### Post by anirudh_sml on 2008-12-09
from where i will uppdate i dont have any dump or anything ...:(

---

### Post by adult swim on 2008-12-09
im not sure what you mean.  now that you have changed your repository server, do you still get the error messages when you run ```
sudo apt-get update
```

---

