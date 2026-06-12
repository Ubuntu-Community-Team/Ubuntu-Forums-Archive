---
title: "replacement for kdialog?"
date: 2009-11-11
forum: Desktop Environments
---

### Post by edgue on 2009-11-11
He there,

is there a better replacement that works for xfce for kdialog?

(i tried gnome zenity, but that thing just sucks: no password
input, no auto-sizing of the window)

---

### Post by Brandon Williams on 2009-11-11
I've never used kdialog, so I'm not sure how it works and whether any of these satisfy your requirements, but ... in addition to zenity, you might also try: dialog, tcdialog, and/or gtkdialog.

If none of these fit the bill, try to describe exactly what you're trying to do so that we can look more carefully.

FWIW ... zenity does support password input (for example: 'zenity --entry --text='Enter password' --hide-text' presents a typical password entry dialog). I'm not sure what you mean by 'auto-resizing', but maybe there's a way to do that, too.

---

### Post by durand on 2009-11-11
Zenity has pretty much the same features as kdialog, albeit in harder to use package. If you read ```
man zenity
```, you should be able to get the hang of it.

---

