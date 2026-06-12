---
title: "Please!! 12.10 Ubuntu installing League of Legends from scratch. Please!!"
date: 2013-08-13
forum: Gaming &amp; Leisure
---

### Post by derek3 on 2013-08-13
Hello Ubuntu Forums,

I recently had windows 7 crash on my Dell Studio 1747 laptop. I am in a unique situation as to where Ubuntu 12.10 is my only option for an Operating system. I live on a military base and have no other means of entertainment other than my favorite game League of legends. I have been reading and watching tutorial after tutorial, but I a beginner when it comes to Linux and that is an overstatement. The only thing I have installed so far is the Adobe Pluggin and playonlinux. Please can anyone give me a detailed *fine detailed* method of installing League of Legends. It would be greatly appreciated!

---

### Post by oldrocker99 on 2013-08-13
Go here: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10436](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10436) where it got a Gold rating.

cd to the directory where the installer is and type

wine [name of installer].exe

And you **should** be good to go.

IF it fails, Steam has a Linux version of DOTA2, a very similar game.

---

### Post by mastablasta on 2013-08-14
there are two problmes with this game. first and major one is that it was made for windows (and i think there is a mac version now but that doens't help. ). SO it will only work propperly in windows. second problem is it has frequent updates. every couple of weeks i believe. so while the game might run nicely in wine in one verison they will do an update (patch) and it will not work anymore. 

bottom line - for windows games use windows.

but you can always mess arround with wine (or play on linux) if you like the frustration every couple of updates.

---

### Post by DarkAmbient on 2013-08-14
> **mastablasta said:**
> i think there is a mac version.

*osx-version ;)


Starting up Ubuntu hoping to bring with you native windows-products is not ideal, even though it's doable. 
There are already several guides on how to install LoL on LoLs forum, like this one: [http://forums.na.leagueoflegends.com/board/showthread.php?t=2020528](http://forums.na.leagueoflegends.com/board/showthread.php?t=2020528)

Instead of installing wine1.3 as mentioned in the guide. Install 1.6 and winetricks.

sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.6 winetricks

---

