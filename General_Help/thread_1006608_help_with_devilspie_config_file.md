---
title: "help with devilspie config file"
date: 2008-12-09
forum: General Help
---

### Post by markp1989 on 2008-12-09
im trying to use devilspie to hold xvkbd in place, and then set openbox margins, to stop other applications from covering up the keyboard for when i convert my eee in to a tablet.

i have attached 2 screen shots, i want devilspie to keep it positioned how it is in the first screen shot, but devilspie isnt placing it properly 

here is the devilspie config file

```
(if
(matches (window_name) "xvkbd - Virtual Keyboard")
(begin
(set_workspace 1)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "+0+720")
(geometry "500x160")
)
) 
```

---

### Post by Penguin Guy on 2009-03-28
Which version of Devilspie are you using?
Does Devilspie have any effect at all or does it simply not work?

---

