---
title: "Widescreen is annoying me with fullscreen games."
date: 2007-07-17
forum: Gaming &amp; Leisure
---

### Post by FRuMMaGe on 2007-07-17
I have a widescreen 1280x800 laptop screen and I find it irritating that most games dont have a widescreen mode.

This doesn't bother me.  What does bother me is that when you run the game fullscreen everything is a little bit squashed.  I tried playing them in windowed mode but this irritates me that i can still see my desktop.

Is there a way to run a game at fullscreen but make sure the game window only takes up 1024x768.  By this I mean a black border around it to make sure there is no image stretching.

---

### Post by Henry Rayker on 2007-07-17
I would guess this is probably a game-by-game issue. Maybe post a list of the offending games, to see if there is a way around it?

---

### Post by Soybean on 2007-07-17
You could make an all-black image file the same size as your screen, then open it in a full-screen image viewer. Then run your game windowed over top of that. ;)

Actually, it'd be really nice if video drivers implemented something like this. Another advantage to it would be that you could always run things at your LCD's native resolution -- if the program you were running didn't support that resolution, it would just be rendered in the center of the screen.

But no, I don't know of a way to do it. :(

---

### Post by FRuMMaGe on 2007-07-17
> **Soybean said:**
> You could make an all-black image file the same size as your screen, then open it in a full-screen image viewer. Then run your game windowed over top of that. ;)

Actually, it'd be really nice if video drivers implemented something like this. Another advantage to it would be that you could always run things at your LCD's native resolution -- if the program you were running didn't support that resolution, it would just be rendered in the center of the screen.

But no, I don't know of a way to do it. :(

The problem with this idea is that alot of games don't keep the mouse focus in windowed mode so the mouse leaves the window when moved too much.  This makes first-person-shooters and other such mouse-reliant games unplayable in window mode

---

### Post by FRuMMaGe on 2007-07-18
bump

---

### Post by frodon on 2007-07-18
Which games create you this problem ?

---

### Post by FRuMMaGe on 2007-07-18
> **frodon said:**
> Which games create you this problem ?

Most games that you have to play using Wine, but also some native games.

Specifically:
> Urban Terror 4.0
> Warcraft III
> Unreal Tournament GOTY
> Unreal Tournament 2004
> zSnes (when run at fullscreen mode)

---

### Post by Skia_42 on 2007-07-18
If you are using WINE, you can configure it such that the mouse does not leave the window.
Type the following command into the Terminal and navigate to the Graphics tab.
> winecfg

---

### Post by FRuMMaGe on 2007-07-18
> **Skia_42 said:**
> If you are using WINE, you can configure it such that the mouse does not leave the window.
Type the following command into the Terminal and navigate to the Graphics tab.

This only works with directx applications.  It has absolutely no effect on opengl games, and barely even works most of the time anyway.  Trust me I have tried all the wine settings.

Does anyone know how to run an application in a seperate xserver at its correct resolution with a black border?

---

### Post by FRuMMaGe on 2007-07-19
bump

---

### Post by frodon on 2007-07-19
Well i think before bumping you should search a little bit, for example this is what gives google after 20 s of searching about UT2004 :
[http://www.widescreengamer.com/u/unreal_tournament_2004.html](http://www.widescreengamer.com/u/unreal_tournament_2004.html)

Really often games who don't offer you the wanted resolution because you have a widescreen let you edit config files to specify explicitly the wanted resolution.
So just take the time to search for each game you have a problem with the way to set widescreen resolutions.

---

### Post by FRuMMaGe on 2007-07-19
> **frodon said:**
> Well i think before bumping you should search a little bit, for example this is what gives google after 20 s of searching about UT2004 :
[http://www.widescreengamer.com/u/unreal_tournament_2004.html](http://www.widescreengamer.com/u/unreal_tournament_2004.html)

Really often games who don't offer you the wanted resolution because you have a widescreen let you edit config files to specify explicitly the wanted resolution.
So just take the time to search for each game you have a problem with the way to set widescreen resolutions.

Thanks for this, but I was just using UT as an example.  I have already sorted it.  What I was looking for was a general fix for all fullscreen applications such as a script to launch a seperate xserver but with the correct resolution.  Thanks though

---

### Post by frodon on 2007-07-19
> **FRuMMaGe said:**
> Thanks for this, but I was just using UT as an example.  I have already sorted it.  What I was looking for was a general fix for all fullscreen applications such as a script to launch a seperate xserver but with the correct resolution.  Thanks thoughUnfortunatly most games which don't handle widescreen within in game options require to edit config files.
A general fix would be hard to find your case, anyway running your games in another xsession may be a dirty workaround since you won't see your desktop ;)

---

### Post by FRuMMaGe on 2007-07-19
> **frodon said:**
> Unfortunatly most games which don't handle widescreen within in game options require to edit config files.
A general fix would be hard to find your case, anyway running your games in another xsession may be a dirty workaround since you won't see your desktop ;)

Thats the thing though.  I know you can make scripts to run a seperate xserver for games and revert to the original when you close it.  However, I don't know how to make it use the correct resolution.

---

