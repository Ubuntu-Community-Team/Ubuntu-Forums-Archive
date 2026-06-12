---
title: "Stones of the Gods(Match-3 Game)"
date: 2008-05-06
forum: Gaming &amp; Leisure
---

### Post by -=Andru=- on 2008-05-06
Stones of the Gods - it's match-3 game, created by me :) The objective of the game is to line up a row of minimum 3 crystals of the same type. Placement is performed by clicking on white circles amid the crystals. When the combination is hit, a jug with magic water is replenished being a time counter. Transit to the next level follows when the jug is full.

screenshots:
[[img]http://andru.2x4.ru/games/sotg/screen01s.jpg[/img]](http://andru.2x4.ru/games/sotg/screen01.jpg) [[img]http://andru.2x4.ru/games/sotg/screen02s.jpg[/img]](http://andru.2x4.ru/games/sotg/screen02.jpg)

[download deb-package(i386, 5.4Mb)](http://andru.2x4.ru/games/sotg/sotg-1.0_i386.deb)
[download bin/src with install/uninstall scripts(4.6Mb)](http://andru.2x4.ru/games/sotg/sotg.tar.bz2)

Game required a OpenGL driver and OpenAL lib's
PS: if you have some problems, please attach to your message log-file(from $HOME/.sotg/log.txt)
PSS: sorry for my bad English :)

---

### Post by Perfect Storm on 2008-05-07
Looks nice :KS
Going try it out.

---

### Post by -=Andru=- on 2008-05-07
>>Ubuntu 64-bit User
mmm... I don't test it on 64-bit.

---

### Post by Perfect Storm on 2008-05-07
No, problem. I see what I can do with it.

Any homepage for it yet?

EDIT:
```
[size=1]	linux-gate.so.1 =>  (0xffffe000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf7f84000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7ec1000)
	libc.so.6 => /lib32/libc.so.6 (0xf7d71000)
	/lib/ld-linux.so.2 (0xf7fa6000)
	libm.so.6 => /lib32/libm.so.6 (0xf7d4c000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf7d34000)
[/size]
```
Shouldn't be a problem as long as ia32-libs are installed.

What is the ZenGL.so.0.017 lib for? This could be a problem if it installs under /usr/lib instead of /usr/lib32, but I could move it it, in the case.

---

### Post by MaindotC on 2008-05-07
Dude you're Ubuntu Game list is unbelievable!

---

### Post by -=Andru=- on 2008-05-07
> Any homepage for it yet?
No, only simple page on my [homepage(rus)](http://andru.2x4.ru/games/sotg.html)

---

### Post by Perfect Storm on 2008-05-07
> **-=Andru=- said:**
> No, only simple page on my [homepage(rus)](http://andru.2x4.ru/games/sotg.html)

ok, :)
Which license is the game under?


[quote=strAlan]Dude you're Ubuntu Game list is unbelievable! [/quote]

Thanks :KS

---

### Post by Cresho on 2008-05-07
ohh my god!  This is one of the nicer games around.  I give this 5 star for a puzzle game.  1 star for not being a first person shooter!!!!!!  1 star for not being a stratagy game!!!!!!

5 star game overall for gameplay
5 star for graphics
5 star for sound and music.

---

### Post by -=Andru=- on 2008-05-07
> Which license is the game under?
GPL :) Source code(and binaries with install/uninstall sh-scrips) available [here(4.6Mb)](http://andru.2x4.ru/games/sotg/sotg.tar.bz2)

2**Cresho**
> ohh my god! This is one of the nicer games around. I give this 5 star for a puzzle game. 1 star for not being a first person shooter!!!!!! 1 star for not being a stratagy game!!!!!!
Thanks :)

---

### Post by Perfect Storm on 2008-05-07
ok, I've repackaged the 32-bit .deb (+ dependencies), moved the lib to lib32
It now works on 64-bit, nice game and nice graphic :KS:KS:KS

for 64-bit users: [http://www.filefactory.com/file/ff26e6/](http://www.filefactory.com/file/ff26e6/)

---

### Post by -=Andru=- on 2008-05-07
> What is the ZenGL.so.0.017 lib for?
It's my own not yet completed 2d/3d engine.

---

### Post by Perfect Storm on 2008-05-07
> **-=Andru=- said:**
> It's my own not yet completed 2d/3d engine.

ah, ok. Thanks.

---

### Post by Perfect Storm on 2008-05-07
I've now added your game to our gamelist: [http://gaming.gwos.org/doku.php/games:alphabetical:s:stones_of_the_gods](http://gaming.gwos.org/doku.php/games:alphabetical:s:stones_of_the_gods)

---

### Post by -=Andru=- on 2008-05-07
> I've now added your game to our gamelist:...
Thanks, but I think better to give direct link on deb-i386, because Russian language know not all :) And also I can host Ubuntu 64-bit package on my homepage(or [www.filefactory.com](www.filefactory.com) have no time limit?)

---

### Post by Perfect Storm on 2008-05-07
> **-=Andru=- said:**
> Thanks, but I think better to give direct link on deb-i386, because Russian language know not all :) And also I can host Ubuntu 64-bit package on my homepage(or [www.filefactory.com](www.filefactory.com) have no time limit?)

ok, that's good. Feel free to host the 64-bit. Then I'll make direct link to the packages ^_^

---

### Post by -=Andru=- on 2008-05-07
I've build amd64 package(and test it on Ubuntu 7.04 64-bit) with dependencies to libopenal0a, ia32-libs and lib32asound2(also move ZenGL.so to lib32), now it can be found at:
[http://andru.2x4.ru/games/sotg/sotg-1.0_amd64.deb](http://andru.2x4.ru/games/sotg/sotg-1.0_amd64.deb)

---

### Post by Perfect Storm on 2008-05-08
ok, both added with direct link.

---

### Post by Lizzy on 2009-03-29
Thanks for the link, i stumbled upon that game while looking for another, i installed it and i love it, that is appart from one problem, whenever i click on the stones to rotate them the screen starts to "blink/flicker". Is there a way to stop it, it hurts my eyes!? Another thing is when you exit the game at level 3 nothing is saved and one has to start at level one again next time you start the game. Apart from that = GREAT GAME :popcorn:

---

### Post by Lizzy on 2009-03-29
Never mind. I figured it out. The screen only flickers when you don't play the game as full screen. But saving the last game would be nice plus a pause button for those who don't know that pressing "P" will pause the game :). Cheers

---

### Post by DoubleClicker on 2010-08-01
the original page for this program is gone.  is there somewhere I can get the source code?

---

### Post by alexandrius on 2011-01-06
Is this game available anywhere else, cause all of the links are dead as Dracula?

---

### Post by alexandrius on 2011-01-06
Ok, i've found :)
[http://andru-kun.inf.ua/games.html](http://andru-kun.inf.ua/games.html)

---

### Post by Rytron on 2011-02-18
> **alexandrius said:**
> Ok, i've found :)
[http://andru-kun.inf.ua/games.html](http://andru-kun.inf.ua/games.html)

Thanks for the link alexandrius.

---

