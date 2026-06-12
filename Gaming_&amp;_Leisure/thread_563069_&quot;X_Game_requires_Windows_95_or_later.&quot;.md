---
title: "&quot;X Game requires Windows 95 or later.&quot;"
date: 2007-09-29
forum: Gaming &amp; Leisure
---

### Post by Ghostlove on 2007-09-29
Having successfully converted a Luddite friend to Ubuntu, I am having a hard time doing what I promised I could - running his two best-loved games through WINE.

The two games are Theme Hospital and Age Of Empires III. Don't laugh, this is serious stuff. ;)

I installed WINE, open the CD, click setup.exe and it goes to try and install before telling me that the game requires Windows 95, NT or later to work.

I have already seen a thread where someone mentions playing Age Of Empires through WINE so evidently it can be done. Tell me, oh Oracle, what am I doing wrong? :confused:

---

### Post by Steveway on 2007-09-29
How about opening winecfg and setting the operating system to 98 or something like that?

---

### Post by cogadh on 2007-09-29
Use the terminal to initially run applications with Wine, don't use the "double-click" method. When run from the terminal, any errors produced by Wine are output to the terminal, which can then be used to troubleshoot the problem. Once you have an application installed, configured and running correctly, then you can create a shortcut to run the application regularly.

As Steveway said, after you install Wine, you need to run "winecfg" in the terminal to create the initial Wine directories and configure your default settings. After you have run "winecfg", install the game like this:
```
wine /media/cdrom/setup.exe
```
Once you do that, post back with any results, including any errors produced in the terminal.

Oh, and since you are new to Wine, you might want to check out the "Stuff I've learned about Wine" link in my sig.

---

### Post by jasay on 2007-09-29
Winehq.org has a large database of what programs work in wine, how well and how to install them.  
Age of Empires looks like it should work . . ..  I'm not so sure about Theme Hospital.

Theme Hospital beta version:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1279](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1279)
Full release:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9212](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9212)

Age of Empires III:
[http://appdb.winehq.org/appview.php?iVersionId=3795&iTestingId=14831](http://appdb.winehq.org/appview.php?iVersionId=3795&iTestingId=14831)

---

