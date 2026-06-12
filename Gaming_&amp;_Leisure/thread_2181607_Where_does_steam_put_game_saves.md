---
title: "Where does steam put game saves?"
date: 2013-10-18
forum: Gaming &amp; Leisure
---

### Post by jumpingclear on 2013-10-18
I have 2 games installed on Steam that don't sync to the cloud (although one should) and I want to copy the game saves to transfer when I reinstall but I can't find them. 

I have been searching through everywhere I can think of with no luck so any help appreciated.

thanks

---

### Post by mcse2000ca on 2013-10-20
Not too sure about saves but the games are in /home/"*yourusername"*/.local/share/Steam/SteamApps/common

---

### Post by dannyboy79 on 2013-10-20
i too am wondering this for the game Shank 2. I installed it originally using the Ubuntu Software Center and played it a lot. The saves are in ~/.klei/shank2/users and I want to move those into where ever steam saves the game so that maybe I can get all the steam achievements. I installed shank 2 via steam and I can see the game itself within ~/.local/share/Steam/Steamapps/common and then game name is it's own folder but i don't see any sub-folder which has any game saves.

---

### Post by paulmckellar on 2013-10-21
it depends on the individual games. they're not neccessarily in the steam folder... duke 3d megaton edition for example puts them in ~/.jfduke3d

---

### Post by Ranko Kohime on 2013-10-21
> **paulmckellar said:**
> it depends on the individual games. they're not neccessarily in the steam folder... duke 3d megaton edition for example puts them in ~/.jfduke3d
This.  They're all over the place.

OP, you can search for them in your home directory, or take the brute force method and backup your ENTIRE home directory before you reinstall.  If you say which games they are, if I know where they are I'll tell you.  I keep a spreadsheet with locations of mine because I have Steam on 2 Linux computers that I synchronize.  :)

---

### Post by MikeCyber on 2013-10-21
If I remeber correctly I've moved games to another partition and did a symlink.

---

### Post by efflandt on 2013-10-21
When I tried a free weekend of Killing Floor it apparently put its files in ~/.killingfloor. A current single player Steam game I have called Salvation Prophecy put its files in ~/.local/share/salvation. But both also have folders under ~/.local/share/Steam/SteamApps/common/.

And Steam itself keeps some things including symlinks in ~/.steam

---

### Post by Ranko Kohime on 2013-10-23
Are there any actual files in ~/.steam?  I was under the impression they were ALL symlinks.

---

### Post by MikeCyber on 2013-10-24
Yes only links. For moving the games do like me:

[http://ubuntuforums.org/showthread.php?t=2182681](http://ubuntuforums.org/showthread.php?t=2182681)

---

