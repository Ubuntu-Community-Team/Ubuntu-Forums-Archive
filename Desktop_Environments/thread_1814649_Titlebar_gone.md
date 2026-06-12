---
title: "Titlebar gone?"
date: 2011-07-29
forum: Desktop Environments
---

### Post by samg34 on 2011-07-29
Well some things had gone wrong with the titlebar at the top of each window, so i reinstalled compiz. When that didn't work I deleted ~/.gnome, ~/.gnome2, ~/metacity, ~/gconf, ~/gconfd to try and reset Gnome desktop. When that didn't work, i made a new user. I thought that would certainly do the trick, but I still lack a titlebar at the top of each window. Changing the theme does not resolve this issue.
Maybe do a hard reset on the window manager somehow...

---

### Post by jerrrys on 2011-07-29
sudo apt-get gnome-desktop-environment

this should give you a fresh desktop

and i suggest backing up personal files first

---

### Post by jfb3 on 2011-07-30
Actually that is what I wish my apps looked like.  I don't need the titlebar for anything.  It just takes up valuable space.

---

### Post by asthor on 2011-07-30
You could try running "metacity --replace &" in a terminal window... this may show some useful debugging messages.

---

### Post by Frogs Hair on 2011-07-30
I used the Window manager icon in to refresh the the desktop when this happened in 10.04  . It can be added from the main menu if the icon is not visible .

---

### Post by samg34 on 2011-07-31
Reinstalling the gnome desktop worked.
Later investigation found that the titlebar gone has something to do with the compiz window switcher settings. I will post more info later

---

### Post by samg34 on 2011-07-31
What i said earlier was correct. When I have the "Shift Switcher" thingy enabled in compiz, i no longer have a titlebar. Where do i report this bug?

---

