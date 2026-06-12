---
title: "Synaptic Failure"
date: 2007-04-20
forum: Desktop Environments
---

### Post by iWill on 2007-04-20
Tried to install virtual box but failed and now i cant do anything with synaptic
(error message:```
E:The package virtualbox needs to be reinstalled, but i can't find an archive for it
E:Internal error opening cache (1)
```
So what's the solution?

---

### Post by taurus on 2007-04-20
Run it from a terminal and see what happens.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install virtualbox
```

---

### Post by iWill on 2007-04-20
even though im logged in as root this is what happens after i type in your commands:
```
E: I wasn't able to locate a file for the virtualbox package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

```

---

### Post by iWill on 2007-04-20
Any solution?
I'm really hoping i dont have to reinstall ubuntu...

---

### Post by taurus on 2007-04-20
Which release are you running right now and can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

p.s.  It's _not_ a good idea to log in as root.  Use sudo instead.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by iWill on 2007-04-20
I am currently running Feisty
Heres what i got after typing in the command:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

Thanks

---

### Post by iWill on 2007-04-20
Anyone?

---

### Post by s_p_a_r_k_y on 2007-04-20
try uninstalling it. then doing the aptitude route again. Make sure synaptic is closed.

---

### Post by gjohn2 on 2007-04-21
I am having the exact same problem.
can't uninstall, can't reinstall. *arggg*
can't update.....

---

### Post by gjohn2 on 2007-04-21
hey i found a solution for myself.
[http://ubuntuforums.org/showthread.php?t=401752&page=2](http://ubuntuforums.org/showthread.php?t=401752&page=2)
here.

---

