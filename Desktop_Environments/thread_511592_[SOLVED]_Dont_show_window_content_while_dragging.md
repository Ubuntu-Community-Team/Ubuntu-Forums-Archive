---
title: "[SOLVED] Dont show window content while dragging?"
date: 2007-07-28
forum: Desktop Environments
---

### Post by bvsingh on 2007-07-28
Is there a way for ubuntu (Feisty) to just show a border (like in Windows) while dragging?
Or is there a hack for faster windows dragging performance?

---

### Post by aysiu on 2007-07-28
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
gconftool-2 -t bool -s /apps/metacity/general/reduced_resources true
```

---

### Post by bvsingh on 2007-07-28
thanks, works well, though still a bit of flickering here and there and of course it shows the whole 'grid' rather than a rectangle...
but works...thanks

---

