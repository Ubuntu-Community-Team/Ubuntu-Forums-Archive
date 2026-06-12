---
title: "window borders disappear"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by rootie on 2007-11-08
Hey there, another one of those things. Window borders disappear (strangely enough) whenever I copy files from my external HD. Anyway, the first time it happened today I ran 'compiz' again (even though compiz was still running) and got this:

```
alvin@Gogo-an:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
```

Window borders reappeared; I kept the terminal window open. When I mounted the HD again and started copying, I got this error:

```
(emerald:7734): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GdkDrawable'

(emerald:7734): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed
```

After which window borders disappeared once more. Now I'm wondering if the copying does trigger the disappearance of window borders, or if I'm just going crazy =P Any help is appreciated. :)

---

### Post by Forlong on 2007-11-08
I recommend filing a bugreport at [http://bugs.opencompositing.org](http://bugs.opencompositing.org)

---

### Post by flipkick on 2008-02-14
Same here. Is there any one else having this bug ?

---

