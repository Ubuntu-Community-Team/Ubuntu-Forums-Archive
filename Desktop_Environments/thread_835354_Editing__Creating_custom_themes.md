---
title: "Editing / Creating custom themes"
date: 2008-06-20
forum: Desktop Environments
---

### Post by Zenze on 2008-06-20
I recently downloaded a new theme for Ubuntu but I am not satisfied with a lot of it. I am interested in modifing it or even create my own, however I have no idea where to start. Anyone have an suggestions? I did some google searches and some searches in the forum but couldnt really find what I was looking for. Thanks. :)

---

### Post by Iandefor on 2008-06-21
Here's some documentation on [making a Metacity (window manager for GNOME) theme]("http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html").

Modifying gtk themes, I've found, is simple enough that you can usually pick it up by opening up a theme's gtkrc (unarchive it, navigate to the gtk-2.0 directory) and poking around. Writing your own theme from scratch would be somewhat more difficult, though here's a ["how to"]("http://ubuntuforums.org/showthread.php?t=377397") that seems to provide a decent skeleton gtkrc.

I recommend installing The Widget Factory ([apt://thewidgetfactory](apt://thewidgetfactory)), which provides a window you can use to preview a GTK theme. It doesn't install a menu entry and the command to launch it is twf.

---

### Post by angry_johnnie on 2008-06-21
If it's only a part of that theme that you don't like, the sort-of-easy, rather dirty way to do it, would be to extract the compressed files, and then manually modify whatever it was that you didn't like.

Of course it takes time, and patience, and some skill with a graphics editor, but then, I did say it was a rather unelegant way to do things. :-)

---

### Post by Zenze on 2008-06-21
Thanks, both of those links seem like what I need. Im going to go read them over and try messing around with some themes I already have.

---

