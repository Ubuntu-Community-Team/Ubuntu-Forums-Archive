---
title: "Change EMACS big menu font?"
date: 2005-01-11
forum: Desktop Environments
---

### Post by istoyanov on 2005-01-11
The menu font of EMACS is rather big, and do not fit nicely in the overall look & feel (on a default Ubuntu install).

Anyone an idea how to change this?

Cheers:)

---

### Post by istoyanov on 2005-02-20
Thanks to a recent thread about GTK1 fonts, I did some research and resolved this problem by creating a .Xresources file in my home folder and putting in it:
```

Emacs.pane.menubar.font:        -*-arial-medium-r-normal--*-96-*-*-*-*-iso10646-1
Emacs.menu*.font:       -*-arial-medium-r-normal--*-96-*-*-*-*-iso10646-1
Emacs.dialog*.font:     -*-arial-medium-r-normal--*-96-*-*-*-*-iso10646-1

```
After restarting X, the menu bar fonts in EMACS became consistent with the overal look and feel of my desktop environment:)
 
P.S. I have a physical display resolution 96x96, that's why I have "96" in the above  font descriptions.

---

### Post by kassetra on 2005-02-20
Great job!  That is a great way of changing the emacs fonts.  :)  I just wish all applications that relied on gtk1 were that flexible!  :)
 
 Hmmm... I'm testing it now on VMWare... :)

---

### Post by istoyanov on 2005-02-20
[QUOTE=kassetra]Great job!  That is a great way of changing the emacs fonts.  :)  I just wish all applications that relied on gtk1 were that flexible!  :)[/QUOTE]

In fact Emacs (as compiled for Ubuntu) use the X toolkit with the Lucid menu widgets, _not_ GTK1. That's why I had such problems with getting the right font for it; but after resolving the GTK1 font-issue on my system, the EMACS menu bar font was still the same -- so I had to search in another direction... The result is already known:)

---

### Post by kassetra on 2005-02-20
ooooh wow.  well that is information I didn't know before (I'm not an emacs user)... so I'll have to tuck that information into my brain for future reference.  :)
 
 Thank you!

---

### Post by istoyanov on 2005-02-20
You're welcome!:)

---

