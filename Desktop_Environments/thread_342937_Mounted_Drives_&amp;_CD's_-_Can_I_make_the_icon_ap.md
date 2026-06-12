---
title: "Mounted Drives &amp; CD's - Can I make the icon appear in the panel?"
date: 2007-01-20
forum: Desktop Environments
---

### Post by BarfBag on 2007-01-20
I found a really cool wallpaper.  Unfortunately, it looks awful with icons on top of it.  I moved all of my icons into the panel except the mounted drives.  Is it possible to get them to appear in the panel instead of on the desktop?

---

### Post by robgill on 2007-01-20
Add to panel -> disk mounter and then hide the desktop icons gconf-editor. I don't remember exactly where the option is but I found it by poking around in there for a few minutes.

---

### Post by BarfBag on 2007-01-20
> **robgill said:**
> Add to panel -> disk mounter and then hide the desktop icons gconf-editor. I don't remember exactly where the option is but I found it by poking around in there for a few minutes.

Thanks for the reply.  Disk mounter is a nice tool.  Got that working, but I don't know that "gconf-editor" is.  Can you please explain?

---

### Post by Dave Burbank on 2007-01-21
Run gconf-editor:
```
gconf-editor
```
Navigate to apps>nautilus>desktop and uncheck the icons you don't want to appear.

---

