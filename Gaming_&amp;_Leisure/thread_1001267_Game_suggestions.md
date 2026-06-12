---
title: "Game suggestions"
date: 2008-12-03
forum: Gaming &amp; Leisure
---

### Post by maddog46113 on 2008-12-03
I have been a Ubuntu user for a little over a year now, However I've neglected signing up on the forums so i figured it was time to appear and finally become part of the community.

If at all possible can you guys suggest some decent games that will run on my system

--Intel 2.4ghz Pentium 4 overclocked to 2.7 
--2 gb 800 mhz RAM
--580 gb storage
--Radeon 9200 256mb 

My system is a bit out of date due to cash issues :( 

All your input is much appreciated. Have fun! :D

---

### Post by magmon on 2008-12-03
You could try saurbraten, its in the add/remove. Make sure to change the settings so you can see all apps. Im testing a game I used to play on vista called Fate with wine now, Ill tell ya how that works too.

---

### Post by MaxIBoy on 2008-12-03
Alien Arena:
[screenshot](http://icculus.org/alienarena/rpa/mediathumbs/aa2k8_17.jpg)
Alien Arena is the repositories, but that version is often out of date. I recommend checking out the game from SVN.

```
mkdir directory/you/want/to/install/the/game/in
cd directory/you/just/made
sudo apt-get install fakeroot devscripts debhelper dpatch libsdl1.2-dev libglu1-mesa-dev libgl1-mesa-dev libjpeg62-dev libxxf86vm-dev subversion libxxf86dga-dev libxext-dev libx11-dev libcurl3 libcurl4-gnutls-dev
svn co svn://svn.icculus.org/alienarena/trunk .
cd source
make 
make install
```

To update the game (every week or two,) do this:
```
cd game_directory
svn co svn://svn.icculus.org/alienarena/trunk .
cd source
make clean
make
make install
```

---

### Post by EdThaSlayer on 2008-12-03
Play Urban Terror, it's a bit like counter-strike but more advanced.
Link:[http://www.urbanterror.net/page.php?6](http://www.urbanterror.net/page.php?6)

Don't forget to choose the Linux version!

---

### Post by maddog46113 on 2008-12-03
I have Sauberaten (now) I got off because i kept fragging team mates on accident >.<; I downloaded Assault Cube yesterday, Enemy Territory, Battle for Wesnoth, and Urban Terror ( lots of fun ), and open arena ill try alien arena. Are there any good RPG's with good graphics? or RTS's besides Spring (Spring runs like complete ****) Possibly any games with a storyline?

Thanks much for the alien arena update script xD

---

### Post by maddog46113 on 2008-12-03
Got an error during the make process with alien arena..

make[1]: *** [release/ref_gl/r_model.o] Error 1
make[1]: Leaving directory `/home/aaron/AlienArena/source'
make: *** [build-release] Error 2

---

### Post by EdThaSlayer on 2008-12-03
> **maddog46113 said:**
> Got an error during the make process with alien arena..

make[1]: *** [release/ref_gl/r_model.o] Error 1
make[1]: Leaving directory `/home/aaron/AlienArena/source'
make: *** [build-release] Error 2

I don't know why you are building it from source.
Just do a > sudo apt-cache search alien-arena and this should appear
```
alien-arena - Standalone 3D first person online deathmatch shooter
alien-arena-browser - stand alone server browser for Alien Arena
alien-arena-data - Game data files for Alien Arena
alien-arena-server - Dedicated server for Alien Arena

```

Just a sudo apt-get will get you the game.:p

---

### Post by maddog46113 on 2008-12-03
> **EdThaSlayer said:**
> I don't know why you are building it from source.
Just do a  and this should appear
```
alien-arena - Standalone 3D first person online deathmatch shooter
alien-arena-browser - stand alone server browser for Alien Arena
alien-arena-data - Game data files for Alien Arena
alien-arena-server - Dedicated server for Alien Arena

```

Just a sudo apt-get will get you the game.:p

Got it, but it runs awfully laggy on my video card. :(

---

### Post by Perfect Storm on 2008-12-04
Any genre you like most?

---

### Post by maddog46113 on 2008-12-04
> **Artificial Intelligence said:**
> Any genre you like most?

Not particularly but ever since I made the leap to linux ive been pretty much stuck to FPS's and a few games I have that run through Cedega or Wine. 

Ive been in kinda an RPG mood lately.

---

### Post by gabril on 2008-12-04
fretsonfire is a great guitarrhero like game! 
and have you considered UT2004 at all? If no do so! Awsome game!:D 

for fretts on fire (written in python) just type!

$sudo aptitiude install fretsonfire

and there you go... lots of dependecys thats a bi**h fixing on your own... may recomend apting the source...makes difference!:D With all games... have a correct kernel!:D as allways...

---

### Post by Perfect Storm on 2008-12-04
> **maddog46113 said:**
> Not particularly but ever since I made the leap to linux ive been pretty much stuck to FPS's and a few games I have that run through Cedega or Wine. 

Ive been in kinda an RPG mood lately.

If you don't mind paying a little buck, I can recommend;

[Eschalon: Book I](http://gaming.gwos.org/doku.php/games:alphabetical:e:eschalon_book_i)
[NWN](http://gaming.gwos.org/doku.php/games:alphabetical:n:neverwinter_nights)

and [Sacred: Gold Edition](http://gaming.gwos.org/doku.php/games:alphabetical:s:sacred_gold_edition) is comming for linux if you like hack'n'slash diablo style. But that is not real RPG if you ask me.

---

### Post by sorrytonny on 2008-12-04
):Ptry runescape.you can buy a decent account in Vgoldseller.com.
the price is reasonable and they deliver it really fast.have fun;)

---

### Post by maddog46113 on 2008-12-04
> **Artificial Intelligence said:**
> If you don't mind paying a little buck, I can recommend;

[Eschalon: Book I](http://gaming.gwos.org/doku.php/games:alphabetical:e:eschalon_book_i)
[NWN](http://gaming.gwos.org/doku.php/games:alphabetical:n:neverwinter_nights)

and [Sacred: Gold Edition](http://gaming.gwos.org/doku.php/games:alphabetical:s:sacred_gold_edition) is comming for linux if you like hack'n'slash diablo style. But that is not real RPG if you ask me.

I enjoyed Diablo a long time ago. Was great on my old 500 mhz AMD K-6 lol

---

