---
title: "gconf-editor.desktop weirdness"
date: 2007-08-13
forum: Desktop Environments
---

### Post by malachias on 2007-08-13
Hi

There are a few threads about getting gconf-editor into your applications menu, but this really doesn't fit into any of them. I wanted to get it in there, so since it wasn't anywhere in 'alacarte' I added a gconf-editor.desktop to my /usr/bin/applications folder (I got it from a gconf-editor tarball). Now, here's the weirdness: it doesn't show up.

After lengthy experimentation, showing that virtually everything else I cared to add worked just fine, I discovered that as long as it was called gconf-editor.desktop, it didn't work. If I renamed the file gconf-edito.desktop, or gconf-editorr.desktop, or even thisisrandom.desktop, it showed up in my menu just fine.

I could just leave it like that, as now I have the menu entry and on the whole everything looks fine. But I'm curious. Why can't I call it gconf-editor.desktop? I figured it might have something to do with hiding so I opened up alacarte again (after all this) and indeed, there was my "Gnome Configuration Editor" right where it was supposed to be, with the little checkbox checked.

Anyone know?

---

### Post by ComplexNumber on 2007-08-13
i imagine because gconf-editor.desktop is reserved.

---

