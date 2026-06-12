---
title: "Failed to install Red Faction"
date: 2006-03-19
forum: Gaming &amp; Leisure
---

### Post by Pyro MX on 2006-03-19
I configured Wine using the winesetuptk package and since it didn't worked, I switched to the Wine package. I also installed XWine and now it seems to work.

Now when I launch the setup.exe from the Red Faction CD, it says: "The InstallShield Engine (iKernel.exe) could not be installed. Write protected." :-k

---

### Post by Pyro MX on 2006-03-22
Not even a small idea? :-(

---

### Post by akiro.yamamoto on 2006-03-23
This site has a little info about  install shield...
[Frank's Corner](http://frankscorner.org/index.php?p=ishield)
I have also heard good reports about this:
[**WineTools**](http://www.von-thadden.de/Joachim/WineTools/)
Hope this helps ;)

---

### Post by Pyro MX on 2006-03-23
[QUOTE=akiro.yamamoto]This site has a little info about  install shield...
[Frank's Corner](http://frankscorner.org/index.php?p=ishield)
I have also heard good reports about this:
[**WineTools**](http://www.von-thadden.de/Joachim/WineTools/)
Hope this helps ;)[/QUOTE]

Installed the stuff needed for installshield, but it doesn't work. I checked the compatible proggys list on WineTools and Red Faction isn't there. But thx for the links tho!

---

### Post by akiro.yamamoto on 2006-03-24
TransGaming has it listed....
[**CLICK ME!!**](http://transgaming.org/gamesdb/games/view.mhtml?game_id=2427)

---

### Post by Pyro MX on 2006-03-24
Yea I know but you must pay for Cedega :mad:

---

### Post by Pyro MX on 2006-04-02
Ohhh it was close! I was able to begin the installation, I was very happy, but then it told me to insert Disc 2... so I ejected using nautilus, and the installation failed there: it was not able to find file on the specified path or filename (and I checked out the path and it was supposed to be OK). Is there something wrong with what I did (I dunno maybe there's a special command to eject the disc while running an installation in Wine)? Any idea?

*We're close!*

---

### Post by YokoZar on 2006-04-02
[QUOTE=Pyro MX]I configured Wine using the winesetuptk package and since it didn't worked, I switched to the Wine package. I also installed XWine and now it seems to work.

Now when I launch the setup.exe from the Red Faction CD, it says: "The InstallShield Engine (iKernel.exe) could not be installed. Write protected." :-k[/QUOTE]
Do not use either winesetuptk or xwine, they break things.

Instead, install the latest Wine (0.9.11), remove your .wine directory with rm -R ~/.wine, and then install your game.

---

### Post by Pyro MX on 2006-04-03
I un-installed the old wine and xwine and installed wine 0.9.11 using Synaptic. It gave me a couple of  error the first time I ran wine (unrotunately I closed the terminal so I don't have any screenshots) they were ole32 errors, anyway... Installed DCOM98 as the Frank's Corner site suggested and tryed to install Red Faction. Now it says "The installShield Engine (iKernel.exe) could not be launched".

In short words, it's worse lol!

---

### Post by Cold Man 1 on 2011-04-19
Alright I got it!!!
What you have to do is copy the files of the cd2 you inserted to a location in ubuntu's dowcuments!
Once that is done then go back to the installation and browse to the folder where you copied the cd's files to. Then press ok and it should work!!!
enjoy :P

---

### Post by sakuramboo on 2011-04-19
Seriously?! 5 year old thread. WTF.

---

