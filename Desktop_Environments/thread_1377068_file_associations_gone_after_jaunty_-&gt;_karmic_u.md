---
title: "file associations gone after jaunty -&gt; karmic upgrade"
date: 2010-01-09
forum: Desktop Environments
---

### Post by markthefart on 2010-01-09
I just upgraded to Karmic from Jaunty, and now my file associations are gone. What's more, if I open Dolphin and try to open for instance an .avi file. There's an empty open with context menu and if I choose open with... dolphin crashes. Anybody know what this might be?

---

### Post by Zorael on 2010-01-10
Try renaming (or removing) your **~/.local/share/applications** and **~/.local/share/mime** directories. Then hit Alt+F2 and run '**kbuildsycoca4**', alternatively do it from a terminal.
```
$ kbuildsycoca4
```

---

### Post by markthefart on 2010-01-10
Thanks got it :)

---

