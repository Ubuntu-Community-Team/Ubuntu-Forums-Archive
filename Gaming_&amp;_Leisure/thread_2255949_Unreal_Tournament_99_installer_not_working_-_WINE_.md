---
title: "Unreal Tournament 99 installer not working - WINE or native"
date: 2014-12-08
forum: Gaming &amp; Leisure
---

### Post by Guyofdoom42 on 2014-12-08
I'm trying to install UT99 under Linux - WINE or native - And neither seem to work.

If I use WINE, the installer works just fine, but craps out at the very last second. (Using WINE 1.6.1)

If I copy the files directly off of the disc, the EXE dosen't run.

If I use the native Linux version, it says I need libgtk-1.2.so.0

HELP!

---

### Post by R33D3M33R on 2014-12-09
Take a look at this wiki: [https://help.ubuntu.com/community/Games/Native/UnrealTournament](https://help.ubuntu.com/community/Games/Native/UnrealTournament)

---

### Post by Guyofdoom42 on 2014-12-09
I've problably downloaded that file ten times... Says I need libgtk-1.2

---

### Post by oldrocker99 on 2014-12-09
I found source code for libgtk+-1.2 and tried compiling it myself, and it needs libglib1.2.0. This would indicate that compilation involves what is known as Dependency Hell.

Perhaps someone else might take a swing at it...

---

### Post by Guyofdoom42 on 2014-12-09
Hoooooo boy... I managed to get the installer to work under PlayOnLinux and Wine 1.5.1, but the actual game still dosen't work.

---

### Post by Guyofdoom42 on 2014-12-09
Hoooooo boy... I managed to get the installer to work under PlayOnLinux and Wine 1.5.1, but the actual game still dosen't work.

---

### Post by adec2 on 2014-12-10
If you've got it installed using POL with wine then looking up the winehq for the game will tell you to use version 1.7.30. Just install it using POL and tell the game to use that version

[https://appdb.winehq.org/objectManager.php?sClass=application&iId=90](https://appdb.winehq.org/objectManager.php?sClass=application&iId=90)

---

### Post by Guyofdoom42 on 2014-12-10
I will try that.

---

### Post by Guyofdoom42 on 2014-12-13
Nope. Not working.

Tried 1.7.30, didn't work.

EDIT: Got it working with 32-bit Wine.

---

