---
title: "window header gone when compiz --replace"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by sdowney717 on 2007-08-23
it was working but I changed it around to try vorian repositories and now I tried to go back to trevino and everytime I run compiz --replace I loose my window top header. Also I cant get emerald to bring the header back up like I used to do.
So, how do I get the window header to show up


I solved this by going into compiz setting manager, preferences and click reset to default. Now emerald loads fine and all plugins working again.

it may have been the 'window decoration' plugin not enabled.
simple stuff, but if you dont find this info somehow, you never figure things out.

---

### Post by Dark Star on 2007-08-23
Everything works fine here maybe Emerald doing something wrong```
 emerald --replace &
```

---

### Post by sdowney717 on 2007-08-23
scott@scott-desktop:~$  emerald --replace &
[2] 7532
scott@scott-desktop:~$ 


is all I get. I have emerald theme manager open and a them selected

---

### Post by Dark Star on 2007-08-23
Do this in Alt+ F2 screen not in terminal :p

---

### Post by sdowney717 on 2007-08-23
here is a picture of what I mean by headers are gone

I tried alt - F2 and no diff

---

### Post by Dark Star on 2007-08-23
Yep I knew that Press Alt+F2 then type ```
emerald --replace &
```

---

### Post by sdowney717 on 2007-08-23
before I messed around with this I used to have in compiz settings manager the ability to change the backend, now all I have is flat file

---

### Post by mrmiserable on 2007-08-23
check you have version 3 i think it is i had same problem edit your apt source list and delete or # next to the one you dont want to get it back to version 3 not version 2 then check synaptic reload and you should see version 3 if it is version 2 now then re-install emerald
hope this make sense 
good luck

---

### Post by sdowney717 on 2007-08-23
here is the list, so which line is wrong??

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
 
## LG3D repsoitories


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
# deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
# deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse

---

### Post by sdowney717 on 2007-08-23
here is a picture of emerald in synaptic showing version 0.5.2, what is version 3?

---

### Post by sdowney717 on 2007-08-23
solved ?

simply go into compiz manager and set to default

title bar returned.

---

### Post by sdowney717 on 2007-08-23
yes, that made it all work again

---

