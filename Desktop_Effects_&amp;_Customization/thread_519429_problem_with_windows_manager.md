---
title: "problem with windows manager"
date: 2007-08-07
forum: Desktop Effects &amp; Customization
---

### Post by rubperezt on 2007-08-07
hello im using beryl and when i apply a theme it will only change the title bar but not the buttoms etc. here is an screen shot so you can see it changed the tittle but not the buttoms, menus (e.g application, places, system, etc menus) i have tried already with several themes, which in the screen shot appears to modify such menus/buttoms.

---

### Post by stido on 2007-08-08
window manager actually only "handles" window borders. Window borders are composed of:  titlebar (including therein window title text, close, min, maximize buttons), side borders, and bottom border. Some people call it window decoration.

So for example if you use a beryl-specific theme, the theme will only "decorate" the above mentioned components of a window.

Everything you interact with inside a window are called widgets. And if you use Ubuntu, those widgets are handled by the GNOME toolkit (Gtk), and for Kubuntu it'd probably be handled by the KDE toolkit (Qt). Widgets inside a window are, for example: toolbar, (push/toggle) buttons, notebooks (microsoft calls them tabs), frames, scrollbars, menus, panels, text labels, etc.

You'd need another theme to decorate those widgets.

PS: The people making the screenshots you see in emerald probably have their own theme for the widgets. You should ask them how to get it.

---

