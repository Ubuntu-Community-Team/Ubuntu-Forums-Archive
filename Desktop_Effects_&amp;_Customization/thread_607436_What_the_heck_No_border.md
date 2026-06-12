---
title: "What the heck? No border?"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by warmwaddle on 2007-11-08
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Thats what I got for starting compiz in the terminal. However, when I close the terminal the border that appeared goes away. Any help with this?

---

### Post by FuturePilot on 2007-11-08
Try pressing Alt+F2 and enter 
```
compiz --replace
```

---

### Post by blackspyder on 2007-11-09
if you use emerald as a window decorator then you will need to turn it on as well, just run this from the terminal.

```
emerald
```

---

