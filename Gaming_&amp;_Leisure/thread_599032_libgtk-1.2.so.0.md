---
title: "libgtk-1.2.so.0"
date: 2007-10-31
forum: Gaming &amp; Leisure
---

### Post by vinls on 2007-10-31
trying to install a game and get this error:
error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory.
any idea where I could get this old library?

---

### Post by DoktorSeven on 2007-11-01
Always search the repositories with the first part of the library name.

$ apt-cache search libgtk1.2
libgtk1.2 - The GIMP Toolkit set of widgets for X
(more that are related, like development files, etc).

So sudo apt-get install libgtk1.2

---

### Post by dfreer on 2007-11-01
Hmmm, by default you should already have libgtk1.2 installed. Are you by any chance trying to install a 32-bit game on a 64-bit OS?

---

### Post by vinls on 2007-11-01
sudo apt-get install libgtk1.2

returns

couldn't find package 1ibgtk1.2

---

### Post by dfreer on 2007-11-01
Can you post the output of these commands?:
```
cat /etc/apt/sources.list
uname -m
```

And also tell us the game you are trying to install?

EDIT:
> couldn't find package 1ibgtk1.2
Looks like you spelled libgtk1.2 wrong, unless that's just a typo.

---

### Post by vinls on 2007-11-02
```
mario@mario-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
mario@mario-desktop:~$ uname -m
i686

```
the game being RTCW:Enemy Territory

---

### Post by Cappy on 2007-11-02
> **vinls said:**
> sudo apt-get install libgtk1.2

returns

couldn't find package 1ibgtk1.2

Copy and paste
```

sudo apt-get install libgtk1.2
``` into the terminal. It looks like there was a typo.

---

### Post by dfreer on 2007-11-02
Ummmm.

Every single line is commented out in your /etc/apt/sources.list, it looks like the installer wasn't able to connect to the internet. Which is probably why apt-get is failing on you, cuz it doesn't know where to search. I assume your able to get connect to the internet with this machine?

Do this:
```
sudo gedit /etc/apt/sources.list
```

And then delete everything in it and replace it with this:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb http://archive.canonical.com/ubuntu gutsy partner
#deb-src http://archive.canonical.com/ubuntu gutsy partner

```

Then do this:
```
sudo apt-get update
sudo apt-get install libgtk1.2
```

That should take care of your libgtk1.2 requirement, unfortunately I can't help you out with installing the game itself. But if you get any more error messages I can help out probably, or someone else who knows the game can help.

---

### Post by vinls on 2007-11-02
problem solved, thx everyone

---

### Post by faical117 on 2007-11-12
thanks :)

---

### Post by belgarion2010 on 2008-04-23
i now get ./n_v14: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
 what do i apt-get now

---

### Post by dfreer on 2008-04-23
Are you in hardy? I do believe that there is an issue with this library in Hardy, something about it not compiling correctly? IDK, I saw it in a thread somewhere. They recommended installing the gutsy version of libstdc++-libc6, you can find the i386 gutsy package here: [http://packages.ubuntu.com/gutsy/libstdc%2B%2B2.10-glibc2.2](http://packages.ubuntu.com/gutsy/libstdc%2B%2B2.10-glibc2.2)

---

### Post by GSZX1337 on 2008-04-23
Not to highjack this thread, but I have a similar [problem]("http://ubuntuforums.org/showthread.php?t=760913").

---

### Post by dfreer on 2008-04-24
> **GSZX1337 said:**
> Not to highjack this thread, but I have a similar [problem]("http://ubuntuforums.org/showthread.php?t=760913").

I replied in your thread.

---

### Post by derekablackburn on 2008-10-11
had to google through a bunch of crap to find this, thanks epsxe was giving me a migraine

---

### Post by Masquerade on 2009-02-11
> **DoktorSeven said:**
> Always search the repositories with the first part of the library name.

$ apt-cache search libgtk1.2
libgtk1.2 - The GIMP Toolkit set of widgets for X
(more that are related, like development files, etc).

So sudo apt-get install libgtk1.2

thankies, very useful

---

### Post by waldherrvonbirnbaum on 2009-08-01
oh jihar! thanks a lot! now duke 3d rocks.

---

