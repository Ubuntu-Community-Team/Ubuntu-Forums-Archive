---
title: "How to make OOo 3.2 look native under Gnome"
date: 2010-10-07
forum: Desktop Environments
---

### Post by Toxicbits on 2010-10-07
Hi,

I have the problem that the OpenOffice UI looks ugly and I don't know how to fix it. I had installed LibreOffice, but as I had problems with the repository I removed it again and reinstalled OOo. I'm sure it didn't look this way before and now I wonder how to make it look native again?

Thanks in advance Toxicbits

[IMG]http://dl.dropbox.com/u/12598822/Bildschirmfoto-6.png[/IMG]

---

### Post by jurco on 2010-10-07
Hi Toxicbits,
your openoffice looks just the way it should look. Used icons are from the most recent version 3 ([evolution of icons here]("http://ui.openoffice.org/VisualDesign/OOo_icon_evolution.html")) and I dont know how to change then ;) If you complain about icon size, you can change to smaller icons (in settings - I dont have OpenOffice here right now), I use small icons too, the UI feels much better for me. And other things like border around the page and other are customizable, I dont use the border for example (disable in settings). Try to play with those settings and give us feedback.

---

### Post by mcduck on 2010-10-07
Check that you have the "openoffice.org-gtk" -package installed. That's the one responsible of applying your GTK theme to OpenOffice. (You probably want at least openoffice.org-gnome as well, in case it's missing).

What comes to icons, they can be changed if you go to Tools/Options,and then to OpenOffice.org/View. Different icon sets for OO.org are available as separate packages through the repositories, for example the Human icons are in the "openoffice.org-style-human" -package.

edit: If you are using a very dark theme, you might want to also go to tools/options/OpenOffice.org/Accessibility and disable the "Automatically detect high contrast mode of operating system".

---

### Post by Toxicbits on 2010-10-08
Hi,

thanks alot for the tips. Installing openoffice.org-gnome actually fixed it, I didn't even need to change any icons or install the gtk package.

---

### Post by budde on 2011-02-06
If anyone has the same problem with LibreOffice, this solution works aswell.

Just install libreoffice-gnome and you should have a good looking LibreOffice in no time!

---

### Post by wommy on 2011-06-18
[FONT="Arial"]I'm currently running Mint 11 which has LibreOffice by default and I'm using latest KDE desktop, so any KDE users of LibreOffice can install "libreoffice-kde" via software manager and your LibreOffice suite will look native in KDE. Looks great!!   [/FONT]

---

