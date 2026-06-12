---
title: "Verdana font on KDE"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Eazy© on 2005-12-17
Hi!
just wanted to share a experience I had.
From the first day I installed my first linux-dist (a couple of years ago) I have always thought that the fonts in Linux don't look good, so I always gone back to Windows so I can use my precious Verdana font :)

Enough of that and to the point....

I installed Verdana and Tahoma throgh KDE's controlpanel (I dualboot with windows and installed the fonts from there) and choose to use Verdana all over.
For some reason Verdana wasnt applied everywhere. On some menue there was another linux-font. Whatever I did I couldnt make KDE to use Verdana all the way.

Last night I got an strange idea....what if I uninstall :rolleyes: all other fonts exept Verdana and Thaoma (+ some other Windows-font I installed) and guesse what... that did the trick. I Now have Verdana fonts everywhere :)

I dont know if I will run into any issue because of this in the future, so if someone wants to test this, be advised, I'm still a noob and I dont know what I do most of the time :P

---

### Post by aysiu on 2005-12-17
How did you install Verdana?
Anything wrong with this? ```
sudo apt-get install msttcorefonts
```

---

### Post by Eazy© on 2005-12-17
[QUOTE=aysiu]How did you install Verdana?
Anything wrong with this? ```
sudo apt-get install msttcorefonts
```[/QUOTE]

I installed the Verdana and the other ms-font I wanted from my windows-partition before I knew that I could install from synaptic. I have tried to install the ms-font with "sudo apt-get install msttcorefonts" but still KDE wouldent let me use the Verdana font all over even if I chosed them in the controllpanel. I dont think it would make any difference if I install them with apt, or install them from my window-disk in the controllpanel.

If someone know how I can get KDE to use Verdana all over without uninstall all other linux-fonts I would be grateful.

---

