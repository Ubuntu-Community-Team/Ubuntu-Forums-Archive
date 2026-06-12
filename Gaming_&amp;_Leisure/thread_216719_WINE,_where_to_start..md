---
title: "WINE, where to start."
date: 2006-07-15
forum: Gaming &amp; Leisure
---

### Post by Banyon on 2006-07-15
Ok, I finaly got Xubuntu setup how I want, everything working correctly, everything updated, ect.

Now I want to try playing some games on here.

Now, I have this system dual booted with XP, XP being just for gaming, but I would like to at least TRY to get the games running on Linux acceptably.

The WINE I have installed is just the one installed by Automatix when I ran it.

For my games thats non native, I'm not sure where to start.  I have WINE installed, I seen something about WINECVE, d3d9 patches, winex3 bunch of other stuff.  Heres what I want to try to get working,

Red Orchestra Retail, UT2k4 based, requires steam
Civilization 4
Battlefield 2, Battlefield 1942/Forgotten Hope mod
UT2k4 (I know this is native, but last time I installed, wouldn't run).
Poker Stars (Got this working in just basic WINE, not perfect, but works).
XFire (Not a game, but I want it working)

Ok, this is all I can think of at the moment, Poker Stars and XFire work, but XFire appears to be having issues with the font, and it runs really slow.

Only issue with Pokerstars is when I join a table, instead of opening a new window and leaving the lobby open, it joins the table and closes the lobby.

---

### Post by nthdegree on 2006-07-16
Make sure you let the WM manage the window and UT games should work.

Fullscreen modes in UT based games running on WINE tend to have a few issues, a tip I would recommend is NOT to use the packaged NVidia drivers (if you have an NVidia card) but to grab the drivers off the NVidia site yourself and set them up.

---

### Post by eqisow on 2006-07-16
A good place to start would be the Wine [application database]("http://appdb.wine.org/").

I know Steam works, though I'm not sure about that particular game. Perhaps, since it is based on UT2004, there is a Linux version.

Battlefield 2 won't work as far as I'm aware, I'm not sure about 1942.

UT2k4 should run just fine native. Give it another go. :)

With Xfire, the issue may be a missing font. If the application DB doesn't have anything about it, just try installing some Windows fonts in Wine.

---

### Post by eqisow on 2006-07-16
> Fullscreen modes in UT based games running on WINE tend to have a few issues, a tip I would recommend is NOT to use the packaged NVidia drivers (if you have an NVidia card) but to grab the drivers off the NVidia site yourself and set them up.

I've personally never had issues with the packaged Nvidia drivers. If you want the newest drivers, however, the ones on the Nvidia site might not be a bad idea. Also, version 0.9.17 of Wine supposedly has better support for fullscreen apps. I haven't really tested this out though.

---

### Post by Banyon on 2006-07-16
Thanks for the info.

Does anyone have any info on how to get Civ 4 working on Linux?  I'm copying my civ 4 folder from windows to WINE directory right now to see if I can get it running, but I've seen posts from people saying it don't work.

---

### Post by Banyon on 2006-07-16
When I start a game in console using WINE command and it comes up with errors listing what DLLs aren't avalible, can I just copy them from windows and put them into WINE or will that not work?

---

### Post by eqisow on 2006-07-16
I think the best solution would be to try actually running the installer in Wine. Sometimes installers put DLLs in funny places or make registry changes that are needed for the game.

You could always give moving the DLLs a shot though.

---

