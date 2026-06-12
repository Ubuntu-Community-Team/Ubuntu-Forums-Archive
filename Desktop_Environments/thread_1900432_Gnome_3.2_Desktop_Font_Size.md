---
title: "Gnome 3.2 Desktop Font Size"
date: 2011-12-26
forum: Desktop Environments
---

### Post by gdi2k on 2011-12-26
I'm using Gnome 3.2, and like to have the file manager handle the desktop so I can have icons on it. I have enabled this using the Advanced Settings tool, under "Desktop". 

But the fonts displayed on the desktop are too large for my taste (I prefer Ubuntu size 9), and I can't figure out how to reduce their size. 

In the same Advanced Settings tool, under "Fonts" it is possible to change the size of many fonts, but not desktop icon fonts. Using gconf-editor, I see there is apps -> natilus -> preferences -> desktop_font, which I have set to "Ubuntu 9", but it has no effect - it still stays at what looks like Ubuntu 11. 

Does anyone know how I can fix this?

---

### Post by Randymanme on 2011-12-26
Hello, 

In advanced settings > fonts, at the top of the box is "text scaling factor."  You can make the desktop fonts smaller by moving the slider to the left, and larger by moving it to the right.

---

### Post by gdi2k on 2011-12-26
Thanks Randy, that's a good solution - setting it at 0.9 and making all the fonts size 10 seems to work well. The desktop font is still slightly bigger than the other fonts (as it seems to be fixed at 11) but I can live with that. 

Cheers!

---

