---
title: "DCONF - No Keys"
date: 2013-02-05
forum: Desktop Environments
---

### Post by dprestemon on 2013-02-05
I'm running 12.10 on an old Vaio notebook.  I would like to make a few tweaks to the user interface, but when I open the dconf editor, no keys are shown.  The categories are all there (Apps, Launcher, etc.), but clicking them does nothing.  I uninstalled and reinstalled dconf to no effect.  Any suggestions?  In all other respects, the system works beautifully, so there does not seem to be any problem with the capabilities of the notebook.

---

### Post by ibjsb4 on 2013-02-05
What tweaks are you trying to make?  Is this Unity?

There are still some tweaks left in gconf.

---

### Post by dprestemon on 2013-02-05
Yes, it's Unity.  Initially, I wanted to get rid of the very annoying "are you sure" box that pops up when I try to shut down for the day.  Generally, though, I would like to be able to browse the keys to get some idea of what things I can customize.  And, yes, I know I can screw things up thoroughly by playing with keys about which I am ignorant.  I try to educate myself first.

---

### Post by ibjsb4 on 2013-02-05
Well Im not going to be any help since I run Classic.  Interesting though, I do not get that popup so must be a Unity thing.  Good luck

---

### Post by Krytarik on 2013-02-05
> **dprestemon said:**
> ...when I open the dconf editor, no keys are shown.  The categories are all there (Apps, Launcher, etc.), but **clicking them** does nothing.
Don't click on the _*folder names themselves*_ to reveal their subfolders, click on the _*triangles in front of them*_, just like in the 'tree view' of a file manager. :-\"

> **dprestemon said:**
> Initially, I wanted to get rid of the very annoying "are you sure" box that pops up when I try to shut down for the day.
It's the key "apps -> indicator-session -> suppress-logout-restart-shutdown".

Regards.

---

