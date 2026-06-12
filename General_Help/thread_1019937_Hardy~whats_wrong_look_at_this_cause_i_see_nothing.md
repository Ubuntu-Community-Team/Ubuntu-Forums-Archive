---
title: "Hardy~whats wrong? look at this cause i see nothing wrong but i help !"
date: 2008-12-23
forum: General Help
---

### Post by KEE on 2008-12-23
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
```

im trying to install ccsm but im getting errors 
```
username@username-desktop:~$ sudo gedit /etc/apt/sources.list
username@username-desktop:~$ ccsm
The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: command not found
username@username-desktop:~$ sudo gedit /etc/apt/sources.list

```

so i entered this ```
sudo apt-get install compizconfig-settings-manager
```
ok thats working but AWN Manager is still not coming up ! please help 

AWN Mangager [HTML]http://ubuntuforums.org/showthread.php?t=762363[/HTML]

---

### Post by fooman on 2008-12-23
what happens when you try to start awn in a terminal?

type or copy/paste the following in a terminal and post the output back here:

```
avant-window-navigator
```

---

### Post by KEE on 2008-12-23
> **fooman said:**
> what happens when you try to start awn in a terminal?

type or copy/paste the following in a terminal and post the output back here:

```
avant-window-navigator
```
lol that did it Merry Christmas!! thank you

---

### Post by KEE on 2008-12-23
> **fooman said:**
> what happens when you try to start awn in a terminal?

type or copy/paste the following in a terminal and post the output back here:

```
avant-window-navigator
```
ok but now as soon as i turn off terminal AWN  goes away?!?

---

### Post by KEE on 2008-12-23
> **KEE said:**
> ok but now as soon as i turn off terminal AWN  goes away?!?

ok i think i got it . its automatic is not checked

---

### Post by fooman on 2008-12-23
sorry, try it like this:

```
avant-window-navigator &
```

it should stick after you close the terminal with a "&" after the command.

is it in your menu? ....applications > accessories > avant window navigator

or is that what does not work?

---

