---
title: "Game on mutual partition"
date: 2016-02-18
forum: Gaming &amp; Leisure
---

### Post by SnuKies on 2016-02-18
Hello guys, 
I've got a question for you:
Currently my laptop has dualboot (Winows 7 Home Premium and Ubuntu 14.04). I also have 3 partitions: "C:" with Windows, "D:" common and "E:" on which is Linux.
Having those facts given, if I will install a game on D, a game that runs on both windows and ubuntu, is it possible to play that game on both operating systems?

---

### Post by potato5 on 2016-02-18
No: if you install the native version
Yes: if you gaming on Linux use Wine

---

### Post by nargaroth_reg on 2016-02-23
> **potato5 said:**
> Yes: if you gaming on Linux use Wine
How would that work? Pointing a wineprefix to the common drive?
What I've tried is copying the game folder between the windows drive and the wine virtual drive and vice versa and it works fine with games that store all files in one folder, like path of exile or world of warships.
In addition you can check this tutorial if the game you want to play is available on steam ([https://nigelmichki.ninja/?p=23](https://nigelmichki.ninja/?p=23)), it does not require moving the game folder.

---

### Post by efflandt on 2016-02-24
Just a point of reference, Steam has many games that work in both Linux Steam or Windows. But to create level maps, Steam's Source SDK or related Hammer editor for Portal2 maps is Windows only. I symlinked my Linux SteamApps to playonlinux virtual drive under Steam. If I previously ran Linux Steam and then run Steam under playonlinux (or vice versa), Steam apparently downloads some files for each game specific to the OS. And since it wanted to do that for all games, I set most games to only update when I run them.

If you use a common NTFS partition for Windows and Linux games, whether the games will run may depend upon mounting options for the NTFS partition in Linux and whether Linux sees certain files as having execute (for game script or binaries) or write permission (for save games). Although, that is probably not an issue for things run in Windows or playonlinux.

---

