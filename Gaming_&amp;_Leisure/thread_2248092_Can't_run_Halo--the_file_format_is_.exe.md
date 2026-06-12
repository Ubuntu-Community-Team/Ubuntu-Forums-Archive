---
title: "Can't run Halo--the file format is .exe"
date: 2014-10-12
forum: Gaming &amp; Leisure
---

### Post by kccv42 on 2014-10-12
I have the game Halo which is in the format of .exe.I played it in windows before i got linux. I had an unsuccessful time trying to run the game with wine maybe because it removed a driver called Nvidia legacy binary. It gives me "error needs at least 2 mb  of temp". I  tried to use playonlinux to run the game but could not figure out how to install a non listed game.

---

### Post by Toz on 2014-10-12
Which version of PlayOnLinux are you running? Which version of Halo are you trying to install?
Halo Combat Evolved is available on POL 4.2.5 (not sure about other versions).
[ATTACH=CONFIG]257151[/ATTACH]

> I tried to use playonlinux to run the game but could not figure out how to install a non listed game. 
If you click on install, there will be a "Install a non-listed program" link in the bottom left of the dialog that shows up.

---

### Post by oldrocker99 on 2014-10-12
He's right, you know.

---

### Post by kira-yamato-2008 on 2014-10-12
You should also take a good look at one of these two WineHQ AppDB pages: [Halo: Combat Evolved,]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=1986") or [Halo Custom Addition]("https://appdb.winehq.org/objectManager.php?sClass=application&iId=7906"). Depending on which version you have. Also to custom install a non-listed application, the option won't come up if PlayOnLinux had to refresh the list, so you'll have to close the install list then open it again to get the option to show up. Both versions of Halo show up as Platinum by the way, which is (nearly)perfectly operational. But check the page for your version as there maybe some bugs you need to address for the game to run correctly in Wine.

Another option you might want to look into if you have a Windows Disc with valid activation (XP/Vista/7/8) is to install Windows on a Virtual Machine (VMWare Player or Oracle Virtualbox both of which are free for personal use.) Which will give you a native version of Windows to play on inside Linux rather than running the software in emulated environments like Wine.

---

