---
title: "Removing the gnome-panel drop shadow?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Reb on 2006-08-24
How do I remove it? I don't like it and the shadow has an ugly gradient.
Thanks!

---

### Post by Saibot on 2006-08-24
Well I assume that you're running compiz, and I don't think there's any way to remove the shadow from the panel.  That ugly gradient seems to be a bug.
If you only have one panel then you could change the Y offset of the shadow so it would be offscreen.  Of course this won't do you any good if you have a panel on the top and bottom of the screen.

---

### Post by Edward Hou on 2007-10-02
A little late, but oh well.

What I did was I went to the Window Decoration plugin settings in ccsm and changed the "Shadow Windows" option from 'any' to '(type=!unknown)'.

Basically it tells compiz not to draw shadows on the windows that have type "unknown." Unfortunately I don't know how specific the unknown type is, you could try finding a better selector. This page helped: [http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

---

### Post by explemonk on 2007-10-02
You can set the Shadow Windows option in CCSM Window Decorations from "any" to "any & !(type=dock)" to remove the shadow from the panel.

---

### Post by Edward Hou on 2007-10-03
You don't need the "any", so "!type=dock" works too.

However, this removes shadows from certain dropdown elements of the dock, such as the calendar, dictionary look-up, et cetera. So to fix this you could get even more specific and select "!title=Expanded Edge Panel" assuming you use panels that stretch the whole length of the window.

---

### Post by extant59 on 2007-10-20
hopefully there will be an update or fix for this... because i upgrade this thing and now its kinda ugly. although i love the fact i didnt have to fight with it at all to get it to work :)

---

### Post by extant59 on 2007-10-21
something you can do too i just found out is turn off reflection. its under effects in CCSM. the ugly pattern and huge shadows went away :)

---

