---
title: "True lxpanel transparency with compton?"
date: 2014-10-13
forum: Desktop Environments
---

### Post by Thimoteus on 2014-10-13
By default lxpanel uses fake transparency, so that you can see the wallpaper on the desktop behind the panel instead of whatever window is underneath. I want to get true transparency to show the window as well.
The closest I came was putting
```

opacity-rule = [
       "0:window_type = 'dock' && class_g = 'lxpanel'"
];

```
into my compton config file, but this makes the *entire* panel transparent, including the icons and clock.

Is there a way to set the transparency of the panel without losing the icons as well?

---

### Post by vasa1 on 2014-10-28
Bumping this (selfishly).

---

