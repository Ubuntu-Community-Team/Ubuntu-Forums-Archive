---
title: "unable to locate apt-get install ia32-libs ia32-libs-gt"
date: 2011-08-04
forum: Desktop Environments
---

### Post by sentinelace on 2011-08-04
sudo apt-get install ia32-libs ia32-libs-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ia32-libs
E: Unable to locate package ia32-libs-gtk


according to cisco, I need these and citrix 32bit libraries.  What is wrong?

---

### Post by sentinelace on 2011-08-06
time for a new fourm.  none of my posts ever get answered.

---

### Post by realzippy on 2011-08-06
Which ubuntu do you run? 64 bit?

---

### Post by oldos2er on 2011-08-06
> **sentinelace said:**
> time for a new fourm.  none of my posts ever get answered.

Answered this yesterday in the Multimedia subforum. Ubuntu repositories only have ia32-libs, none of the other files you mentioned.

---

### Post by realzippy on 2011-08-06
Is your universe repository enabled ?

---

### Post by Frogs Hair on 2011-08-06
The package ia32-libs appears in my 11.04 synaptic package manager . I have the Medibuntu repository enabled . I don't know if that repository required  though .

---

### Post by sentinelace on 2011-08-10
Sorry for the smart comment, just getting frustrated. I am running Destkop 11.04 and as far as I can see all the respositories are turned on. What am I missing?  How do I enable teh Medibuntu repository?

---

### Post by realzippy on 2011-08-10
you could post your sources.list....

---

### Post by oldos2er on 2011-08-10
> **sentinelace said:**
>   How do I enable teh Medibuntu repository?

[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)

---

### Post by sentinelace on 2011-08-11
so run that command or add that address somewhere?

---

### Post by realzippy on 2011-08-11
Here is a natty sources list ("with ia32libs"):

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse
```

...you could compare it with your current /etc/apt/sources.list or
use it as a whole.
Or enable universe..

---

### Post by oldos2er on 2011-08-11
> **sentinelace said:**
> so run that command or add that address somewhere?

As the page says, run the command in a terminal.

---

### Post by realzippy on 2011-08-11
*ia32-libs* is not part of the medibuntu repo..although adding it might be a good idea generally.
It is *universe*  see post **#5**  ;-)

---

