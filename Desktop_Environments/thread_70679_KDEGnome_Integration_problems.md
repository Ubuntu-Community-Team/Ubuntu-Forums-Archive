---
title: "KDE/Gnome Integration problems"
date: 2005-09-30
forum: Desktop Environments
---

### Post by Omnios on 2005-09-30
I installed KDE onto Ubuntu a while ago and only over the last few days have managed to play around with it a bit. Anyways I am having some problems with dual MW KDE/Gnome set ups. I had to manualy put in trash.desktop and the home.desktop in kde the problem I am having is that when I log into Gnome the kde desktop stuff appears as links on my gnome desktop and my firefox icon is huge. I can probably go without the firefox icon but the rest of the stuff is pretty standard. I managed to get other issues straghtened out like GTK rendering realy crappy but am at a loss to the links apearing. Also the log out has only log out it does not display shutdown or restart which isnt critical but would be nice. 

 This is an issue as I intend to install Ubuntu Breezy and KDE as a second wm which is a fairly good arangment as they have shared software. This would be a good arangement to allow users to see what wm they like and for people who have family and kids also using there computer (KDE is a bit safer lol) 

Anyways any one else having problems please post then and maybe we may be able to get them addressed.

---

### Post by mlomker on 2005-09-30
Not directly related to your questions, but there was an interesting thread about [integration today.]("http://www.ubuntuforums.org/showthread.php?t=70410")

---

### Post by Knome_fan on 2005-10-01
[QUOTE=Omnios]I installed KDE onto Ubuntu a while ago and only over the last few days have managed to play around with it a bit. Anyways I am having some problems with dual MW KDE/Gnome set ups. I had to manualy put in trash.desktop and the home.desktop in kde the problem I am having is that when I log into Gnome the kde desktop stuff appears as links on my gnome desktop and my firefox icon is huge. I can probably go without the firefox icon but the rest of the stuff is pretty standard. I managed to get other issues straghtened out like GTK rendering realy crappy but am at a loss to the links apearing. Also the log out has only log out it does not display shutdown or restart which isnt critical but would be nice. 
This is an issue as I intend to install Ubuntu Breezy and KDE as a second wm which is a fairly good arangment as they have shared software. This would be a good arangement to allow users to see what wm they like and for people who have family and kids also using there computer (KDE is a bit safer lol) 
Anyways any one else having problems please post then and maybe we may be able to get them addressed.[/QUOTE]

Hm, about the log out issue, I don't think there is much you can do. If you run Gnome from kdm, Gnome will not have options to shutdown or reboot and if you run KDE from gdm you'll have the same problem.

About putting icons on the desktop.
I remember that I also had this problem. However, I don't have it anymore as I placed both, home and trash on the panel. I think this is the easiest and cleanest solution for this problem.
If however you want to keep the on the kde desktop, there is a really dirty workaround:
In Gnome, simply make the offending file icons as small as possible and hide them behind a panel. Dirty, I know, but it worked for me.

---

