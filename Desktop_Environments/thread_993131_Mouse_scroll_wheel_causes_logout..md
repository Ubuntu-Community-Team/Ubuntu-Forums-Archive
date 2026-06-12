---
title: "Mouse scroll wheel causes logout."
date: 2008-11-25
forum: Desktop Environments
---

### Post by Monkey.feets on 2008-11-25
Hey...

I'm using Ibex and a logitech laser mouse....when I accidentally use the scroll wheel in an area that is not scrollable, such as desktop(didn't realize pointer was outside window) the system crashes and goes to login screen....any ideas???

---

### Post by ajgreeny on 2008-11-25
Could be something to do with compiz.  When you scroll on the empty desktop area it normally moves to the next workarea and so on, perhaps that is causing the problem.  Try without compiz running ```
metacity --replace
``` and see if that helps.

---

### Post by Monkey.feets on 2008-11-25
thanks that fixed it....any idea why that was happening....maybe video card isn't up to it???

---

### Post by ajgreeny on 2008-11-25
I'm not sure, but you may be right.  I don't know which setting actually gives you the scroll workspace change, but if you can find it in CCSM it may be easy enough to disable and then you may be able to still use compiz, if you want to.

OK, just found it.  Disable the **Viewport switcher** in CCSM and you may be alright.

---

