---
title: "Compiz-Fusion + Games are unplayable"
date: 2007-11-26
forum: Gaming &amp; Leisure
---

### Post by barronmb on 2007-11-26
I have finally gotten Compiz-Fusion running on my box... but here's the rub.  When I launch ANY OpenGL game...  The game launches but the graphics are completely screwy.. blacking in and out in patches.  WoW is completely unplayable, UT2003, UT, UT2k4 all do it as well.  Yes, this in both full-screen and windowed mode.  I am hoping that we have a fix for this.  (Other than disabling CF everytime I want to play).  I know I have seen screenshots of people playing OpenGL games while using Compiz-Fusion...  What am I missing?  I have tried individually killing each addon in CCSM and starting my game.. no effect at all.  Anyone know a fix for this?

System:
Athalon XP 2600+
ATI Radeon 9800se
1.5GB RAM

Running the latest ATI drivers and latest CF ver.  glxgears shows smoothly rotating gears... but a little glitchy in CF.  fglrxinfo shows proper ATI driver.  glxinfo shows direct rendering.

---

### Post by boast on 2007-11-26
Search the forums for two scripts. 


one to replace compiz with metacity
and one to replace metacity with compiz

you place the scripts in /usr/bin/
and make them executable (chmod +x )

and then you use gconf-editor to set keyboard shortcuts.

I have <Alt> q - to disable compiz
and when I'm done gaming, <Alt> w  - to turn it back on.
=======
but for the most part, gaming with compiz = decreased performance

---

### Post by Naegling23 on 2007-11-26
um...kill compiz fusion before launching the game.  Trust me, your comp will also benefit from the added performace boost.

If you dont want to manually turn it off, try launching your games with a script to turn off compiz fusion, and relaunch it when the game is closed.  Search through this forum, I know I've posted the script before, but im too lazy to go find it right now.

---

### Post by Vadi on 2007-11-26
There's some bug with CF and OpenGL.

Before starting a game, alt+f2, **metacity --replace**, and when done **compiz --replace**.

---

### Post by barronmb on 2007-11-26
Thanks for the replies. 

I am aware of the replace solution...  and the performance boost from disabling CF.  However, I am hoping to find a way to work with both at the same time.  I have seen people do it and know people who do it successfully...  I may wind up just scripting... but I am one of those wierd people who can't get over it until the "problem" is fixed. lol

Any clues what causes this trouble between CF and OpenGL?  I almost feel certain that there is an addon or specific group of addons that cause the flickering graphics.

---

### Post by Vadi on 2007-11-26
I don't remember the exact answer, I asked this on CF forums a while ago (search for "google earth flickering", you should come acress my thread)

---

### Post by barronmb on 2007-11-26
Ok.. found that thread:

[http://forum.compiz-fusion.org/showthread.php?t=3367&highlight=google+earth+flickering](http://forum.compiz-fusion.org/showthread.php?t=3367&highlight=google+earth+flickering)

It appears that the issue is restricted to ATI users (2 of my friends that do NOT have this issue use nVidia -- though I was certain that another friend of mine uses ATI, maybe he doesn't).  Though the posters seem to refer only to the Open Source drivers... not the ATI driver.  (They probably share the same flaw).  

I will keep digging on this.  If anyone else has some ideas please chime in.

---

### Post by KhaaL on 2007-11-26
Does he really need to replace CF with metacity? Dosen't starting the game in a diffrent X-server (through xinit) give same - and even more - benefits?

---

### Post by cogadh on 2007-11-26
Yes and no. If you kill the current X session and launch the new one from the console, then yes, you get the same and even more benefits. If you just switch to a new X session without killing the current one, then some of those resources are not released for use with the new session and you won't get the full benefits from the separate X session, but you should still eliminate the CF problem.

---

### Post by Sayers on 2007-11-26
Compiz seemed to fix this for me, itself. I can play ET: Quake Wars full power with fusion on full power and not notice a difference.

---

### Post by boast on 2007-11-26
with compiz on, I lag playing enemy-territory, even cs1.6 !!

---

### Post by hikaricore on 2007-11-27
Compiz was not meant to be run along side games.
This is the exact reason you're all having trouble.

You're using beta software in a way that it really wasn't meant to be used.
There have been 1,001 different threads on this topic for years now, I can't imagine why is such a difficult concept.

---

### Post by buntunub on 2007-11-27
> **hikaricore said:**
> Compiz was not meant to be run along side games.
This is the exact reason you're all having trouble.

You're using beta software in a way that it really wasn't meant to be used.
There have been 1,001 different threads on this topic for years now, I can't imagine why is such a difficult concept.

I have Compiz on with all affects working great, yet when I run glxinfo I get Direct Rendering: No.

I turn Compiz off and run glxinfo and get, Direct Rendering: No!

Compiz does not have a thing to do with wether you can run games or not dude. Not one stinkin thing. If Direct Rendering is ON, then you can play 3D games. That simple. If Direct Rending wont enable, like for one of my boxes, then you cant play 3D games wether Compiz is on or not, or never enabled. Dont matter one bit. The only caveat is wether your system's resources can handle the load of running games with Compiz enabled. By my own tests, Compiz takes up next to nothing when your running games in full screen mode, and thus does not impact the games performance one iota. If you run a game in windowed mode and spin the cube around non stop, then ya, Compiz is going to hog up resources and thus, your game will suffer. Either way, you must have Direct Rendering ON.

---

### Post by hikaricore on 2007-11-27
> **buntunub said:**
> I have Compiz on with all affects working great, yet when I run glxinfo I get Direct Rendering: No.

I turn Compiz off and run glxinfo and get, Direct Rendering: No!

Compiz does not have a thing to do with wether you can run games or not dude. Not one stinkin thing. If Direct Rendering is ON, then you can play 3D games. That simple. If Direct Rending wont enable, like for one of my boxes, then you cant play 3D games wether Compiz is on or not, or never enabled. Dont matter one bit. The only caveat is wether your system's resources can handle the load of running games with Compiz enabled. By my own tests, Compiz takes up next to nothing when your running games in full screen mode, and thus does not impact the games performance one iota. If you run a game in windowed mode and spin the cube around non stop, then ya, Compiz is going to hog up resources and thus, your game will suffer. Either way, you must have Direct Rendering ON.

**You really need to learn to read what was written before responding.**

Compiz/Beryl was created to be an efficient and useful 3d desktop environment.
It **WAS NOT** intended to be run along side other processes that also use a large amount of GPU time.
In the same way that the developers of World of Warcraft didn't design it with the intention of 2 other copies being run at the same time.
Sure if you have the resources by all means you can do it, but if you don't have the resources it will drag your system to its knees.

p.s. Your poor CPU must be suffering the wrath of having to do the job of your video card /w Compiz running like that.

---

### Post by derekr44 on 2007-11-27
Install Fusion-Icon :)

Easy switching from Compiz to Metacity by right-clicking and selecting the window manager of your choice.

I love it.

---

