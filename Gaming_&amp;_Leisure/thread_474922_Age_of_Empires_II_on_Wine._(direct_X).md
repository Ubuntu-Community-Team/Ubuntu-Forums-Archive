---
title: "Age of Empires II on Wine. (direct X)"
date: 2007-06-15
forum: Gaming &amp; Leisure
---

### Post by OmnificienT on 2007-06-15
I already started [this]("http://ubuntuforums.org/showthread.php?t=474784&highlight=wine") thread, but I don't think it's the right forum. I was wondering if I could get direct X working in Ubuntu so that it might work. Can I do this?

---

### Post by cogadh on 2007-06-15
Wine has DirectX functions built in, but Age of Empires 2 is listed as Bronze in AppDB, so it won't work very well:
[http://appdb.winehq.org/appview.php?iAppId=99](http://appdb.winehq.org/appview.php?iAppId=99)

---

### Post by KaeseEs on 2007-06-15
I have Age of Empires II, and the Conquerors expansion, working on my computer through WINE.  It runs quite well, with three exceptions - the main menu text is black and hard to read, netplay doesn't work, and there's slowdown if you have a bunch of units selected (doesn't matter how many are on the screen, just how many are selected).

If you have issues with the game crashing when you do a random map skirmish, downgrade your WINE to 0.9.36 (this was broken in 0.9.37, but should work again in the latest version).

---

### Post by GMU_DodgyHodgy on 2007-07-12
I have Age of Empires 2 running in wine right now.  The balck text menus is still an issue but it plays quite well.  

I think if you boost the memory on your machine - it runs smoother.

---

### Post by dhomba on 2007-07-13
Please can some one explain on how to run Age on emperors in Linux.

I have wine installed, but is it not required to install the game?

Can I just copy the files and run the exe? will it work..

---

### Post by cogadh on 2007-07-13
Copying the files over from a Windows installation will usually work, but it will sometimes produce errors, if the game needs to read from or write to the Windows registry. It is better and strongly recommended that you run the install like you would in Windows. Just put the game CD in and run this in a terminal:
```
wine /media/cdrom0/setup.exe
```
Change the code to match your actual CD drive mount point and the correct install executable name. After that, it should be just like installing a game in Windows.

---

