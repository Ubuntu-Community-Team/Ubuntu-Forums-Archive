---
title: "Compiz drop shadows are opaque!"
date: 2009-11-18
forum: Desktop Environments
---

### Post by Coder543 on 2009-11-18
I have completely removed all compiz components and reinstalled them, and drop shadows are still suddenly opaque. Additionally, compiz performance has gone down the drain. Before today, all was well. I am using metacity for now, please help me! (Furthermore, I cannot use gnome-shell [gnome 3.0] because the desktop icons and wallpaper fail to draw now that compiz is dying)

Laptop: Acer Aspire One
Graphics Card: GMA950
Screen Size: 1024x600

---

### Post by Islington on 2009-11-18
wait what, afaik gnome shell doesnt use compiz at all.

run ```
compiz --replace 
``` in a terminal, is there any output?

---

### Post by Coder543 on 2009-11-18
```
coder@coder-laptop:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x600) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


```

While gnome shell doesn't.... whatever is killing compiz is killing gnome shell too.

---

