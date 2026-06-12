---
title: "Gnome not installing themes"
date: 2007-01-24
forum: Desktop Environments
---

### Post by souteneur3190 on 2007-01-24
[http://www.roberto-studios.hu/Files/Carbonit/Carbonit-1.0.5-Full.jpg](http://www.roberto-studios.hu/Files/Carbonit/Carbonit-1.0.5-Full.jpg)

i installed that theme, the windows look how there supposed to but the rest is just different colors but still ugly, what am i doing wrong, it doesn't look like it should.(square boxes very very default it looks).

---

### Post by ComplexNumber on 2007-01-24
its because you have 1 or more theme engines missing. go to synaptic and type in "engine". you are probably missing the pixbuf engine at least.
if the correct engine isn't installed, the many of the widgets end up  looking a bit 'flat'

---

### Post by souteneur3190 on 2007-01-24
searched engine and pixbuf got nuffin

---

### Post by bg1256 on 2007-01-24
Download the tarball to your desktop.

Extract it to your desktop.

Open your home folder and hit ctrl+h.

Find .themes and open it.

Cut and past the theme from your desktop to the .themes folder.

All should be good, assuming you have the engine installed like posted above.

---

### Post by ComplexNumber on 2007-01-24
> **souteneur3190 said:**
> searched engine and pixbuf got nuffin
go to synaptic, click on 'settings' in the menu, then 'repositories'. then tick all the boxes (for universe and multiverse) and press 'close. it should ask you to reload. reload, then try searching on "engine" again.

---

### Post by souteneur3190 on 2007-01-24
my theme is fine but now the icons are small, i just installed every gtk engine i saw

---

### Post by ComplexNumber on 2007-01-24
> **souteneur3190 said:**
> my theme is fine but now the icons are small, i just installed every gtk engine i saw
whats the name of the icon theme?

---

### Post by souteneur3190 on 2007-01-24
osx

---

### Post by ComplexNumber on 2007-01-25
maybe the xserver just needs refreshing, i suspect. logout, then log back in again.

---

