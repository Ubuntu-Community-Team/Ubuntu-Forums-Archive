---
title: "FlightGear 2.6.0 RC with Ubuntu 10.04"
date: 2012-02-17
forum: Gaming &amp; Leisure
---

### Post by CivilizationII on 2012-02-17
A great news, The release candidate of Flightgear 2.6.0 compiles perfectly with Ubuntu 10.04.4.

A lot of enhancement, the final release will be great :D

---

### Post by Dlambert on 2012-02-19
Good to know. lol.

---

### Post by MdMax on 2012-03-09
Hello !

FlightGear 2.6.0.1 is now available:
[http://www.flightgear.org/](http://www.flightgear.org/)

I'm using the [Git version](http://wiki.flightgear.org/Scripted_Compilation_on_Linux_Debian/Ubuntu) with Precise Pangolin (12.04), but I noticed the default package is still 2.4.0:
[https://launchpad.net/ubuntu/precise/+source/flightgear/](https://launchpad.net/ubuntu/precise/+source/flightgear/)

Happy flying ! ):P

---

### Post by BJCV86 on 2012-03-09
Ya, that's nice. I have 11.10 and I can't install the latest version. I'm sad now. Alot sad. I can't install the 2.4 either. How do I do it. I followed directions elsewhere but I get, cannot find file from some thing called a terminal. and I have a fancy video card and it works good and I just baught more ram to play x-plane cuz it installs properly, but if I can avoid 80-90$ I will try. how do I make 2.6 work on 11.10? or even 2.4 would be nicer. or 2.0 with more planes but it won't let me add more files to the folder cuz it restricts me access.

---

### Post by TejasMChavan on 2012-03-10
> **BJCV86 said:**
> Ya, that's nice. I have 11.10 and I can't install the latest version. I'm sad now. Alot sad. I can't install the 2.4 either. How do I do it. I followed directions elsewhere but I get, cannot find file from some thing called a terminal. and I have a fancy video card and it works good and I just baught more ram to play x-plane cuz it installs properly, but if I can avoid 80-90$ I will try. how do I make 2.6 work on 11.10? or even 2.4 would be nicer. or 2.0 with more planes but it won't let me add more files to the folder cuz it restricts me access.

[http://pkgs.org/ubuntu-11.10/getdeb-games-i386/flightgear_2.6.0-1~getdeb1_i386.deb.html](http://pkgs.org/ubuntu-11.10/getdeb-games-i386/flightgear_2.6.0-1~getdeb1_i386.deb.html)

I am following this instructions on site above. I am downloading right now and its around 46% done. Even I am using 11.10.
Hope it works..!! :)

---

### Post by BJCV86 on 2012-03-10
> **TejasMChavan said:**
> [http://pkgs.org/ubuntu-11.10/getdeb-games-i386/flightgear_2.6.0-1~getdeb1_i386.deb.html]("http://pkgs.org/ubuntu-11.10/getdeb-games-i386/flightgear_2.6.0-1%7Egetdeb1_i386.deb.html")

I am following this instructions on site above. I am downloading right now and its around 46% done. Even I am using 11.10.
Hope it works..!! :)

I do not understand how a 3MB file can hold 800MB

**lightgear - Flight Gear Flight Simulator.**  Flight Gear is a free and highly sophisticated flight simulator.
 This package contains the runtime binaries.
 
[LIST]
[*]**Repository**: GetDeb Games for Ubuntu 11.10
[*]**Download size**: 3,12 MB
[*]**Installed size**: 7,71 MB
[*]**Package filename**: flightgear_2.6.0-1~getdeb1_i386.deb
[*]**Source package**: flightgear
[/LIST]


It is just when I am doing terminal I do not want to add unnecessary files and or damage my HDD. PLUS! I cannot install in some directories because I am not "ROOT"
This has got to get under control for myself. I have zero idea what it is saying. 



 
[LIST=1]
[*]Install the repository GPG key: # wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
[*]Add the following line to /etc/apt/sources.list: deb [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) oneiric-getdeb games
[*]Update the package index: # sudo apt-get update
[*]Install flightgear deb package: # sudo apt-get install flightgear
[/LIST]


So if I type in number one to the temrinal, it will go smoothy? But I have to download the 3MB file first?
Why do they confuse my eyes and say I need these files

[LIST]
[*][fgfs-base (>= 2.6.0)]("http://pkgs.org/download/fgfs-base")
[*][freeglut3]("http://pkgs.org/download/freeglut3")
[*][libc6 (>= 2.4)]("http://pkgs.org/download/libc6")
[*][libgcc1 (>= 1:4.1.1)]("http://pkgs.org/download/libgcc1")
[*][libgl1-mesa-glx | libgl1]("http://pkgs.org/download/libgl1-mesa-glx")
[*][libglu1-mesa | libglu1]("http://pkgs.org/download/libglu1-mesa")
[*][libopenscenegraph80]("http://pkgs.org/download/libopenscenegraph80")
[*][libopenthreads14]("http://pkgs.org/download/libopenthreads14")
[*][libplib1 (>= 1.8.5-1)]("http://pkgs.org/download/libplib1")
[*][libpng12-0 (>= 1.2.13-4)]("http://pkgs.org/download/libpng12-0")
[*][libstdc++6 (>= 4.6)]("http://pkgs.org/download/libstdc++6")
[*][simgear2.6.0 (>= 2.6.0)]("http://pkgs.org/download/simgear2.6.0")
[*][zlib1g (>= 1:1.1.4)]("http://pkgs.org/download/zlib1g")
[/LIST]
   **Files**

 
[LIST]
[*]/usr/games/alcinfo
[*]/usr/games/est-epsilon
[*]/usr/games/fgfs
[*]/usr/games/fgjs
[*]/usr/games/fgviewer
[*]/usr/games/gl-info
[*]/usr/games/js_demo
[*]/usr/games/metar
[*]/usr/games/terrasync
[*]/usr/games/yasim
[*]/usr/share/applications/flightgear.desktop
[*]/usr/share/doc/flightgear/AUTHORS
[*]/usr/share/doc/flightgear/AptNavFAQ.FlightGear.html
[*]/usr/share/doc/flightgear/FlightGear-FAQ.html
[*]/usr/share/doc/flightgear/NEWS.gz
[*]/usr/share/doc/flightgear/Nasal.html
[*]/usr/share/doc/flightgear/README
[*]/usr/share/doc/flightgear/README.Cygwin
[*]/usr/share/doc/flightgear/README.Debian
[*]/usr/share/doc/flightgear/README.IO.gz
[*]/usr/share/doc/flightgear/README.IRIX
[*]/usr/share/doc/flightgear/README.JSBSim
[*]/usr/share/doc/flightgear/README.Joystick
[/LIST]
Am I to individually put these files? WHAT IN THE HECK ARE ALL OF THESE?!?!?!?!?! AND WHY ARE THEY BELOW THE SUDO STUFF.
Can someone enlighten me to what the FRICK THESE ARE. They say free. I'm becoming sad and brain dead trying to learn this.
 If someone can get this Step ABC like a baby for me. I will tip my hat off to you.

---

### Post by BJCV86 on 2012-03-10
Wrong button: EDIT

---

### Post by TejasMChavan on 2012-03-11
ok.. Those files you see are dependencies... meaning to run the game, you need those files which you may have not installed by default.

To get root priveleges you put sudo

Regarding installation, you need not place them youself, Software center will do by itself.

---

