---
title: "KDE problems"
date: 2007-01-11
forum: Desktop Environments
---

### Post by Caligula on 2007-01-11
hi all.
I seem to have a strange problem with KDE. After i'm deleting some programs i still see them on the KDE menu, even after i've deleted the menu edit file. I suppose their *.desktop files have somehow stayed on the system, but why? and where?

another side affect of that is that for example when i right-click on an image in konqueror i can still see "edit with GIMP" even though i don't have GIMP installed. Or in konqueror i have an option of "open this location with firefox". And so on. :confused: 

Why does that happen? and how can I fix it?

thanks, :D 
Josh

---

### Post by kerry_s on 2007-01-11
Thats just how it is. Sometimes you have to log out and back in for the menu to update. The other thing is just the stock settings, you can right click and change the file association to what you want it to be. There's no real cure for kde's little quirks, you just learn to work around them. There will usually be a setting for everything in kde you just have to find it. ;)

---

### Post by Caligula on 2007-01-11
> **kerry_s said:**
> Thats just how it is. Sometimes you have to log out and back in for the menu to update. The other thing is just the stock settings, you can right click and change the file association to what you want it to be. There's no real cure for kde's little quirks, you just learn to work around them. There will usually be a setting for everything in kde you just have to find it. ;)

Thanks, I never though of messing with the file associations. What is the stick settings?

this reminds me too much of windows' registry problems, only here there is no registry to edit](*,) 

I have logged out of KDE many times by now, it's a consistent problem.
And how can I make konqueror realise firefox is not installed?

---

### Post by mjfleck2000 on 2007-01-11
[QUOTEAnd how can I make konqueror realise firefox is not installed?[/QUOTE]
> 
After i'm deleting some programs i still see them on the KDE menu, even after i've deleted the menu edit file. I suppose their *.desktop files have somehow stayed on the system, but why? and where?
Just checking here(I'm not sure of your knowledge level), you say that firefox (and the gimp) are not installed.  Did you remove them from your Kmenu, or did you uninstall the programs?
If you only removed them from the menu, but the programs are still installed, you will continue to see references to them in the right-click menus.

You could go to a command prompt and type "dpkg -l |grep gimp".  If you get back  something like "gimp                                   2.2.13-1ubuntu3                      The GNU Image Manipulation Program" then the gimp is still installed.

---

### Post by Caligula on 2007-01-11
> **mjfleck2000 said:**
> [QUOTEAnd how can I make konqueror realise firefox is not installed?

Just checking here(I'm not sure of your knowledge level), you say that firefox (and the gimp) are not installed.  Did you remove them from your Kmenu, or did you uninstall the programs?
If you only removed them from the menu, but the programs are still installed, you will continue to see references to them in the right-click menus.

You could go to a command prompt and type "dpkg -l |grep gimp".  If you get back  something like "gimp                                   2.2.13-1ubuntu3                      The GNU Image Manipulation Program" then the gimp is still installed.[/QUOTE]


Thanks, but i'm pretty certain they're not installed, they don't open, and i'm removed them in synaptics, and even purged them :P

---

