---
title: "Can't edit Gnome menu"
date: 2007-02-10
forum: Desktop Environments
---

### Post by axcairns on 2007-02-10
Hey all,

I have a fresh edgy install and am trying to edit the applications menu.

I right-clicked on the menu and selected edit menu. The menu layout window comes up but everything seems to be read-only. No edits work.

Help!

allan

---

### Post by ComplexNumber on 2007-02-10
> **axcairns said:**
> Hey all,

I have a fresh edgy install and am trying to edit the applications menu.

I right-clicked on the menu and selected edit menu. The menu layout window comes up but everything seems to be read-only. No edits work.

Help!

allan
fire up the terminal and type in the following (i'm going to assume that your username is axcairns):
**sudo chown -R axcairns:axcairns /home/axcairns/.local**

---

### Post by axcairns on 2007-02-10
Thanks, that did it.

Cheers,

allan

---

### Post by addisor on 2007-02-14
thanks did the trick for me also

---

