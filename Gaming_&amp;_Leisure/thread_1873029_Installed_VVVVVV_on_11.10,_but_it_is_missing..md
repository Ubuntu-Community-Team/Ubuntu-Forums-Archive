---
title: "Installed VVVVVV on 11.10, but it is missing."
date: 2011-10-31
forum: Gaming &amp; Leisure
---

### Post by liquidcross on 2011-10-31
I installed VVVVVV from its .deb file, and Ubuntu Software Center says it's installed and ready...but how can I run it? The dashboard does not list it, even when I search for it by name.

---

### Post by DoktorSeven on 2011-10-31
Looking at the .deb file contents now, it should have a shortcut entry named VVVVVV -- not sure why it's not showing up.  You should be able to manually run it from /usr/games/VVVVVV

---

### Post by liquidcross on 2011-11-01
Sounds good. Thanks!

---

### Post by fleamour on 2011-12-02
I installed, also under 11.10.  Shortcut is present but nothing happens when clicking on said shortcut.

Installed & ran on 10.04 laptop, but my what with my 8MB graphics ***"accelerator"***, it kinda sucks.  Running through a layer of treacle, unlike browser based demo.


:confused::shock::confused::frown:

EDIT: Oh & no entry in usr folder.  VVVVVV in terminal also no worky.

---

### Post by fleamour on 2011-12-02
```
/opt/VVVVVV/VVVVVV
```

Returns:

```
./VVVVVV_32: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory
```

So installed missing dependency, libsdl-image1.2.  Game now runs.

Yey!  Such a cool little game.


:mrgreen: 8) :mrgreen:

---

