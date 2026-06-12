---
title: "pcsx2 missing dependencies"
date: 2020-05-14
forum: Emulators
---

### Post by Gareth_2007 on 2020-05-14
Hi All,

I'm trying to install PCSX2 32bit on ubuntu server 64 bit as many others have.

before attempting i ran - sudo dpkg --add-architecture i386

But get the following errors - 


```
RetroPie-Setup version: 4.6.1 (1340a40)
System: Ubuntu 18.04.4 LTS - Linux RetroPie 4.15.0-99-generic #100-Ubuntu SMP Wed Apr 22 20:32:56 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

= = = = = = = = = = = = = = = = = = = = =
Installing dependencies for 'pcsx2' : PS2 emulator PCSX2
= = = = = = = = = = = = = = = = = = = = =

Hit:1 http://ppa.launchpad.net/gregory-hainaut/pcsx2.official.ppa/ubuntu bionic InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu bionic InRelease
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Hit:4 http://ppa.launchpad.net/pcsx2-team/pcsx2-daily/ubuntu bionic InRelease
Get:5 http://gb.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Hit:6 http://ppa.launchpad.net/ubuntu-x-swat/updates/ubuntu bionic InRelease
Get:7 http://gb.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Fetched 252 kB in 0s (662 kB/s)
Reading package lists...

= = = = = = = = = = = = = = = = = = = = =
Installing 'pcsx2' : PS2 emulator PCSX2
= = = = = = = = = = = = = = = = = = = = =

Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 pcsx2-unstable:i386 : Depends: libasound2:i386 (>= 1.0.16)
                       Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                       Depends: libglib2.0-0:i386 (>= 2.31.18) but it is not going to be installed
                       Depends: libglx0:i386 but it is not going to be installed
                       Depends: libgtk2.0-0:i386 (>= 2.24.0) but it is not going to be installed
                       Depends: libopengl0:i386 but it is not going to be installed
                       Depends: libportaudio2:i386 (>= 19+svn20101113) but it is not going to be installed
                       Depends: libsdl2-2.0-0:i386 (>= 2.0.8) but it is not going to be installed
                       Depends: libudev1:i386 (>= 183) but it is not going to be installed
                       Depends: libwxgtk3.0-0v5:i386 (>= 3.0.4+dfsg) but it is not going to be installed
                       Depends: libx11-6:i386 but it is not going to be installed
                       Recommends: libasound2-plugins:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
Unable to install binary for pcsx2

Log ended at: Thu 14 May 17:40:36 BST 2020
Total running time: 0 hours, 0 mins, 4 secs
```

---

### Post by deadflowr on 2020-05-14
[I]Thread moved to **Emulators**
[/I]

It looks like the ppa for bionic [https://launchpad.net/~pcsx2-team/+archive/ubuntu/pcsx2-daily](https://launchpad.net/~pcsx2-team/+archive/ubuntu/pcsx2-daily)
failed to build, so it produced no pcsx2-unstable package.

---

### Post by Perfect Storm on 2020-05-14
Have you tried install the dependencies one by one?

---

