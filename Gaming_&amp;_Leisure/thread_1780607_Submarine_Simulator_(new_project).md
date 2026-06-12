---
title: "Submarine Simulator (new project)"
date: 2011-06-12
forum: Gaming &amp; Leisure
---

### Post by thnewguy on 2011-06-12
Hello all. I've been working on a new gaming project in an effort to bring a new submarine simulator to Linux. With a few exceptions, submarine sims are an genre of gaming we don't see much in the open source community and I hope to change that.

My project, OpenSSN, is in its early stages, but I've finally got something to demo for you. Players are able to pilot a submarine, detect nearby ships, fire torpedoes and sink enemies. So far the game just has one mission, but I'm hoping to expand game play soon.

If you'd like to help out, I can use some beta testers. Please check out the project at [http://openssn.sf.net](http://openssn.sf.net) and feel free to send in any suggestions.

---

### Post by CreativeReach on 2011-06-12
I'd be happy to try it out but the site won't load?

---

### Post by thnewguy on 2011-06-12
Maybe it's just SF being slow to load, it's taking a long time to bring up the site on my machine too. I'm copying/pasting the link here in case I made a typo.

[http://openssn.sourceforge.net/](http://openssn.sourceforge.net/)

---

### Post by CreativeReach on 2011-06-12
LOL, nothing on SF loads, maybe there a server problem.
I recommend posting it somewhere else

---

### Post by thnewguy on 2011-06-13
I'm not having any problem accessing SF. But since it's not working for you, I've published the latest OpenSSN via Ubuntu One:
[http://ubuntuone.com/p/z2Y/](http://ubuntuone.com/p/z2Y/)

---

### Post by cgroza on 2011-06-13
Nice interface, and all that is done with SDL? Cool.
I will take a look at the source code...

---

### Post by NM5TF on 2011-06-14
I must be doing something wrong, or not have all required files.
Here is a list of messages I get when trying to compile; I do have
GCC installed.

tommy@tommy-desktop:~$ tar zxf openssn-0.4.tar.gz
tommy@tommy-desktop:~$ cd openssn/src
tommy@tommy-desktop:~/openssn/src$ make
g++ -g -Wall `sdl-config --cflags` -Wno-write-strings  -c radar.cpp
radar.cpp:28:26: error: SDL_rotozoom.h: No such file or directory
radar.cpp: In member function ‘void Radar::DisplaySweep()’:
radar.cpp:767: error: ‘rotozoomSurface’ was not declared in this scope
make: *** [radar.o] Error 1
tommy@tommy-desktop:~/openssn/src$ 

here is ls of openssn

tommy@tommy-desktop:~/openssn$ ls
CHANGELOG  data    LICENSE     manual.pdf  ships  TODO
CREDITS    images  manual.odt  README      src

when I type ./openssn I get error message saying 

bash: ./openssn: No such file or directory

I am hardware guy, not software guy...what have I done wrong???:(

---

### Post by realzippy on 2011-06-14
> **NM5TF said:**
> I must be doing something wrong, or not have all required files.
Here is a list of messages I get when trying to compile; I do have
GCC installed.

tommy@tommy-desktop:~$ tar zxf openssn-0.4.tar.gz
tommy@tommy-desktop:~$ cd openssn/src
tommy@tommy-desktop:~/openssn/src$ make
g++ -g -Wall `sdl-config --cflags` -Wno-write-strings  -c radar.cpp
radar.cpp:28:26: error: SDL_rotozoom.h: No such file or directory
radar.cpp: In member function ‘void Radar::DisplaySweep()’:
radar.cpp:767: error: ‘rotozoomSurface’ was not declared in this scope
make: *** [radar.o] Error 1
tommy@tommy-desktop:~/openssn/src$ 

here is ls of openssn

tommy@tommy-desktop:~/openssn$ ls
CHANGELOG  data    LICENSE     manual.pdf  ships  TODO
CREDITS    images  manual.odt  README      src

when I type ./openssn I get error message saying 

bash: ./openssn: No such file or directory

I am hardware guy, not software guy...what have I done wrong???:(

Run

```
sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev
```

and try again.Here it works on a nearly vanilla system (11.04)

To start game (something is wrong with the openssn executive):
```

cd ./openssn && ./openssn
```

---

### Post by NM5TF on 2011-06-14
still doesn't work...here is latest:

tommy@tommy-desktop:~$ sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev
[sudo] password for tommy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl1.2-dev is already the newest version.
libsdl-image1.2-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  python-gtkmozembed
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tommy@tommy-desktop:~$ cd ./openssn && ./openssn
bash: ./openssn: No such file or directory
tommy@tommy-desktop:~/openssn$ 


frustrating.....kind of like trying to run DangerDeep

---

### Post by thnewguy on 2011-06-14
It looks like you are missing one of the SDL libraries. You'll need SDL_gfx, SDL and SDL_image. Try running

sudo apt-get install libsdl-gfx1.2-dev

make
cd ..
./openssn

---

### Post by NM5TF on 2011-06-14
> **thnewguy said:**
> It looks like you are missing one of the SDL libraries. You'll need SDL_gfx, SDL and SDL_image. Try running

sudo apt-get install libsdl-gfx1.2-dev

make
cd ..
./openssn

loading the SDL library above fixed the error message I was getting...


congrats thnewguy for a great looking game...will get back to you if
I have any more problems...

---

### Post by thnewguy on 2011-06-26
Hi all, I've just released an update to OpenSSN ([http://openssn.sf.net](http://openssn.sf.net)). The game now features two combat missions, the torpedoes work better and the sonar display is much nicer. Some nasty bugs that would cause crashes have been fixed. Things are shaping up nicely and I'm looking forward to adding more ships, subs and missions soon.

---

### Post by Dlambert on 2011-06-28
Looks promising, hopefully you can keep working on it unlike the Danger from the Deep crew.

Is it going to be 3D?

---

### Post by thnewguy on 2011-06-28
At the moment I don't have any plans for 3-D. Partly because there's a lot to do before I can get to that point, partly because my art skills are so poor and partly because I want to keep the system requirements as low as possible.

This last point, video drivers, is something I see causing problems with other games and I want to avoid the crashes which come from bad video drivers or low-end cards.

Something I'm considering is including a "periscope view" which would allow players to check out ships on the surface. If someone steps forward to draw ships, we'll probably see them rendered in 2.5-D.

---

### Post by thnewguy on 2011-07-09
I've got a new release up on the site. Version 0.6 fixes a bunch of issues, improves the install process and features three missions. The source is available at [http://openssn.sf.net](http://openssn.sf.net)

---

### Post by thnewguy on 2011-08-15
I'm happy to report I've released OpenSSN 0.7. This version includes some important fixes, fixes the X11 disconnect problem and improves the sonar display. Sound support and a few effects have been added. The AI is improved, torpedoes work better and there's a new mission which pits the player and a friendly sub against four destroyers. Active sonar has been added too.
[http://openssn.sf.net](http://openssn.sf.net)

Let me know what you think.

If you're compiling from source, the sound support requires the SDL and SDL_mixer libraries be installed.

---

