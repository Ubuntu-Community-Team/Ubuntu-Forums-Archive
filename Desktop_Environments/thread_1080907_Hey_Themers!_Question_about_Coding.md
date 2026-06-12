---
title: "Hey Themers! Question about Coding"
date: 2009-02-25
forum: Desktop Environments
---

### Post by theyain on 2009-02-25
Basically what I want to know is that is it possible to have a picture, like one drawn and colored by an artist, as the background of a GTK or Emerald window theme? For clarification, like this

[img]http://i7.photobucket.com/albums/y263/theyain/backgroundadded.jpg[/img]

---

### Post by theyain on 2009-02-26
bump?

---

### Post by mcduck on 2009-02-26
Might be possible as a GTK theme with the pixbuf engine, although you would get problems with different amounts of toolbars in programs, and different toolbar orders. Also windows with different widths would be a problem.

Emerald is just a window decorator so it only affects window borders, not the actual programs running in the windows.

---

### Post by theyain on 2009-02-28
Thanks for clearing that up on Emerald.  

So in other words for that to work I or who ever codes it would have to tile each stripe of the image, correct?  That poses some problems :|

---

### Post by theyain on 2009-03-03
Bump

---

### Post by mcduck on 2009-03-03
Yes, the textures would have to be made tileable, and also all toolbars would look the same.

Until somebody adds a way to theme each toolbar separately and detect their locations relative to each other, and perhaps creates a GTK engine that supports SVG graphics (to solve the need to tile graphics) themes like that are very hard (or impossible) to create.

Still, with if you figure a nice way to tile the graphics, and accept that some parts of the window can't have that kind of graphics, you can do at least something like that with the pixbuf engine.

---

