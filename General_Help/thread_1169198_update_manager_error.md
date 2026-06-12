---
title: "update manager error"
date: 2009-05-24
forum: General Help
---

### Post by ctrlmd on 2009-05-24
when i try to install or update anything from update manager of terminal i receive the following error 

[PHP]Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages
[/PHP]

any idea how to reslove this issue

---

### Post by RedSingularity on 2009-05-24
Look in your sources list for a bad source?

---

### Post by ctrlmd on 2009-05-24
> **Shadow121 said:**
> Look in your sources list for a bad source?

ty for replying i don't know which one is a bad source

my sources list  

> #deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by RedSingularity on 2009-05-24
They look fine.  Have you added any custom ones?

---

### Post by ctrlmd on 2009-05-24
> **Shadow121 said:**
> They look fine.  Have you added any custom ones?

no i did not add a custom ones  the last application i installed was x-sensors 

and when i tried to remove it i couldn't maybe its the one causing this issue

---

### Post by RedSingularity on 2009-05-24
System>Admin>Software sources>Third party tab.  Uncheck them all and try out the update again.

---

### Post by ctrlmd on 2009-05-24
> **Shadow121 said:**
> System>Admin>Software sources>Third party tab.  Uncheck them all and try out the update again.

nothing checked from third party tab

---

### Post by ctrlmd on 2009-05-24
Ok i did something else to solve this issue 

i uncheck all the selection on UBUNTU SOFTWARE 

then i tried to update  after updating which didn't update anything it just display [[COLOR=Blue]Reading package lists... Done[/COLOR]]

then i check them all on UBUNTU SOFTWARE and i update it and it works fine 


thanks shadow121 for helping :p

---

### Post by RedSingularity on 2009-05-25
No problem, glad you got it:)

---

