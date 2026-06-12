---
title: "Inkscape Show/Hide"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Ryan H on 2006-09-09
In Inkscape I clicked on an object and went to Object -> Object Properties ->  Hide, but now I can't find the objects I've hid. I want to be able to select them to bring them back but I don't know how?

-Ryan H

---

### Post by cwaldbieser on 2006-09-09
> **Ryan H said:**
> In Inkscape I clicked on an object and went to Object -> Object Properties ->  Hide, but now I can't find the objects I've hid. I want to be able to select them to bring them back but I don't know how?

-Ryan H

The best way I could find was Edit -> XML Editor.
Use the drill-down menus to find the object and erase it's "style display: none" attribute.

---

### Post by Ryan H on 2006-09-09
Thanks! That works, but is there not an easier way?

-Ryan H

---

### Post by cwaldbieser on 2006-09-09
> **Ryan H said:**
> Thanks! That works, but is there not an easier way?

-Ryan H

Not that I have found, though I only just looked.  If you use inkscape a lot, you should go to the project web site [http://www.inkscape.org/]("http://www.inkscape.org/") and either 1) Use the "Request feature" option to request something like a "Show Hidden Objects" menu option, 2) File a bug report that hidden objects cannot be revealed without editing the XML, or 3) join the mailing list and discuss the problem in more depth.

It seems like it would be an easy problem to solve if the developers receive feedback.

---

