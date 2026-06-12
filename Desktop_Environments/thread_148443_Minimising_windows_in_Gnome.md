---
title: "Minimising windows in Gnome"
date: 2006-03-22
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-03-22
I've just moved from xfce to Gnome (having added lots more memory!).

When I minimise a window, it doesn't show up in icon form on my Taskbar.  The animation shows it disappearing towards the Trash icon - but there's nothing I can click on to maximise again.

What bit of my preferences to I have to tweak to fix this?

---

### Post by Buffalo Soldier on 2006-03-22
right click on any empty part of your panel -> add to panel -> window list

---

### Post by Edward The Bonobo on 2006-03-22
Ah...so simple.  Thanks, Dreadlock Rasta.

---

### Post by DeusEx on 2006-03-22
can this been done with a command in the console too?

---

### Post by Ramses de Norre on 2006-03-22
Since the gnome panel is a GUI application I don't really see how that would be handy.
Maybe if you find a file where those settings are stored you can vi it.

---

### Post by Wolki on 2006-03-22
panel configuration is stored in gconf, so yeah, you could use gconftool for this. It tends  tends to be rather complicated though, as you'd probabaly have to set a large number of keys, and things depend on your setup. I'd advise against doing it this way.

---

