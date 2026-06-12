---
title: "The Grand Experiment..."
date: 2007-04-17
forum: Gaming &amp; Leisure
---

### Post by paul.r.stoner on 2007-04-17
Ok, now that I am fully converted over to Ubuntu - thank god - none of that Vista crap for me....

I have some Windows games that I know are NOT ported over to Linux...

So, I want to play :)  Has anyone had any experience in getting any Windows games (non-linux ports) to work on Ubuntu?  If so, can you point me in the right direction of where to start?  Is there some sort of emu that you can use?

I am all ears!

Thanks gang....

---

### Post by christhemonkey on 2007-04-17
Wine would be what you want to use.

You just need to:
```
sudo apt-get install wine 
```
And then type:
```
winecfg 
```
To configure it, then finally:
```
wine /path/to/your/application.exe 
```

Also it doesnt 100% work, so you might want to check on [http://appdb.winehq.org/](http://appdb.winehq.org/) to check compatibility with your game.

---

### Post by justin whitaker on 2007-04-17
> **prstoner2 said:**
> Ok, now that I am fully converted over to Ubuntu - thank god - none of that Vista crap for me....

I have some Windows games that I know are NOT ported over to Linux...

So, I want to play :)  Has anyone had any experience in getting any Windows games (non-linux ports) to work on Ubuntu?  If so, can you point me in the right direction of where to start?  Is there some sort of emu that you can use?

I am all ears!

Thanks gang....

Start with the stickies in this forum, particularly this one:

[http://ubuntuforums.org/showthread.php?t=359842](http://ubuntuforums.org/showthread.php?t=359842)

Next, try going to WineHQ. [http://www.winehq.com/](http://www.winehq.com/) 

The app database has pretty good information on what does and does not work.

Crossover Office runs many Steam based titles, and World of Warcraft. 

[http://www.codeweavers.com/](http://www.codeweavers.com/)

Transgaming is a dirty word here, but it does allow you to run a bunch of games which are basically coasters via these other methods.

[www.cedega.com](www.cedega.com)

Also, some Windows titles have native ports: Neverwinter, Doom III, the Quake series, Unreal series...

---

### Post by cor2y on 2007-04-17
Yes wine is good also before plunking down the cash on  Cedega there is the free time demo as well as a How To in this section on compiling the CVS free version.
I have read that the Cedega folks make it difficult for you to compile the free version but if you follow the How To it should work.
Also i don't know if this How To will apply to the latest version of the program.
Cedega 6

---

### Post by paul.r.stoner on 2007-04-17
Well the game I am specifically looking to play are "John Deere: American Farmer Deluxe" (gee what a guess), and a few of those Gamehouse / MSN games like family feud 1 & II, Wheel of fortune, Jeopardy, Monopoly Here & Now Edition, etc..

---

### Post by cor2y on 2007-04-17
well you may have to check the wine database at winehq.org to see if its in there and if it runs.
If  its not listed then give it a try via wine with installing and running to see if it works.
Cedega has a database of working games as well can't remember the link for it right now.

---

### Post by motin on 2007-04-17
I just read [http://en.wikipedia.org/wiki/Linux_gaming](http://en.wikipedia.org/wiki/Linux_gaming) yesterday and loved it!

If you are up to it - give your opinion on what the market-shaping features of either Ubuntu, Windows and/or OS X are:

- [What are the ultimate features of Vista that Ubuntu needs?]("http://ubuntuforums.org/showthread.php?t=409721")
- [What are the ultimate features of OS X that Ubuntu needs?]("http://ubuntuforums.org/showthread.php?t=409722")
- [What are the ultimate features of Ubuntu that neither Vista nor OS X has?]("http://ubuntuforums.org/showthread.php?t=409720")

I believe defining these will help the community focus on aspects that would make the community stronger.

---

