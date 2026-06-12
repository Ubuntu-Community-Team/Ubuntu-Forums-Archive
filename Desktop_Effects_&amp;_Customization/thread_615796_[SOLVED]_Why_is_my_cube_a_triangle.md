---
title: "[SOLVED] Why is my cube a triangle?"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by perlluver on 2007-11-17
My compiz cube is a three sided triangle.  I have it set to four desktops in the settings.  Any Idea Why???

---

### Post by Zorael on 2007-11-17
You'll want to set Number of Desktops to 1 and Horizontal Virtual Desktops to 4.

---

### Post by perlluver on 2007-11-17
It is still a triangle, I have Horizontal to 4, Vertical to 4, and desktop to 1?  Any other Ideas?

---

### Post by Darkade on 2007-11-17
I have it configured to
Horizontal :4
vertical 1
Desktops 1
and works for me, however I tried out this triangle thing and it's kind o cool hehe.

---

### Post by desudesudesu on 2007-11-17
I had the same problem.
I just bumped the number up to 5, down to 1, and then back to 4.
Now I have a cube.

---

### Post by Zorael on 2007-11-17
Adding --ignore-desktop-hints as an argument when starting Compiz (if you do it through a script or a launcher) *might* help; it makes it ignore how many desktops you set up Gnome/KDE to have and instead only abides the settings in the settings manager.

If you put KDE to have 4 desktops, you end up with 2x2; two vertical, two horizontal. When Compiz comes into play it makes it 4x4.

I'm not sure how big an issue this is with Gnome.

---

### Post by perlluver on 2007-11-17
Changed to Ubuntu desktop and it is working fine now...

:lolflag:

---

