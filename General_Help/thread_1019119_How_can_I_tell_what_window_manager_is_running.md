---
title: "How can I tell what window manager is running?"
date: 2008-12-22
forum: General Help
---

### Post by Mewshi on 2008-12-22
How can I tell if I have Metacity or Compiz running?

---

### Post by gettinoriginal on 2008-12-22
Install Compiz Fusion Icon, and with that you can see which one you are using, and change it if you want to.   If you do not want to do that, then you can type in terminal:

metacity --replace
or 
compiz --replace

That will set your window manager   :P

---

### Post by buzzbo on 2008-12-23
pstree?

---

### Post by jordanmthomas on 2008-12-23
If you are wanting to do it programmatically, you can use pgrep
```
pgrep metacity
```
If this returns a number (the pid of metacity) then metacity is running.

Otherwise, you just kind of have to know or manually look at your process list.

---

