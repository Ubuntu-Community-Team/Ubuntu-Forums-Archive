---
title: "Building a new system and..."
date: 2005-12-21
forum: Desktop Environments
---

### Post by ShadyTails on 2005-12-21
I was wondering if i would be able to install this without windows, I have a amd 64 processor sitting next to me along with a motherboard and ram till i get more parts >.> and I was wondering if i could install the 32 bit Ubuntu on the machine without having windows installed? also could it play games and does it support wireless network cards? or would the 64 bit version work just as well for all those things? thanks! 

~ShadyTails~

---

### Post by dafrabbit on 2005-12-21
Windows is not necessary to run Ubuntu. The two are strictly exclusive of each other and are completely not related. Usually it's suggested you install windows (if you are planning to use it along with ubuntu) first just so that the windows boot manager doesn't inadvertently erase GRUB (ubuntu's boot manager).

You can certainly play games! Although keep in mind that most windows games most likely do not work under linux. You can try with WINE, or if you get lucky your game may have been ported (like Enemy Territory, Doom, Quake, etc.) There are also many open source games that are quite well done. Check out freeciv, tuxrider and of course gnome mines (personal favorite :)).

Wireless cards in general should work. Although if you have something quirky ubuntu may not autodetect/setup on its own and you may need to go digging for help. Do some research on the particular card you are planning to use before hand so you'll know.

To be honest the difference between 64 and 32 bit is negligible at the moment. Although having never spent much time with Ubuntu 64, I will leave that question to someone else.

Good luck!

---

### Post by ShadyTails on 2005-12-21
Whats WINE? If it could play most windows games, i might never need to have windows! which would rock! i dont feel like paying for it!

---

### Post by dafrabbit on 2005-12-21
[WINE]("http://www.winehq.org") is an attempt to mimic windows to the point that windows programs are tricked into thinking they're running on windows.

In terms of games, this gets a little tricky since many windows games are written with DirectX, which WINE has only supported to a certain extent. Your mileage will vary. There are howtos on this forum for setting up WINE (just use the search).

Basically this depends on what kinds of games you are trying to play.

---

### Post by ShadyTails on 2005-12-21
well... [www.psobb.com](www.psobb.com) and soon PSU [http://www.sega.com/games/game_temp.php?game=psu&id=hp_pldwnlst#requirements](http://www.sega.com/games/game_temp.php?game=psu&id=hp_pldwnlst#requirements)

and those are windows games, hmmm i will eventually get windows but im gonna have to save up for it, so ill use Ubuntu to start with and if games work ill forget about windows, and if they dont, ill start saving up for windows :p

---

### Post by towsonu2003 on 2005-12-21
[QUOTE=ShadyTails]well... [www.psobb.com](www.psobb.com) and soon PSU [http://www.sega.com/games/game_temp.php?game=psu&id=hp_pldwnlst#requirements](http://www.sega.com/games/game_temp.php?game=psu&id=hp_pldwnlst#requirements)
[/QUOTE]
[http://appdb.winehq.org/appview.php?appId=2170](http://appdb.winehq.org/appview.php?appId=2170) seems it wont work. but you can help them make it work :)

[QUOTE=ShadyTails]those are windows games, hmmm i will eventually get windows but im gonna have to save up for it[/quote] why not buying a game console instead of windows (if linux works with your hardware)?

---

### Post by ShadyTails on 2005-12-22
[QUOTE=towsonu2003][http://appdb.winehq.org/appview.php?appId=2170](http://appdb.winehq.org/appview.php?appId=2170) seems it wont work. but you can help them make it work :)

 why not buying a game console instead of windows (if linux works with your hardware)?[/QUOTE]
errr im not sure if it works with my hardware >.>
and i got PSO for gamecube but i cant get online with it! >.> it annoys me so
and PSU is gonna be for PS2 and PC and i dont have/want a ps2

---

### Post by briancurtin on 2005-12-22
[QUOTE=ShadyTails]i might never need to have windows! which would rock![/QUOTE]
yes it definitely would. if you end up going through, try to do everything possible in linux with as little windows usage as possible. that is just so you really get a feel for windows, im not telling you what to do with your time and life. its just best that if you are going to start using linux; try and do everything in linux first, second, third, and then you can go do whatever you were trying to do over in windows.

---

### Post by Dr. Nick on 2005-12-22
I run ubuntu 64bit, word of warning - If you are going to need ndiswrapper for your wireless card use the 32bit version of ubuntu, Most windows drivers are 32 bit which wont work on the 64bit version.

If your wireless is natively supported its up to you which to use, 32 will be a bit easier and more compatible with some applications, but 64 bit isnt that bad

---

