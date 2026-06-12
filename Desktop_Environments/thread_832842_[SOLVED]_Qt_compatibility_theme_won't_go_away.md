---
title: "[SOLVED] Qt compatibility theme won't go away"
date: 2008-06-18
forum: Desktop Environments
---

### Post by sumguy231 on 2008-06-18
I just got tired of KDE and decided to switch to XFCE. When I used KDE, I used the Qt compatibility theme for Gtk apps, so that they would "fit in" on my KDE desktop. Now, no matter what I try to change the theme to in XFCE, at least some traces of the old theme remain, usually the scrollbars and coloring.
I've even removed the gtk2-engines-qtpixmap package, but I still can't get rid of it! Any suggestions?

---

### Post by sumguy231 on 2008-06-18
Ok, I got it. It was the 'gtk-qt-engine' package I needed to remove. Everything is back to normal now.

---

