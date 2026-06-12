---
title: "How to uninstall GnoMenu?"
date: 2009-02-21
forum: General Help
---

### Post by solwic on 2009-02-21
SOLVED:  See below.

---

### Post by solwic on 2009-02-21
Searching for "how to uninstall GnoMenu" turned up nothing.  "How to uninstall .deb package" gave me instructions on how to use dpkg --purge, and I put that together with guessing the package names from the .deb files.  Thought I'd post so this information exists *somewhere* on the net:

Run this to get rid of this garbage:

```
sudo dpkg --purge gnomenu && sudo dpkg --purge gnomenuthemes
```

It really shouldn't be that sneaky. 

Thanks anyway.  Would mark SOLVED if I could.

EDIT:  If there's a more elegant way to combine those commands, somebody post it please.  I'm no CLI expert.  :)

---

### Post by Miaxi on 2009-02-21
sudo apt-get purge gnomenu*

;)

---

### Post by solwic on 2009-02-21
> **miaxi said:**
> sudo apt-get purge gnomenu*

;)

ty :)

---

### Post by paulsa on 2010-02-22
Hi there,
does this then revert to the default menus within the panel as it is when ubuntu is first installed?

Cheers

---

