---
title: "Icon paths? Crunchbang, Openbox and iDesk."
date: 2009-02-18
forum: Desktop Environments
---

### Post by casbahdk on 2009-02-18
What are the icon paths for Ubuntu Intrepid? I am using Crunchbang (Ubuntu derivative) with Openbox, trying to set some desktop icons with iDesk.

Cheers

---

### Post by snova on 2009-02-18
**/usr/share/pixmaps**, I believe.

---

### Post by casbahdk on 2009-02-19
> **snova said:**
> **/usr/share/pixmaps**, I believe.

Great. Spot on. Any chance you know the path to desktop icons? I have been looking around in /usr/share/icons/gnome/32x32/places but these are clearly too small to use on the desktop.

Cheers

---

### Post by snova on 2009-02-19
Well, I'm not entirely sure what you mean by "desktop icons", but if 32x32 is too small, try looking in **/usr/share/icons/gnome/scalable**. Icons in here are SVG images, which will scale infinitely.

---

### Post by mcduck on 2009-02-19
All icon themes are installed either in /usr/share/icons, or ~/.icons. Additional icons ad program icons are in /usr/share/pixmaps.

What icons are actually used on your desktop depends on what icon theme you have selected. And I think snova is right about desktop icons being scalable ones (when available) instead of fixed sized ones.

---

### Post by casbahdk on 2009-02-19
> **mcduck said:**
> All icon themes are installed either in /usr/share/icons, or ~/.icons. Additional icons ad program icons are in /usr/share/pixmaps.

What icons are actually used on your desktop depends on what icon theme you have selected. And I think snova is right about desktop icons being scalable ones (when available) instead of fixed sized ones.

I found a scalable "home" icon that I could export to 48 pixels, but Sound Juicer and Gwibber refuse to cooperate. There doesn't seem to be much logic as to icons used and where they reside
 :-(

---

