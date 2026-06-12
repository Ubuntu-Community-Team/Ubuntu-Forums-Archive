---
title: "Change font colors in menu"
date: 2008-04-19
forum: Desktop Effects &amp; Customization
---

### Post by maol62 on 2008-04-19
I have downloaded and installed Darker Theme from [here]("http://www.gnome-look.org/content/show.php?content=32768&forumpage=0"). The problem is that, in the menu, the unselected entres is too dark so it is almost impossible to read theese lines. My question to you is how to change that? There are two files in the package, gtkrc and panel.rc, but I am not sure which line in one or both of theese files to change. Anyone got any ideas?

---

### Post by Genius314 on 2008-04-19
It's probably in gtkrc, not panel.rc (although that's up to the author... But I'd assume that panel.rc is just for the panels)

Look for the code in gtkrc, something like:
```
fg[NORMAL]        = "#d8d8d8"
  fg[PRELIGHT]      = "#d8d8d8"
  fg[ACTIVE]        = "#d8d8d8"
  fg[SELECTED]      = "#ffffff"
  fg[INSENSITIVE]   = "#000f14"
  
  bg[NORMAL]        = "#000f14"
  bg[PRELIGHT]      = "#0096c8"
  bg[ACTIVE]        = "#454f60"
  bg[SELECTED]      = "#0096c8"
  bg[INSENSITIVE]   = "#000f14"

  text[NORMAL]      = "#d8d8d8"
  text[PRELIGHT]    = "#d8d8d8"
  text[ACTIVE]      = "#ffffff"
  text[SELECTED]    = "#ffffff"
  text[INSENSITIVE] = "#000f14"

  base[NORMAL]      = "#333d40"
  base[PRELIGHT]    = "#0096c8"
  base[ACTIVE]      = "#607880"
  base[SELECTED]    = "#0096c8"
  base[INSENSITIVE] = "#000f14"
```

And just change the line "fg[NORMAL]   = "#xxxxxx"" to a different color.

---

### Post by tommyhakinen on 2008-04-19
> **Genius314 said:**
> It's probably in gtkrc, not panel.rc (although that's up to the author... But I'd assume that panel.rc is just for the panels)

Look for the code in gtkrc, something like:
```
fg[NORMAL]        = "#d8d8d8"
  fg[PRELIGHT]      = "#d8d8d8"
  fg[ACTIVE]        = "#d8d8d8"
  fg[SELECTED]      = "#ffffff"
  fg[INSENSITIVE]   = "#000f14"
  
  bg[NORMAL]        = "#000f14"
  bg[PRELIGHT]      = "#0096c8"
  bg[ACTIVE]        = "#454f60"
  bg[SELECTED]      = "#0096c8"
  bg[INSENSITIVE]   = "#000f14"

  text[NORMAL]      = "#d8d8d8"
  text[PRELIGHT]    = "#d8d8d8"
  text[ACTIVE]      = "#ffffff"
  text[SELECTED]    = "#ffffff"
  text[INSENSITIVE] = "#000f14"

  base[NORMAL]      = "#333d40"
  base[PRELIGHT]    = "#0096c8"
  base[ACTIVE]      = "#607880"
  base[SELECTED]    = "#0096c8"
  base[INSENSITIVE] = "#000f14"
```

And just change the line "fg[NORMAL]   = "#xxxxxx"" to a different color.

I am agree. I have been playing with the panel font color in the panel.rc. I think for the menu, it should be under gtkrc.

---

