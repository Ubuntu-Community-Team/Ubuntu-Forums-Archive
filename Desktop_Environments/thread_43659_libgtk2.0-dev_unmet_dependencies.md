---
title: "libgtk2.0-dev unmet dependencies"
date: 2005-06-22
forum: Desktop Environments
---

### Post by virgule on 2005-06-22
ok I hope this is the right place. Yesterday I have submited a bug report on bugzilla and still waiting for a fix. Someone else reported the same problem. Im not sure whats causing this it should be fix soon. Please, those who can fix this just do it. I want to compile these gtk apps!  :) 

]# sudo apt-get install libgtk2.0-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.5.1) but it is not going to be installed
E: Broken packages
]#

---

### Post by Xian on 2005-06-22
This is what I get by copying your command to my system:
```
$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libatk1.0-dev libpango1.0-dev
Suggested packages:
  libgtk2.0-doc libpango1.0-doc
The following NEW packages will be installed:
  libatk1.0-dev libgtk2.0-dev libpango1.0-dev
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 7468kB of archives.
After unpacking 37.3MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```
Check your /etc/apt/sources.list.
Do they look like mine?

If not then backup your current sources.list and use mine instead.
Then do a 'sudo apt-get update'.

```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe



## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

#deb http://www.os-works.com/debian testing main
#deb-src http://www.os-works.com/debian testing main
```

---

### Post by virgule on 2005-06-22
I just did it. Same thing happen. Besides that I am on a PowerPC computer maybe that is the real culprit?

---

### Post by Xian on 2005-06-22
Something is just not right here.
Are you sure you don't have some broken deps on you system?

```
$ sudo apt-get -f install
```
If not, then what version of libpango1.0-dev do you have installed?

Mine (output below after wajig install) is 1.8.1-0ubuntu2 and the libgtk2-dev package only requires a version >= 1.5.1. 

```
$ sudo wajig status libpango1.0-dev
Package                 Installed       Previous        Now             State
=======================-===============-===============-===============-=====
libpango1.0-dev         N/A             1.8.1-0ubuntu2  1.8.1-0ubuntu2

```

```
$ sudo wajig detail libgtk2.0-dev
Package: libgtk2.0-dev
Priority: optional
Section: libdevel
Installed-Size: 35104
Maintainer: Sebastien Bacher <seb128@debian.org>
Architecture: i386
Source: gtk+2.0
Version: 2.6.4-0ubuntu3
Replaces: libgtk1.3-dev
Depends: libgtk2.0-0 (= 2.6.4-0ubuntu3), libglib2.0-dev (>= 2.4.1-2), libpango1.0-dev (>= 1.5.1), libatk1.0-dev (>= 1.6.1-2), libx11-dev | xlibs-dev, libxext-dev | xlibs-dev, pkg-config
```

---

### Post by virgule on 2005-06-22
Well.. Something must have gone bad. Im sure its my fault. :roll:  So, In a hurry I just re-installed from scratch. heh. I just did it because I lack some know-how to diagnose such problems. If I see no obvious answer(s) I choose the simpliest solution: re-install. I love Linux so much but when this thing start to break it kinda freak me... :grin: My system was up since a week only its no big deal. Now that I know about **sudo apt-get -f install** I will work harder if this happen again.

 Im glad it work now but I must say I feel a little sad because I will never know what actually caused this issue. So be it!

-Cheers

---

