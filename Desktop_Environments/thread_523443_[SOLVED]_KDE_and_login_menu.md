---
title: "[SOLVED] KDE and login menu"
date: 2007-08-11
forum: Desktop Environments
---

### Post by oldos2er on 2007-08-11
I have KDE set as my default DE. I have installed a few different DEs just to play with, and have uninstalled a couple of them (namely icewm and fluxbox). However, they still show up on the login menu under 'session type.' How can I remove them from the menu? I've searched for a file containing the words icewm, fluxbox, and kde, but turned up nothing.

 Thanks for any pointers.

---

### Post by meierfra on 2007-08-11
I think your need to delete

/usr/share/xsessions/fluxbox.desktop

and 

/usr/share/xsessions/icewm.desktop

 But I'm not sure.

---

### Post by oldos2er on 2007-08-11
It worked! Thank you.

---

