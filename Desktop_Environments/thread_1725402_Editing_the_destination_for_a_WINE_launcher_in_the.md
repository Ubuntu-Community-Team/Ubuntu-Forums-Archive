---
title: "Editing the destination for a WINE launcher in the Applications menu?"
date: 2011-04-09
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-04-09
I would like to edit the destination a launcher which opens a program using WINE. It is *Applications* >> *Wine* >> *Programs* >> *World of Warcraft* >> *World of Warcraft*.

When I use *Edit Menus* to check the launcher properties I learn it is set as *Type: Application*, and *Command: wine "/home/laeg/.wine/dosdevices/c:/Program Files/World of Warcraft" -opengl*.

How would I instead have it point directly at opening, with WINE, */home/dusf/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe*?

The -opengl argument shouldn't matter as I have it preconfigured to run with opengl in the config.

If relevant, when I navigate to *c:/Program Files/World of Warcraft/, *and open *Wow.exe *manually, it opens using WINE automatically.

---

### Post by Dáire Fagan on 2011-04-11
Setting the *Command* to *"/home/dusf/.wine/drive_c/Program Files/World of Warcraft/Wow.exe"* opens it just the same way as it did before. It seems to open first */home/dusf/.wine/drive_c/Program Files/World of Warcraft/Launcher.exe* which in turn then runs the main game when you click a button to play. I want it to go directly into the game bypassing the launcher.

If I navigate with nautilus to the directory and manually open *Wow.exe* like any other program it skips the launcher, as it does when I right click it and click *Open With Wine Windows Program Loader*.

Is there anyway I can make the launcher in my *Applications* menu open it the same way?

---

