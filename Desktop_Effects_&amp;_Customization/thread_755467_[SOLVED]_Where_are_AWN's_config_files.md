---
title: "[SOLVED] Where are AWN's config files?"
date: 2008-04-14
forum: Desktop Effects &amp; Customization
---

### Post by dwasifar on 2008-04-14
How do I remove AWN's configuration files?  I have upgraded AWN from the bzr repositories and I want to start fresh without it remembering my previous configuration.  Where are the config files stored?  I tried deleting the obvious locations, ~/.config/awn and ~/.gconf/apps/avant-window-navigator, but the old configuration still keeps popping up anyway.

---

### Post by Eclipse. on 2008-04-14
AWN Is werid in the way it stores its config files, I had the same problem a while ago.

gconftool-2 --recursive-unset /apps/avant-window-navigator

Run that command in the terminal and it will reset everything, got it from the awn wiki.

---

