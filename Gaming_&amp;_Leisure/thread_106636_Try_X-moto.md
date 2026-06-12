---
title: "Try X-moto"
date: 2005-12-21
forum: Gaming &amp; Leisure
---

### Post by kairu0 on 2005-12-21
I just found a gem in the Linux Game Tome: X-Moto.

It is a simple, 2d platform game that is highly addictive and doesn't require any special/good hardware.

Here is the site: [http://xmoto.sourceforge.net/](http://xmoto.sourceforge.net/)

Compiling requires libsdl1.2-dev, sdl mixer, and a few miscellaneous other libraries.

---

### Post by NunoCorreia on 2005-12-23
It compiled correctly (after some pains to get libsdl_mixer working, I had to compile it myself and couldn't find it anywhere) but it bombs out to Gnome when I start playing it... a precompiled .deb would be good.

Edit: This was a month ago... the source must've been altered incorrectly, because I just did it all again and it worked flawlessly :)

---

### Post by kidcharles on 2005-12-27
Yeah, X-moto is a blast. I've been teaching myself C++ and SDL making very simple games lately, and I play it when I need a break. It's actually very hard, but once you learn some tricks, it's a really fun game to play.

---

### Post by Griff on 2005-12-27
Is...is that Elastomania?  If it is...and I can play it on my linux box... :razz:.

---

### Post by Griff on 2005-12-28
So, I'm getting an error during the 'make install':

stephen@ubuntu:~/downloads/Games/xmoto-0.1.10$ sudo make install
Password:
Making install in bin
make[1]: Entering directory `/home/stephen/downloads/Games/xmoto-0.1.10/bin'
make[2]: Entering directory `/home/stephen/downloads/Games/xmoto-0.1.10/bin'
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ../mkinstalldirs /usr/local/share/xmoto
mkdir -p -- /usr/local/share/xmoto
 /usr/bin/install -c -m 644 anims.dat /usr/local/share/xmoto/anims.dat
 /usr/bin/install -c -m 644 sprites.dat /usr/local/share/xmoto/sprites.dat
 /usr/bin/install -c -m 644 editor.dat /usr/local/share/xmoto/editor.dat
 /usr/bin/install -c -m 644 fonts.dat /usr/local/share/xmoto/fonts.dat
 /usr/bin/install -c -m 644 xmoto.bin /usr/local/share/xmoto/xmoto.bin
make[2]: Leaving directory `/home/stephen/downloads/Games/xmoto-0.1.10/bin'
make[1]: Leaving directory `/home/stephen/downloads/Games/xmoto-0.1.10/bin'
make[1]: Entering directory `/home/stephen/downloads/Games/xmoto-0.1.10'
make[2]: Entering directory `/home/stephen/downloads/Games/xmoto-0.1.10'
/bin/sh ./mkinstalldirs /usr/local/bin
  /usr/bin/install -c xmoto /usr/local/bin/xmoto
  /usr/bin/install -c xmoto-edit /usr/local/bin/xmoto-edit
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stephen/downloads/Games/xmoto-0.1.10'
make[1]: Leaving directory `/home/stephen/downloads/Games/xmoto-0.1.10'

Anyone see the problem here?

---

### Post by Imexius on 2005-12-28
Heh, yeah it looks alot like elastomania, ill give it a try :cool:

---

### Post by NunoCorreia on 2005-12-28
[QUOTE=Griff]So, I'm getting an error during the 'make install':

stephen@ubuntu:~/downloads/Games/xmoto-0.1.10$ sudo make install
Password:
Making install in bin
make[1]: Entering directory `/home/stephen/downloads/Games/xmoto-0.1.10/bin'
(...)
make[2]: Entering directory `/home/stephen/downloads/Games/xmoto-0.1.10'
/bin/sh ./mkinstalldirs /usr/local/bin
  /usr/bin/install -c xmoto /usr/local/bin/xmoto
  /usr/bin/install -c xmoto-edit /usr/local/bin/xmoto-edit
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stephen/downloads/Games/xmoto-0.1.10'
make[1]: Leaving directory `/home/stephen/downloads/Games/xmoto-0.1.10'

Anyone see the problem here?[/QUOTE]
Uh... there was no error there! Won't running 'xmoto' work?

BTW, it might look like Elastomania but it handles quite differently. The "rider" feels much stiffer, for example.

---

### Post by Griff on 2005-12-28
[QUOTE=NunoCorreia]Uh... there was no error there! Won't running 'xmoto' work?
[/QUOTE]
*Yes. it does work.*  ;)   And btw, Grey Goose + terminal = bad idea. lol.  I thought I put xmoto in the terminal; guess I didn't.  I feel like such an a--.  Thanks for the response, though.

---

### Post by kairu0 on 2006-01-01
How far have those of you who have tried X-moto gotten? I'm working on Level 16.

---

### Post by Gustav on 2006-01-02
Argh, it's harder than I remember that elastomania were, or maybe I haven't played it enough yet :).

---

### Post by Jacky_J on 2006-02-07
[QUOTE=kairu0]How far have those of you who have tried X-moto gotten? I'm working on Level 16.[/QUOTE]

I beat all the levels for version 0.1.10 (which had 31 + 3 tutorial levels).  It isn't trivial.
I even hold a high score for one of the levels (the high scores list is linked on the homepage)

There's easily 40+ hours of gameplay.  The game is very frustrating and rewarding.  

It looks like 0.1.11 has two new levels, so i better get busy.

---

### Post by kairu0 on 2006-02-11
[QUOTE=Jacky_J]I beat all the levels for version 0.1.10 (which had 31 + 3 tutorial levels).  It isn't trivial.
I even hold a high score for one of the levels (the high scores list is linked on the homepage)[/QUOTE]

That's pretty good! Some of the levels are very taxing, indeed. I can't get passed 18 for the life of me.

---

### Post by Jacky_J on 2006-02-11
Ah yes, how could i forget the beloved Boingo level.  There's so many little parts on that level that you can mess up.  However, when you win it, you'll be as happy as a little boy on christmas.

Seems like someone took my highscore by 0.05 seconds :(

---

### Post by kairu0 on 2006-02-12
It used to bother me. And then I cleared Frozen Bubble and felt like a jaybird on penicillin.

---

### Post by gremlin hunter on 2006-02-13
Dapper has an xmoto package. w00t!

---

