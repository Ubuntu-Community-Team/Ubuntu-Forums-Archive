---
title: "Go up (hotkey) in Nautilus 3.6.2 (Gnome Shell 3.6)"
date: 2012-10-31
forum: Desktop Environments
---

### Post by lores on 2012-10-31
Hi!

Does anyone know how to re-enable the possibility to go up (and not back) in the filesystem hierarchy in the newest Nautilus 3.6.2 shipped with Gnome Shell 3.6? My original hotkey ("backspace") doesn't work any more...

Best

lores

EDIT: I've just noticed that "alt+up" does this job. Is it possible to customise this hotkey?

---

### Post by jbicha on 2012-11-12
No, Alt+Up is how you go up a directory.

---

### Post by lores on 2012-11-12
Alt+Up is rather useless because it not only incorporates two keys, but also requires two hands. Therefore, backspace (or similar) would be way better.

---

### Post by sledgeas on 2012-11-13
> **lores said:**
> Alt+Up is rather useless because it not only incorporates two keys, but also requires two hands. Therefore, backspace (or similar) would be way better.

110% agree, is there a way to make backspace work again?

---

### Post by razerraz on 2012-12-29
If you have a multimedia keyboard, the back key in it do the trick :
```
File : nautilus-window.c
#ifdef HAVE_X11_XF86KEYSYM_H
        { XF86XK_AddFavorite,   NAUTILUS_ACTION_ADD_BOOKMARK },
        { XF86XK_Favorites,     NAUTILUS_ACTION_EDIT_BOOKMARKS },
        { XF86XK_Go,            NAUTILUS_ACTION_ENTER_LOCATION },
        { XF86XK_HomePage,      NAUTILUS_ACTION_GO_HOME },
        { XF86XK_OpenURL,       NAUTILUS_ACTION_ENTER_LOCATION },
        { XF86XK_Refresh,       NAUTILUS_ACTION_RELOAD },
        { XF86XK_Reload,        NAUTILUS_ACTION_RELOAD },
        { XF86XK_Search,        NAUTILUS_ACTION_SEARCH },
        { XF86XK_Start,         NAUTILUS_ACTION_GO_HOME },
        { XF86XK_Stop,          NAUTILUS_ACTION_STOP },
        { XF86XK_ZoomIn,        NAUTILUS_ACTION_ZOOM_IN },
        { XF86XK_ZoomOut,       NAUTILUS_ACTION_ZOOM_OUT },
        { XF86XK_Back,          NAUTILUS_ACTION_BACK },
        { XF86XK_Forward,       NAUTILUS_ACTION_FORWARD }

```

---

