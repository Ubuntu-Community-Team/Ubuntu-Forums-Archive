---
title: "Fonts in XMMS's options are very small"
date: 2004-11-13
forum: Desktop Environments
---

### Post by tilko on 2004-11-13
Hi!
I recently installed xmms from universe and encountered a problem with options menu font. It is so small I hardly read the menu items. Also the options window font and warnings are very small.
This is my configuration:
screen resolution: 1600x1200
gpu: Nvidia geforce4mx
driver: nvidia glx
using gnome.

I would really appreciate your help. Thanx

lp, tilko

---

### Post by HiddenWolf on 2004-11-13
Hm, I run 1600x1200 on a 17" crt. I tend to run into similar problems once in every while.

---

### Post by nocturn on 2004-12-23
[QUOTE=HiddenWolf]Hm, I run 1600x1200 on a 17" crt. I tend to run into similar problems once in every while.[/QUOTE]


I have the same problem.  All GTK1 apps have fonts that are not readable (small), all other apps are fine.
My resolution is 1280x1024

---

### Post by Akrame on 2005-04-01
[QUOTE=nocturn]I have the same problem.  All GTK1 apps have fonts that are not readable (small), all other apps are fine.
My resolution is 1280x1024[/QUOTE]
 i ve got the same problem , if someone has the answer tell me :)

---

### Post by 1000i1 on 2005-06-01
I've found a solution to this problem that has worked for me, I've installed the following packages with apt-get:
xfonts-100dpi - 100 dpi fonts for X
xfonts-75dpi - 75 dpi fonts for X
xfonts-100dpi-transcoded - 100 dpi fonts for X (transcoded from ISO 10646-1)
xfonts-75dpi-transcoded - 75 dpi fonts for X (transcoded from ISO 10646-1)

Hope this works for you.

---

### Post by tOMky on 2006-07-05
I had the same problem and the solutions above was not enough for me. Small fonts in GTK 1 apps could be made by corrupted xorg configuration due to automatic reconfigurations of fglrx or others. You should add following lines in /etc/X11/xorg.conf in section Files:

FontPath   "/usr/share/X11/fonts/misc/"
FontPath   "/usr/share/X11/fonts/75dpi/"
FontPath   "/usr/share/X11/fonts/100dpi/"
FontPath   "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath   "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath   "/usr/share/X11/fonts/Type1/"

---

### Post by yabbadabbadont on 2006-07-05
If you install gtk-theme-switch and then run switch (for gtk1), (switch2 for gtk2), you can specify the font to be used by gtk1 applications.  I think it writes out a .gtkrc file, so you may have to rename it to .gtkrc.mine for it to take effect.

---

