---
title: "[SOLVED] Team Fortress 2 on multiple monitors"
date: 2008-01-30
forum: Gaming &amp; Leisure
---

### Post by AegisTalons on 2008-01-30
Hey everyone,

So I got Team Fortress 2 (TF2) installed and working on my system. Surprisingly, it works pretty well. I'm running a multiple monitor setup, specifically a 22" WS and a 19". 

When I start up TF2, it occasionally gives me some errors regarding some registry, but other times it works just fine.

I cannot change the resolution of the game. It is set to play in windowed over my entire desktop. What results is the "center" of the screen being a few inches away from the center. Not exactly optimal for a FPS. Does anyone have any suggestions?

---

### Post by AegisTalons on 2008-01-30
So I just went into the game and grabbed a couple of screenshots for people to understand exactly what I'm talking about.

You can still see that AWN is still running over the game. AWN runs on my primary monitor and is dead center at the bottom of it. 

Let me hear what you have to say.

---

### Post by shad0w_walker on 2008-01-30
I haven't had much experience with Linux and dual screen (Waiting for 8.04 so I can get proper hotplugging) but couldn't you force the game to run at a certain resolution? Theres the possibility of using the ingame resolution option and I believe there is also the command line way of doing thingse, either with wine, but I see a big performance hit using windowed mode or with steams option settings.

---

### Post by AegisTalons on 2008-01-30
The issue is in the game, I cannot change the resolution at all. Its set to only that resolution. As why I'm running in windowed mode, its because I want to avoid the issue of the game spanning multiple moniors.

If someone knows an easy way where I can switch on and off my secondary monitor, I would appreciate it. It took me forever to try and figure out how to get to span both monitors.

---

### Post by macabro22 on 2008-01-31
How did you get the game to work?

Wine? Can you post me the links to the how-to's?

---

### Post by peitschie on 2008-01-31
Have a look at xrandr for something that can dynamically disable a single screen: [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12).  I'm assuming you use an Nvidia card...?

You can also set up multiple MetaModes that can then be loaded using xrandr.  Referencing [ftp://download.nvidia.com/solaris/1.0-8178/README/appendix-g.html:](ftp://download.nvidia.com/solaris/1.0-8178/README/appendix-g.html:)
> If you want a display device to not be active for a certain MetaMode, you can use the mode name "NULL", or simply omit the mode name entirely:

    "1600x1200, NULL; NULL, 1024x768"
For example, if I have two metamodes defined, and the second one has 1600x1200, NULL, I'd run the following code in a terminal to disable one of the screens:
```
xrandr -s 1
```

(actually... it might be -s 2, I don't remember.. have a play though :))

---

### Post by AegisTalons on 2008-02-06
peitschie, I'll give it a try with xrandr when I get home. As for installing TF2 on linux, a good tutorial I used was [this one]("http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/"). He goes through it step by step. I download my games directly from steam so it takes longer than having the CDs on had.

---

### Post by AegisTalons on 2008-02-11
One of the things I did to fix the problems, I looked through the command line arguements when opening for hl2. There is a command -width XXXX -length YYYY that forces the game to play in that specific resolution. So say you want 1280x1024. You would then place "-width 1280 -length 1024" in the arguements run at startup. If you don't know what I'm talking about, in the steam menu where you can double click on a game to start, right click and select properties. Select "Set Launch Options" button and place your variables there.

If you also want to speed up the game try also the flags "-novid" (no opening movie) and "-heapsize 512000" (forces the game to use 512megs of RAM. You can change it to want you want relative to your computer. Make sure not too set your entire memory to the heapsize otherwise you'll get a crash.

New Windows TF2

[IMG]http://www.andrew.cmu.edu/user/avasiles/Ubuntu%20Pictures/Screenshot4-TF2.png[/IMG]

---

