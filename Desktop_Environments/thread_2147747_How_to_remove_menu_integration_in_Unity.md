---
title: "How to remove menu integration in Unity?"
date: 2013-05-22
forum: Desktop Environments
---

### Post by seruling on 2013-05-22
How to remove menu integration in Unity?
It makes my work with LibreOffice a lot of slower than normal menu.
anyway, how to completely remove the unity, and change to gnome?
Unity kills LO mnemonic keyboard for menu, and kills **all** "Alt+" keyboard shortcut :(. I don't know this is Unity bug or feature?

---

### Post by galgalesh on 2013-05-23
Remove global menu in Libreoffice: [http://askubuntu.com/questions/206448/how-do-i-disable-app-menu-in-libreoffice](http://askubuntu.com/questions/206448/how-do-i-disable-app-menu-in-libreoffice)

---

### Post by galgalesh on 2013-05-23
Install classic gnome (old gnome interface): [http://www.liberiangeek.net/2013/04/no-unity-here-enable-classic-gnome-in-ubuntu-13-04/](http://www.liberiangeek.net/2013/04/no-unity-here-enable-classic-gnome-in-ubuntu-13-04/)

Install Gnome shell (new gnome interface): sudo apt-get update && sudo apt-get install gnome-shell ubuntu-gnome-desktop(I think this is in the default repo's, no need for a ppa)


I personally had a lot of problems with gnome shell in Ubuntu, weird crashes and such. I hope you have more luck.

---

### Post by seruling on 2013-05-23
Thank you for your advice.

I read some user experience installing gnome in ubuntu desktop, and they get some crash problem. And I think it better to install clean Ubuntu-Gnome edition instead of adding extra environment.
I already download the ubuntu gnome edition from ubuntugnome.org but not yet install it.
 
My work with Libre office a lot of slower because the "Alt+..." shortcut were dead, and the LibreOffice main menu is dead as well. I think this is Unity bug.
I try ubuntugnome in live USB, and didn't find any problem.

I will try to replace my current Ubuntu desktop with ubuntu gnome edition.

Thank You

---

### Post by vanadium on 2013-05-23
In 13.04, removing global menu disables the (albeit limited) File menu of nautilus. Thus, it cripples gnome3 applications, although the impact of that is limited yet.

I currently install LibreOffice from the tar.gz downloads on the LO website. For a reason unknown, that version does not use the Unity global menu, yet it (mostly) integrates very well in the desktop otherwise. Thus, you can keep the Unity global menu, and have the traditional, normally functioning menu in LO. There is a glitch, though: all instances of LibreOffice are grouped under one launcher on Unity, e.g. both a Calc windows and a Writer window could be under a Calc icon or under a Writer icon, dependent on what you launched first.

This does not work using the PPA of LO: a version installed using the PPA does use the Unity global menu.

---

### Post by galgalesh on 2013-05-23
I tried the clean Ubuntu Gnome but it crashed a lot. I had the same problems with installing Gnome over normal Ubuntu and with Gnome on Fedora. I think it's a Gnome problem...

---

