---
title: "Opened Windows not filling desktop - gap at top"
date: 2009-10-12
forum: Desktop Environments
---

### Post by webheadjunky on 2009-10-12
Hi
Running Kubuntu Jaunty KDE 4.3.2
Noticed a new problem yesterday in that for some reason, any new window I open falls a little short of the tp edge of the screen
YetI can resise it manually to fill the screen???
I have attached a screenshot for info
It's almost as if there is an invisible toolbar at the top....
Hope someone can help
Cheers
Raaj

---

### Post by webheadjunky on 2009-10-17
Hell-ohh!!
Any kindly knoweldgeable user out there who has any ideas to help me out here??
Cheers
Raaj

---

### Post by s3a on 2009-10-17
Click on the square on the top right of the window.

---

### Post by webheadjunky on 2009-10-20
Hi there
Clicking on the middle square minimises the window

---

### Post by webheadjunky on 2009-10-23
Thanks for nothing folks! Guess I'll keep on Googling.....Linux fans always say Linux support is great but sadly my experience doesn't reflect that :(

---

### Post by NovaWasp on 2009-10-23
Looks to me like you have a panel with opacity set to 0% and the window is maximised but bumping up against your top panel.

---

### Post by webheadjunky on 2009-10-23
Hey thanks
But if that was the case, would I not be able to unlock widgets and right click on it??
At present,, right clicking in that area is no different from right clicking elsewhere on the desktop
Cheers
Raaj

---

### Post by Zorael on 2009-10-24
Curious.

You could try restoring to plasma defaults and see if there's something wrong with the settings, I guess. The files are at **~/.kde/share/config/plasma***, and I think they need to be replaced when plasma itself isn't running (as quitting plasma would save the current settings).

Do it manually by closing the plasma-desktop process with ksysguard or **kquitapp plasma-desktop**, and then delete/rename/move the files elsewhere. Then rerun plasma-desktop via a run box. Or just do the following in a terminal.
```
$ kquitapp plasma-desktop
$ mkdir ~/plasmabackup
$ mv ~/.kde/share/config/plasma* ~/plasmabackup
$ plasma-desktop
```
You should get the same widget setup as you had after installion.

kquitapp is part of kdebase-runtime so you should have it, else just use pkill.

---

### Post by webheadjunky on 2009-10-26
HELP!! Just booting into darkness now with only my cairo dock visible:(

---

### Post by webheadjunky on 2009-10-26
OK...managed to overcome my last problem by removing and re-installing plasma-dataengines-addons

Have a new problem now in that add widgets is missing losts of basic widgets like lancelot and picture frame and comics etc

Managed to find some via Adept but not all

Worse still, when I get my desktop looking the way I want it, I reboot back into the standard blue desktop and all my customisations are gone

I have tried deleting the plasmarc and desktoprc files but it made no difference

Any ideas?

Thanks

Raaj

---

### Post by webheadjunky on 2009-10-28
Ok, fixed this myself after much googling and tinkering about
Cheers
R

---

