---
title: "ut 2004 patch"
date: 2008-08-17
forum: Gaming &amp; Leisure
---

### Post by chiefgeargrinder on 2008-08-17
I managed to install ut2004 in ubuntu 8.4 was quite a mission since I have only 2 weeks experience with linux. cant figure out how to patch it.
I downloaded the mega pack for linux but it gives me a tzo file.not really sure where to unzip that. the files doesn't seem to have a installer.
also the mouse has a mind of its own which makes it very unpleasent to play.is there a mouse fix? also where to you unzip the files to?

---

### Post by Perfect Storm on 2008-08-17
example takes that you have the patch on Desktop and you installed UT2004 at /usr/local/games/ut2004

```
cd ~/Desktop
tar jxfv ut2004megapack-linux.tar.bz2 
cd UT2004MegaPack
sudo cp -r * /usr/local/games/ut2004
```

---

### Post by chiefgeargrinder on 2008-08-17
> **Artificial Intelligence said:**
> example takes that you have the patch on Desktop and you installed UT2004 at /usr/local/games/ut2004

```
cd ~/Desktop
tar jxfv ut2004megapack-linux.tar.bz2 
cd UT2004MegaPack
sudo cp -r * /usr/local/games/ut2004
```

thanks for the reply the first 3 commands worked unziped the file to desktop but the last command sudo cp -r */usr/local/games/ut2004 says no such directory. I have the game installed in the home folder/usr local/games/ut2004 so shouldnt that command you gave me work?

---

### Post by Perfect Storm on 2008-08-17
Have you checked if it's the correct path?
/usr/local/games/ut2004 is not your home folder, so if you have installed it in a diffrent place you have to change the last command line.

sudo cp -r * <your ut 2004 path>

---

