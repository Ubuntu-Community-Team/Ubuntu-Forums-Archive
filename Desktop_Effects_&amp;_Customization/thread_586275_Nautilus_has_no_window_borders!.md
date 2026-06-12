---
title: "Nautilus has no window borders!"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by Protoss on 2007-10-22
I've got Compiz-Fusion on in Gutsy, and whenever I open a Nautilus window, the file browser takes up the entire screen and has no borders. If I do "sudo metacity --replace" then the borders are of course back, and the window doesn't take over my screen. Anyone got any suggestions?

---

### Post by Nonno Bassotto on 2007-10-22
Try to launch manually the
```

gtk-window-decorator

```
In case this works, add this program to your session, so it will load at startup.

---

