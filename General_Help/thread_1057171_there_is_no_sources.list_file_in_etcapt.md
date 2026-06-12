---
title: "there is no sources.list file in /etc/apt"
date: 2009-02-01
forum: General Help
---

### Post by rsleventhal on 2009-02-01
Hi folks,

I'm struggling with two things.  The first is that there's no file called sources.list in /etc/apt/.  The second is I have no idea how it got  'gone', because I'm sure it was there when last I looked.

Is there a simple way to restore the file to defaults?  I'm running a recently updated version of intrepid:

$ uname -a
Linux rsllt 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux


Any help is greatly appreciated.

-Ray

---

### Post by taurus on 2009-02-01
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la /etc/apt
```

---

### Post by rsleventhal on 2009-02-01
Thanks for your reply.  It really isn't there :)

$ ls -la /etc/apt
total 44
drwxr-xr-x   4 root root  4096 2009-02-01 14:24 .
drwxr-xr-x 135 root root 12288 2009-02-01 08:14 ..
drwxr-xr-x   2 root root  4096 2009-01-21 14:06 apt.conf.d
-rw-------   1 root root     0 2008-10-29 18:54 secring.gpg
drwxr-xr-x   2 root root  4096 2008-08-14 12:55 sources.list.d
-rw-------   1 root root  1200 2008-10-29 18:54 trustdb.gpg
-rw-r--r--   1 root root  6713 2008-10-29 18:54 trusted.gpg
-rw-r--r--   1 root root  6713 2008-10-29 18:54 trusted.gpg~


I'm new to this distro but have been running Linux for ages (mostly RHEL and CentOS servers)

I truly appreciate your help..

-Ray

---

### Post by taurus on 2009-02-01
I guess you just have to create a new one then.  You can use mine if you wish.  Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and paste these lines to it.

```

#deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```
Save it and close down gedit editing window.  Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rsleventhal on 2009-02-01
Thank you *very* much!

-Ray

---

