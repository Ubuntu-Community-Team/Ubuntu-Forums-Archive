---
title: "HOWTO Turn Off Automount USB Floppy or CD ROM"
date: 2009-03-26
forum: General Help
---

### Post by timandjulz on 2009-03-26
I googled a while to figure this out and thought I would share so others wouldn't have to go through my pain.  :-)

Turn off auto mount for USB CD ROM and Floppies via gconf-editor.

$ gconf-editor

Then go to apps-nautilus-preferences and un-check "media-automount"

This works in Ubuntu 8.10

-------------
Most sites suggested uninstalling HAL and using autofs.  Personally, I think unchecking a box is easier.  :-)

Cheers,
Tim

---

