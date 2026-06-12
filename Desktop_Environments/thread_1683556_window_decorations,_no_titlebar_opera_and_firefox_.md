---
title: "window decorations, no titlebar opera and firefox when maximized?"
date: 2011-02-07
forum: Desktop Environments
---

### Post by Intsmssss on 2011-02-07
I was wondering how i could achieve this. I know about !state=maxvert but this removes the titlebars on all applications.

(any)&!(name=opera) will do this just for opera but the problem is when i unmaximize it the titlebar will still be gone.

How can i make sure that all applications will have their titlebar when maximized exept opera and firefox, and all applications inclusing these 2 have titlebars when unmaximized?

Thanks, 
David

---

### Post by Krytarik on 2011-02-07
This one should work, I tested it with Firefox:
```
!((class=Opera | class=Firefox) & state=maxvert & state=maxhorz)
```

---

### Post by Intsmssss on 2011-02-07
> **Krytarik said:**
> This one should work, I tested it with Firefox:
```
!((class=Opera | class=Firefox) & state=maxvert & state=maxhorz)
```

awesome, ty for the help

---

