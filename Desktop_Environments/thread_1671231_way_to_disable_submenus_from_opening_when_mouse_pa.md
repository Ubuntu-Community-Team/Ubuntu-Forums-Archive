---
title: "way to disable submenus from opening when mouse pauses over menu?"
date: 2011-01-19
forum: Desktop Environments
---

### Post by nrundy on 2011-01-19
Anybody know how to disable this, maybe with a gconf-editor hack or something?  For example, if you click System and pause the mouse over Preferences, the submenu listing will pop open and display. I want the submenu to open only when I click on Preferences.

---

### Post by stinkeye on 2011-01-20
> **nrundy said:**
> Anybody know how to disable this, maybe with a gconf-editor hack or something?  For example, if you click System and pause the mouse over Preferences, the submenu listing will pop open and display. I want the submenu to open only when I click on Preferences.

Add something like
```
gtk-menu-popup-delay = 999999
```
to your **~/.gtkrc-2.0** file.
Create a ~/.gtkrc-2.0 file if you don't have one.

---

### Post by nrundy on 2011-01-20
Didn't work. Thanks though.  I'm wondering if there's a setting somewhere for this option.

---

### Post by stinkeye on 2011-01-20
You need to log out and back in, or change themes and back.

---

### Post by nrundy on 2011-01-20
Got it. Thanks stinkeye for posting about needing to log out. Thanks so much for your help :)

---

### Post by nrundy on 2011-01-20
Got it. Thanks stinkeye for posting about needing to log out. Thanks so much for your help :)

---

