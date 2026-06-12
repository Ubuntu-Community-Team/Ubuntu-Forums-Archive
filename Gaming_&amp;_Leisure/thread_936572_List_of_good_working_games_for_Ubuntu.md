---
title: "List of good working games for Ubuntu?"
date: 2008-10-02
forum: Gaming &amp; Leisure
---

### Post by askyourpc.com on 2008-10-02
I switched to Ubuntu and would like to know what games are available on Ubuntu Linux. Ones that are somewhat professional. I am a casual gamer. Ones that people have made for linux that are have good quality.

---

### Post by MaxIBoy on 2008-10-02
Alien Arena comes to mind. It's a community developed game, but it's still very slick.

Do not install it from the repos, that version is out of date. Either get the latest version at [http://red.planetarena.org](http://red.planetarena.org). You will get a zip file that you can extract somewhere and just start playing. No need to run an installer. 


Better yet, compile from SVN (which will get you the absolute latest version, and I mean latest as in new versions every week.)

First, install every program that is required for the compiling process to work. You may have some of these installed already; that's no big deal, apt will just skip over those. Copy and paste the following into a console window:
```
sudo apt-get install fakeroot devscripts debhelper dpatch libsdl1.2-dev libglu1-mesa-dev libgl1-mesa-dev libjpeg62-dev libxxf86vm-dev libxxf86dga-dev libxext-dev libx11-dev subversion libcurl build-essential
```
You won't need to install any of those ever again. Ubuntu will take care of updating them for you.


Then, get download the game from the SVN server.
```
mkdir nameOfFolderYouWantToInstallTheGameTo
cd nameOfFolderYouWantToInstallTheGameTo
svn co svn://svn.icculus.org/alienarena/trunk .
``` The period at the end of that last line is important!

Finally, build the game from source.
```
cd source
make
make install
```


Afterwords, to update the game, do this:
```
cd nameOfFolderYouInstalledTheGameTo
svn co svn://svn.icculus.org/alienarena/trunk .
cd source
make clean
make
make install
```



It's easier than it looks.

---

### Post by davidryder on 2008-10-02
[5 Best OSS RTS Games](http://www.junauza.com/2008/09/5-best-free-and-open-source-real-time.html)
[5 Top Cross-playform FPS Games](http://www.makeuseof.com/tag/top-5-free-cross-platform-fps-games/)
[Top 25 Games for Linux in 2007](http://rangit.com/software/top-8-linux-games-of-2007/)

:D

---

### Post by Bios Element on 2008-10-03
No need to compile Alien Arena from Source. Just get it from [http://www.playdeb.net/](http://www.playdeb.net/) .

---

### Post by compiledkernel on 2008-10-03
Full list here -- [http://gaming.gwos.org](http://gaming.gwos.org)

---

### Post by rossjman1 on 2008-10-03
Wolfenstein: Enemy Territory.

---

### Post by MaxIBoy on 2008-10-03
> **Bios Element said:**
> No need to compile Alien Arena from Source. Just get it from [http://www.playdeb.net/](http://www.playdeb.net/) .

Will that get you SVN commits as soon as they happen?


The latest STABLE release can be downloaded as a zip archive, extracted, and run, no installer or anything.

---

### Post by Hyside on 2008-10-04
Nexuiz has a large amount of Linux gamers playing it. 
Its based on the Darkplaces Engine, and it runs on Windows, Mac, and Linux.

---

### Post by sc0tt10 on 2008-10-04
I strongly suggest Astromenace, its an open source 3D Space shooter that is highly addictive, easy to install (just get a .deb package) and has a great single player mode.

---

### Post by mhh91 on 2008-10-04
which of those games has the best graphics?

---

### Post by xakh on 2008-10-04
While this is objective, I'd say Nexuiz does, it's my personal favorite.

---

### Post by rick08 on 2008-10-07
I really like open arena and if you are looking for something more simple check out super tux 1 & 2.  Open arena is an fps that does not have amazing graphics like UT3, but it still looks pretty good and there are a good amount of people playing online.  Super tux is a super mario-like 2D side-scroller that is pretty good and addictive.  Both of these can be found in the repositories, but the open arena is an old version.  I forgot to mention that you can import models into open arena which gives you more possibilities, such as Mario vs. Sonic.  Here is a good website to find OA models, sounds, weapons and more [http://ioquake3.org/extras/models/](http://ioquake3.org/extras/models/)

---

### Post by MaxIBoy on 2008-10-07
> **mhh91 said:**
> which of those games has the best graphics?

Um... 
Alien Arena is pretty darn good.

There are some good screenshots here: 
[http://corent.proboards42.com/index.cgi?board=aatech&action=display&thread=3053&page=1#30292](http://corent.proboards42.com/index.cgi?board=aatech&action=display&thread=3053&page=1#30292)
Some slightly more out-of-date ones here:
[http://en.wikipedia.org/wiki/CodeRED:_Alien_Arena#Screenshots](http://en.wikipedia.org/wiki/CodeRED:_Alien_Arena#Screenshots)
Some recent screenshots with the settings turned down a little:
[http://corent.proboards42.com/index.cgi?board=mapping&action=display&thread=3153&page=1#31191](http://corent.proboards42.com/index.cgi?board=mapping&action=display&thread=3153&page=1#31191)
Out-of-date screenshots with my personal settings, compare to someone else's (more typical) settings:
[http://corent.proboards42.com/index.cgi?board=configs&action=display&thread=3028](http://corent.proboards42.com/index.cgi?board=configs&action=display&thread=3028)

---

### Post by MaxIBoy on 2008-10-07
I think the OP was asking for native games, but WINE is still very cool.

---

