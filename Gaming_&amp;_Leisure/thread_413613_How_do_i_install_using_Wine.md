---
title: "How do i install using Wine?"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by Fowlwing on 2007-04-19
I do not have the slightest clue on how to use wine..... and to be honest... im not understanding the manual to use....   I am trying to install an older game called Omikron: The Nomad Soul.....  please help me, i would be grateful, thank you

---

### Post by Kay The Bantu on 2007-04-19
ok i'm assuming you have an exe file, first go to the term and type 
winecfg
you'll get a dialog add your exe file,apply and run the install. next do the winecfg command again and add the executable of the game. hope this helps

---

### Post by Fowlwing on 2007-04-19
can you be more specific as to what i need to do..... i do not understand this whole terminal/ wine concept..  sorry

---

### Post by justin whitaker on 2007-04-19
> **Fowlwing said:**
> can you be more specific as to what i need to do..... i do not understand this whole terminal/ wine concept..  sorry

Sure, it's pretty simple. Open up a terminal (start>accessories), and at the command prompt, type winecfg. That will bring up a tool that allows you to define how WINE works. There is a tab which says install programs or something like that. Click that, and follow the dialog.

---

### Post by 1oki on 2007-04-19
man wine



all you should have to do is type 
wine *.exe 

where as the *.exe is your install executable. 

Wine is pretty standard and you shouldn't have to mess with any config's unless you want to change the install location.

---

### Post by lakersforce on 2007-04-19
First you will have to get the newest version of wine. go to <a href="http://www.winehq.com">www.winehq.com</a>. Choose "Get Wine Now" and fellow the instructions for how to obtain the newest version for Ubuntu.

---

### Post by barmazal on 2007-04-20
is there any decent Gnome interface for wine, ive seen somewhere such app with install uninstall reedit notepad and other option it wasd not for Ubuntu/Debian though and did not work for me.

---

### Post by bluewagon on 2007-04-20
i have a quick question.. im trying to install steam (first time using wine) and im trying to copy tahome.tff to ~/.wine/drive_c/windows/fonts   ... but i can't find the directory at all.. where is it?

---

### Post by zerosystem on 2007-04-20
An interface? You might be talking about WineXS, but AFAIK, it hasn't been updated for a while.

Any folder in your home folder with a period at the front of it's name is hidden by default. Press ctrl+h to temporarily show hidden directories in Nautilus to reveal the .wine folder.

---

### Post by AndrewRiedi on 2007-04-21
> **bluewagon said:**
> i have a quick question.. im trying to install steam (first time using wine) and im trying to copy tahome.tff to ~/.wine/drive_c/windows/fonts   ... but i can't find the directory at all.. where is it?

Make sure you have a ~/.wine directory first.  (You do as long as you have run Wine at least once.)

Then try this if you like nice pretty graphics:  nautilus ~/.wine/drive_c

---

