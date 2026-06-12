---
title: "disabling thumbnails per file type"
date: 2005-12-05
forum: Desktop Environments
---

### Post by everdred on 2005-12-05
I know how to disable all thumbnails for all file types in Gnome, but I was wondering if anyone could help me figure out how to disable them on a type-by-type basis.

For instance, I'd like to keep thumbnails enabled for all image and video types, but disabled for PDFs.


Many thanks, if you can help.

---

### Post by everdred on 2005-12-06
Anyone... help... please?

---

### Post by aysiu on 2005-12-06
I don't know.
Use KDE?

---

### Post by ow50 on 2005-12-07
From the panel menu, open Applications -> System -> Configuration Editor and navigate to /desktop/gnome/thumbnailers. Under that you'll find entries for individual thumbnailers and you can uncheck the "enable" box.

After changing the setting you will probably still see previously generated thumbnails, but no new ones will be generated. To get rid of **all** previously generated thumbnails, remove the ".thumbnails" directory under your home folder.

---

### Post by everdred on 2005-12-07
Thank you! Thumbs of HTML and PDFs have been driving me insane!

Figured there had to be some way to do this :)

---

### Post by everdred on 2005-12-11
Alright, now that I've tried this and am half-satisfied, let me ask... is there any way to disable thumbnailers for file types that don't show up under /desktop/gnome/thumbnailers in the Config Editor...? Like, custom types. 

HTML in particular.

---

