---
title: "UT2004 sudo only?"
date: 2007-04-23
forum: Gaming &amp; Leisure
---

### Post by Hildsvfar on 2007-04-23
I installed UT2004, and I can only get it to run when typing "sudo ut2004"  otherwise if I just type "ut2004" it says an error occured and doesn't load.  It's kind of annoying because that means the ubuntu menu icons don't really do much good.  Does anyone know a way to fix this?  So I don't have to type 'sudo' in order to run it?

---

### Post by Perfect Storm on 2007-04-24
It's because you hit the launch button in the installer window (which ran with sudo permission)
```
cd
sudo chown -R USERNAME:USERNAME .ut2004

```
should do it, or simple delete .ut2004



[http://gaming.gwos.org/e107_plugins/content/content.php?content.56](http://gaming.gwos.org/e107_plugins/content/content.php?content.56)

---

### Post by Hildsvfar on 2007-04-24
That did it!  Thank you.

---

