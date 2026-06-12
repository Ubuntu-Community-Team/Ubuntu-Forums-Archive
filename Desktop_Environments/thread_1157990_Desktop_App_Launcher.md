---
title: "Desktop App Launcher"
date: 2009-05-13
forum: Desktop Environments
---

### Post by vmorgs on 2009-05-13
I recently switched from Vista to Ubuntu and I love it. My only complaint is that I miss the RocketDock desktop application launcher. I've tried GNOME Do and a few others, and while they look good and have decent functionality, I* hate* their fixed position at the bottom of the desktop. Are there any dock style app launchers for Ubuntu that allow you to move them around the desktop?

---

### Post by micio on 2009-05-13
Try AWN (Avant-window-navigator) and Cairo-Dock.
You can get them from synaptic.

---

### Post by vmorgs on 2009-05-13
> **micio said:**
> Try AWN (Avant-window-navigator) and Cairo-Dock.
You can get them from synaptic.
 
I've tried both of them, but I can't move them from their fixed position on the screen. Are they unmoveable or am I doing something wrong? Additionally, Cairo has a black snoflake background that won't go away even when I change the theme. What gives?

---

### Post by fabounet on 2009-05-13
remove completely Cairo-Dock (it is a totally out-dated version) and install Cairo-dock2 fro the official repository.
(see the english wiki on cairo-dock.org)

it is the one that looks the most like rocket-dock, but simply better (and can be placed anywhere on your desktop) ;-)

---

### Post by vmorgs on 2009-05-13
> **fabounet said:**
> remove completely Cairo-Dock (it is a totally out-dated version) and install Cairo-dock2 fro the official repository.
(see the english wiki on cairo-dock.org)
 
it is the one that looks the most like rocket-dock, but simply better (and can be placed anywhere on your desktop) ;-)
 
Ok wow, thanks. I will try that tonight and report back. =) 
 
And, where is the official repository? Is that the Synaptic thing in my Admin menu? If so, I thought's that where I installed Cairo from. I'll double check though.

---

### Post by Favux on 2009-05-13
Hi vmorgs,

Synaptics Package Manager has the official Ubuntu repositories.  The Cairo Dock in them is outdated.  Fabounet wants you to remove it through Synaptics.  Then you could install using the deb.s here:  [http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)  Or better still add the official Cairo Dock repository to Software Sources.  That way you can run Update Manager and Cairo Dock 2.0 will install automatically.  See here:  [http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en](http://www.cairo-dock.org/ww_page.php?p=From%20the%20repository&lang=en)

---

