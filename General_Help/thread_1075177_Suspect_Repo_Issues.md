---
title: "Suspect Repo Issues"
date: 2009-02-20
forum: General Help
---

### Post by sswittch on 2009-02-20
I'm guessing there are multiple topics on this forum I can post in but to me this is a question that can be answered by anyone with a little knowledge.

I have ubuntu server 8.10 installed

Everything is working except apt-get.

I am not sure why but any time I use apt-get I am presented with error messages.

apt-get error
```
dallas@ubuntu-ritzphoto:/etc/apt$ sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package proftpd

```

sources.list
```
# deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ i$

#deb cdrom:[Ubuntu-Server 8.10 _Intrepid Ibex_ - Release i386 (20081028.1)]/ in$
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted uni$
deb-src http://au.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted$

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by jerome1232 on 2009-02-20
Did you do a 'sudo apt-get update' first? If there's any errors from that can you post them?

---

### Post by sswittch on 2009-02-20
> **jerome1232 said:**
> Did you do a 'sudo apt-get update' first? If there's any errors from that can you post them?

Thankyou, your completely right.

I never thought of that as I attempted to do it eairler and got the same error.  

However I didn't retry the command after editing /etc/network/interfaces and actually getting the computer on the network.

Cheers for the help

---

