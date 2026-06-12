---
title: "Default text selection Gnome/GEdit/GTK(?)"
date: 2009-12-20
forum: Desktop Environments
---

### Post by sototallycarl on 2009-12-20
In KDE and Mac OS (unsure about Windows) when you double click text in a text editor on a word like "_initFunction" it would select the whole thing "_initFunction" but in Gnome/GEdit it on selected "initFunction" minus the underscore.

I am really not sure which package denotes this, Gnome, GEdit or GTK  or something I really just have no idea about.

I was wondering if there is ANY way to change this. gui, terminal, source code, anything. It drives me nuts and slows me down since I have to manually select things.

If not are there any decent code editors that can handle this one little detail?

---

### Post by hugmenot on 2009-12-20
I think the Pango text library determines word boundaries. No idea if that is configurable.
But it should give you something to Google for.

Gnome-Terminal has a gconf key "word_chars", but you didn&#8217;t ask for g-t.

---

### Post by Derek_ on 2010-01-01
I've just made a Gedit plugin that will allow you to configure this for Gedit.

[http://code.google.com/p/gedit-click-config/](http://code.google.com/p/gedit-click-config/)

---

