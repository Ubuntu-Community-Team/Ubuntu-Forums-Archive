---
title: "Is it possible to disable compiz temporarily for games?"
date: 2016-12-08
forum: Desktop Environments
---

### Post by raptir on 2016-12-08
I love Unity for the most part but I've found that it causes a lot of slowdown, especially in OpenGL games. Is there any simple way to disable compiz (or at least, the compositing effects) in order to get a game running?

Forgot to mention, I'm in 16.10. I found some guides for older versions but the suggestions don't seem to work on 16.10.

---

### Post by raptir on 2016-12-13
Well, I figured out a way, though it is not perfect. Setting the unredirect_fullscreen_windows flag for Compiz seems to help:

```
gconftool-2 --set /apps/compizconfig-1/profiles/Default/plugins/composite/screen0/options/unredirect_fullscreen_windows --type bool 1
```

---

