---
title: "XFCE and aterm fonts"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Gentist on 2006-08-30
I'm trying to set up XFCE, and since I'm currently using aterm as my main terminal, I want to use that too. My only problem is that the font looks horrible. This isn't the case in any other WM or DE I've used, so I suppose that XFCE doesn't read the .Xresources properly.

Does anyone know how I can have XFCE use the font as specified in .Xresources?

---

### Post by croak77 on 2006-08-30
You cna specify a font in your ~/.Xdefaults. Add a line like;

```
aterm*font:                    -*-proggysquaresz-*-*-*-*-*-*-*-*-*-*-*-*
```

Change proggysquaresz to whatever you wnat. Use xfontsel to get a list of fonts.

---

