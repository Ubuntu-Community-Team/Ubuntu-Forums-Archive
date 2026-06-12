---
title: "Gnome and KDE font problems on 7.10 Ubuntu"
date: 2007-10-21
forum: Desktop Environments
---

### Post by Tekno_Cowboy on 2007-10-21
I'm having font problems in KDE and Gnome. It seems that when I get all the fonts correct in Gnome, the fonts in KDE for some things are waaay too small for my 1360x768 32" HDTV. If I get most of the fonts correct in  KDE, the fonts go way too big in Gnome. Does anyone know how to make sure they stay the same in both? Does anyone know the files these settings are stored in, so I could manually edit them?

I noticed Sabayon runs both without issues, and I intend to post on their forum to see if they have a fix for this issue. If I find one I'll post it here.

---

### Post by anal.expert on 2007-10-22
Same problem here. The font is so small in Gutsy KDE that I cant even read it on my 42" plasma. Cant seem to set it right although I did notice that if I set the resolution in Gnome to less than 1020*768 that the font size in KDE is WAY huge. Is there no middle ground? I should also note that the font problem is not in application windows like terminal etc. but in menus, icon text, log on screen etc. Please help if you have any info as I cannot use KDE until such time. Glad that Gnome with compiz fusion kicks so much *** that it doesn't really bother me at this time. Also, I have not posted a bug on this yet.

---

### Post by Tekno_Cowboy on 2007-10-22
If you set the fonts in KDE very small, you can get Gnome to work fine, but no matter what I do, I can't get the login screen to display right. Does anyone know which files contain the resolution/text size config info for the login screen?

---

### Post by Tekno_Cowboy on 2007-11-06
I managed to solve this problem by simply installing Kubuntu. For some reason, as long as I install everything from KDE, everything works fine in both Gnome and KDE.

---

### Post by ariel on 2008-01-21
> **Tekno_Cowboy said:**
> I managed to solve this problem by simply installing Kubuntu. For some reason, as long as I install everything from KDE, everything works fine in both Gnome and KDE.


I had the same problem, for some reason kde apps fonts got unreadably small, I guess after an upgrade. I followed your solution (sudo apt-get install kubuntu-desktop) and that fixed the problem.

Thanks!

---

