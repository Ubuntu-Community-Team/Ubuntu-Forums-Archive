---
title: "gnome+compiz+default icon size for file type"
date: 2009-02-17
forum: Desktop Environments
---

### Post by {Nabla} on 2009-02-17
Hi, I'm using Ubuntu 8.04 with gnome and compiz fusion. I can change the global default icon size from the preferences menu in the file browser, but my pdf's and image files are always alot bigger than other icons.

This makes my desktop look really messy, since icons overlap even when 'keep aligned' is on.

Is there anyway to change this?

---

### Post by Tibuda on 2009-02-17
I agree. Thumbnails are always larger than the icons. I'm getting used to it, but would like to change it too.

---

### Post by {Nabla} on 2009-02-17
You'll be happy to hear I found the solution then :)

press Alt+F2, and enter gconf-editor. under Apps > nautilus > icon_view click the thumbnail size setting, and change the default value of 96 to something smaller.

---

