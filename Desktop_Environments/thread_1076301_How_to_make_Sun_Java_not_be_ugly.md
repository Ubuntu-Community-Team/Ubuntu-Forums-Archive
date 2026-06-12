---
title: "How to make Sun Java not be ugly?"
date: 2009-02-21
forum: Desktop Environments
---

### Post by Vadi on 2009-02-21
Hi all,

Does anyone know how to make sun's java look like my gtk theme, and not it's own 90's theme?

---

### Post by Armor Nick on 2009-02-21
Try this:
[http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html](http://java.sun.com/docs/books/tutorial/uiswing/lookandfeel/plaf.html)

As far as I know, if you can't set it, it means the author of the program set its own look and feel manually.

---

### Post by Vadi on 2009-02-21
Thanks for that. By that document, I do fill the gtk2.2+ requirement - and the applet does use the windows look and feel on windows. So I guess their detection is buggy.

I tried the swing.properties file, but now the applet cannot load, with a rather unhelpful error message. I'll file a bug...

---

