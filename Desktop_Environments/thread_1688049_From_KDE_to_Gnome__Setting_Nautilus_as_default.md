---
title: "From KDE to Gnome:  Setting Nautilus as default"
date: 2011-02-14
forum: Desktop Environments
---

### Post by mikecrowe on 2011-02-14
Hey folks,

I had KDE installed (kubuntu maverick), and moved to Gnome (to support screen dimming on my dell laptop).

Now, when I click on Places and anything (say Desktop), Krusader starts up (I set krusader to the default in KDE).

Where do I change this?  I can't find the location in preferences to change this.

TIA
Mike

---

### Post by jerrrys on 2011-02-16
if you now have gnome and kde installed you can select from boot which one you want

---

### Post by Krytarik on 2011-02-17
To choose Nautilus as the default app for opening folders:

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Greetings.

---

