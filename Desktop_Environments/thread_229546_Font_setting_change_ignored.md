---
title: "Font setting change ignored"
date: 2006-08-04
forum: Desktop Environments
---

### Post by darkaudit on 2006-08-04
I'm having difficulty changing the Application font settings. I'm using the normal procedure of System->Preferences->Font->Application font, but none of my changes take effect. Other settings in Font work fine. I tried logging into a root GNOME session, and the changes took immediately.

I started with a Kubuntu install, then added Xubuntu and finally full-on Ubuntu. Is there something in the KDE settings that are conflicting here?

[edit] Created a new user and logged straight into GNOME. Worked as intended. It has to be a KDE conflict [/edit]

---

### Post by darkaudit on 2006-08-04
Bump with further info...

When attempting to change the Applications font, .xsession-errors has a set of 'make transparent again' lines.

Where did I change this, and how do I put it back?

---

### Post by darkaudit on 2006-08-06
Bump with a fix

Gtk2-engines-gtk-qt put a .gtk2rc file in that locked my GNOME font setting for applications. Removed that, logged out and back, and now it's working as it should.

---

