---
title: "WoP logs me out"
date: 2007-05-18
forum: Gaming &amp; Leisure
---

### Post by whayong on 2007-05-18
So I rescently decided to step up my linux usage in this computer and start playing some games.  After browsing a few games, I decided to install WoP.  I followed the how to found in UGA.  Everything went well except I can't play the game, lol!  Everytime I run it I get a black screen, then get logged out.  Is my system to slow to run the game?  The video card is on board. 10MB shared but can play up to 16MB.


edit: WoP = World of Padman

---

### Post by mbradlcu on 2007-05-18
ouch, yea you're specs are a little light,, but the q3 engine is pretty forgiving..

if you start wop from the command like what exit errors do you get?

BTW quake1&2 are pretty fun, and have shareware so you can check to see how/if it runs on your system

---

### Post by whayong on 2007-05-18
I don't really see any errors, even when I start it in terminal.  It just goes straight to the black screen and goes directly to the log in screen fairly quickly.  Actually, a lot faster then me hitting the "log out" key, haha!  SO am I pretty much SOL in this case?

edit:  Just wanted to say also that under XP, I've been able to play everything short of games requiring a 32MB video card.  I've had problems running the splash screen at boot.  I have an onboard intel graphics.  I think this is the main problem, and they must be related.

---

### Post by mbradlcu on 2007-05-19
another check would be to run 'glxinfo | grep direct' and look for:
direct rendering: Yes

if you see know then q3/wop would run too slow anyway.. if not lets keep trying!

---

### Post by FragUPlenty on 2007-05-19
Essentially all the newer quake 3 based standalone games are based on an engine called ioquake3, which is currently in its 1.34 beta release. WoP uses this engine. There is a bug where alot of the current stand-alone games based off the engine, including WoP and Urban Terror, do not have vis-blocking. A technique of rendering a map that allows only the portion of the map viewable to the player at that time to be rendered. 

The lack of vis blocking means that the CPU, Graphics card, and Memory is being pushed very very hard. Now on alot of current configurations this isnt exactly a problem but when you try and play the game on the bare minimum specs for vanilla Quake 3 it does cause a problem one of those being spontaneous crashes and poor performance. The poor performance and crashing likely doesnt have anything to do with Ubuntu or the software that they develop.

Also soon enough as the ioquake3 project is very active, it will more then likely be fixed.

If you want some good games to try might I suggest boswars, a great CnC clone that I love playing, especially if you are a fan of old school RTS.

Rock on:guitar:

---

### Post by whayong on 2007-05-19
glxinfo | grep direct comes back "no"

I actually just installed bos.  I loved the old school CnC games.  I played everything up to Red Alert 2 on this laptop.  Generals was just choppy.  I haven't played bos yet though, maybe sometime tonight.  Thanks for the tip fellas!

---

