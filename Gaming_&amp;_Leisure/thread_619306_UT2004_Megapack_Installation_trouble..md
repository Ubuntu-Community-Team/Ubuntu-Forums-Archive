---
title: "UT2004 Megapack Installation trouble."
date: 2007-11-21
forum: Gaming &amp; Leisure
---

### Post by DarkSim on 2007-11-21
I was setting up UT2004 following this great guide :
[http://gaming.gwos.org/doku.php/guides:ut2004dvd?s=unreal%20tournament%202004](http://gaming.gwos.org/doku.php/guides:ut2004dvd?s=unreal%20tournament%202004)

I installed the game without a hitch.Now I am trying to add the Megapack mentioned. When i use the ```
sudo mv * /usr/local/games/ut2004
``` command I get these errors:
```
mv: cannot move `Animations' to a subdirectory of itself, `/usr/local/games/ut2004/Animations'
mv: cannot move `Help' to a subdirectory of itself, `/usr/local/games/ut2004/Help'
mv: cannot move `Maps' to a subdirectory of itself, `/usr/local/games/ut2004/Maps'
mv: cannot move `Music' to a subdirectory of itself, `/usr/local/games/ut2004/Music'
mv: cannot move `Sounds' to a subdirectory of itself, `/usr/local/games/ut2004/Sounds'
mv: cannot move `Speech' to a subdirectory of itself, `/usr/local/games/ut2004/Speech'
mv: cannot move `StaticMeshes' to a subdirectory of itself, `/usr/local/games/ut2004/StaticMeshes'
mv: cannot move `System' to a subdirectory of itself, `/usr/local/games/ut2004/System'
mv: cannot move `Textures' to a subdirectory of itself, `/usr/local/games/ut2004/Textures'
mv: cannot move `Web' to a subdirectory of itself, `/usr/local/games/ut2004/Web'

```

I know I'm overlooking something simple. Anyone help me out? I want to get this setup for the kids coming over tomorrow for Thanksgiving. Thanks in advance for any help.

---

### Post by wishyjr on 2007-11-21
By the way -did you just extract the files to a directory and then run the move command about to put them into the game's directory?

---

### Post by stuart.crouch on 2007-11-21
You definitely extracted it to your desktop?  that message seems to imply you extracted it into the /usr/local/games/ut2004 directory

Try doing it with a folder copy from the desktop - so put the megapack on your desktop, launch a terminal and run the following 3 lines.


```

cd ~/Desktop
tar -xvjf ut2004megapack-linux.tar.bz2
sudo cp -r UT2004MegaPack/* /usr/local/games/ut2004/

```

If it goes wrong, grab everything from the console and paste it here.

---

### Post by buffalotrace34 on 2007-11-21
You could also press alt+F2 then:

```

gksudo nautilus

```

then just browse to where you extracted the megapack and copy then paste all folders to the ut2004 install directory overwriting all.

---

### Post by Vitamin-Carrot on 2007-11-21
Is that the Zip version?

I know theres a linux specific version of the pack available [here](http://www.3dgamers.com/dlselect/games/unrealtourn2k4/Missions/ut2004megapack-linux.tar.bz2.html)

---

### Post by DarkSim on 2007-11-25
Sorry for the delay.I got caught up with the holiday madness. I definitely extracted it to my desktop. The copy idea stuart.crouch posted seemed to work. I wonder why the move command wouldn't work? Anyways, thanks for the fix.

---

