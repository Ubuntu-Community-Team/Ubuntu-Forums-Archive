---
title: "Problems with Kiba-dock"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by shawnlogic on 2007-09-16
hey everyone,

i tried installing kiba-dock according to this guide: [http://linuxinside.blogspot.com/2007/04/kiba-dock.html](http://linuxinside.blogspot.com/2007/04/kiba-dock.html)

installation went well, once i run kiba-dock in the terminal, i get the following error:
```
(kiba-dock:5946): Gdk-CRITICAL **: gdk_screen_get_monitor_geometry: assertion `monitor_num < GDK_SCREEN_X11 (screen)->num_monitors' failed
Error (main.c @ line 1184):
        Failed to load Plugins from '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the --plugin-path parameter.

```

does anyone kno how i can resolve this?  i'm using feisty fawn and i have compiz fusion installed.

thanks in advance.

---

### Post by Achetar on 2007-09-18
You need to install the 'kiba-plugins' package if you were using the repo (NOT RECOMMENDED) or install the plugins from the sourceforge stuff, which takes longer, but ultimately gives you the best.

---

