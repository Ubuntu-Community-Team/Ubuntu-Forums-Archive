---
title: "GNOME window list doesn't use theme icons?"
date: 2006-04-26
forum: Desktop Environments
---

### Post by cskeide on 2006-04-26
Ok, I've been searching both google and this forum but I can't seem to figure this out. I'm using [lokheed's]("http://lokheed.deviantart.com") gperfection2 iconset at the moment. But the window list uses gnome's default icons for most applications.

I know that for example gnome-terminal allows you to select a custom icon, and the window list will use the one you choose... But most applications won't let you select an icon.

So I guess my question is: Where does the window list in gnome-panel get its icons from?

---

### Post by Efwis on 2006-04-26
[QUOTE=cskeide]Ok, I've been searching both google and this forum but I can't seem to figure this out. I'm using [lokheed's]("http://lokheed.deviantart.com") gperfection2 iconset at the moment. But the window list uses gnome's default icons for most applications.

I know that for example gnome-terminal allows you to select a custom icon, and the window list will use the one you choose... But most applications won't let you select an icon.

So I guess my question is: Where does the window list in gnome-panel get its icons from?[/QUOTE]
I was looking at lokheeds gperfection2 icon set, for the most part his set is using the standard Gnome2 icon set. it would be helpful to know what Icons you think are missing?

[quote=Artists Comments from site]GNOME2 icon set **based on the default GNOME2 icon set** originally designed by Jakub 'Jimmac' Steiner.[/quote]

---

### Post by cskeide on 2006-04-26
[QUOTE=Efwis]I was looking at lokheeds gperfection2 icon set, for the most part his set is using the standard Gnome2 icon set. it would be helpful to know what Icons you think are missing?[/QUOTE]

Ok, here are some examples.

The icons for Firefox, Terminal Server Client and XChat in the menu,
[IMG]http://home.no.net/cskeide/Screenshot2.png[/IMG]

are different from the icons used in the window list.
[IMG]http://home.no.net/cskeide/Screenshot.png[/IMG]

---

### Post by Efwis on 2006-04-27
[QUOTE=cskeide]Ok, here are some examples.

The icons for Firefox, Terminal Server Client and XChat in the menu,
[IMG]http://home.no.net/cskeide/Screenshot2.png[/IMG]

are different from the icons used in the window list.
[IMG]http://home.no.net/cskeide/Screenshot.png[/IMG][/QUOTE]
not sure why those are different. 
as for the there is a script that will change that system wide on a permanent basis. You can find that [here](http://ubuntuforums.org/showthread.php?t=34354&highlight=back+firefox+logos)

as for the Xchat one and terminal I'm not sure why those didnt change, I'm not on my ubuntu install at the moment, unless someone else answers before I get back, I will check into that. I know it's a gconf file, but not sure exactly which one.

---

### Post by cskeide on 2006-04-27
Thanks, very useful script.

So, it seems like the icons used by the gnome window list depends on how the individual applications are developed?

---

