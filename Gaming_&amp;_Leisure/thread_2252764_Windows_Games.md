---
title: "Windows Games?"
date: 2014-11-14
forum: Gaming &amp; Leisure
---

### Post by peterkirylo on 2014-11-14
Is there a way to run windows games on Ubuntu?:confused:

---

### Post by slickymaster on 2014-11-14
*Moved to the ***Gaming & Leisure**[I] sub-forum

[/I]Here are a few starter points:
[Games/Emulators]("https://help.ubuntu.com/community/Games/Emulators")
[Steam]("http://store.steampowered.com/about/")
[Humble Bundle]("https://www.humblebundle.com/")

---

### Post by oldrocker99 on 2014-11-14
First, open a terminal and install wine:
```
sudo apt-get install wine
```
Then go here:[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html), and download the Ubuntu version (which is newer than the version in the Ubuntu repositories).
Then, assuming it got saved to youe Downloads folder,
```
cd Downloads
sudo dpkg -i PlayOnLinux_4.2.5.deb
```
PlayOnLinux will properly install a raft of Windows programs, including games. It does **not** work on everything, so look to see what game you want to install. If it's from GOG.com, it'll even download the installation files, if it's in your GOG library. If it's a Steam game in your Steam library, it will install Steam for Windows, from which you can install that program.

As said above, Steam for Linux has over 800 games for Linux, and is highly recommended for any Linux gamer.

Good luck!

---

### Post by Mark Phelps on 2014-11-14
Windows games generally do not work well in Linux, even with Wine and POL.  IF you have some specific games in mind, BEFORE you go through all this work, go to the WineHQ website, the application compatibility section, and do searches for the games and versions you want to install.  Anything not listed, or rated lower than Gold, is essentially going to be a waste of your time installing.

---

### Post by adec2 on 2014-11-14
> **Mark Phelps said:**
> Windows games generally do not work well in Linux, even with Wine and POL.  IF you have some specific games in mind, BEFORE you go through all this work, go to the WineHQ website, the application compatibility section, and do searches for the games and versions you want to install.  Anything not listed, or rated lower than Gold, is essentially going to be a waste of your time installing.

I think that very much depends on what era windows games you play. I have bought over 700 games from the 1998 - 2006 era and a vast majority of them work fine. Of course mileage may vary and by distribution BUT windows games generally do not work well in Linux is far off the mark unless you haven't used wine for years

---

### Post by oldrocker99 on 2014-11-14
I have always had a couple of dozen games I've gotten from GOG.com running with PlayOnLinux, for some years now. Many, many games from 1990 to 2005, or so, run very well with wine. The Inifinty Engine games (Baldurs Gates, Icewind Dales, Planescape:Torment) have been working well with wine since 1999, when I first heard about wine and what it does. **Mark Phelps,** I didn't think I was making him do "all this work." I made my instructions as easy as possible for the OP to follow.

This being said, there is also a raft of Windows programs that don't run very well at all on wine, or don't run at all. [https://appdb.winehq.org/](https://appdb.winehq.org/) will go a long way to point out what runs and what doesn't.

---

