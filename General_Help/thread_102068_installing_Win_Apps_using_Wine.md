---
title: "installing Win Apps using Wine"
date: 2005-12-11
forum: General Help
---

### Post by Gary Lambert on 2005-12-11
I need a more coprehensive user friendly guide on installing win appps with wine Iam able to get to the add apps windows menu but I am not sure how to proceed.

---

### Post by MetalMusicAddict on 2005-12-11
With WINE properly installed you can use the install .exe like in windows. Exactly what is your problem?

---

### Post by Gary Lambert on 2005-12-11
I am not sure what I am doing wrong and was looking for some instructions.  I can't seem to get the wins apps to execute.  I am sure I am missing a step somewhere.

---

### Post by aysiu on 2005-12-11
[QUOTE=Gary Lambert]I am not sure what I am doing wrong and was looking for some instructions.  I can't seem to get the wins apps to execute.  I am sure I am missing a step somewhere.[/QUOTE] I'm going to assume two things here:

1. You already have Wine installed
2. You have setup.exe for a Windows program

Double-click on the setup.exe file and the installer wizard should pop up.
Go through the wizard, just as you would in Windows.

You're going to do something a little bit different, though. The wizard will most likely want to install it to C:\Program Files\Program_Name
You should install it instead to z:\home\gary\.wine\drive_c\Program Files\Program_Name

.wine is a hidden directory, by the way. If you have a file browser window open, you can hit control-h to see it and its contents.

Then, to launch the program, you go to z:\home\gary\.wine\drive_c\Program Files\Program_Name and double-click the appropriate .exe file there. That's it.

If you want to create a launcher for it, make this the command: ```
wine "z:\home\gary\.wine\drive_c\Program Files\Program_Name\Program_Name.exe"
```

---

### Post by Qrk on 2005-12-11
Another thing, that Aysiu forgot to mention. Did you install the windows installer? Some programs use the windows installer, which is a separate program for installation. (Remember installsheild from your windows days?) 

Fortunatly there is a setup program that will install these programs. Its called winetools. Its available in the repositories.

---

### Post by aysiu on 2005-12-11
[QUOTE=Qrk]
Fortunatly there is a setup program that will install these programs. Its called winetools. Its available in the repositories.[/QUOTE] Can I ask *which* repositories it's in? I don't see it in the standard Ubuntu ones (or Universe or Multiverse)...

---

### Post by Qrk on 2005-12-11
Sorry... its in the wine hq repository. 

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

