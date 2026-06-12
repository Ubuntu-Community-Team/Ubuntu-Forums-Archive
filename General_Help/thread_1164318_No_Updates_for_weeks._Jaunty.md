---
title: "No Updates for weeks. Jaunty"
date: 2009-05-19
forum: General Help
---

### Post by carl99fan on 2009-05-19
I have not had any updates to my computer in weeks.
If fact it has been since I upgraded to Jaunty.

I may have messed something up. I checked my software sources and it says daily.
Please help.

---

### Post by Keithhed on 2009-05-19
Do you have the updates set up so they install in the background?

---

### Post by paradigm2 on 2009-05-19
What is in /etc/apt/sources.list ?

```

cat /etc/apt/sources.list

```

(in a terminal)

---

### Post by carl99fan on 2009-05-19
```
 sara@sara-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse #Added by software-properties
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe #Added by software-properties
# deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock


```

---

### Post by carl99fan on 2009-05-19
> **Keithhed said:**
> Do you have the updates set up so they install in the background?

No I have only notify about updates.

---

### Post by paradigm2 on 2009-05-19
Your sources.list mostly seems okay from a quick glance.  If you go to System -> Administration -> Update Manager and then hit CHECK, what happens?

Jaunty does not notify daily as it used.  Only for security updates, otherwise once a week.  At least this wa the behaviour from the beta version.

---

### Post by carl99fan on 2009-05-19
> **paradigm2 said:**
> Your sources.list mostly seems okay from a quick glance.  If you go to System -> Administration -> Update Manager and then hit CHECK, what happens?

Jaunty does not notify daily as it used.  Only for security updates, otherwise once a week.  At least this wa the behaviour from the beta version.

The same 3 are there since I upgraded to Jaunty.
No security, mozilla, kernel, nothing.

So I decided to go ahead and install the updates.... And I got Picture #2

---

### Post by carl99fan on 2009-05-19
I am going to uninstall the game causing the problem.


OK IT was a broken package.
I now have 274 megs of updates I need to do. 
Thanks for your help. sorry I am waisting time with easy stuff.

---

### Post by Soul-Sing on 2009-05-19
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```
and you got the updates on a daily base.

---

