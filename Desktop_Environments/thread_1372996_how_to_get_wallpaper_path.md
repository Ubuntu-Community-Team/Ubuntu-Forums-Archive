---
title: "how to get wallpaper path?"
date: 2010-01-05
forum: Desktop Environments
---

### Post by Jasonx86 on 2010-01-05
hi,

How can I view the file path to the wallpaper used in GNOME?


Thanks.

---

### Post by o1911 on 2010-01-05
Try this:

```
gconftool-2 -g /desktop/gnome/background/picture_filename
```

---

### Post by Jasonx86 on 2010-01-05
Thanks Slick.

Exactly what I needed.

---

