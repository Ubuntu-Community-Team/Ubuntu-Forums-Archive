---
title: "Unable to install required package &amp; dependencies on Desktop 14.04"
date: 2014-12-30
forum: Gaming &amp; Leisure
---

### Post by ravi9 on 2014-12-30
Hello,
I'm trying to run a game called dwarf fortress on my system but I'm having an issue with the required libraries. 
Upon running the game start script, I get the following error
```
./libs/Dwarf_Fortress: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory
```
I searched to see what package   libSDL-1.2.so.0 is part of and its [COLOR=#333333][FONT=Ubuntu]libsdl1.2debian. I checked to see if it's installed
[/FONT][/COLOR]```
$ apt-cache policy libsdl1.2debianlibsdl1.2debian
  Installed: 1.2.15-8ubuntu1.1
  Candidate: 1.2.15-8ubuntu1.1
  Version table:
 *** 1.2.15-8ubuntu1.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.2.15-8ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```
[COLOR=#333333][FONT=Ubuntu]The x64 package is but the x32 is not. DF is a x32 application so I attempted to add it.
[/FONT][/COLOR]```
$ sudo dpkg --add-architecture i386
$ sudo apt-get install libsdl1.2debian:i386
...
The following packages have unmet dependencies:
 libsdl1.2debian:i386 : Depends: libpulse0:i386 (>= 1:0.99.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]So then I tried to install libpulse0:i386 and it was also missing a dependency. This happened with a few more till I eventually reached this point
```
$ sudo apt-get install libvorbis0a:i386
The following packages have unmet dependencies:
 aspectj : Depends: default-jre-headless but it is not going to be installed or
                    java2-runtime-headless
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```
Now the problem is that my system is reporting that aspectj and default-jre-headless are already installed.

I am not sure how to proceed from this point. I'm still a linux newbie and would appreciate some guidance. If more info is required, please let me know and I will provide it.

Thanks.

---

### Post by ian-weisser on 2014-12-30
> **ravi9 said:**
> Now the problem is that my system is reporting that aspectj and default-jre-headless are already installed.

Great job following the chain of missing dependencies. You are on the right track.

Please show us how the system is reporting that those two packages are already installed.

---

### Post by MAFoElffen on 2014-12-30
Just checking-- Trying not to assume. Do you have ia32-libs installed? That would be required  for multi-arch support (to run 32 bit app's on 64bit arch) If not, then it would say that a package was installed, but wouldn't reqcognize that's it 32bit counterpart wasn't. Just thinking out loud.

---

### Post by Bucky Ball on 2014-12-31
*Thread moved to **Gaming & Leisure**.*

Installation & Upgrade is for support installing and upgrading the OS, not programs. You might have more luck here. ;)

---

