---
title: "Can't install g++"
date: 2009-06-09
forum: General Help
---

### Post by wbest on 2009-06-09
For work, I need to get g++ working on my Ubuntu machine. However, because of the security and blocks, I can't download anything off synaptic. I was able to get gcc working by going to packages.ubuntu.com and downloading the required packages and installing them, which for some reason the network allows. The problem is, whenever I try to install g++ I keep getting dependencies which I cannot download. Often times, these dependences either have themselves as dependencies, or have a package that depends on THEM as dependencies (A requires B and B requires A) it sounds crazy, I know, but it is seriously driving me crazy. Also, the scree keeps flickering, which really does not help at all, but I'm hoping the tech guy who set up the computer can help fix that (I have a windows machine and a Linux machine hooked to the same monitor, to me it looks all fine. Plus the flicker gets worse when I have multiple windows open, so I'm not conviced its a hardware problem).
Also, to make matters even more interesting, I'm pretty sure the tech guy said I'm the only Linux machine in the office.

---

### Post by ActiveFrost on 2009-06-09
Download ALL build-essential parts/packages in one folder ( eg. /home/user/compiler/ ) from [http://packages.ubuntu.com/jaunty/devel/build-essential](http://packages.ubuntu.com/jaunty/devel/build-essential) & try to install again.

---

### Post by rbueno on 2009-06-09
I'm not sure that this can help for you but it works on me.
***sudo apt-get install gcc make g++ ***
Just try, if it will downloading g++

---

### Post by wbest on 2009-06-09
Yeah, the network won't let me connect that way either.
It lets me download the packages from packages.ubuntu, but two packages (g++-4.3 and some library, I think) require each other and, as far as I can tell, need to be downloaded simultaneously.

---

### Post by wbest on 2009-06-09
It won't let me install build-essential, because I don't have g++, which is strange because from what I have read, build-install contains g++ and other such things.
I can't install g++ because it requires some library which itself requires g++.

---

### Post by TrakerJon on 2009-06-09
~$ apt-cache showpkg g++
Package: g++
Versions: 
4:4.3.3-1ubuntu1 (/var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_jaunty_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/mirror.cc.columbia.edu_pub_linux_ubuntu_archive_dists_jaunty_main_binary-i386_Packages
                  MD5: abf7a21a88a8ba95858d401b8ca23b7c


Reverse Depends: 
  u++,g++ 1:3.3
  r-base-dev,g++
  python-scipy,g++
  pmk,g++
  plib-doc,g++
  pentium-builder,g++
  openc++,g++
  octave3.0-headers,g++
  mffm-timecode-dev,g++
  lsb-build-cc3,g++
  lightning,g++
  libstlport5.1-dev,g++
  libroot-dev,g++
  libocc0-dev,g++
  libginac-dev,g++
  kimwitu++,g++
  kaya,g++
  gobjc++,g++ 4:4.3.3-1ubuntu1
  geordi,g++
  freehdl,g++
  felix,g++
  eclipse-cdt,g++
  codelite,g++
  codeblocks,g++
  binfmtc,g++
  aspectc++,g++
  apt-build,g++
  anjuta,g++
  acovea,g++
  openoffice.org-dev-doc,g++
  openoffice.org-dev,g++
  libstlport4.6-dev,g++
  libcln-dev,g++
  konwert-dev,g++
  hardening-wrapper,g++
  gccxml,g++
  g++-multilib,g++ 4:4.3.3-1ubuntu1
  build-essential,g++ 4:4.3.1
Dependencies: 
4:4.3.3-1ubuntu1 - cpp (2 4:4.3.3-1ubuntu1) gcc (2 4:4.3.3-1ubuntu1) g++-4.3 (2 4.3.3-1) gcc-4.3 (2 4.3.3-1) g++-multilib (0 (null)) 
Provides: 
4:4.3.3-1ubuntu1 - c++-compiler

---

### Post by benj1 on 2009-06-09
build-essential contains the g++ compiler.

i assume its a work computer? if you need it for work why don't you get someone from IT with root privileges to install it

---

### Post by michy99 on 2009-06-09
> **benj1 said:**
> build-essential contains the g++ compiler.

Actually, build-essential is a meta-package which makes sure that the different components, like g++ get installed by depending on them. You still have to have the individual packages.

---

### Post by lloyd_b on 2009-06-09
Assuming you have an install CD available - in a terminal window:```
sudo apt-cd add
(insert CD)
sudo apt-get install build-essential
```Depending on which version you're running, this may not get you the latest and greatest packages, but it should get you a working c++ compiler.

Lloyd B.

---

### Post by nanometer on 2010-07-18
hi
build essential also needs g++ what should i do?
tnx

---

