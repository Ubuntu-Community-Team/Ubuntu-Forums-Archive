---
title: "Any EQ1/NWN gamers?"
date: 2007-10-05
forum: Gaming &amp; Leisure
---

### Post by disposition on 2007-10-05
Anyone out there a NWN1 or EQ1 player? Anyone interested in reviving the game and playing again?

As far as EQ goes, I've been playing on Shards of Dalaya ([www.shardsofdalaya.com](www.shardsofdalaya.com)) which is a free EQEmu as long as you have the install CD's (in one form or another). 

As far as NWN goes, perhaps we could get an Ubuntu group going on some persistant world, or just have periodic game nights? I seem to remember the Penultimate mods being entertaining/amusing.

---

### Post by DoktorSeven on 2007-10-05
I love NWN.  Haven't played in a little while though, but I'd love to play.

---

### Post by cogadh on 2007-10-05
I actually just got the Diamond version of the game about a month ago, but I haven't tried playing online yet, still trying out all the single player goodness. I wouldn't mind finding a good group to play with though.

---

### Post by fadastic on 2007-10-05
I, too, have the Diamond edition and would love to play, except I'm experiencing a bug. When I use the start script (./nwn) my screen turns black for a second, as if it is going to enter the game, and just returns to my desktop instead of entering the game.

---

### Post by DoktorSeven on 2007-10-05
I have the Platinum edition bought some time ago.  Also, many servers require the CEP ([here](http://nwn.bioware.com/players/cep.html)).

fadastic, did you run ./fixinstall after installation?  3D drivers properly installed?  Any messages printed out after you run ./nwn from a terminal?

---

### Post by KhaaL on 2007-10-06
I got NWN + the two expansions, and I'd LOVE to play on a nice PW with ubuntians :)
(I'm a european though so we need to keep track of the time diffrence)

---

### Post by Tyke91 on 2007-10-06
there's a great mod that I help to dm (along with 10 other dms) called the Three Towns

we've got two servers (A and B) and can support an excess of 100 people playing at one time. 

around 1/2 of our population is european, the rest primarily being east coast US/Canada... but we also get people from everywhere else in the world. We've got a customized spell/feats system and we DON'T REQUIRE and haks in order to play... just update to the latest version of NWN and play :D

o yeah... and I'm hosting a large scale 'day long' event on sunday... if you are a noob, you can meet higher level players there and get some tips :)

for more info, our website is [www.trustinginthefuture.com/3towns](www.trustinginthefuture.com/3towns)

---

### Post by madsmeg on 2007-10-06
I am currently a WoW player but am basicly getting sick of spam/goldselling/5-yr-old players/etc would this make a good alternative?

P.S. i know its not an MMO

---

### Post by happy-and-lost on 2007-10-06
NWN suffers from random white outs on the OSS ATi driver :(

Once they've put Aiglx support in fglrx, I'll start playing again :)

---

### Post by fadastic on 2007-10-07
> **DoktorSeven said:**
> I have the Platinum edition bought some time ago.  Also, many servers require the CEP ([here](http://nwn.bioware.com/players/cep.html)).

fadastic, did you run ./fixinstall after installation?  3D drivers properly installed?  Any messages printed out after you run ./nwn from a terminal?

Ah, yes. I forgot. I get this: ```
Fatal signal: Segmentation Fault (SDL Parachute Deployed)

```

which I assume means I don't have libsdl...but...I do have it installed (libsdl1.2-debian-all, to be exact). Unless...there is some other sdl library that I don't know about.

---

### Post by DoktorSeven on 2007-10-07
No, "SDL parachute deployed" is SDL catching a segfault (program crash).  Basically it means that something's not working right with your NWN install or you don't have 3d enabled, or some other reason.

---

### Post by fadastic on 2007-10-07
Well, I definitely have 3D enabled, as I'm able to play UT2004, Tremulous, Nexuiz, etc.

I guess I'll try a reinstall.

Update: Ok, I did a reinstall and now can start properly :). One final question, can I put the "nwn" start script in the main menu and start from there? I tried listing it in the main menu, but nothing happens when I click it. I don't really want to have to open up the terminal and browse to my nwn directory to start.

---

### Post by cogadh on 2007-10-07
Modify the start script to look like this:
```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

cd /$HOME/nwn #<--this line is the important one
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
export SDL_AUDIODRIVER=esd

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so

./nwmain $@
```
Adding the "cd" line will allow the script to be run from a menu shortcut. The rest of the start script should be left alone (mine has been changed from the default quite a bit).

---

