---
title: "Devils Pie Help"
date: 2008-09-05
forum: Desktop Environments
---

### Post by skipsbro on 2008-09-05
I'm having trouble with a terminal window on devilspie, it refuses to follow the geometry rules I set for it and it will not move to the other side of the screen.

```


(if
        (matches (window_name) "DesktopMonitor")
        (begin
                (below)
                (undecorate)
                (skip_pager)
                (skip_tasklist)               
		(wintype "utility")
		(geometry "+1120")		
        )
)


```

---

