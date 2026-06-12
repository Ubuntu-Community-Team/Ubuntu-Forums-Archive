---
title: "Red Eclipse 1.0: Ides Edition"
date: 2011-03-15
forum: Gaming &amp; Leisure
---

### Post by Arand on 2011-03-15
[[IMG]http://img858.imageshack.us/img858/3105/redeclipseregular.png[/IMG]]("http://www.redeclipse.net/")
A single-player and multi-player first-person ego-shooter, built as a total conversion of Cube Engine 2, which lends itself toward a balanced gameplay, with a general theme of agility in a variety of environments.

[[IMG]http://img196.imageshack.us/img196/6375/90164402.jpg[/IMG]]("http://www.redeclipse.net/")
[[COLOR=DarkBlue]www.redeclipse.net[/COLOR]]("http://www.redeclipse.net/")

The main RE forum are at [[COLOR=DarkBlue]http://forum.freegamedev.net/viewforum.php?f=53[/COLOR]]("http://forum.freegamedev.net/viewforum.php?f=53")

[**[COLOR=DarkBlue]Static Binary tarballs[/COLOR]**]("http://redeclipse.net/download") available for 32/64bit linux (and win/osx/bsd).

Debian/Ubuntu packages for 1.0 are available from [**[COLOR=DarkBlue]playdeb.net[/COLOR]**]("http://www.playdeb.net/software/Red%20Eclipse")

Debian/Ubuntu packages for 1.0 Ides and tracking SVN are also available from my [[COLOR=DarkBlue]**PPA**[/COLOR]]("https://launchpad.net/%7Earand/+archive/redeclipse").
PPA package names are "redeclipse-svn" (currently including "redeclipse" transitional dummy packages) and redeclipse-ides for 1.0.
Do bug me, and not developers if something goes wrong with these PPA packages =).

- arand

---

### Post by pieman711 on 2011-03-15
Looks good! Is the first person mode like a campaign mode with missions and plot or is the same as multi-player with AI bots?
I'll download it later and have a go. Do you know roughly how much it space it takes up when installed?

---

### Post by Arand on 2011-03-15
> **pieman711 said:**
> Looks good! Is the first person mode like a campaign mode with missions and plot or is the same as multi-player with AI bots?
I'll download it later and have a go. Do you know roughly how much it space it takes up when installed?There is a "campaign" level, but that part of the game is still very much work-in-progress, it is mainly AI bots for single-player as of now.
Game is  450/400MB, depending if you get the static or debian(PPA) package(s).

- arand

---

### Post by Shazzner on 2011-03-15
Hooray! Downloading now. :)

---

### Post by Arand on 2011-03-17
Game is now up on playdeb.net: [http://www.playdeb.net/software/Red%20Eclipse](http://www.playdeb.net/software/Red%20Eclipse)
* Added link to OP

-arand

---

### Post by bluereg133 on 2011-03-18
Thanks for information about "[B]Red Eclipse 1.0: Ides Edition".:p


[/B]   Kevin

---

### Post by kn0w-b1nary on 2011-03-18
I love this game, glad it's on playdeb, as I've been playing the SVN. Note that it is fairly resource intensive. Even with graphic turned all the way down, AI caused lag, and i have 2.0 gigahertz x64 w/ 1.4 gig of RAM.

---

### Post by Arand on 2011-03-26
PPA is now re-enabled after some kerfuffle regarding whether or not freeware-ish licensed material could go in a PPA, got the final go-ahead from Launchpad staff now though.

- arand

---

### Post by ElSlunko on 2011-03-26
Great game! Just installed and played it for am hour but already liking it.

---

### Post by xXDestroyerGRXx on 2011-03-28
[http://sourceforge.net/apps/mediawiki/redeclipse/index.php?title=Obtain_development_version](http://sourceforge.net/apps/mediawiki/redeclipse/index.php?title=Obtain_development_version)

svn co [https://redeclipse.svn.sourceforge.net/svnroot/redeclipse](https://redeclipse.svn.sourceforge.net/svnroot/redeclipse) RedEclipseSVN

---

### Post by hane on 2011-04-06
[B]Red Eclipse 1.0: Ides Edition is really nice game. I enjoyed it to play. :D





Alex
[/B]

---

### Post by HolgerB on 2011-04-13
I didn't find RedEclipse too CPU-intensive. It scales well in terms of performance. Runs quite nice at low details on my Athlon 2800+ with GeForce 4400 Ti in 1024x768 as well as in full 1080p with all eye candy on my Athlon X2 5200+ with GeForce 9800GT.

Only the single player campaign sometimes slows down. It even happens on my 2.7 GHz Dualcore. May be this is caused by the bots AI ?

I rather use the SVN version than the ppa packages. For this I followed the instructions given here:
[http://www.webupd8.org/2011/01/install-red-eclipse-successor-of-blood.html](http://www.webupd8.org/2011/01/install-red-eclipse-successor-of-blood.html)

I am using a small shell script to grab the latest SVN version and compile it:
```

cd ~/games/redeclipse_svn 
svn co https://redeclipse.svn.sourceforge.net/svnroot/redeclipse .
cd src 
make clean 
make install 
cd .. 

```

Works like a charm but of course at the risk that it screws up your working version if a corrupt version is pulled from the svn server.

---

### Post by Arand on 2011-04-13
> **HolgerB said:**
> (...)
Only the single player campaign sometimes slows down. It even happens on my 2.7 GHz Dualcore. May be this is caused by the bots AI ?
Might be the amount of actors on the map...
The alphacampaign is currently more like a concept more than anything else, it's unfinished, the AI bugs out a lot, etc.

> **HolgerB said:**
> I am using a small shell script to grab the latest SVN version and compile it:
```

cd ~/games/redeclipse_svn 
svn co https://redeclipse.svn.sourceforge.net/svnroot/redeclipse .
cd src 
make clean 
make install 
cd .. 

```

Works like a charm but of course at the risk that it screws up your working version if a corrupt version is pulled from the svn server.
I would say it's probably a better idea to use svn update instead, also, linux binaries are built in the SVN daily, so unless you are very impatient to try the fix that went in 7h ago, it really shouldn't be needed:```
RE_DIR=$HOME/redeclipse-svn
cd $RE_DIR
svn up
```

Impatiently:
```
RE_DIR=$HOME/redeclipse-svn
cd $RE_DIR
make -C src/ clean install-client
```(skipping recompilation of server in this case)

Do note that currently if you run SVN, the impulse mechanics has diverged quite a lot from the 1.0 release, so preferably try to find fellow SVN-players...

- arand

---

### Post by HolgerB on 2011-04-14
Thanks for replying !

> **Arand said:**
> Might be the amount of actors on the map...
The alphacampaign is currently more like a concept more than anything else, it's unfinished, the AI bugs out a lot, etc.

I just mentioned this in regard to the comment of kn0w-b1nary saying RE is CPU-intense.

[QUOTE=Arand]
I would say it's probably a better idea to use svn update instead, also, linux binaries are built in the SVN daily, 
[/QUOTE]
Granted, using svn update after copying works faster and puts less load on the svn server. I should have thought about this. In regard to the PPA build, I prefer the "non-deb" package from the RE page over a PPA.
Using the SVN version is just a sneak peek for me to see what upcoming versions will bring.

[QUOTE=Arand]
Do note that currently if you run SVN, the impulse mechanics has diverged quite a lot from the 1.0 release, so preferably try to find fellow SVN-players...
[/QUOTE]
For online-play I prefer the original release since most servers out there are the same version.

-Holger

---

### Post by Arand on 2011-06-27
There's now redeclipse-svn and redeclipse-ides packages in my PPA (see original, now edited, post).

In other news, the main developer is back after a long hiatus so progress is slowly picking up, will likely not be as crazy fast as it was a while there, so expect less frequent updates.

Playermodel colouring is now in SVN, along with some new crosshairs, and a preliminary "league" team-fortress-esque mode.

Also to note, the main forums of RE is now at [[COLOR=DarkBlue]http://forum.freegamedev.net/viewforum.php?f=53[/COLOR]]("http://forum.freegamedev.net/viewforum.php?f=53"), much of the modding discussions are there, for example.


- arand

---

