---
title: "Apps with KDE"
date: 2006-01-08
forum: General Help
---

### Post by Mazin on 2006-01-08
I installed KDE after I already installed the regular Ubuntu release.  Still, Firefox and other apps, like Synaptic, continue to use the GNOME interface (for chrome and fs dialogs and whatnot).  They should be independent of GNOME and KDE, so how do I make them switch to the KDE stuff?

---

### Post by aysiu on 2006-01-08
Actually, they're not independent--they use Gtk, not Qt, and, thus, look like Gtk apps (Gnome), not Qt ones (KDE).

You can try ```
sudo apt-get install gtk2-engines-gtk-qt
```

---

