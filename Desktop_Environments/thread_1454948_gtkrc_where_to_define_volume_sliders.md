---
title: "gtkrc: where to define volume sliders?"
date: 2010-04-15
forum: Desktop Environments
---

### Post by pickarooney on 2010-04-15
This is quite a specific request, but I've been hacking together a theme from bits of old themes and I cannot make out this one last piece of the puzzle. 

The slider icon that's used in e.g. smplayer or the xfce colume mixer, amongst other things - where do I set it in the gtkrc file?

---

### Post by mcduck on 2010-04-15
That's going to be a bit more complicated, as most theme engines simply use a built-in picture for that and only let you define the colors.

So, you'll have to define the image you want to use using the pixmap GTK engine. I suggest checking some pixmap-based GTK theme to see how it's used.

---

### Post by pickarooney on 2010-04-15
The image itself exists as part of the Mac4Lin theme and I've managed to recycle most of the other icons from that (in the Icons directory of the theme) for things like tabs, scrollbars etc., but this particular slider icon has be flummoxed.

---

### Post by stinkeye on 2010-04-15
In my themes it's called slider-horiz.png
and in some cases in a folder called Range.

---

### Post by pickarooney on 2010-04-16
That's what I thought as well. I have a section of the gtkrc pointing to that exact file, but I must have something else overriding it in the same file.

---

