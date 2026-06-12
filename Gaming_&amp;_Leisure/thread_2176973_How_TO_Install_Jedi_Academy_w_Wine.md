---
title: "How TO Install Jedi Academy w/ Wine"
date: 2013-09-26
forum: Gaming &amp; Leisure
---

### Post by elundmark on 2013-09-26
I had some problems installing [this game]("http://en.wikipedia.org/wiki/Star_Wars_Jedi_Knight:_Jedi_Academy"), and after searching for any solutions out there I found that I wasn't alone. I was [surprised]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1713") to find that it does install pretty easily, and runs bloody well. I compared the performance with the open sourced version of [Jedi Outcast]("https://github.com/xLAva/JediOutcastLinux"), and considering that Jedi Academy is a bit more resource heavy, it's close to native speeds.

So, the problem I noticed many had, is the installer, because there are 2 CDs, and switching cds in Wine is always a problem, especially when you're mounting them as iso's. Beware that this solution requires you to use a "NoCd" exe, but since you own the original game you have nothing to worry about. Follow these steps:


[LIST=1]
[*]Pop in the CDs and [convert them to iso images]("http://askubuntu.com/questions/136165/how-to-create-iso-images"). 
[*]Install and launch [Furius ISO Mount]("https://launchpad.net/furiusisomount"). 
[*]Mount each iso image, and keep the application open throughout this process. 
[*](Install Wine) and launch **winecfg** ("Configure Wine"). 
[*]In **winecfg**, select the tab Drives and click "Add", select a drive letter and "Browse" for the folder where the iso is mounted (for me it was /home/me/swjacd1). Then click "Show advanced" and select CDROM as the Type. Repeat these steps for CD2. Then click "Ok". 
[*]Now open */home/me/swjacd1* in ex. nautilus and launch **autorun.exe**. Click "Install" and wait for it to ask for CD2. 
[*]This installer is nice enough to give you a path to the CD, so all you have to do now is change the drive letter. So say CD1 is in D:\ and CD2 in E:\, change "D:\GameData" so it says "E:\GameData". Hit "Ok". 
[*]Once the installer has finished it will ask you to change CD again to CD1. You know what to do. 
[*]Before you can launch the game you need to replace the installed **jasp.exe** with the one found in the NoCd package (link further down). For me this file was installed here: */home/me/.wine/drive_c/Program\ Files/LucasArts/Star\ Wars\ Jedi\ Knight\ Jedi\ Academy/GameData/jasp.exe* 
[*]Once you have the new exe in place, you can unmount the iso's in **Furious ISO Mount** and exit the app. Don't launch the game with the installed shortcut, instead launch it with a desktop file (code further down). Or, if you prefer, open nautilus and open **jasp.exe** normally. 
[/LIST]

_**Launching the game**_

Create a file and name it star-wars-jk-jedi-academy.desktop, save it in *~/.local/share/applications/*
*Remember to edit the paths in the code below to match your local installation.*

```
[Desktop Entry]
Name=Launch Star Wars JK Jedi Academy
Path=/home/me/.wine/drive_c/Program Files/LucasArts/Star Wars Jedi Knight Jedi Academy/GameData
Exec=env WINEPREFIX="/home/me/.wine" wine C:\\\\Program\ Files\\\\LucasArts\\\\Star\ Wars\ Jedi\ Knight\ Jedi\ Academy\\\\GameData\\\\jasp.exe
Type=Application
StartupNotify=true
```

Then open a terminal and run [COLOR=#a52a2a]chmod +x ~/.local/share/applications/star-wars-jk-jedi-academy.desktop[/COLOR]

_**Performance**_

I made the mistake to enable everything in the Video options, thinking my laptop from 2008 with integrated graphics could handle it. Didn't work out to well. I had to disable "Detailed Shader" to get a smooth framerate. Just a heads up. With that turned off it runs FAST.

_**NoCd info**_

I tried several diff ones from [gamecopyworld.com]("http://www.gamecopyworld.com") and found this to work best. Navigate to the PC game section and look for Jedi Academy, then look for "Jedi Academy v1.0 *FINAL* SP/MP [ALL] No-CD/Fixed EXE #1" [gruswjkafcd.rar 519KB].

Yes I will add this result to winehq a.s.a.p., it truly deserves a better grade than Silver.
Hope you found this useful, sharing is caring!

---

### Post by mastablasta on 2013-09-27
cool.

only why would instaling from CD present a problem? i know it's just a command you add when you launch install. like in diablo. and then when it promtps you to change CD oyu just change it.

---

