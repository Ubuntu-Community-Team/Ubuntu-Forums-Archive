---
title: "Make Epiphany titlebar != web page title ?"
date: 2009-01-09
forum: General Help
---

### Post by oedipuss on 2009-01-09
Is there any way to stop epiphany from showing the current page's title in its titlebar and just say 'Epiphany' ?

I'm checking out the global-menu panel applet (mac OS style menus for gtk apps) and it displays the title of the current window next to the menus so a long title is somewhat problematic and kind of ugly.

Thanks =D

---

### Post by mssever on 2009-01-09
> **oedipuss said:**
> Is there any way to stop epiphany from showing the current page's title in its titlebar and just say 'Epiphany' ?

I'm checking out the global-menu panel applet (mac OS style menus for gtk apps) and it displays the title of the current window next to the menus so a long title is somewhat problematic and kind of ugly.

Thanks =D
You can check the Epiphany settings in gconf-editor and search the available Epiphany extensions, but my guess is that you can't do what you want. Epiphany is part of Gnome, and Gnome tends to have as little configuration options as possible.

---

### Post by oedipuss on 2009-01-10
Apparently it's possible with a simple extension .. I can do it from the epiphany python console with window.set_title, but I don't know how to put it in an extension so it activates with tab switches and address changes...

---

