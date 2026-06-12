---
title: "gnome-panel advanced gtk2 customization"
date: 2008-01-24
forum: Desktop Environments
---

### Post by edv on 2008-01-24
Hello, I've managed to change the font color on my gnome-panel by creating a gtkrc-2.0 file. Now I'd like to go a bit further and also remove those annoying 'handles' or whatever they are that are drawn on each side of the panel when it's unexpanded. The ones that show up even if you disable the arrow-options. I tried to read some GTK documentation and compared themes but couldn't find the setting responsible for those. With the default theme they have some sort of a grid-texture and with Glider theme a small single dot(?) in the middle.

I even went as far as running gdb and setting breakpoints for some functions like gtk_paint_handle() trying to find a way to disable them from getting drawn to no avail. Heh, kinda far fetched I guess. But can anyone help me? Those handles are ruining the otherwise transparent bar. One option would be to just keep the panel expanded and manually place everything in the middle to achieve the same look, but I'd really prefer a proper solution here.

---

### Post by sageb1 on 2008-01-24
You might try [http://bugzilla.gnome.org/show_bug.cgi?id=125226](http://bugzilla.gnome.org/show_bug.cgi?id=125226)

This post's topic might be high above most people's skillset level here.

---

### Post by edv on 2008-01-24
Thanks for the link. I was able to compile the panel with the supplied patch, and while it doesn't really draw the handles anymore (button texture is gone), there are still lightgray boxes on each side... on which the transparency/color settings of the panel don't affect. Time to learn more gtk or ditch gnome-panel I guess :)

---

