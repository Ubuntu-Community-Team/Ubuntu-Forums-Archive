---
title: "icons for removable media on ALL workspaces"
date: 2008-02-08
forum: Desktop Environments
---

### Post by Haus Neuerburg on 2008-02-08
Hi
I do have a problem with the appearance of my desktop: I would love to have all removable media shown on all workspaces all the time. I ticked show icons in the nautilus section of the configurations editor but I don't see any icon! I'm using Gutsy. Does anyone have any idea? As a workaround I added the "mount volume" applet to my panel, but I'd prefer an icon.
Many thanks for any hints and regards from
Haus Neuerburg

---

### Post by renzokuken on 2008-02-08
are you sure you ticked the correct box? it should be

```
gconf-editor
```

apps -> nautilus -> desktop 

and check **volumes visible**

---

### Post by Haus Neuerburg on 2008-02-08
well, I guess so, it was this one:

[http://img219.imageshack.us/img219/7726/bildschirmfotokonfiguraoc6.png](http://img219.imageshack.us/img219/7726/bildschirmfotokonfiguraoc6.png)

but I just noticed, that files I saved o the Desktop are not shown either; where do I re-enable that, and maybe than all drives are shown again, too?
Haus

---

