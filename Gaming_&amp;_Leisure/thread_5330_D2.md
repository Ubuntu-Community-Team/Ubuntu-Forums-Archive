---
title: "D2"
date: 2004-11-17
forum: Gaming &amp; Leisure
---

### Post by trivialpackets on 2004-11-17
All I'm interested in and all that keeps me from ditching Windows from the other partition altogether is my dependency on playing Diablo 2 every once in a while.  Any advice on how to get this so that I can play?  Not familiar with any windows emulators or how to use them.  Let me know, as this would resolve a growing technical divide between my computer preferences and my greatest time waster I have when I'm not doing homework.  Thanks all as always in advance. 8-[

---

### Post by anklator on 2004-11-17
hi,

i like that game too, its supposed to work with wine, in the universe rep, i only tried on debian sid(havent tested in ubuntu yet), it worked, but by a strange reason keyboard didtwork(that sux for diablo), and bnet didt identify my version correctly(using latest,1.10)

---

### Post by trivialpackets on 2004-11-17
No keyboard, that would be pretty harsh...looks like my win partition is going to be hanging around for a bit.  lol

---

### Post by jdodson on 2004-11-17
try wine in universe first.  it might be newer and work well, plus ubuntus version might change something that allows the keyboard to not error, more than likely it will have that problem.  but i have found wine to perform differently using the same version on different distros fwiw.

if that doesnt work try this:

[http://www.unet.univie.ac.at/%7Ea0201073/cedega.html](http://www.unet.univie.ac.at/%7Ea0201073/cedega.html)

cedega is a wine game version that plays D2 very very well.  its one of the highest rated for playability.

---

### Post by zenwhen on 2004-11-17
Yeah, cedega is the way to roll for Diablo 2.

---

### Post by trivialpackets on 2004-11-17
If this is the case, and cadega works, I cannot wait to format my windows partition.  Or do I?  The D2 game needs to be installed somwhere right?  So Do I need to leave my Win partition in order to just access the game on the other partition?  Also, installing tar formats has proven difficult for me in the past, what are the commands necessary for installing cadega

---

### Post by jdodson on 2004-11-17
commands to install the .deb of cedega is:

```
sudo dpkg -i cedega?????.deb
``` 

replace the ???? with the right version info.

after that you can install D2 from the CDS by(btw you dont need a win partition for this, it can install in ubuntu fine):
```

cd /media/cdrom0
cedega install.exe

``` 

if install.exe indeed is the d2 installer exe and cdrom0 is the drive that has the D2 cd in it.  so many variables...

---

### Post by adbak on 2004-11-17
For files with .tar.gz
```
tar -xvzf <filename>
```

For files with .tar.bz
```
tar -xjf <filename>
```

For files with .deb
```
dpkg -i <filename>
```

---

### Post by trivialpackets on 2004-11-17
cedega got the game installed fine with no hitch, however, now that I have the icon, it will not start the game.  I tried changing the permissions to execute and the open with to cedega, but no reaction whatsoever.  Any advice?

---

### Post by trivialpackets on 2004-11-20
I removed the game, as I was having difficulty getting it to work, now when I try to reinstall, thinking I should have saved it to the transware whatever directory, I am getting the error No Program Start Menu Found.  That's it nothing else.  Any ideas?

---

### Post by ante0 on 2005-05-17
when u install click no when it asks if you want to place icon on desktop.
then just cd in to the dir where u installed the game and type: wine diablo\ II.exe / cedega diablo\ II.exe or use the game.exe instead.

---

