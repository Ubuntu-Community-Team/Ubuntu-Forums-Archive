---
title: "Gtk Qt: lost control of fonts in gnome!!!"
date: 2005-07-19
forum: Desktop Environments
---

### Post by lorenzo on 2005-07-19
Ciao,
yesterday I have installed KDE and gtk-qt engines. Today, back in gnome, i have HUGE fonts on my menu bar, even though I have uninstalled gtk-qt-engine.

I try to change fonts aspect from gnome but: nothing changes....

Can anyone help me?

Thanks,
Lorenzo

SOLUTION:
After removing gtk-qt-engine, you also have to remove from your home directory:

.gtkrc-2.0

---

### Post by ilbahr on 2005-07-21
I am afraid that i also have the same problem and would be quite interested to know how to rectify that. xpdf, evince and other gnome applications fonts are messed up and in the terminal window i got this error message
Error: Bad bounding box in Type 3 glyph

---

### Post by royg1234 on 2005-07-21
Yeah this thing gave others problems too.  I think the basic consensus is that gtk-qt is not ready yet.

---

