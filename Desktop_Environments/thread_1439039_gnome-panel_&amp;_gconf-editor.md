---
title: "gnome-panel &amp; gconf-editor"
date: 2010-03-25
forum: Desktop Environments
---

### Post by KozyMatt on 2010-03-25
I use cairo-dock with systray, window list, etc which leaves me with no need to also have a panel on the screen.

After searching around a bit, I found I could effectively hide the last panel in gconf-editor (> apps > panel > toplevels > top_panel_screen0) by unchecking `expand` and setting `monitor` to 3.

This allowed me to keep the functionality of Alt+F1 (pulling up the menu from where my pointer is), Alt+F2 (Run Application), Print (Save Screenshot), and Alt+Print (Save Screenshot of window).

I recently upgraded one of my computers to 9.10 from 9.04. To my disappointment I found my empty panel had returned and setting `monitor` to 3 for the panel had no effect (reverted back to 0 immediately).

This is, honestly, unacceptable. I will not be forced into having a panel that I do not want and I will not discard the Alt+F1, Alt+F2, and Print Screen functions the panel provides.

Is there any way to achieve what I'm looking for?
Why did the gconf-editor workaround stop working with 9.10 when I've been using it since 8.04?


~Kozy

---

### Post by spiderbatdad on 2010-03-25
It's a great question. Unfortunately I don't have a great answer!
gconf-editor, i believe, is a front end to gconftool-1. Ubuntu presently uses gconftool-2, though gconf-editor still has some functionality...it isn't 100%, more like 50%.
Maybe you can get something from the documentation: [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/)

---

### Post by KozyMatt on 2010-03-27
Using `gconftool-2 --get /apps/panel/toplevels/top_panel_screen0/monitor` outputs its value.

Then `gconftool-2 --set --type=int /apps/panel/toplevels/top_panel_screen0/monitor 3` changes that value to 3.

The change doesn't automatically revert back to 0, like it does with gconf-editor, but still acts as 0. Rebooting returns the value to 0 at any rate.


Ubuntu 9.04 appears to use gconf2 version 2.26.0 while 9.10 uses 2.28.0. Is this the offending package I should revert?


~Kozy

---

### Post by drs305 on 2010-03-27
In 9.10, can you not just right click the top panel and select "Delete panel"? Note this is only something to do if you *really* don't want the panel.

---

### Post by KozyMatt on 2010-03-29
That will not work on the last panel. "Delete panel" is greyed out.


~Kozy

---

