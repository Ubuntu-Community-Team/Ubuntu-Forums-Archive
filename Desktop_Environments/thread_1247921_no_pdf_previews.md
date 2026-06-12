---
title: "no pdf previews"
date: 2009-08-23
forum: Desktop Environments
---

### Post by schmolch on 2009-08-23
I use karmic on 3 computers and on one of them i get no pdf (or chm, png, djvu) previews from nautilus.
i know about nautilus' settings dialog and it sure is enabled there (always, 1G).

What can i do to figure out the cause of this malfunction?
There is nothing in .xsession-errors.

Update: After some googling and swearing it turns out that there were no thumbnailer commands configured in gconf.
I added those with gconf-editor and now it works.

---

