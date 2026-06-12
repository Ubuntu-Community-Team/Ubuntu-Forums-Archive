---
title: "Can't install Cedega"
date: 2006-08-19
forum: Gaming &amp; Leisure
---

### Post by SZF2001 on 2006-08-19
This is what happens after following [this HOWTO page](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Cedega+CVS):

```
coleman@colecomp:~$ sudo apt-get install cvs build-essential bison flex-old liba sound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxr ender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev l ibsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
Password:
Reading package lists... Done
Building dependency tree... Done
bison is already the newest version.
libttf2 is already the newest version.
msttcorefonts is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.0) but it is not going to be installed
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
  libasound2-dev: Depends: libc6-dev but it is not going to be installed or
                           libc-dev
  libfontconfig1-dev: Depends: libexpat1-dev but it is not going to be installed
  libfreetype6-dev: Depends: libc6-dev but it is not going to be installed or
                             libc-dev
                    Depends: zlib1g-dev but it is not going to be installed or
                             libz-dev
  libjpeg62-dev: Depends: libc-dev
  libpng12-dev: Depends: zlib1g-dev but it is not going to be installed
  libsdl-net1.2-dev: Depends: libc6-dev but it is not going to be installed
  libsdl-ttf2.0-dev: Depends: libc6-dev but it is not going to be installed
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not going to be installed o r
                          libglu-dev
                 Depends: libaa1-dev but it is not going to be installed
                 Depends: libartsc0-dev but it is not going to be installed
                 Depends: libesd0-dev but it is not going to be installed
  libttf-dev: Depends: libc6-dev but it is not going to be installed
  x-window-system-dev: Depends: libgl1-mesa-dev but it is not going to be instal led
                       Depends: libglu1-mesa-dev but it is not going to be insta lled
                       Depends: xlibs-static-dev but it is not going to be insta lled
E: Broken packages
coleman@colecomp:~$

```

Anything I can do? I don't wanna upgrade to 6.06, Breezy runs just fine on my comp.

---

### Post by croak77 on 2006-08-19
Try it with sudo aptitude instead of apt-get.

---

### Post by SZF2001 on 2006-08-19
Then this happens:

```
coleman@colecomp:~$ sudo aptitude install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Unable to correct problems, you have held broken packages.
E: Unable to correct dependencies, some packages cannot be installed
E: Unable to resolve some dependencies!
Some packages had unmet dependencies.  This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

The following packages have unmet dependencies:
  libsdl1.2-dev: Depends: libglu1-mesa-dev but it is not installable or
                          libglu-dev which is a virtual package.
                 Depends: libaa1-dev but it is not installable
                 Depends: libartsc0-dev but it is not installable
                 Depends: libesd0-dev but it is not installable
  libsdl-net1.2-dev: Depends: libc6-dev but it is not installable
  libpng12-dev: Depends: zlib1g-dev but it is not installable
  libfontconfig1-dev: Depends: libexpat1-dev but it is not installable
  x-window-system-dev: Depends: libgl1-mesa-dev but it is not installable
                       Depends: libglu1-mesa-dev but it is not installable
                       Depends: xlibs-static-dev but it is not installable
  libjpeg62-dev: Depends: libc-dev which is a virtual package.
  libfreetype6-dev: Depends: libc6-dev but it is not installable or
                             libc-dev which is a virtual package.
                    Depends: zlib1g-dev but it is not installable or
                             libz-dev which is a virtual package.
  libttf-dev: Depends: libc6-dev but it is not installable
  libasound2-dev: Depends: libc6-dev but it is not installable or
                           libc-dev which is a virtual package.
  libsdl-ttf2.0-dev: Depends: libc6-dev but it is not installable
  build-essential: Depends: libc6-dev but it is not installable or
                            libc-dev which is a virtual package.
                   Depends: gcc (>= 4:4.0) but it is not installable
                   Depends: g++ (>= 4:4.0) but it is not installable
coleman@colecomp:~$

```

---

### Post by croak77 on 2006-08-19
Why don't you try installing 1 package at a time.

---

