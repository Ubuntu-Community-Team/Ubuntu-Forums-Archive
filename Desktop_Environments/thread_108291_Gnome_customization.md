---
title: "Gnome customization"
date: 2005-12-25
forum: Desktop Environments
---

### Post by PascalGR on 2005-12-25
Hi,

I'd like to have windows remember their size, state and position each time I open them (as other WMs do).

For example to open the gnome terminal at 150x90 by default instead of 80x25.

Is this possible?

Thanks

---

### Post by pharcyde on 2005-12-25
You can try making the shortcut of the terminal window use a parameter switch.  Try doing man aterm, xterm, Eterm, etc.  For what ever type of console you are running and add the appropriate command line parameter to that.  You can also edit your ~/.Xdefaults file and add custom application specific parameters there.

---

### Post by PascalGR on 2005-12-25
At least, that's better than nothing. I added the *--geometry* parameter to the icon's properties...

Thanks

---

