---
title: "Registry error when trying to launch half life2?"
date: 2007-08-21
forum: Gaming &amp; Leisure
---

### Post by fizz on 2007-08-21
Every time i try to launch the game, i get the following message

SteamStartup() failed: SteamStartup(0xf,0034DFF4) failed with error
1: The registry is in use by another process, timeout expired.

I also get a message about installing the gecko engine everytime its launched and dont know if this has anything to do with it.

Any help would be great, running latest wine 9.10.43? on a macbook pro.

---

### Post by cogadh on 2007-08-21
Well, you do need to install Gecko before Steam will work correctly, and HL2 requires a functional Steam installation. I would fix that problem first, then work on the other one, if it still continues.

I think you misstyped that Wine version, the latest Wine is only 0.9.43.

---

### Post by fizz on 2007-08-22
Ok, got the HTML rendering engine fixed, and it also at the time appears to have fixed the registry error i was receiving. 

a few questions remain.
How come it shows in WineCFG that im running DX6? and could this be related to poor performance?
When I exit the game, why doesnt gnome go back to its original reoslution?
im running at 800x600 with everything at low and its just unplayable, im sure there is something that can be done to corrcet this.

Im running on a macbook pro, so the hardware is decent, i can run WoW in full settings almost and it plays fine. Any advice is appriciated..
thanks

---

### Post by cogadh on 2007-08-22
Where in winecfg are you seeing DX version info?

Try running the game with this command:
```
WINEDEBUG=-all wine steam.exe -applaunch 220 -dxlevel 90
```
That will turn off Wine's debugging message (can improve performance) and forces the game to use DX 9 interfaces. If you don't have a fully DX 9 compatible video card, change the DX variable to "-dxlevel 80".

---

### Post by fizz on 2007-08-22
Think im making some head way.. Just found out direct rendering = no when i do glxinfo | grep render

Reading more, i noted that if people startx instead of using gdm, it changes to yes.. Looks like i need to troubleshoot this before steam now :P

---

### Post by cogadh on 2007-08-22
If you are getting "direct rendering = no" then you probably don't have the 3D acellerated driver for your video card installed or it is installed, but not active. What video card/chipset does the Macbook have?

---

### Post by fizz on 2007-08-22
Macbook Pro 15", ATI Radeon X1600

I just started X without XGL (which compiz-fusion runs awesome i might add), i have it saying yes...

---

### Post by fizz on 2007-08-22
Ok, good news, bad news!

Good news first, after getting it to finally run without XGL, I cranked all the settings 1024x768, model terrain, ect and it runs awesome!

The bad news
Cant get direct rendering to work in XGL so I guess when I want to play games i logout and change my session temporarily to play.. Hopefully ATI will release some decent damn drivers to help with this in the future. 

As for the registry error i was getting, it seems random, and seems that its plauging the cedega people currently too.

---

### Post by splintercellguy on 2007-08-22
The registry issue is a known bug. I think you do verify game cache to resolve.

---

