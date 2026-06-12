---
title: "Terminal transparency"
date: 2009-09-04
forum: Desktop Environments
---

### Post by mnml on 2009-09-04
Hi, I'm using ubuntu at work and debian at home and I have noticied that gnome-terminal has real transparency on ubuntu while on debian I can only see the desktop in the transp.
Does anyone know why, I'm using debian testing.

---

### Post by SoftwareExplorer on 2009-09-04
I'm guessing you don't have 3d or compositing on the debian machine right? Gnome-terminal shows the desktop when the desktop isn't running with transparency.

---

### Post by mnml on 2009-09-04
> **SoftwareExplorer said:**
> I'm guessing you don't have 3d or compositing on the debian machine right? Gnome-terminal shows the desktop when the desktop isn't running with transparency.

no, do I need compiz for that?

---

### Post by SoftwareExplorer on 2009-09-04
> **mnml said:**
> no, do I need compiz for that?
I'm not 100% sure, but I think metacity can do compositing. Though if you got compiz working, you could be pretty sure compoziting is working.

---

### Post by mcduck on 2009-09-05
> **mnml said:**
> no, do I need compiz for that?

You need some compositing manager to run for real transparency. Compiz, Xcompmgr or built-in compositing of Metacity, Xfwm or Kwin, as long as you have any compositing manager running Gnome-terminal will switch to real transparency automatically.

---

