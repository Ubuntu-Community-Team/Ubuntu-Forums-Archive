---
title: "NeverWinter Nights issues"
date: 2006-02-02
forum: Gaming &amp; Leisure
---

### Post by MacV on 2006-02-02
I installed NWN on my 5.10 machine using the Loki installer. Everything works ok but for a few things.

1. I can only get teh game to start when i use sudo. I really don't want to have to do that all the time just to play. I assume I have to change permissions, but I dont know how.
edit-Hmm, it appears I should have installed the game on my /home directory instead of the default /usr/local/games. I'm gonna re-do it and see what happens,

2. I have no sound from the game. No big deal really, just wondering if anyone knows how to change that.:mrgreen: 

3. My one true isssue is that when i get into the game world, the mouse is very sluggish. Before I enter the game(IE, at the game menus) the mouse is fine. As so as I start a game though, everything moves slowly. Is there anyway to fix this? Or do I have to go through Bioware's (complicated) instructions. 

Note, I just brought NWN and not gold/priemium/diamond editon.

---

### Post by Perfect Storm on 2006-02-03
1. My recommendation is you don't install nwn as root. 

2. Make sure you have the right SDL libs. installed.

A good installer and instruction you find here: [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

---

### Post by MacV on 2006-02-03
Thanks, I'll try that out tonight. Will that installer also grab the 1.66 patch, or will i have to compile that myself?

---

### Post by Perfect Storm on 2006-02-03
The patch 1.66 isn't included. You just extract patch 1.66 to nwn folder and overwrite existing files.

A good place I always use for games which aren't installed universal /home/<username>/.games/nwn
pay closer look where it says /.games it makes the folder invisble if you havn't show all files. A good way so there aren't filled up with tons of folders in your home directory.

---

### Post by leech on 2006-02-03
The first question I always ask about Nwn in linux is which version of the game are you trying to install?  If it's just the normal version, then the ones on ravage's site work quite well, or the liflg.org ones.  If you're running the Platinum edition, check out my thread [http://ubuntuforums.org/showthread.php?t=113259](http://ubuntuforums.org/showthread.php?t=113259)

Leech

---

### Post by MacV on 2006-02-03
Grr, I keep getting the Fatal signal: Segmentation Fault (SDL Parachute Deployed)
error.
edit-Bah, I really got to start reading these readme files better. I used the HoU patch instead of the plain one. Hopefully I can just overwrite the wrong patch.

---

### Post by MacV on 2006-02-04
Execellent, I got the game to work as well as the hardware mouse. Now I just have to figure out how to make it run more smoothly instead of it running sluggish. I had the game before for Windows and it ran perfect.

---

### Post by Perfect Storm on 2006-02-04
and you did install the graphic card driver for your card?

---

### Post by MacV on 2006-02-04
[QUOTE=Artificial Intelligence]and you did install the graphic card driver for your card?[/QUOTE]

Oh yeah, i got the driver long ago. Otherwise, I wouldn't be able to play Unreal Tournament 2k4.

edit-Geoforce 440 Go 64meg, on a Dell Laptop.
Driver version 1.0-7667 is the driver version

---

### Post by MacV on 2006-02-05
Ok, from what I researched, in order to play the game smootly, I have to change my xconfig from 16bit to 24 bit. I have no idea how to go about doing that. Also, I read a forum posting at some other site saying that he just had 2 x-server sessions. One at 24bit for playing NWN and the other at the default 16. If anyone could point me in the direction of learning how to do that, I'd be greatful.

---

### Post by leech on 2006-02-06
You'd want 24bit for pretty much everything anyhow.  What you'll want to do is ```
sudo nano /etc/X11/xorg.conf
```

Use Control+W to do a find for DefaultDepth.  Change that from 16 to 24.  Then use Control+X to save it, you'll have to press Y to confirm and enter again to overwrite the file.  

After doing this, log out, at the GDM screen press Control+Alt+Backspace.  This will restart X.org.  You will now be in 24bit.

Leech

---

### Post by MacV on 2006-02-08
Thanks guys, I have everything working great now!:D

---

