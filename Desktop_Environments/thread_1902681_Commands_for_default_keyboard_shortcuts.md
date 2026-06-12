---
title: "Commands for default keyboard shortcuts"
date: 2011-12-31
forum: Desktop Environments
---

### Post by Sun_Master on 2011-12-31
I'm using Ubuntu 11.04 and I'm trying to find the text command for the keyboard shortcuts that come as default. E.g Volume controls, play/pause, window/workspace management etc. For some of them I can find similar commands but I'm trying to achieve the exact same effect. I searched through gconf but it references the shortcuts by title, not by command. Is there anywhere they are actually stored? Do they even have a CLI counterpart?

---

### Post by Paddy Landau on 2012-01-01
That's an interesting question, and I'd love to have the answer because of a problem I have with one of them.

From 11.04, I believe that Gnome is gradually changing over from Gconf to Dconf. Install [dconf-tools]("apt:dconf-tools") (if you don't already have it installed), open *Configuration Editor (dconf)*, and perhaps it's in there? I don't know how to search dconf.

---

### Post by Sun_Master on 2012-01-01
I've just had a look through dconf, I can't see anything related to keyboard shortcuts. Thanks though, it did have a load of other useful options I was searching for.

---

### Post by Paddy Landau on 2012-01-01
Well, if you do come across where they're stored, let us know!

---

