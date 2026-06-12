---
title: "Good games from Ubuntu Software Center"
date: 2013-03-16
forum: Gaming &amp; Leisure
---

### Post by ViliX64 on 2013-03-16
Hi, I would like to play some FREE games and I think, the easiest way is Ubuntu Software Center. 
So are there any games? (except Battle for Wesnoth, AssaultCube, Glest, Tux Racer, Xmoto and Sauerbraten)

NOTE1: I don't mind link for game that is not in ubuntu software center, but keep on mind, that I have Xubuntu, which can run mostly .deb packages
NOTE2: Please don't send me links for website with tons of games, I'm asking for personal opinion..
NOTE3: Those games listed in brackets are just awesome!

---

### Post by myromance123 on 2013-03-16
Here's a snazzy 3D horror game that's FREE, but it's not in the USC.
**_One Late Night:_** [Link1]("http://www.desura.com/games/one-late-night")  [Link2]("http://www.moddb.com/games/one-late-night/downloads")

I've played it in Ubuntu 12.10, so it should work just fine in Xubuntu. It scares the bejabbers out of me!
I even have a video where I play it a bit, if you're interested in seeing it in action :)
[Youtube link]("https://www.youtube.com/watch?v=Q_xCZvbNzGc")

There's also Matter, a 3D first-person puzzle solving game. It's an executable, so you right click it -> Properties -> Permissions -> Tick allow executing. Double click it to run it.
**_Matter:_** [Link]("http://mattergame.webs.com/") [Link2]("http://scrawl.bplaced.net/matter/Matter_Linux.tar.xz")

I've played it and recorded it as well :P
[Youtube Link]("https://www.youtube.com/watch?v=YRii7ceLysA")

There's also BattleMass, which only recently became free to play. Not my cup of tea, but you can play against others online. It's a 3D turn-based strategy game.
**_BattleMass:_** [Link]("http://www.desura.com/games/battlemass")

---

### Post by ViliX64 on 2013-03-16
OH GOD!!
Thank you myromance123.. I have googled some linux games, but none of them were so nice as one late night and matter.. how is it even possible that is is so hidden on the internet and I have to ask at forum?

---

### Post by ViliX64 on 2013-03-16
Could you please help me with Matter?
I have downloaded archive tar.gz and extracted it and ran matter file (like a program) but nothing happened..

---

### Post by myromance123 on 2013-03-16
Glad you like the games :)

Alright, have you made sure to set it's permissions?

You need to right click it and go to Properties. Then go to the Permissions tab, and Tick "Allow executing file as a program".

I'm not sure how much the wording might differ, but that should be the gist of it. Now double click it and it should run.

If it doesn't, we can always test it via Terminal. Open any Terminal, and type in this:
```
./
```

Now just drag the executable into there, and hit Enter. Let me know what the errors might be. Also, would you kindly let me know what your graphics card is and maybe what driver you are using?
[B][U]
EDIT: [/U][/B] I apologize, I forgot that Matter needs to be run through the terminal. Why this is the case, I am unsure. It probably has to do with Ogre3D.

So, I'll run you through the basic steps.

1. Open a Terminal.
2. CD to the folder of Matter. E.g:
```
cd '/home/ismail/Desktop/Matter_Linux'
```
3. Run the game using ./ E.g:
```
./matter
```

Instead of typing the entire CD command, just type CD and then drag the Matter folder into the Terminal. It will automatically give you the folder directory in text like the above example.

I hope this helps a bit :)

---

### Post by ViliX64 on 2013-03-16
Yes, I have allowed that and running it from Terminal does not seems to work as well :(

---

### Post by myromance123 on 2013-03-16
That's very peculiar. Just to get the basics out of the way, what graphics card and drivers are you using?

It doesn't return any errors in the Terminal either?

---

### Post by JLeon85 on 2013-03-16
My favorite game from the software center is Freeciv. 

Most of the games available through the Chrome webstore run just fine on Ubuntu, so you may find that a good source of free games.

---

### Post by ViliX64 on 2013-03-16
I have integrated graphic processor in intel pentium P987 1.5GHz.. (I have netbook)
Result of ./matter
```
/home/vilem/Downloads/Matter_Linux/data/bin/64/matter: error while loading shared libraries: libmng.so.1: cannot open shared object file: No such file or directory
```

---

### Post by myromance123 on 2013-03-16
> **ViliX64 said:**
> I have integrated graphic processor in intel pentium P987 1.5GHz.. (I have netbook)

I'm sorry to say, you might not be able to get the games working :/
I have a netbook with an Intel GMA945, and I can't play these games on it. Hopefully in the future we will be able to but the drivers aren't up to par just yet. The upcoming 13.04 releases hopefully will give us better drivers, but we'll have to wait a while. I'm sorry man.

---

### Post by ViliX64 on 2013-03-16
That is a shame, hopefully Desura will give me better experience..

---

### Post by myromance123 on 2013-03-16
This might help with Matter, but I'm not sure.

```
sudo apt-get install libmng1
```

This might help you fix the dependency that's missing.

---

### Post by ViliX64 on 2013-03-16
:( that is really shame.. because I think, linux best fit on netbooks and notebooks and a lot of them are using intel integreted graphic adapter..

---

### Post by ViliX64 on 2013-03-16
actually matter worked!

---

### Post by myromance123 on 2013-03-16
> **ViliX64 said:**
> actually matter worked!

Hahahaha, I'm glad it does :)
Happy gaming man, I think you might be able to get BattleMass working as well.

One Late Night probably not. It's very heavy on graphics.

---

### Post by ViliX64 on 2013-03-16
Well Matter will keep me busy for a few days for now.. that is what matters me :D

---

### Post by neruson on 2013-03-16
Limbo. It's a beautiful puzzle platformer. It only runs on Linux through Wine and I've heard mixed things about it's performance on it. I'm not terribly sure though. I bought it off of Steam over a year ago for PC, and I refuse to buy the same game twice. If it's true and you dual boot you might be better off buying it for Windows.

[http://limbogame.org/](http://limbogame.org/)

---

### Post by ViliX64 on 2013-03-17
That's why I asked for games from Ubuntu Software Center or from external links, I want to play games on linux and for free..

---

### Post by istealth shadow on 2013-03-17
download supertux its a really good platformer a spinoff of super mario

[http://supertux.lethargik.org/](http://supertux.lethargik.org/)

that is the official website.

---

### Post by rich4421972 on 2013-03-18
You might want to check out Supertuxkart for your setup. It's very good and a spin-off of the popular Mario Kart console game. 

Additionally, check out the playdeb and getdeb repositories for even more free games. You have to install the repository links by hand or by using the downloadable .deb packages. For 12.10 versions, search  "getdeb V2" and/or "playdeb V2" All of the games are free and the site is maintained by volunteers. Once you have installed the repositories, you can work entirely from the software center app.

---

