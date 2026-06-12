---
title: "Keeping the Applications Menu Ubuntu Logo."
date: 2007-03-19
forum: Desktop Environments
---

### Post by ihavenoname on 2007-03-19
I am in the process of re-theming my Ubuntu install, but there is one thing that gets to me. I like the Ubuntu logo that comes with the default Human icon theme. But sometimes that icon theme does not go with the rest of my themes. When I change the icons I lose the nice 3d looking icon for the old archaic one. Does anyone know I can keep that icon?
To clarify this I am talking about the Ubuntu logo that is right next to (on the left side of) the Applications menu on the top gnome panel.

---

### Post by dbbolton on 2007-03-19
there is a key in Gconf-editor that you can use to specify a file as a custom distributor logo. unfortunately, i don't quite remember where it is.

try here:  gconf > apps > gnome panel

---

### Post by ardchoille42 on 2007-03-20
> **dbbolton said:**
> there is a key in Gconf-editor that you can use to specify a file as a custom distributor logo. unfortunately, i don't quite remember where it is.

try here:  gconf > apps > gnome panel

I believe that is in /apps/panel/objects  but you'd have to figure out which of those objects is the correct one for the menu bar.

---

### Post by ihavenoname on 2007-03-20
I couldn't find one that would change the icon for the menu bar, but the one you told me about did change the main menu icon. (I am going based off the name in the add applets menu).

---

