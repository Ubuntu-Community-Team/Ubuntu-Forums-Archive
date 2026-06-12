---
title: "Suspend to RAM and screensaver activation"
date: 2006-06-05
forum: Desktop Environments
---

### Post by monkeyhelper on 2006-06-05
I've been having some problems with Suspend to RAM in relation to the screensaver starting up when I suspend the machine.

I'd like to disable this to help with my testing but I've not managed to identify why the screensaver starts when suspending - it doesn't appear to be initiated in /etc/acpi/*

Does anybody know where I can find out where/how the screensaver is initiated when suspending ?

---

### Post by blingboi on 2007-08-05
if anyone knows where this setting is because I'd like to disable the screensaver while suspending to test something

---

### Post by blingboi on 2007-08-07
hey bump

---

### Post by fwojciec on 2007-08-07
If you're using gnome then look in configuration manager (gconf-editor) in apps/gnome-power-manager and uncheck lock on suspend / lock on hibernate (or something like that).  You can also check your screensaver settings and uncheck screen locking there, just to be sure.

KDE?  No idear....

---

